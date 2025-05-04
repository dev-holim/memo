### 1. 데이터 준비

```python
import pandas as pd  
import numpy as np  
  
train = pd.read_csv(f"{DATA_PATH}titanic_train.csv") # 학습데이터  
test = pd.read_csv(f"{DATA_PATH}titanic_test.csv") # 테스트 데이터  
test_target = pd.read_csv(f"{DATA_PATH}titanic_test_target.csv") # 테스트데이터 정답값
```

이하 데이터 결측치 제거 생략...

- 특성으로 사용할 변수 추가
```python
cols = ["age","sibsp","parch","fare","pclass","gender","embarked"]  
train_ft = train[cols].copy()  
test_ft = test[cols].copy() # 테스트 데이터  
train_ft.shape, test_ft.shape
```


- 범주형 변수 원핫인코딩하여 특성 추가
```python
from sklearn.preprocessing import OneHotEncoder  
cols = ['gender','embarked']  
enc = OneHotEncoder(handle_unknown = 'ignore') # 모르는 범주가 있을 경우 무시  
enc.fit(train_ft[cols])

# 학습 데이터  
tmp = pd.DataFrame(  
    enc.transform(train_ft[cols]).toarray(), # ndarray  
    columns = enc.get_feature_names_out() # 컬럼명  
)  
train_ft = pd.concat([train_ft,tmp],axis=1)  
train_ft.head()

# 테스트 데이터  
tmp = pd.DataFrame(  
    enc.transform(test_ft[cols]).toarray(),  
    columns = enc.get_feature_names_out()  
)  
test_ft = pd.concat([test_ft,tmp],axis=1)  
test_ft.head()
```

- 문자열 데이터 제거
```python
cols = ["gender","embarked"]  
train_ft = train_ft.drop(columns=cols)  
test_ft = test_ft.drop(columns=cols)
```

- Min-Max Scaling
```python
from sklearn.preprocessing import MinMaxScaler  
scaler = MinMaxScaler()  
scaler.fit(train_ft)

train_ft[train_ft.columns] = scaler.transform(train_ft) # 학습 데이터
test_ft[test_ft.columns] = scaler.transform(test_ft) # 테스트 데이터
```

- 정답 데이터
```python
target = train["survived"]
```

### 2. K-NN
> - k-최근접 이웃 알고리즘  
> - 새로운 샘플을 예측할 때 학습데이터의 K개의 가까운 이웃을 이용해서 예측  
> - 제일 가까운 데이터 포인트를 찾아서 결정하는 방식  
> - 회귀, 분류 둘다 사용 가능한 알고리즘
>![[image 25.png]]
```python
# cv 객체 생성  
from sklearn.model_selection import KFold, cross_val_score
from sklearn.neighbors import KNeighborsClassifier

cv = KFold(n_splits=5,shuffle=True, random_state=42)
model = KNeighborsClassifier(n_neighbors=10,p=2,weights = "uniform")  
scores = cross_val_score(model,train_ft,target,cv = cv ,scoring='roc_auc',n_jobs = -1)  
print(scores) # 폴드별 검증점수 리스트  
np.mean(scores) # cv 평균 점수
```

```python
from sklearn.metrics import roc_auc_score  
  
model = KNeighborsClassifier(n_neighbors=10,p=2,weights = "uniform")  
model.fit(train_ft,target) #학습 데이터 전체 다시학습  
  
# 테스트 데이터 예측 및 평가  
y_test = test_target["survived"] # 테스트셋 y값  
pred = model.predict_proba(test_ft)[:,1] # 예측  
roc_auc_score(y_test,pred) # AUC 평가
```


### 의사결정나무(Decision Tree)
> - 회귀, 분류 둘다 사용 가능한 알고리즘 
> - 여러 가지 규칙을 순차적으로 적용하면서 트리기반의 규칙을 만들어 예측하는 알고리즘
> - 쉽게 규칙들을 if else 기반으로 찾아서 예측하는 알고리즘
> - if else 기반의 규칙을 순수도를 이용하여 정한다.
> - 데이터를 분할 할때 순수도가 높아지는 방향으로 규칙을 정한다.
> - 순수도  
	  각 노드의 규칙에 의해 동일한 class가 포함되는 정도를 의미
	  부모노드의 순수도에 비해 자식노드들의 순수도가 증가하도록 노드를 형성  
> - 순수도 척도  
	  Gini와 Entropy : 둘다 0에 가까울수록 순수도가 높아 진다.  
> - Root node: 최상단에 위치
> - Decision node: 중간에 위치하는 노드(Internal node)
> - Leaf node: 최종 분류 값을 가짐

```python
# 딕셔너리를 언패킹하여 키워드 아규먼트 전달 방식으로 하이퍼파라미터 지정  
hp = {  
    "random_state" : 42,  
    "criterion" :"entropy",  
    "min_samples_split": 5 ,  
    "max_depth" : 5,  
    "min_samples_leaf" : 20,  
    "max_leaf_nodes" : None , # 제한 없음  
}  
  
model = DecisionTreeClassifier(**hp)  
scores = cross_val_score(model,train_ft,target,cv = cv ,scoring='roc_auc',n_jobs = -1)  
print(scores) # 폴드별 검증점수 리스트  
np.mean(scores) # cv 평균 점수
```


```python
model.fit(train_ft,target) #학습 데이터 전체 다시학습  
  
# 테스트 데이터 예측 및 평가  
y_test = test_target["survived"] # 테스트셋 y값  
pred = model.predict_proba(test_ft)[:,1] # 예측  
roc_auc_score(y_test,pred) # AUC 평가
```


### knn 모델과 tree 모델 예측 결과를 결합하여 성능 평가

- tree 모델 학습 및 test 데이터 예측
```python
tree = DecisionTreeClassifier(**hp)
tree.fit(train_ft,target) #학습 데이터 전체 다시학습
  
pred_tree = tree.predict_proba(test_ft)[:,1] # 예측
```

- knn 모델 학습 및 test 데이터 예측  
```python
knn = KNeighborsClassifier(n_neighbors=10,p=2,weights = "uniform")
knn.fit(train_ft,target) #학습 데이터 전체 다시학습

pred_knn = knn.predict_proba(test_ft)[:,1] # 예측
```

```python
pred = np.mean([pred_tree,pred_knn],axis=0) # 산술 평균 앙상블

# 테스트 데이터 예측 및 평가  
y_test = test_target["survived"] # 테스트셋 y값  
roc_auc_score(y_test,pred) # AUC 평가
```

### 특성 중요도 시각화

```python
import matplotlib.pyplot as plt  
import seaborn as sns  
  
model = DecisionTreeClassifier(max_depth=3,random_state=42)  
model.fit(train_ft,target)

sns.barplot(x=model.feature_importances_, y=train_ft.columns) # x 에 중요도, y 에 컬럼명 넣어서 시각화  
plt.show()
```


### 의사결정나무 모델 시각화

```python
from sklearn.tree import export_graphviz # 그래프 형태로 시각화 할수 있는 파일을 저장하는 함수  
  
params = {  
    "decision_tree": model, # 학습된 모델 객체  
    "out_file": "tree.dot", # 저장할 파일명  
    "feature_names": train_ft.columns, # 사용한 피쳐들의 컬럼명  
    "class_names": ["죽는다","산다"], # 클래스 별칭 리스트로 전달  
}  
  
export_graphviz(**params)
```

```python
import graphviz # 그래프 형태의 파일 형식을 읽어드려 시각화해주는 라이브러리  
with open("tree.dot") as f:  
    tree = graphviz.Source(f.read()) # Source 클래스에 파일객체를 넣어주면 그래프 객체가 반환된다.  
tree
```