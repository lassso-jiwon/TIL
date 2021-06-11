```python
import numpy as np
import pandas as pd
import matplotlib as mp
import matplotlib.pyplot as plt
import seaborn as sns
```

# 한글화


```python
fm = mp.font_manager.FontManager()
# 한글 지원하는 폰트명으로 재할당
# plt.rcParams['font.family'] = 'Malgun Gothic'
plt.rc('font', family='Malgun Gothic')
```

# 맥 파이썬 그래프 한글이 깨질때&마이너스 부호 사용


```python
import matplotlib
from matplotlib import font_manager, rc
import platform

if platform.system() == 'Windows':
# 윈도우인 경우
    font_name = font_manager.FontProperties(fname="c:/Windows/Fonts/malgun.ttf").get_name()
    rc('font', family=font_name)
else:    
# Mac 인 경우
    rc('font', family='AppleGothic')
    
matplotlib.rcParams['axes.unicode_minus'] = False   
#그래프에서 마이너스 기호가 표시되도록 하는 설정입니다. 
```


```python
# 데이터 불러오기
df = pd.read_csv('seoul_20200630.csv', sep ='|')
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>상가업소번호</th>
      <th>상호명</th>
      <th>지점명</th>
      <th>상권업종대분류코드</th>
      <th>상권업종대분류명</th>
      <th>상권업종중분류코드</th>
      <th>상권업종중분류명</th>
      <th>상권업종소분류코드</th>
      <th>상권업종소분류명</th>
      <th>표준산업분류코드</th>
      <th>...</th>
      <th>건물관리번호</th>
      <th>건물명</th>
      <th>도로명주소</th>
      <th>구우편번호</th>
      <th>신우편번호</th>
      <th>동정보</th>
      <th>층정보</th>
      <th>호정보</th>
      <th>경도</th>
      <th>위도</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>19964615</td>
      <td>석봉토스트</td>
      <td>NaN</td>
      <td>Q</td>
      <td>음식</td>
      <td>Q07</td>
      <td>패스트푸드</td>
      <td>Q07A10</td>
      <td>토스트전문</td>
      <td>I56192</td>
      <td>...</td>
      <td>1121510300100770047020647</td>
      <td>NaN</td>
      <td>서울특별시 광진구 자양로39길 20, (구의동)</td>
      <td>143200</td>
      <td>4992.0</td>
      <td>NaN</td>
      <td>1</td>
      <td>NaN</td>
      <td>127.088387</td>
      <td>37.549245</td>
    </tr>
    <tr>
      <th>1</th>
      <td>19977290</td>
      <td>피자마루</td>
      <td>약수점</td>
      <td>Q</td>
      <td>음식</td>
      <td>Q07</td>
      <td>패스트푸드</td>
      <td>Q07A01</td>
      <td>피자전문</td>
      <td>I56192</td>
      <td>...</td>
      <td>1114016200103720095000001</td>
      <td>현진빌딩</td>
      <td>서울특별시 중구 동호로7길 37, (신당동)</td>
      <td>100450</td>
      <td>4596.0</td>
      <td>NaN</td>
      <td>1</td>
      <td>NaN</td>
      <td>127.010861</td>
      <td>37.552153</td>
    </tr>
    <tr>
      <th>2</th>
      <td>19979960</td>
      <td>홍능갈비</td>
      <td>NaN</td>
      <td>Q</td>
      <td>음식</td>
      <td>Q01</td>
      <td>한식</td>
      <td>Q01A02</td>
      <td>갈비/삼겹살</td>
      <td>I56111</td>
      <td>...</td>
      <td>1150010300110860003013118</td>
      <td>NaN</td>
      <td>서울특별시 강서구 화곡로18길 31, (화곡동)</td>
      <td>157010</td>
      <td>7718.0</td>
      <td>NaN</td>
      <td>1</td>
      <td>NaN</td>
      <td>126.836078</td>
      <td>37.538927</td>
    </tr>
    <tr>
      <th>3</th>
      <td>19983535</td>
      <td>초밥왕</td>
      <td>NaN</td>
      <td>Q</td>
      <td>음식</td>
      <td>Q03</td>
      <td>일식/수산물</td>
      <td>Q03A03</td>
      <td>음식점-초밥전문</td>
      <td>I56113</td>
      <td>...</td>
      <td>1171010200100070028000237</td>
      <td>현대타워아파트</td>
      <td>서울특별시 송파구 올림픽로 293-19, (신천동, 현대타워아파트)</td>
      <td>138735</td>
      <td>5510.0</td>
      <td>NaN</td>
      <td>1</td>
      <td>NaN</td>
      <td>127.102490</td>
      <td>37.515149</td>
    </tr>
    <tr>
      <th>4</th>
      <td>19969945</td>
      <td>에브리돈</td>
      <td>북가좌점</td>
      <td>Q</td>
      <td>음식</td>
      <td>Q01</td>
      <td>한식</td>
      <td>Q01A01</td>
      <td>한식/백반/한정식</td>
      <td>I56111</td>
      <td>...</td>
      <td>1141011900103070003002306</td>
      <td>NaN</td>
      <td>서울특별시 서대문구 응암로 65, (북가좌동)</td>
      <td>120130</td>
      <td>3681.0</td>
      <td>NaN</td>
      <td>1</td>
      <td>NaN</td>
      <td>126.910288</td>
      <td>37.579029</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 39 columns</p>
</div>




```python
df.shape
```




    (370321, 39)




```python
# 컬럼이 총 39개임!!!!
df.columns
```




    Index(['상가업소번호', '상호명', '지점명', '상권업종대분류코드', '상권업종대분류명', '상권업종중분류코드',
           '상권업종중분류명', '상권업종소분류코드', '상권업종소분류명', '표준산업분류코드', '표준산업분류명', '시도코드',
           '시도명', '시군구코드', '시군구명', '행정동코드', '행정동명', '법정동코드', '법정동명', '지번코드',
           '대지구분코드', '대지구분명', '지번본번지', '지번부번지', '지번주소', '도로명코드', '도로명', '건물본번지',
           '건물부번지', '건물관리번호', '건물명', '도로명주소', '구우편번호', '신우편번호', '동정보', '층정보',
           '호정보', '경도', '위도'],
          dtype='object')




```python
# 39개의 컬럼 중 상권업종대분류명 만 가지고 온다!!!
set(df['상권업종대분류명'])
# 결과값이 딕셔너리로 나오넹????
```




    {'관광/여가/오락', '부동산', '생활서비스', '소매', '숙박', '스포츠', '음식', '학문/교육'}




```python
# 39개의 컬럼 중 상권업종중분류명만 가져옴
# print는 가로로 출력하려고 씀
print(set(df['상권업종중분류명']))
```

    {'유스호스텔', '운송/배달/택배', '별식/퓨전요리', '법무세무회계', '세탁/가사서비스', '이/미용/건강', '학문교육기타', '분식', '가방/신발/액세서리', '예식/의례/관혼상제', '음식배달서비스', '시계/귀금속소매', '도서관/독서실', '학원-예능취미체육', '요가/단전/마사지', '무도/유흥/가무', '건강/미용식품', '연구소', '민박/하숙', '기타판매업', '가정/주방/인테리어', '자동차/자동차용품', '학원-컴퓨터', '일식/수산물', '기타교육기관', '의약/의료품소매', '책/서적/도서', '종교용품판매', '부페', '가전제품소매', '유흥주점', '대중목욕탕/휴게', '학교', '선물/팬시/기념품', '유아용품', '캠프/별장/펜션', '광고/인쇄', '패스트푸드', '개인서비스', '운동/경기용품소매', '중식', '화장품소매', '부동산중개', '중고품소매/교환', '자동차/이륜차', '운영관리시설', '기타음식업', '양식', '학원-창업취업취미', '개인/가정용품수리', '유아교육', '사진', 'PC/오락/당구/볼링등', '부동산관련서비스', '호텔/콘도', '취미/오락관련소매', '사진/광학/정밀기기소매', '스포츠/운동', '음/식료품소매', '전시/관람', '실외운동시설', '대행업', '분양', '행사/이벤트', '철물/난방/건설자재소매', '물품기기대여', '실내운동시설', '기타서비스업', '예술품/골동품/수석/분재', '학원-음악미술무용', '평가/개발/관리', '의복의류', '인력/고용/용역알선', '사무/문구/컴퓨터', '학원기타', '학원-자격/국가고시', '커피점/카페', '한식', '연극/영화/극장', '가구소매', '주택수리', '제과제빵떡케익', '페인트/유리제품소매', '놀이/여가/취미', '장례/묘지', '주유소/충전소', '부동산임대', '종합소매점', '모텔/여관/여인숙', '애견/애완/동물', '학원-보습교습입시', '학원-어학', '닭/오리요리', '경마/경륜/성인오락'}


# 결측값


```python
# null 은 True 아니면 False 로 나옴
df.isnull()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>상가업소번호</th>
      <th>상호명</th>
      <th>지점명</th>
      <th>상권업종대분류코드</th>
      <th>상권업종대분류명</th>
      <th>상권업종중분류코드</th>
      <th>상권업종중분류명</th>
      <th>상권업종소분류코드</th>
      <th>상권업종소분류명</th>
      <th>표준산업분류코드</th>
      <th>...</th>
      <th>건물관리번호</th>
      <th>건물명</th>
      <th>도로명주소</th>
      <th>구우편번호</th>
      <th>신우편번호</th>
      <th>동정보</th>
      <th>층정보</th>
      <th>호정보</th>
      <th>경도</th>
      <th>위도</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>...</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>1</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>...</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>2</th>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>...</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>3</th>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>...</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>4</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>...</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>370316</th>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>...</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>370317</th>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>...</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>370318</th>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>...</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>370319</th>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>...</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>370320</th>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>...</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
    </tr>
  </tbody>
</table>
<p>370321 rows × 39 columns</p>
</div>




```python
# 결측치 합 구해봄
df.isnull().sum()
```




    상가업소번호            0
    상호명               0
    지점명          315822
    상권업종대분류코드         0
    상권업종대분류명          0
    상권업종중분류코드         0
    상권업종중분류명          0
    상권업종소분류코드         0
    상권업종소분류명         12
    표준산업분류코드      25266
    표준산업분류명       25266
    시도코드              0
    시도명               0
    시군구코드             0
    시군구명              0
    행정동코드             0
    행정동명              1
    법정동코드             0
    법정동명              0
    지번코드              0
    대지구분코드            0
    대지구분명             0
    지번본번지             0
    지번부번지         70637
    지번주소              0
    도로명코드             0
    도로명               0
    건물본번지             0
    건물부번지        325767
    건물관리번호            0
    건물명          191777
    도로명주소             0
    구우편번호             0
    신우편번호             2
    동정보          341396
    층정보          120053
    호정보          314429
    경도                0
    위도                0
    dtype: int64




```python
# 시도명 유니크값으로 찍어보자
df.columns
```




    Index(['상가업소번호', '상호명', '지점명', '상권업종대분류코드', '상권업종대분류명', '상권업종중분류코드',
           '상권업종중분류명', '상권업종소분류코드', '상권업종소분류명', '표준산업분류코드', '표준산업분류명', '시도코드',
           '시도명', '시군구코드', '시군구명', '행정동코드', '행정동명', '법정동코드', '법정동명', '지번코드',
           '대지구분코드', '대지구분명', '지번본번지', '지번부번지', '지번주소', '도로명코드', '도로명', '건물본번지',
           '건물부번지', '건물관리번호', '건물명', '도로명주소', '구우편번호', '신우편번호', '동정보', '층정보',
           '호정보', '경도', '위도'],
          dtype='object')




```python
# 시도명에서 unique 해보니까 '서울특별시'만 존재한다.
df['시도명'].unique()
```




    array(['서울특별시'], dtype=object)




```python
# missingno 실행 시 오류가 발생하면 외부 라이브러리를 설치해준다.
!pip install missingno
```

    Collecting missingno
      Downloading missingno-0.4.2-py3-none-any.whl (9.7 kB)
    Requirement already satisfied: seaborn in /Users/jiwon/opt/anaconda3/lib/python3.8/site-packages (from missingno) (0.11.0)
    Requirement already satisfied: matplotlib in /Users/jiwon/opt/anaconda3/lib/python3.8/site-packages (from missingno) (3.3.2)
    Requirement already satisfied: scipy in /Users/jiwon/opt/anaconda3/lib/python3.8/site-packages (from missingno) (1.5.2)
    Requirement already satisfied: numpy in /Users/jiwon/opt/anaconda3/lib/python3.8/site-packages (from missingno) (1.19.2)
    Requirement already satisfied: pandas>=0.23 in /Users/jiwon/opt/anaconda3/lib/python3.8/site-packages (from seaborn->missingno) (1.1.3)
    Requirement already satisfied: kiwisolver>=1.0.1 in /Users/jiwon/opt/anaconda3/lib/python3.8/site-packages (from matplotlib->missingno) (1.3.0)
    Requirement already satisfied: cycler>=0.10 in /Users/jiwon/opt/anaconda3/lib/python3.8/site-packages (from matplotlib->missingno) (0.10.0)
    Requirement already satisfied: pillow>=6.2.0 in /Users/jiwon/opt/anaconda3/lib/python3.8/site-packages (from matplotlib->missingno) (8.0.1)
    Requirement already satisfied: certifi>=2020.06.20 in /Users/jiwon/opt/anaconda3/lib/python3.8/site-packages (from matplotlib->missingno) (2020.6.20)
    Requirement already satisfied: python-dateutil>=2.1 in /Users/jiwon/opt/anaconda3/lib/python3.8/site-packages (from matplotlib->missingno) (2.8.1)
    Requirement already satisfied: pyparsing!=2.0.4,!=2.1.2,!=2.1.6,>=2.0.3 in /Users/jiwon/opt/anaconda3/lib/python3.8/site-packages (from matplotlib->missingno) (2.4.7)
    Requirement already satisfied: pytz>=2017.2 in /Users/jiwon/opt/anaconda3/lib/python3.8/site-packages (from pandas>=0.23->seaborn->missingno) (2020.1)
    Requirement already satisfied: six in /Users/jiwon/opt/anaconda3/lib/python3.8/site-packages (from cycler>=0.10->matplotlib->missingno) (1.15.0)
    Installing collected packages: missingno
    Successfully installed missingno-0.4.2



```python
# 결측치를 시각화할 수 있음!!!
import missingno as msno
```


```python
msno.matrix(df)
```




    <AxesSubplot:>




    
![png](output_17_1.png)
    


# 데이터 수 확인하기


```python
df['상권업종대분류명'].value_counts()
```




    음식          124001
    소매          123003
    생활서비스        64529
    학문/교육        29985
    부동산          14975
    관광/여가/오락     10454
    숙박            2971
    스포츠            403
    Name: 상권업종대분류명, dtype: int64




```python
df['상권업종중분류명'].value_counts()
```




    한식          38703
    이/미용/건강     31717
    종합소매점       25716
    의복의류        23307
    커피점/카페      18220
                ...  
    유스호스텔          14
    부동산관련서비스        4
    기타교육기관          4
    연구소             3
    학교              1
    Name: 상권업종중분류명, Length: 94, dtype: int64




```python
# 시각화해서 살펴보자!
# 그래프 크기 조정
plt.figure(figsize = (15,6))

# 그래프 그리기
sns.countplot(data=df, y='상권업종대분류명')

# x축, y축 글자 색 조정
plt.xticks(fontsize = 14, color = 'w')
plt.yticks(fontsize = 14, color = 'w')
# 음식점이 많네
```




    (array([0, 1, 2, 3, 4, 5, 6, 7]),
     [Text(0, 0, '음식'),
      Text(0, 1, '소매'),
      Text(0, 2, '생활서비스'),
      Text(0, 3, '학문/교육'),
      Text(0, 4, '관광/여가/오락'),
      Text(0, 5, '부동산'),
      Text(0, 6, '숙박'),
      Text(0, 7, '스포츠')])




    
![png](output_21_1.png)
    



```python
df_food = df.loc[df['상권업종대분류명'].str.contains('음식')]
df_food.shape
```




    (124001, 39)




```python
# 그래프 크기 조정
plt.figure(figsize = (15,6))

sns.countplot(data=df_food, y = '상권업종중분류명')

# x축, y축 글자 색 조정
plt.xticks(fontsize = 14, color = 'w')
plt.yticks(fontsize = 14, color = 'w')
```




    (array([ 0,  1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11, 12, 13]),
     [Text(0, 0, '패스트푸드'),
      Text(0, 1, '한식'),
      Text(0, 2, '일식/수산물'),
      Text(0, 3, '커피점/카페'),
      Text(0, 4, '분식'),
      Text(0, 5, '중식'),
      Text(0, 6, '양식'),
      Text(0, 7, '유흥주점'),
      Text(0, 8, '별식/퓨전요리'),
      Text(0, 9, '기타음식업'),
      Text(0, 10, '음식배달서비스'),
      Text(0, 11, '제과제빵떡케익'),
      Text(0, 12, '닭/오리요리'),
      Text(0, 13, '부페')])




    
![png](output_23_1.png)
    


# 스타벅스와 이디야


```python
df.columns
```




    Index(['상가업소번호', '상호명', '지점명', '상권업종대분류코드', '상권업종대분류명', '상권업종중분류코드',
           '상권업종중분류명', '상권업종소분류코드', '상권업종소분류명', '표준산업분류코드', '표준산업분류명', '시도코드',
           '시도명', '시군구코드', '시군구명', '행정동코드', '행정동명', '법정동코드', '법정동명', '지번코드',
           '대지구분코드', '대지구분명', '지번본번지', '지번부번지', '지번주소', '도로명코드', '도로명', '건물본번지',
           '건물부번지', '건물관리번호', '건물명', '도로명주소', '구우편번호', '신우편번호', '동정보', '층정보',
           '호정보', '경도', '위도'],
          dtype='object')




```python
dataset = df[['상호명', '지점명', '상권업종중분류명', '시도명', '시군구명', '행정동명', '도로명', '경도', '위도']]
dataset.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>상호명</th>
      <th>지점명</th>
      <th>상권업종중분류명</th>
      <th>시도명</th>
      <th>시군구명</th>
      <th>행정동명</th>
      <th>도로명</th>
      <th>경도</th>
      <th>위도</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>석봉토스트</td>
      <td>NaN</td>
      <td>패스트푸드</td>
      <td>서울특별시</td>
      <td>광진구</td>
      <td>구의2동</td>
      <td>서울특별시 광진구 자양로39길</td>
      <td>127.088387</td>
      <td>37.549245</td>
    </tr>
    <tr>
      <th>1</th>
      <td>피자마루</td>
      <td>약수점</td>
      <td>패스트푸드</td>
      <td>서울특별시</td>
      <td>중구</td>
      <td>약수동</td>
      <td>서울특별시 중구 동호로7길</td>
      <td>127.010861</td>
      <td>37.552153</td>
    </tr>
    <tr>
      <th>2</th>
      <td>홍능갈비</td>
      <td>NaN</td>
      <td>한식</td>
      <td>서울특별시</td>
      <td>강서구</td>
      <td>화곡1동</td>
      <td>서울특별시 강서구 화곡로18길</td>
      <td>126.836078</td>
      <td>37.538927</td>
    </tr>
    <tr>
      <th>3</th>
      <td>초밥왕</td>
      <td>NaN</td>
      <td>일식/수산물</td>
      <td>서울특별시</td>
      <td>송파구</td>
      <td>잠실6동</td>
      <td>서울특별시 송파구 올림픽로</td>
      <td>127.102490</td>
      <td>37.515149</td>
    </tr>
    <tr>
      <th>4</th>
      <td>에브리돈</td>
      <td>북가좌점</td>
      <td>한식</td>
      <td>서울특별시</td>
      <td>서대문구</td>
      <td>북가좌2동</td>
      <td>서울특별시 서대문구 응암로</td>
      <td>126.910288</td>
      <td>37.579029</td>
    </tr>
  </tbody>
</table>
</div>



# 커피만 가져오자


```python
df_coffee = dataset[dataset['상권업종중분류명']=='커피점/카페']
df_coffee.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>상호명</th>
      <th>지점명</th>
      <th>상권업종중분류명</th>
      <th>시도명</th>
      <th>시군구명</th>
      <th>행정동명</th>
      <th>도로명</th>
      <th>경도</th>
      <th>위도</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>9</th>
      <td>왕실</td>
      <td>NaN</td>
      <td>커피점/카페</td>
      <td>서울특별시</td>
      <td>중구</td>
      <td>명동</td>
      <td>서울특별시 중구 남대문로</td>
      <td>126.982419</td>
      <td>37.562274</td>
    </tr>
    <tr>
      <th>13</th>
      <td>커피빈</td>
      <td>코리아교대점</td>
      <td>커피점/카페</td>
      <td>서울특별시</td>
      <td>서초구</td>
      <td>서초1동</td>
      <td>서울특별시 서초구 서초중앙로</td>
      <td>127.014217</td>
      <td>37.492388</td>
    </tr>
    <tr>
      <th>15</th>
      <td>고려대학교교육관쎄리오점</td>
      <td>NaN</td>
      <td>커피점/카페</td>
      <td>서울특별시</td>
      <td>성북구</td>
      <td>안암동</td>
      <td>서울특별시 성북구 안암로</td>
      <td>127.031702</td>
      <td>37.588485</td>
    </tr>
    <tr>
      <th>18</th>
      <td>스완카페트</td>
      <td>NaN</td>
      <td>커피점/카페</td>
      <td>서울특별시</td>
      <td>영등포구</td>
      <td>대림3동</td>
      <td>서울특별시 영등포구 도신로10가길</td>
      <td>126.897710</td>
      <td>37.503693</td>
    </tr>
    <tr>
      <th>26</th>
      <td>커피빈코리아선릉로93길점</td>
      <td>코리아선릉로93길점</td>
      <td>커피점/카페</td>
      <td>서울특별시</td>
      <td>강남구</td>
      <td>역삼1동</td>
      <td>서울특별시 강남구 선릉로93길</td>
      <td>127.047883</td>
      <td>37.505675</td>
    </tr>
  </tbody>
</table>
</div>



# 상호명 확인하자


```python
# 상호명 확인해보자
df_coffee.columns
# 중복이 있을 수 있으니 유니크값 보자
```




    Index(['상호명', '지점명', '상권업종중분류명', '시도명', '시군구명', '행정동명', '도로명', '경도', '위도'], dtype='object')




```python
print(df_coffee['상호명'].unique().shape)
df_coffee['상호명'].unique
```

    (12426,)





    <bound method Series.unique of 9                    왕실
    13                  커피빈
    15         고려대학교교육관쎄리오점
    18                스완카페트
    26        커피빈코리아선릉로93길점
                  ...      
    370260              웻커피
    370261      커피인류고덕아르테온점
    370270           삼청동에그롤
    370271            할리스커피
    370297              밀스톤
    Name: 상호명, Length: 18220, dtype: object>




```python
df_coffee['상호명'].value_counts()
```




    간단하지만특별한화피디Cafe    1198
    이디야커피               338
    스타벅스                303
    커피빈                 146
    투썸플레이스              119
                       ... 
    스타벅스커피가산그레이트          1
    스타벅스황학사거리점            1
    더치앤빈가산디폴리스점           1
    티렉스                   1
    카페리엔                  1
    Name: 상호명, Length: 12426, dtype: int64




```python
df_coffee.loc[df_coffee['상호명'].str.contains('스타벅스|starbucks|STARBUCKS'), '상호명'].shape
```




    (506,)




```python
df_coffee.loc[df_coffee['상호명'].str.contains('이디야|ediya|EDIYA'), '상호명'].shape
```




    (432,)



# 스타벅스 이름이 들어간 상호명 출력


```python
df_coffee.loc[df_coffee['상호명'].str.contains('스타벅스|starbucks|STARBUCKS'), '상호명'].unique()
```




    array(['스타벅스', '스타벅스종로3가점', '스타벅스커피여의도IFC1F', '스타벅스신림사거리점', '스타벅스커피홍대역',
           '스타벅스새문안로점', '스타벅스올림픽평화의문점', '스타벅스가락시장역점', '스타벅스외대점', '스타벅스연신내역',
           '스타벅스연세백양로점', '스타벅스석촌역', '스타벅스연대동문', '스타벅스명지대점', '스타벅스압구정로데오역',
           '스타벅스신림점', '스타벅스사당점', '스타벅스강남삼성타운점', '스타벅스서울대입구역점', '스타벅스명동미래',
           '스타벅스건국클래식점', '스타벅스신촌명물거리점', '스타벅스광장점', '스타벅스커피여의도호성',
           '스타벅스올림픽공원북문점', '스타벅스삼선교점', '스타벅스연희DT점', '스타벅스충정타워', '스타벅스종각점',
           '스타벅스이수역점', '스타벅스방배카페입구', '스타벅스W-MALL점', '스타벅스마포일진빌딩점',
           '스타벅스천호로데오점', '스타벅스용산역점', '스타벅스중계역점', '스타벅스명동메트로', '스타벅스마포아크로타워점',
           '스타벅스중랑구청점', '스타벅스남부터미널2점', '스타벅스구로디지털로점', '스타벅스종로관수점', '스타벅스논현힐탑',
           '스타벅스삼성도심공항점', '스타벅스선정릉역점', '스타벅스종로2가점', '스타벅스미아역점', '스타벅스선릉로점',
           '스타벅스명동역', '스타벅스역삼럭키', '스타벅스커피신도림디큐브시티B2', '스타벅스이태원거리점',
           '스타벅스구로에이스트윈타워1점', '스타벅스교대역점', '스타벅스을지로입구', '스타벅스서울중앙우체국점',
           '스타벅스명일이마트점', '스타벅스조선호텔후문', '스타벅스목동점', '스타벅스구로하이엔드점', '스타벅스삼성교점',
           '스타벅스남산스테이트', '스타벅스서울교대점', '스타벅스커리학동사거리점', '스타벅스강북구청사거리점',
           '스타벅스방이역점', '스타벅스청담사거리점', '스타벅스서초파라곤점', '스타벅스종로평창', '스타벅스신압구정점',
           '스타벅스명동중앙로', '스타벅스올림픽공원남문점', '스타벅스강변역점', '스타벅스광화문역점', '스타벅스세종로점',
           '스타벅스서소문배재', '스타벅스커피가산그레이트', '스타벅스여의도점', '스타벅스경복궁역', '스타벅스차병원사거리',
           '스타벅스예술의전당점', '스타벅스을지로센타', '스타벅스중랑역점', '스타벅스학여울점', '스타벅스사당로데오점',
           '스타벅스상봉역점', '스타벅스구파발역점', '스타벅스신천역점', '스타벅스숙대입구역점', '스타벅스가든파이브',
           '스타벅스동교삼거리점', '스타벅스커피가산브이타워', '스타벅스커피신도림디큐브시티2F', '스타벅스차병원사거리점',
           '스타벅스뱅뱅사거리점', '스타벅스석촌서호점', '스타벅스경복아파트점', '스타벅스동교점',
           'STARBUCKSCOFFEE', '스타벅스월계이마트점', '스타벅스신촌점', '스타벅스광화문점', '스타벅스구산역점',
           '스타벅스숭실대점', '스타벅스상일동점', '스타벅스대치점', '스타벅스광운대점', '스타벅스합정메세나몰점',
           '스타벅스목동5단지점', '스타벅스역삼역점', '스타벅스석촌호수점', '스타벅스상암DMC센트럴몰점',
           '스타벅스청량리역점', '스타벅스홍대갤러리점', '스타벅스홍대삼거리점', '스타벅스삼청동점', '스타벅스서소문배재점',
           '스타벅스숙대점', '스타벅스송파사거리점', '스타벅스길동사거리점', '스타벅스한성대입구역점', '스타벅스잠실점',
           '스타벅스가산디지털단지점', '스타벅스오목교역점', '스타벅스금천독산점', '스타벅스노원케이티점',
           '스타벅스고대프라자점', '스타벅스황학캐슬점', '스타벅스코엑스사거리점', '스타벅스명동역점',
           '스타벅스압구정로데오역점', '스타벅스월드컵경기장점', '스타벅스강남에비뉴점', '스타벅스연신내역점',
           '스타벅스상암디지털큐브점상암디지털큐브점', '스타벅스명동길점', '스타벅스방배카페입구점', '스타벅스마포트라팰점',
           '스타벅스엔터식스한양대점', '스타벅스종로수송점', '스타벅스미아사거리역점', '스타벅스소공로북창점',
           '스타벅스포스코사거리점', '스타벅스신설동역점', '스타벅스화곡동점', '스타벅스종암점', '스타벅스서교동사거리점',
           '스타벅스역삼럭키점', '스타벅스동묘앞역점동묘앞역점', '스타벅스둔촌동점', '스타벅스청계산입구역점',
           '스타벅스송파방이DT점', '스타벅스숭실대입구역점', '스타벅스염창역점', '스타벅스마포이마트점', '스타벅스약수역점',
           '스타벅스회현역점', '스타벅스명동입구점', '스타벅스대치은마사거리점', '스타벅스대치사거리점',
           '스타벅스영등포신길DT점', '스타벅스충정타워점', '스타벅스중구저동점', '스타벅스신촌오거리점', '스타벅스강동역점',
           '스타벅스합정점', '스타벅스압구정점', '스타벅스가산디지털단지역점', '스타벅스낙성대DT점', '스타벅스성신여대정문',
           '스타벅스한남동점', '스타벅스커피마포염리', '스타벅스화곡DT점', '스타벅스강남우성점', '스타벅스양천향교역점',
           '스타벅스송파구청점', '스타벅스양천향교역', '스타벅스신사가로수점', '스타벅스신세계본점', '스타벅스청담영동대로점',
           '스타벅스서울대역점', '스타벅스서강광흥창역점', '스타벅스경희대삼거리점', '스타벅스신세계본점5F',
           '스타벅스문정역점', '스타벅스황학사거리점', '스타벅스문정하비오점', '스타벅스송파위례점',
           '스타벅스구로디지털타워점', '스타벅스외대정문점', '스타벅스공릉역점', '스타벅스이수역사거리점',
           '스타벅스잠실대교남단점', '스타벅스커피강남대로신사', '스타벅스강남점', '스타벅스신도림점', '스타벅스역점',
           '스타벅스강남오거리점', '스타벅스마곡나루역점', '스타벅스노원마들역점', '스타벅스신대방삼거리역점', '스타벅스공덕',
           '스타벅스방화DT'], dtype=object)



# 이디야가 들어간 상호명 출력


```python
df_coffee.loc[df_coffee['상호명'].str.contains('이디야|ediya|EDIYA'), '상호명'].unique()
```




    array(['이디야커피', '이디야IBK고객센터', '이디야서대문점2호', 'EDIYA커피', '이디야커피전농뉴타운점',
           '이디야커피자양동점', '이디야커피은행나무사거리점', '이디야커피마포KCC점', '이디야커피천호현대점',
           '이디야커피연구소', '이디야커피동소문동점', '이디야커피전문점', '이디야커피세광교회점', '이디야마들역',
           '이디야커피봉천역점', '이디야커피신도림테크노마트', '이디야커피점', '이디야역삼플래티넘', '이디야커피망우점',
           'EDIYACOFFEE', '부일이디야커피', 'EDIYACOFFEESHOP', '이디야에스프레소',
           '이디야커피경희대점', '이디야커피청계천점', '이디야커피애오개역점', '이디야커피자양사거리점', '이디야커피용두점',
           '이디야커피낙원동점', '이디야커피양재AT점', '이디야커피강남역지하상가점', '이디야커피봉천중앙점',
           '이디야커피가든파이브', '이디야카페', '이디야커피신림중앙점', '이디야커피수유역점', '이디야커피약수점',
           '이디야커피을지로역점', '이디야커피김안과점', '이디야커피한성대역점2층', '이디야커피삼성봉은사로점',
           'EDIYA카페', 'ediyacoffee', '이디야커피정릉아리랑점', '이디야커피한국수출입은행점',
           '이디야커피디지털미디어시티역사점', '이디야커피일원동점', '이디야커피신금호역점', '이디야커피영등포본동점',
           '이디야커피광산사거리점', '이디야커피신길썬프라자점', '이디야커피도봉산역사점', '이디야커피신당중앙점',
           '이디야커피중곡대원점', '이디야커피논골사거리점', '이디야커피개봉북부점', '이디야커피돈암아리랑점',
           '이디야커피사당역점', '이디야커피텐즈힐점', '이디야커피마곡역점', '이디야커피마곡엠밸리점',
           '이디야커피신림문화교점', '이디야커피창신중앙점', '이디야커피한강공원로점', '이디야커피등촌동점',
           '이디야커피건대스타시티점', '이디야커피가좌역점', '이디야커피선정릉역점', '이디야불광역', '이디야을지로3가',
           '이디야충무로3가', '서아이디야', '이디야당산', '이디야잠실', '이디야커피신림남부초교점', '이디야역삼역',
           '이디야삼성', '을지사거리이디야커피숍', '이디야커피우장산동점', '이디야커피문정현대시티몰점', '이디야노원사거리',
           '이디야신사역', '이디야사러가', '엠케이이디야마곡나루역점', '마스터키이디야마곡나루역점'], dtype=object)




```python
# 스타벅스 데이터 뽑아온다
df_seoul_starbucks = df_coffee[df_coffee['상호명'].str.contains('스타벅스|starbucks|STARBUCKS')]
df_seoul_starbucks.shape
```




    (506, 9)




```python
df_seoul_starbucks.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>상호명</th>
      <th>지점명</th>
      <th>상권업종중분류명</th>
      <th>시도명</th>
      <th>시군구명</th>
      <th>행정동명</th>
      <th>도로명</th>
      <th>경도</th>
      <th>위도</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>752</th>
      <td>스타벅스</td>
      <td>이태원점</td>
      <td>커피점/카페</td>
      <td>서울특별시</td>
      <td>용산구</td>
      <td>이태원1동</td>
      <td>서울특별시 용산구 이태원로</td>
      <td>126.994781</td>
      <td>37.534303</td>
    </tr>
    <tr>
      <th>1406</th>
      <td>스타벅스종로3가점</td>
      <td>종로3가점</td>
      <td>커피점/카페</td>
      <td>서울특별시</td>
      <td>종로구</td>
      <td>종로1.2.3.4가동</td>
      <td>서울특별시 종로구 종로</td>
      <td>126.990207</td>
      <td>37.570585</td>
    </tr>
    <tr>
      <th>1875</th>
      <td>스타벅스</td>
      <td>신사2점</td>
      <td>커피점/카페</td>
      <td>서울특별시</td>
      <td>서초구</td>
      <td>잠원동</td>
      <td>서울특별시 서초구 강남대로</td>
      <td>127.019763</td>
      <td>37.513663</td>
    </tr>
    <tr>
      <th>9952</th>
      <td>스타벅스커피여의도IFC1F</td>
      <td>NaN</td>
      <td>커피점/카페</td>
      <td>서울특별시</td>
      <td>영등포구</td>
      <td>여의동</td>
      <td>서울특별시 영등포구 국제금융로</td>
      <td>126.924863</td>
      <td>37.525172</td>
    </tr>
    <tr>
      <th>9957</th>
      <td>스타벅스</td>
      <td>삼성역점</td>
      <td>커피점/카페</td>
      <td>서울특별시</td>
      <td>강남구</td>
      <td>삼성1동</td>
      <td>서울특별시 강남구 테헤란로103길</td>
      <td>127.063878</td>
      <td>37.510038</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 이디야 데이터 뽑아온다
df_seoul_edi = df_coffee[df_coffee['상호명'].str.contains('이디야|ediya|EDIYA')]
df_seoul_edi.shape
```




    (432, 9)




```python
df_seoul_edi.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>상호명</th>
      <th>지점명</th>
      <th>상권업종중분류명</th>
      <th>시도명</th>
      <th>시군구명</th>
      <th>행정동명</th>
      <th>도로명</th>
      <th>경도</th>
      <th>위도</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1153</th>
      <td>이디야커피</td>
      <td>신길역점</td>
      <td>커피점/카페</td>
      <td>서울특별시</td>
      <td>영등포구</td>
      <td>신길1동</td>
      <td>서울특별시 영등포구 영등포로</td>
      <td>126.918062</td>
      <td>37.515118</td>
    </tr>
    <tr>
      <th>1981</th>
      <td>이디야커피</td>
      <td>이마트구로점</td>
      <td>커피점/카페</td>
      <td>서울특별시</td>
      <td>구로구</td>
      <td>구로3동</td>
      <td>서울특별시 구로구 디지털로32길</td>
      <td>126.897870</td>
      <td>37.484385</td>
    </tr>
    <tr>
      <th>5352</th>
      <td>이디야커피</td>
      <td>중계롯데우성점</td>
      <td>커피점/카페</td>
      <td>서울특별시</td>
      <td>노원구</td>
      <td>중계1동</td>
      <td>서울특별시 노원구 노원로22길</td>
      <td>127.072754</td>
      <td>37.646364</td>
    </tr>
    <tr>
      <th>9359</th>
      <td>이디야커피</td>
      <td>금호역점</td>
      <td>커피점/카페</td>
      <td>서울특별시</td>
      <td>성동구</td>
      <td>금호2.3가동</td>
      <td>서울특별시 성동구 장터길</td>
      <td>127.017791</td>
      <td>37.548427</td>
    </tr>
    <tr>
      <th>10176</th>
      <td>이디야커피</td>
      <td>NaN</td>
      <td>커피점/카페</td>
      <td>서울특별시</td>
      <td>강남구</td>
      <td>대치2동</td>
      <td>서울특별시 강남구 테헤란로104길</td>
      <td>127.064790</td>
      <td>37.508585</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 스타벅스와 이디야 데이터 뽑아오기
df_coffee_star_edi = df_coffee[df_coffee['상호명'].str.contains('스타벅스|starbucks|STARBUCKS|이디야|ediya|EDIYA')].copy()
df_coffee_star_edi.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>상호명</th>
      <th>지점명</th>
      <th>상권업종중분류명</th>
      <th>시도명</th>
      <th>시군구명</th>
      <th>행정동명</th>
      <th>도로명</th>
      <th>경도</th>
      <th>위도</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>752</th>
      <td>스타벅스</td>
      <td>이태원점</td>
      <td>커피점/카페</td>
      <td>서울특별시</td>
      <td>용산구</td>
      <td>이태원1동</td>
      <td>서울특별시 용산구 이태원로</td>
      <td>126.994781</td>
      <td>37.534303</td>
    </tr>
    <tr>
      <th>1153</th>
      <td>이디야커피</td>
      <td>신길역점</td>
      <td>커피점/카페</td>
      <td>서울특별시</td>
      <td>영등포구</td>
      <td>신길1동</td>
      <td>서울특별시 영등포구 영등포로</td>
      <td>126.918062</td>
      <td>37.515118</td>
    </tr>
    <tr>
      <th>1406</th>
      <td>스타벅스종로3가점</td>
      <td>종로3가점</td>
      <td>커피점/카페</td>
      <td>서울특별시</td>
      <td>종로구</td>
      <td>종로1.2.3.4가동</td>
      <td>서울특별시 종로구 종로</td>
      <td>126.990207</td>
      <td>37.570585</td>
    </tr>
    <tr>
      <th>1875</th>
      <td>스타벅스</td>
      <td>신사2점</td>
      <td>커피점/카페</td>
      <td>서울특별시</td>
      <td>서초구</td>
      <td>잠원동</td>
      <td>서울특별시 서초구 강남대로</td>
      <td>127.019763</td>
      <td>37.513663</td>
    </tr>
    <tr>
      <th>1981</th>
      <td>이디야커피</td>
      <td>이마트구로점</td>
      <td>커피점/카페</td>
      <td>서울특별시</td>
      <td>구로구</td>
      <td>구로3동</td>
      <td>서울특별시 구로구 디지털로32길</td>
      <td>126.897870</td>
      <td>37.484385</td>
    </tr>
  </tbody>
</table>
</div>



# 브랜드명 컬럼 추가하기


```python
# 상호명에 스타벅스가 포함된 것에 브랜드 컬럼을 추가하고 '스타벅스'를 저장한다.
df_coffee_star_edi.loc[df_coffee_star_edi['상호명'].str.contains('스타벅스|starbucks|STARBUCKS'), '브랜드명'] = '스타벅스'
df_coffee_star_edi.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>상호명</th>
      <th>지점명</th>
      <th>상권업종중분류명</th>
      <th>시도명</th>
      <th>시군구명</th>
      <th>행정동명</th>
      <th>도로명</th>
      <th>경도</th>
      <th>위도</th>
      <th>브랜드명</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>752</th>
      <td>스타벅스</td>
      <td>이태원점</td>
      <td>커피점/카페</td>
      <td>서울특별시</td>
      <td>용산구</td>
      <td>이태원1동</td>
      <td>서울특별시 용산구 이태원로</td>
      <td>126.994781</td>
      <td>37.534303</td>
      <td>스타벅스</td>
    </tr>
    <tr>
      <th>1153</th>
      <td>이디야커피</td>
      <td>신길역점</td>
      <td>커피점/카페</td>
      <td>서울특별시</td>
      <td>영등포구</td>
      <td>신길1동</td>
      <td>서울특별시 영등포구 영등포로</td>
      <td>126.918062</td>
      <td>37.515118</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1406</th>
      <td>스타벅스종로3가점</td>
      <td>종로3가점</td>
      <td>커피점/카페</td>
      <td>서울특별시</td>
      <td>종로구</td>
      <td>종로1.2.3.4가동</td>
      <td>서울특별시 종로구 종로</td>
      <td>126.990207</td>
      <td>37.570585</td>
      <td>스타벅스</td>
    </tr>
    <tr>
      <th>1875</th>
      <td>스타벅스</td>
      <td>신사2점</td>
      <td>커피점/카페</td>
      <td>서울특별시</td>
      <td>서초구</td>
      <td>잠원동</td>
      <td>서울특별시 서초구 강남대로</td>
      <td>127.019763</td>
      <td>37.513663</td>
      <td>스타벅스</td>
    </tr>
    <tr>
      <th>1981</th>
      <td>이디야커피</td>
      <td>이마트구로점</td>
      <td>커피점/카페</td>
      <td>서울특별시</td>
      <td>구로구</td>
      <td>구로3동</td>
      <td>서울특별시 구로구 디지털로32길</td>
      <td>126.897870</td>
      <td>37.484385</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 상호명에 스타벅스가 포함된 것에 브랜드 컬럼을 추가하고 '이디야'를 저장한다.
df_coffee_star_edi.loc[df_coffee_star_edi['상호명'].str.contains('이디야|ediya|EDIYA'), '브랜드명'] = '이디야'
df_coffee_star_edi.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>상호명</th>
      <th>지점명</th>
      <th>상권업종중분류명</th>
      <th>시도명</th>
      <th>시군구명</th>
      <th>행정동명</th>
      <th>도로명</th>
      <th>경도</th>
      <th>위도</th>
      <th>브랜드명</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>752</th>
      <td>스타벅스</td>
      <td>이태원점</td>
      <td>커피점/카페</td>
      <td>서울특별시</td>
      <td>용산구</td>
      <td>이태원1동</td>
      <td>서울특별시 용산구 이태원로</td>
      <td>126.994781</td>
      <td>37.534303</td>
      <td>스타벅스</td>
    </tr>
    <tr>
      <th>1153</th>
      <td>이디야커피</td>
      <td>신길역점</td>
      <td>커피점/카페</td>
      <td>서울특별시</td>
      <td>영등포구</td>
      <td>신길1동</td>
      <td>서울특별시 영등포구 영등포로</td>
      <td>126.918062</td>
      <td>37.515118</td>
      <td>이디야</td>
    </tr>
    <tr>
      <th>1406</th>
      <td>스타벅스종로3가점</td>
      <td>종로3가점</td>
      <td>커피점/카페</td>
      <td>서울특별시</td>
      <td>종로구</td>
      <td>종로1.2.3.4가동</td>
      <td>서울특별시 종로구 종로</td>
      <td>126.990207</td>
      <td>37.570585</td>
      <td>스타벅스</td>
    </tr>
    <tr>
      <th>1875</th>
      <td>스타벅스</td>
      <td>신사2점</td>
      <td>커피점/카페</td>
      <td>서울특별시</td>
      <td>서초구</td>
      <td>잠원동</td>
      <td>서울특별시 서초구 강남대로</td>
      <td>127.019763</td>
      <td>37.513663</td>
      <td>스타벅스</td>
    </tr>
    <tr>
      <th>1981</th>
      <td>이디야커피</td>
      <td>이마트구로점</td>
      <td>커피점/카페</td>
      <td>서울특별시</td>
      <td>구로구</td>
      <td>구로3동</td>
      <td>서울특별시 구로구 디지털로32길</td>
      <td>126.897870</td>
      <td>37.484385</td>
      <td>이디야</td>
    </tr>
  </tbody>
</table>
</div>




```python
df_coffee_star_edi['브랜드명'].value_counts()
```




    스타벅스    506
    이디야     432
    Name: 브랜드명, dtype: int64



# 지도에 그려서 확인하기


```python
geo_df_coffee = df_coffee_star_edi
```


```python
# folium 설치하기
# !pip install folium
```

    Collecting folium
      Downloading folium-0.12.1-py2.py3-none-any.whl (94 kB)
    [K     |████████████████████████████████| 94 kB 2.2 MB/s eta 0:00:011
    [?25hRequirement already satisfied: numpy in /Users/jiwon/opt/anaconda3/lib/python3.8/site-packages (from folium) (1.19.2)
    Requirement already satisfied: requests in /Users/jiwon/opt/anaconda3/lib/python3.8/site-packages (from folium) (2.24.0)
    Collecting branca>=0.3.0
      Downloading branca-0.4.2-py3-none-any.whl (24 kB)
    Requirement already satisfied: jinja2>=2.9 in /Users/jiwon/opt/anaconda3/lib/python3.8/site-packages (from folium) (2.11.2)
    Requirement already satisfied: urllib3!=1.25.0,!=1.25.1,<1.26,>=1.21.1 in /Users/jiwon/opt/anaconda3/lib/python3.8/site-packages (from requests->folium) (1.25.11)
    Requirement already satisfied: certifi>=2017.4.17 in /Users/jiwon/opt/anaconda3/lib/python3.8/site-packages (from requests->folium) (2020.6.20)
    Requirement already satisfied: chardet<4,>=3.0.2 in /Users/jiwon/opt/anaconda3/lib/python3.8/site-packages (from requests->folium) (3.0.4)
    Requirement already satisfied: idna<3,>=2.5 in /Users/jiwon/opt/anaconda3/lib/python3.8/site-packages (from requests->folium) (2.10)
    Requirement already satisfied: MarkupSafe>=0.23 in /Users/jiwon/opt/anaconda3/lib/python3.8/site-packages (from jinja2>=2.9->folium) (1.1.1)
    Installing collected packages: branca, folium
    Successfully installed branca-0.4.2 folium-0.12.1



```python
import folium
```


```python
map = folium.Map(location=[geo_df_coffee['위도'].mean(), 
                           geo_df_coffee['경도'].mean()],
                           zoom_start=12, tiles='Stamen Toner')

for n in geo_df_coffee.index:
    # 팝업에 들어갈 텍스를 지정해 준다.
    popup_name = geo_df_coffee.loc[n,'상호명'] + ' - '\
    + geo_df_coffee.loc[n,'도로명']
    
    # 브랜드명에 따라 아이콘 색상을 다르게 준다.
    if geo_df_coffee.loc[n,'브랜드명']=='스타벅스':
        icon_color = 'green'
    else:
        icon_color = 'blue'
    
    
    folium.CircleMarker(
         location=[geo_df_coffee.loc[n,'위도'],geo_df_coffee.loc[n,'경도']],
         radius =3,
         popup = popup_name,
         color=icon_color,
         fill = True,
         fill_color=icon_color     
         
    ).add_to(map)
```


```python
map
```








```python
# 지도 html 파일로 저장하기
map.save('./df_coffee.html')
```

# 서울시 구 별 스타벅스, 이디야 수


```python
df_coffee_brand = pd.DataFrame(df_coffee_star_edi.groupby(['시군구명', '브랜드명'])['상호명'].count()).reset_index()
df_coffee_brand.columns = ['구', '브랜드명', '매장수']
df_coffee_brand.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>구</th>
      <th>브랜드명</th>
      <th>매장수</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>강남구</td>
      <td>스타벅스</td>
      <td>85</td>
    </tr>
    <tr>
      <th>1</th>
      <td>강남구</td>
      <td>이디야</td>
      <td>40</td>
    </tr>
    <tr>
      <th>2</th>
      <td>강동구</td>
      <td>스타벅스</td>
      <td>12</td>
    </tr>
    <tr>
      <th>3</th>
      <td>강동구</td>
      <td>이디야</td>
      <td>10</td>
    </tr>
    <tr>
      <th>4</th>
      <td>강북구</td>
      <td>스타벅스</td>
      <td>5</td>
    </tr>
  </tbody>
</table>
</div>




```python
# x = 구, y = 매장 수 hue = 브랜드명 으로 그래프 만들기
plt.figure(figsize=(24, 6))
sns.barplot(data=df_coffee_brand, x = '구', y='매장수', hue='브랜드명')

# x축, y축 글자 색 조정
plt.xticks(fontsize = 14, color = 'w')
plt.yticks(fontsize = 14, color = 'w')
```




    (array([ 0., 10., 20., 30., 40., 50., 60., 70., 80., 90.]),
     [Text(0, 0, ''),
      Text(0, 0, ''),
      Text(0, 0, ''),
      Text(0, 0, ''),
      Text(0, 0, ''),
      Text(0, 0, ''),
      Text(0, 0, ''),
      Text(0, 0, ''),
      Text(0, 0, ''),
      Text(0, 0, '')])




    
![png](output_57_1.png)
    



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