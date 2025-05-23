### 데이터 불러오기
```python
import pandas as pd  
import numpy as np  

# 학습데이터(고객 개인정보)
train_customer = pd.read_csv(f"{DATA_PATH}credit_customer_train.csv")
# 학습데이터(고객의 카드값 변제 내역)
train_payment = pd.read_csv(f"{DATA_PATH}credit_payment_train.csv")
# 테스트데이터(고객 개인정보)
test_customer = pd.read_csv(f"{DATA_PATH}credit_customer_test.csv")
# 테스트데이터(고객의 카드값 변제 내역)
test_payment = pd.read_csv(f"{DATA_PATH}credit_payment_test.csv")
```

- 하나의 샘플이 여러 개의 행으로 구성된 데이터 집계하여 피쳐 생성
```python
agg_dict = {"연체횟수유형1":"sum"}  
# 집계 > 컬럼명변경 > groupby 기준컬럼 컬럼데이터로 변경  
tmp = train_payment.groupby("고객ID").agg(agg_dict).add_suffix("_sum").reset_index()
```

- 추출한 피쳐 merge
```python
pd.merge(train_customer,tmp,how="left",on="고객ID")
```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```