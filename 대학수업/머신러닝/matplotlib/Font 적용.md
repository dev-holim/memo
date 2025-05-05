- 코랩에서 적용
```python
import matplotlib  
from matplotlib import font_manager  
  
!sudo apt-get install -y fonts-nanum  
!sudo fc-cache -fv  
  
fontpaths = ["/usr/share/fonts/truetype/nanum/"]  
font_files = font_manager.findSystemFonts(fontpaths=fontpaths)  
  
for ff in font_files:  
    font_manager.fontManager.addfont(ff)  
  
matplotlib.rc('font', family="NanumGothic")  
matplotlib.rcParams['axes.unicode_minus'] = False
```


- 서버에서 적용
```python
import matplotlib.pyplot as plt  
import matplotlib.font_manager as fm  
import os  
  
current_dir = os.getcwd()  
path = f'{current_dir}/src/font/NotoSansKR-Bold.otf'  
font_nanum = fm.FontProperties(fname=path)  
  
plt.figure(figsize=(16,4))  
plt.bar(sum_by_channel['channel_title'], sum_by_channel['views'], color='skyblue')  
plt.xlabel('channel_title')  
plt.ylabel('views')  
plt.title('채널별 조회수 합계', size=15, fontproperties=font_nanum)  
plt.xticks(rotation=45, size=6, fontproperties=font_nanum)  
plt.show()
```