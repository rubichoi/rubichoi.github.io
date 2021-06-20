---
layout: single
title:  "데이터 분석 실습_insurance"
---



```python
import pandas as pd

from pandas import Series, DataFrame

import numpy as np
np.random.seed(12345)
import matplotlib.pyplot as plt
plt.rc('figure', figsize=(10, 6))
PREVIOUS_MAX_ROWS = pd.options.display.max_rows
pd.options.display.max_rows = 20
np.set_printoptions(precision=4, suppress=True)
```

### 1. 데이터 로딩: pd.read_csv()

 'datasets/exercise/insurance.csv'파일 읽어서 df에 할당하기


```python
df = pd.read_csv('insurance.csv')
```


```python
df = pd.read_csv('datasets/exercise/insurance.csv')
```

### 2. df의 상위 5개 항목 출력


```python
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
      <th>age</th>
      <th>sex</th>
      <th>bmi</th>
      <th>children</th>
      <th>smoker</th>
      <th>region</th>
      <th>charges</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>19</td>
      <td>female</td>
      <td>27.900</td>
      <td>0</td>
      <td>yes</td>
      <td>southwest</td>
      <td>16884.92400</td>
    </tr>
    <tr>
      <th>1</th>
      <td>18</td>
      <td>male</td>
      <td>33.770</td>
      <td>1</td>
      <td>no</td>
      <td>southeast</td>
      <td>1725.55230</td>
    </tr>
    <tr>
      <th>2</th>
      <td>28</td>
      <td>male</td>
      <td>33.000</td>
      <td>3</td>
      <td>no</td>
      <td>southeast</td>
      <td>4449.46200</td>
    </tr>
    <tr>
      <th>3</th>
      <td>33</td>
      <td>male</td>
      <td>22.705</td>
      <td>0</td>
      <td>no</td>
      <td>northwest</td>
      <td>21984.47061</td>
    </tr>
    <tr>
      <th>4</th>
      <td>32</td>
      <td>male</td>
      <td>28.880</td>
      <td>0</td>
      <td>no</td>
      <td>northwest</td>
      <td>3866.85520</td>
    </tr>
  </tbody>
</table>
</div>




```python
def seperate():
    if insurance['bmi']>=30:
        print('비만')
    elif insurance['bmi']>=25:
        print('과체중')
    else:
        print('정상')

df['구분'] = 
```

### 3. df의 요약(평균, 4분위수, 전체 갯수 등)


```python
df.describe()
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
      <th>age</th>
      <th>bmi</th>
      <th>children</th>
      <th>charges</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>1338.000000</td>
      <td>1338.000000</td>
      <td>1338.000000</td>
      <td>1338.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>39.207025</td>
      <td>30.663397</td>
      <td>1.094918</td>
      <td>13270.422265</td>
    </tr>
    <tr>
      <th>std</th>
      <td>14.049960</td>
      <td>6.098187</td>
      <td>1.205493</td>
      <td>12110.011237</td>
    </tr>
    <tr>
      <th>min</th>
      <td>18.000000</td>
      <td>15.960000</td>
      <td>0.000000</td>
      <td>1121.873900</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>27.000000</td>
      <td>26.296250</td>
      <td>0.000000</td>
      <td>4740.287150</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>39.000000</td>
      <td>30.400000</td>
      <td>1.000000</td>
      <td>9382.033000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>51.000000</td>
      <td>34.693750</td>
      <td>2.000000</td>
      <td>16639.912515</td>
    </tr>
    <tr>
      <th>max</th>
      <td>64.000000</td>
      <td>53.130000</td>
      <td>5.000000</td>
      <td>63770.428010</td>
    </tr>
  </tbody>
</table>
</div>



### 4. 신규 컬럼(double bmi)을 생성하고, bmi의 2배가 되는 값을 할당하기


```python
df['double bmi'] = df['bmi'] * 2
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
      <th>age</th>
      <th>sex</th>
      <th>bmi</th>
      <th>children</th>
      <th>smoker</th>
      <th>region</th>
      <th>charges</th>
      <th>double bmi</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>19</td>
      <td>female</td>
      <td>27.900</td>
      <td>0</td>
      <td>yes</td>
      <td>southwest</td>
      <td>16884.92400</td>
      <td>55.80</td>
    </tr>
    <tr>
      <th>1</th>
      <td>18</td>
      <td>male</td>
      <td>33.770</td>
      <td>1</td>
      <td>no</td>
      <td>southeast</td>
      <td>1725.55230</td>
      <td>67.54</td>
    </tr>
    <tr>
      <th>2</th>
      <td>28</td>
      <td>male</td>
      <td>33.000</td>
      <td>3</td>
      <td>no</td>
      <td>southeast</td>
      <td>4449.46200</td>
      <td>66.00</td>
    </tr>
    <tr>
      <th>3</th>
      <td>33</td>
      <td>male</td>
      <td>22.705</td>
      <td>0</td>
      <td>no</td>
      <td>northwest</td>
      <td>21984.47061</td>
      <td>45.41</td>
    </tr>
    <tr>
      <th>4</th>
      <td>32</td>
      <td>male</td>
      <td>28.880</td>
      <td>0</td>
      <td>no</td>
      <td>northwest</td>
      <td>3866.85520</td>
      <td>57.76</td>
    </tr>
  </tbody>
</table>
</div>



### 5. 신규 컬럼(debt)을 생성하고, 0으로 채우기


```python
df['debt'] = 0
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
      <th>age</th>
      <th>sex</th>
      <th>bmi</th>
      <th>children</th>
      <th>smoker</th>
      <th>region</th>
      <th>charges</th>
      <th>double bmi</th>
      <th>debt</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>19</td>
      <td>female</td>
      <td>27.900</td>
      <td>0</td>
      <td>yes</td>
      <td>southwest</td>
      <td>16884.92400</td>
      <td>55.80</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>18</td>
      <td>male</td>
      <td>33.770</td>
      <td>1</td>
      <td>no</td>
      <td>southeast</td>
      <td>1725.55230</td>
      <td>67.54</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>28</td>
      <td>male</td>
      <td>33.000</td>
      <td>3</td>
      <td>no</td>
      <td>southeast</td>
      <td>4449.46200</td>
      <td>66.00</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>33</td>
      <td>male</td>
      <td>22.705</td>
      <td>0</td>
      <td>no</td>
      <td>northwest</td>
      <td>21984.47061</td>
      <td>45.41</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>32</td>
      <td>male</td>
      <td>28.880</td>
      <td>0</td>
      <td>no</td>
      <td>northwest</td>
      <td>3866.85520</td>
      <td>57.76</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>



### 6. debt에 0부터 값이 증가하도록 채우기


```python
#df['debt'] = np.arange(len(df),0,-1)
df['debt'] = np.arange(0, len(df))
```

### 7. 1번 인덱스의 정보 출력:iloc


```python
# 특정 row에 해당하는 값 : loc 
df.iloc[1]
```




    age                  18
    sex                male
    bmi               33.77
    children              1
    smoker               no
    region        southeast
    charges         1725.55
    double bmi        67.54
    debt                  1
    Name: 1, dtype: object



### 8. 3,5,8번 인덱스의 'debt'값을 12, 13, 14로 설정하기


```python
df['debt'][3] = 12
```

    <ipython-input-38-7f2047568f7e>:1: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame
    
    See the caveats in the documentation: https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html#returning-a-view-versus-a-copy
      df['debt'][3] = 12
    


```python
val = pd.Series([12, 13, 14], index=[3, 5, 8])
df['debt'] = val
# df
```


```python
df['debt'].fillna(0, inplace=True)
```


```python
df.loc[3, 'debt'] = 12
```


```python
df
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
      <th>age</th>
      <th>sex</th>
      <th>bmi</th>
      <th>children</th>
      <th>smoker</th>
      <th>region</th>
      <th>charges</th>
      <th>double bmi</th>
      <th>debt</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>19</td>
      <td>female</td>
      <td>27.900</td>
      <td>0</td>
      <td>yes</td>
      <td>southwest</td>
      <td>16884.92400</td>
      <td>55.80</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>18</td>
      <td>male</td>
      <td>33.770</td>
      <td>1</td>
      <td>no</td>
      <td>southeast</td>
      <td>1725.55230</td>
      <td>67.54</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>28</td>
      <td>male</td>
      <td>33.000</td>
      <td>3</td>
      <td>no</td>
      <td>southeast</td>
      <td>4449.46200</td>
      <td>66.00</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>33</td>
      <td>male</td>
      <td>22.705</td>
      <td>0</td>
      <td>no</td>
      <td>northwest</td>
      <td>21984.47061</td>
      <td>45.41</td>
      <td>12.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>32</td>
      <td>male</td>
      <td>28.880</td>
      <td>0</td>
      <td>no</td>
      <td>northwest</td>
      <td>3866.85520</td>
      <td>57.76</td>
      <td>0.0</td>
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
    </tr>
    <tr>
      <th>1333</th>
      <td>50</td>
      <td>male</td>
      <td>30.970</td>
      <td>3</td>
      <td>no</td>
      <td>northwest</td>
      <td>10600.54830</td>
      <td>61.94</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>1334</th>
      <td>18</td>
      <td>female</td>
      <td>31.920</td>
      <td>0</td>
      <td>no</td>
      <td>northeast</td>
      <td>2205.98080</td>
      <td>63.84</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>1335</th>
      <td>18</td>
      <td>female</td>
      <td>36.850</td>
      <td>0</td>
      <td>no</td>
      <td>southeast</td>
      <td>1629.83350</td>
      <td>73.70</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>1336</th>
      <td>21</td>
      <td>female</td>
      <td>25.800</td>
      <td>0</td>
      <td>no</td>
      <td>southwest</td>
      <td>2007.94500</td>
      <td>51.60</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>1337</th>
      <td>61</td>
      <td>female</td>
      <td>29.070</td>
      <td>0</td>
      <td>yes</td>
      <td>northwest</td>
      <td>29141.36030</td>
      <td>58.14</td>
      <td>0.0</td>
    </tr>
  </tbody>
</table>
<p>1338 rows × 9 columns</p>
</div>



### 9. 'double bmi'열 삭제하기


```python
del df['double bmi']
# df.drop(['double bmi'], axis=1)
```

### 10. 'age'열, 'sex'열만 출력하기


```python
df[['age', 'sex']]
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
      <th>age</th>
      <th>sex</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>19</td>
      <td>female</td>
    </tr>
    <tr>
      <th>1</th>
      <td>18</td>
      <td>male</td>
    </tr>
    <tr>
      <th>2</th>
      <td>28</td>
      <td>male</td>
    </tr>
    <tr>
      <th>3</th>
      <td>33</td>
      <td>male</td>
    </tr>
    <tr>
      <th>4</th>
      <td>32</td>
      <td>male</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>1333</th>
      <td>50</td>
      <td>male</td>
    </tr>
    <tr>
      <th>1334</th>
      <td>18</td>
      <td>female</td>
    </tr>
    <tr>
      <th>1335</th>
      <td>18</td>
      <td>female</td>
    </tr>
    <tr>
      <th>1336</th>
      <td>21</td>
      <td>female</td>
    </tr>
    <tr>
      <th>1337</th>
      <td>61</td>
      <td>female</td>
    </tr>
  </tbody>
</table>
<p>1338 rows × 2 columns</p>
</div>



### 11. 함수 생성, 적용(apply/map)

나이를 1살씩 증가시키기


```python
f = lambda x: x+1
df['age'].apply(f)
```




    0       20
    1       19
    2       29
    3       34
    4       33
            ..
    1333    51
    1334    19
    1335    19
    1336    22
    1337    62
    Name: age, Length: 1338, dtype: int64



### 12. 함수 생성, 적용(apply/map)

charges의 표시형식을 소수점 아래 2자리로 바꾸기


```python
format = lambda x: '%.2f' % x
df['charges'].map(format)
```




    0       16884.92
    1        1725.55
    2        4449.46
    3       21984.47
    4        3866.86
              ...   
    1333    10600.55
    1334     2205.98
    1335     1629.83
    1336     2007.94
    1337    29141.36
    Name: charges, Length: 1338, dtype: object



### 13. 함수 생성, 적용(applymap)

데이터프레임 전체 값을 대괄호[ ] 로 감싸기

예: 	[19]	[female]	[27.9]	[0]	[yes]	[southwest]	[16884.924]


```python
ff = lambda x: '[' + str(x) + ']'
df.applymap(ff)
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
      <th>age</th>
      <th>sex</th>
      <th>bmi</th>
      <th>children</th>
      <th>smoker</th>
      <th>region</th>
      <th>charges</th>
      <th>debt</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>[19]</td>
      <td>[female]</td>
      <td>[27.9]</td>
      <td>[0]</td>
      <td>[yes]</td>
      <td>[southwest]</td>
      <td>[16884.924]</td>
      <td>[0.0]</td>
    </tr>
    <tr>
      <th>1</th>
      <td>[18]</td>
      <td>[male]</td>
      <td>[33.77]</td>
      <td>[1]</td>
      <td>[no]</td>
      <td>[southeast]</td>
      <td>[1725.5523]</td>
      <td>[0.0]</td>
    </tr>
    <tr>
      <th>2</th>
      <td>[28]</td>
      <td>[male]</td>
      <td>[33.0]</td>
      <td>[3]</td>
      <td>[no]</td>
      <td>[southeast]</td>
      <td>[4449.462]</td>
      <td>[0.0]</td>
    </tr>
    <tr>
      <th>3</th>
      <td>[33]</td>
      <td>[male]</td>
      <td>[22.705]</td>
      <td>[0]</td>
      <td>[no]</td>
      <td>[northwest]</td>
      <td>[21984.47061]</td>
      <td>[12.0]</td>
    </tr>
    <tr>
      <th>4</th>
      <td>[32]</td>
      <td>[male]</td>
      <td>[28.88]</td>
      <td>[0]</td>
      <td>[no]</td>
      <td>[northwest]</td>
      <td>[3866.8552]</td>
      <td>[0.0]</td>
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
    </tr>
    <tr>
      <th>1333</th>
      <td>[50]</td>
      <td>[male]</td>
      <td>[30.97]</td>
      <td>[3]</td>
      <td>[no]</td>
      <td>[northwest]</td>
      <td>[10600.5483]</td>
      <td>[0.0]</td>
    </tr>
    <tr>
      <th>1334</th>
      <td>[18]</td>
      <td>[female]</td>
      <td>[31.92]</td>
      <td>[0]</td>
      <td>[no]</td>
      <td>[northeast]</td>
      <td>[2205.9808]</td>
      <td>[0.0]</td>
    </tr>
    <tr>
      <th>1335</th>
      <td>[18]</td>
      <td>[female]</td>
      <td>[36.85]</td>
      <td>[0]</td>
      <td>[no]</td>
      <td>[southeast]</td>
      <td>[1629.8335]</td>
      <td>[0.0]</td>
    </tr>
    <tr>
      <th>1336</th>
      <td>[21]</td>
      <td>[female]</td>
      <td>[25.8]</td>
      <td>[0]</td>
      <td>[no]</td>
      <td>[southwest]</td>
      <td>[2007.945]</td>
      <td>[0.0]</td>
    </tr>
    <tr>
      <th>1337</th>
      <td>[61]</td>
      <td>[female]</td>
      <td>[29.07]</td>
      <td>[0]</td>
      <td>[yes]</td>
      <td>[northwest]</td>
      <td>[29141.3603]</td>
      <td>[0.0]</td>
    </tr>
  </tbody>
</table>
<p>1338 rows × 8 columns</p>
</div>



### 14. 컬럼 정렬(알파벳 순서대로) : sort_index
age, bmi, charges... 순으로 정렬


```python
df.sort_index(axis=1)
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
      <th>age</th>
      <th>bmi</th>
      <th>charges</th>
      <th>children</th>
      <th>debt</th>
      <th>region</th>
      <th>sex</th>
      <th>smoker</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>19</td>
      <td>27.900</td>
      <td>16884.92400</td>
      <td>0</td>
      <td>0.0</td>
      <td>southwest</td>
      <td>female</td>
      <td>yes</td>
    </tr>
    <tr>
      <th>1</th>
      <td>18</td>
      <td>33.770</td>
      <td>1725.55230</td>
      <td>1</td>
      <td>0.0</td>
      <td>southeast</td>
      <td>male</td>
      <td>no</td>
    </tr>
    <tr>
      <th>2</th>
      <td>28</td>
      <td>33.000</td>
      <td>4449.46200</td>
      <td>3</td>
      <td>0.0</td>
      <td>southeast</td>
      <td>male</td>
      <td>no</td>
    </tr>
    <tr>
      <th>3</th>
      <td>33</td>
      <td>22.705</td>
      <td>21984.47061</td>
      <td>0</td>
      <td>12.0</td>
      <td>northwest</td>
      <td>male</td>
      <td>no</td>
    </tr>
    <tr>
      <th>4</th>
      <td>32</td>
      <td>28.880</td>
      <td>3866.85520</td>
      <td>0</td>
      <td>0.0</td>
      <td>northwest</td>
      <td>male</td>
      <td>no</td>
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
    </tr>
    <tr>
      <th>1333</th>
      <td>50</td>
      <td>30.970</td>
      <td>10600.54830</td>
      <td>3</td>
      <td>0.0</td>
      <td>northwest</td>
      <td>male</td>
      <td>no</td>
    </tr>
    <tr>
      <th>1334</th>
      <td>18</td>
      <td>31.920</td>
      <td>2205.98080</td>
      <td>0</td>
      <td>0.0</td>
      <td>northeast</td>
      <td>female</td>
      <td>no</td>
    </tr>
    <tr>
      <th>1335</th>
      <td>18</td>
      <td>36.850</td>
      <td>1629.83350</td>
      <td>0</td>
      <td>0.0</td>
      <td>southeast</td>
      <td>female</td>
      <td>no</td>
    </tr>
    <tr>
      <th>1336</th>
      <td>21</td>
      <td>25.800</td>
      <td>2007.94500</td>
      <td>0</td>
      <td>0.0</td>
      <td>southwest</td>
      <td>female</td>
      <td>no</td>
    </tr>
    <tr>
      <th>1337</th>
      <td>61</td>
      <td>29.070</td>
      <td>29141.36030</td>
      <td>0</td>
      <td>0.0</td>
      <td>northwest</td>
      <td>female</td>
      <td>yes</td>
    </tr>
  </tbody>
</table>
<p>1338 rows × 8 columns</p>
</div>



### 15. 값 정렬(age) : sort_values
나이 순으로 정렬


```python
df.sort_values(by='age')
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
      <th>age</th>
      <th>sex</th>
      <th>bmi</th>
      <th>children</th>
      <th>smoker</th>
      <th>region</th>
      <th>charges</th>
      <th>debt</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1248</th>
      <td>18</td>
      <td>female</td>
      <td>39.820</td>
      <td>0</td>
      <td>no</td>
      <td>southeast</td>
      <td>1633.96180</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>482</th>
      <td>18</td>
      <td>female</td>
      <td>31.350</td>
      <td>0</td>
      <td>no</td>
      <td>southeast</td>
      <td>1622.18850</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>492</th>
      <td>18</td>
      <td>female</td>
      <td>25.080</td>
      <td>0</td>
      <td>no</td>
      <td>northeast</td>
      <td>2196.47320</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>525</th>
      <td>18</td>
      <td>female</td>
      <td>33.880</td>
      <td>0</td>
      <td>no</td>
      <td>southeast</td>
      <td>11482.63485</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>529</th>
      <td>18</td>
      <td>male</td>
      <td>25.460</td>
      <td>0</td>
      <td>no</td>
      <td>northeast</td>
      <td>1708.00140</td>
      <td>0.0</td>
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
    </tr>
    <tr>
      <th>398</th>
      <td>64</td>
      <td>male</td>
      <td>25.600</td>
      <td>2</td>
      <td>no</td>
      <td>southwest</td>
      <td>14988.43200</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>335</th>
      <td>64</td>
      <td>male</td>
      <td>34.500</td>
      <td>0</td>
      <td>no</td>
      <td>southwest</td>
      <td>13822.80300</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>378</th>
      <td>64</td>
      <td>female</td>
      <td>30.115</td>
      <td>3</td>
      <td>no</td>
      <td>northwest</td>
      <td>16455.70785</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>1265</th>
      <td>64</td>
      <td>male</td>
      <td>23.760</td>
      <td>0</td>
      <td>yes</td>
      <td>southeast</td>
      <td>26926.51440</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>635</th>
      <td>64</td>
      <td>male</td>
      <td>38.190</td>
      <td>0</td>
      <td>no</td>
      <td>northeast</td>
      <td>14410.93210</td>
      <td>0.0</td>
    </tr>
  </tbody>
</table>
<p>1338 rows × 8 columns</p>
</div>



### 16. 평균구하기: mean


```python
df.mean()
```




    age            39.207025
    bmi            30.663397
    children        1.094918
    charges     13270.422265
    debt            0.029148
    dtype: float64



### 17. 공분산 구하기: cov


```python
df.cov()
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
      <th>age</th>
      <th>bmi</th>
      <th>children</th>
      <th>charges</th>
      <th>debt</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>age</th>
      <td>197.401387</td>
      <td>9.362337</td>
      <td>0.719303</td>
      <td>5.087480e+04</td>
      <td>-0.158619</td>
    </tr>
    <tr>
      <th>bmi</th>
      <td>9.362337</td>
      <td>37.187884</td>
      <td>0.093795</td>
      <td>1.464730e+04</td>
      <td>-0.128027</td>
    </tr>
    <tr>
      <th>children</th>
      <td>0.719303</td>
      <td>0.093795</td>
      <td>1.453213</td>
      <td>9.926742e+02</td>
      <td>-0.010996</td>
    </tr>
    <tr>
      <th>charges</th>
      <td>50874.802298</td>
      <td>14647.304426</td>
      <td>992.674197</td>
      <td>1.466524e+08</td>
      <td>-86.168280</td>
    </tr>
    <tr>
      <th>debt</th>
      <td>-0.158619</td>
      <td>-0.128027</td>
      <td>-0.010996</td>
      <td>-8.616828e+01</td>
      <td>0.379853</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 상관계수
df.corr()
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
      <th>age</th>
      <th>bmi</th>
      <th>children</th>
      <th>charges</th>
      <th>debt</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>age</th>
      <td>1.000000</td>
      <td>0.109272</td>
      <td>0.042469</td>
      <td>0.299008</td>
      <td>-0.018318</td>
    </tr>
    <tr>
      <th>bmi</th>
      <td>0.109272</td>
      <td>1.000000</td>
      <td>0.012759</td>
      <td>0.198341</td>
      <td>-0.034064</td>
    </tr>
    <tr>
      <th>children</th>
      <td>0.042469</td>
      <td>0.012759</td>
      <td>1.000000</td>
      <td>0.067998</td>
      <td>-0.014800</td>
    </tr>
    <tr>
      <th>charges</th>
      <td>0.299008</td>
      <td>0.198341</td>
      <td>0.067998</td>
      <td>1.000000</td>
      <td>-0.011545</td>
    </tr>
    <tr>
      <th>debt</th>
      <td>-0.018318</td>
      <td>-0.034064</td>
      <td>-0.014800</td>
      <td>-0.011545</td>
      <td>1.000000</td>
    </tr>
  </tbody>
</table>
</div>



### 18. 남자, 여자가 각각 몇명있는지 구하기


```python
pd.value_counts(df.sex)   
```




    male      676
    female    662
    Name: sex, dtype: int64



### 19. 자녀(children)이 3명인 데이터 출력하기


```python
df[df['children'].isin([3])]
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
      <th>age</th>
      <th>sex</th>
      <th>bmi</th>
      <th>children</th>
      <th>smoker</th>
      <th>region</th>
      <th>charges</th>
      <th>debt</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2</th>
      <td>28</td>
      <td>male</td>
      <td>33.000</td>
      <td>3</td>
      <td>no</td>
      <td>southeast</td>
      <td>4449.46200</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>7</th>
      <td>37</td>
      <td>female</td>
      <td>27.740</td>
      <td>3</td>
      <td>no</td>
      <td>northwest</td>
      <td>7281.50560</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>25</th>
      <td>59</td>
      <td>female</td>
      <td>27.720</td>
      <td>3</td>
      <td>no</td>
      <td>southeast</td>
      <td>14001.13380</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>36</th>
      <td>62</td>
      <td>female</td>
      <td>32.965</td>
      <td>3</td>
      <td>no</td>
      <td>northwest</td>
      <td>15612.19335</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>54</th>
      <td>40</td>
      <td>female</td>
      <td>28.690</td>
      <td>3</td>
      <td>no</td>
      <td>northwest</td>
      <td>8059.67910</td>
      <td>0.0</td>
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
    </tr>
    <tr>
      <th>1301</th>
      <td>62</td>
      <td>male</td>
      <td>30.875</td>
      <td>3</td>
      <td>yes</td>
      <td>northwest</td>
      <td>46718.16325</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>1314</th>
      <td>30</td>
      <td>female</td>
      <td>23.655</td>
      <td>3</td>
      <td>yes</td>
      <td>northwest</td>
      <td>18765.87545</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>1320</th>
      <td>31</td>
      <td>male</td>
      <td>31.065</td>
      <td>3</td>
      <td>no</td>
      <td>northwest</td>
      <td>5425.02335</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>1332</th>
      <td>52</td>
      <td>female</td>
      <td>44.700</td>
      <td>3</td>
      <td>no</td>
      <td>southwest</td>
      <td>11411.68500</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>1333</th>
      <td>50</td>
      <td>male</td>
      <td>30.970</td>
      <td>3</td>
      <td>no</td>
      <td>northwest</td>
      <td>10600.54830</td>
      <td>0.0</td>
    </tr>
  </tbody>
</table>
<p>157 rows × 8 columns</p>
</div>



### 20. 자녀(children)가 5명 이상인 데이터 출력하기


```python
df[df['children'] > 4]
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
      <th>age</th>
      <th>sex</th>
      <th>bmi</th>
      <th>children</th>
      <th>smoker</th>
      <th>region</th>
      <th>charges</th>
      <th>debt</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>32</th>
      <td>19</td>
      <td>female</td>
      <td>28.600</td>
      <td>5</td>
      <td>no</td>
      <td>southwest</td>
      <td>4687.79700</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>71</th>
      <td>31</td>
      <td>male</td>
      <td>28.500</td>
      <td>5</td>
      <td>no</td>
      <td>northeast</td>
      <td>6799.45800</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>166</th>
      <td>20</td>
      <td>female</td>
      <td>37.000</td>
      <td>5</td>
      <td>no</td>
      <td>southwest</td>
      <td>4830.63000</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>413</th>
      <td>25</td>
      <td>male</td>
      <td>23.900</td>
      <td>5</td>
      <td>no</td>
      <td>southwest</td>
      <td>5080.09600</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>425</th>
      <td>45</td>
      <td>male</td>
      <td>24.310</td>
      <td>5</td>
      <td>no</td>
      <td>southeast</td>
      <td>9788.86590</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>438</th>
      <td>52</td>
      <td>female</td>
      <td>46.750</td>
      <td>5</td>
      <td>no</td>
      <td>southeast</td>
      <td>12592.53450</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>568</th>
      <td>49</td>
      <td>female</td>
      <td>31.900</td>
      <td>5</td>
      <td>no</td>
      <td>southwest</td>
      <td>11552.90400</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>640</th>
      <td>33</td>
      <td>male</td>
      <td>42.400</td>
      <td>5</td>
      <td>no</td>
      <td>southwest</td>
      <td>6666.24300</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>877</th>
      <td>33</td>
      <td>male</td>
      <td>33.440</td>
      <td>5</td>
      <td>no</td>
      <td>southeast</td>
      <td>6653.78860</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>932</th>
      <td>46</td>
      <td>male</td>
      <td>25.800</td>
      <td>5</td>
      <td>no</td>
      <td>southwest</td>
      <td>10096.97000</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>937</th>
      <td>39</td>
      <td>female</td>
      <td>24.225</td>
      <td>5</td>
      <td>no</td>
      <td>northwest</td>
      <td>8965.79575</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>969</th>
      <td>39</td>
      <td>female</td>
      <td>34.320</td>
      <td>5</td>
      <td>no</td>
      <td>southeast</td>
      <td>8596.82780</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>984</th>
      <td>20</td>
      <td>male</td>
      <td>30.115</td>
      <td>5</td>
      <td>no</td>
      <td>northeast</td>
      <td>4915.05985</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>1085</th>
      <td>39</td>
      <td>female</td>
      <td>18.300</td>
      <td>5</td>
      <td>yes</td>
      <td>southwest</td>
      <td>19023.26000</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>1116</th>
      <td>41</td>
      <td>male</td>
      <td>29.640</td>
      <td>5</td>
      <td>no</td>
      <td>northeast</td>
      <td>9222.40260</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>1130</th>
      <td>39</td>
      <td>female</td>
      <td>23.870</td>
      <td>5</td>
      <td>no</td>
      <td>southeast</td>
      <td>8582.30230</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>1245</th>
      <td>28</td>
      <td>male</td>
      <td>24.300</td>
      <td>5</td>
      <td>no</td>
      <td>southwest</td>
      <td>5615.36900</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>1272</th>
      <td>43</td>
      <td>male</td>
      <td>25.520</td>
      <td>5</td>
      <td>no</td>
      <td>southeast</td>
      <td>14478.33015</td>
      <td>0.0</td>
    </tr>
  </tbody>
</table>
</div>



### 21. bmi가  17 미만인 데이터 출력하기


```python
df[df['bmi'] < 17]
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
      <th>age</th>
      <th>sex</th>
      <th>bmi</th>
      <th>children</th>
      <th>smoker</th>
      <th>region</th>
      <th>charges</th>
      <th>debt</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>172</th>
      <td>18</td>
      <td>male</td>
      <td>15.960</td>
      <td>0</td>
      <td>no</td>
      <td>northeast</td>
      <td>1694.79640</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>428</th>
      <td>21</td>
      <td>female</td>
      <td>16.815</td>
      <td>1</td>
      <td>no</td>
      <td>northeast</td>
      <td>3167.45585</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>1226</th>
      <td>38</td>
      <td>male</td>
      <td>16.815</td>
      <td>2</td>
      <td>no</td>
      <td>northeast</td>
      <td>6640.54485</td>
      <td>0.0</td>
    </tr>
  </tbody>
</table>
</div>



### 22. debt가 null이 아닌데이터 출력하기


```python
df[df['debt'].notnull()]
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
      <th>age</th>
      <th>sex</th>
      <th>bmi</th>
      <th>children</th>
      <th>smoker</th>
      <th>region</th>
      <th>charges</th>
      <th>debt</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>19</td>
      <td>female</td>
      <td>27.900</td>
      <td>0</td>
      <td>yes</td>
      <td>southwest</td>
      <td>16884.92400</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>18</td>
      <td>male</td>
      <td>33.770</td>
      <td>1</td>
      <td>no</td>
      <td>southeast</td>
      <td>1725.55230</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>28</td>
      <td>male</td>
      <td>33.000</td>
      <td>3</td>
      <td>no</td>
      <td>southeast</td>
      <td>4449.46200</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>33</td>
      <td>male</td>
      <td>22.705</td>
      <td>0</td>
      <td>no</td>
      <td>northwest</td>
      <td>21984.47061</td>
      <td>12.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>32</td>
      <td>male</td>
      <td>28.880</td>
      <td>0</td>
      <td>no</td>
      <td>northwest</td>
      <td>3866.85520</td>
      <td>0.0</td>
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
    </tr>
    <tr>
      <th>1333</th>
      <td>50</td>
      <td>male</td>
      <td>30.970</td>
      <td>3</td>
      <td>no</td>
      <td>northwest</td>
      <td>10600.54830</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>1334</th>
      <td>18</td>
      <td>female</td>
      <td>31.920</td>
      <td>0</td>
      <td>no</td>
      <td>northeast</td>
      <td>2205.98080</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>1335</th>
      <td>18</td>
      <td>female</td>
      <td>36.850</td>
      <td>0</td>
      <td>no</td>
      <td>southeast</td>
      <td>1629.83350</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>1336</th>
      <td>21</td>
      <td>female</td>
      <td>25.800</td>
      <td>0</td>
      <td>no</td>
      <td>southwest</td>
      <td>2007.94500</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>1337</th>
      <td>61</td>
      <td>female</td>
      <td>29.070</td>
      <td>0</td>
      <td>yes</td>
      <td>northwest</td>
      <td>29141.36030</td>
      <td>0.0</td>
    </tr>
  </tbody>
</table>
<p>1338 rows × 8 columns</p>
</div>



### 23. 'age'가 60보다 큰 값만 출력하기


```python
df[df['age'] > 60]
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
      <th>age</th>
      <th>sex</th>
      <th>bmi</th>
      <th>children</th>
      <th>smoker</th>
      <th>region</th>
      <th>charges</th>
      <th>debt</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>11</th>
      <td>62</td>
      <td>female</td>
      <td>26.290</td>
      <td>0</td>
      <td>yes</td>
      <td>southeast</td>
      <td>27808.72510</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>26</th>
      <td>63</td>
      <td>female</td>
      <td>23.085</td>
      <td>0</td>
      <td>no</td>
      <td>northeast</td>
      <td>14451.83515</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>33</th>
      <td>63</td>
      <td>male</td>
      <td>28.310</td>
      <td>0</td>
      <td>no</td>
      <td>northwest</td>
      <td>13770.09790</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>36</th>
      <td>62</td>
      <td>female</td>
      <td>32.965</td>
      <td>3</td>
      <td>no</td>
      <td>northwest</td>
      <td>15612.19335</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>62</th>
      <td>64</td>
      <td>male</td>
      <td>24.700</td>
      <td>1</td>
      <td>no</td>
      <td>northwest</td>
      <td>30166.61817</td>
      <td>0.0</td>
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
    </tr>
    <tr>
      <th>1301</th>
      <td>62</td>
      <td>male</td>
      <td>30.875</td>
      <td>3</td>
      <td>yes</td>
      <td>northwest</td>
      <td>46718.16325</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>1321</th>
      <td>62</td>
      <td>male</td>
      <td>26.695</td>
      <td>0</td>
      <td>yes</td>
      <td>northeast</td>
      <td>28101.33305</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>1322</th>
      <td>62</td>
      <td>male</td>
      <td>38.830</td>
      <td>0</td>
      <td>no</td>
      <td>southeast</td>
      <td>12981.34570</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>1325</th>
      <td>61</td>
      <td>male</td>
      <td>33.535</td>
      <td>0</td>
      <td>no</td>
      <td>northeast</td>
      <td>13143.33665</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>1337</th>
      <td>61</td>
      <td>female</td>
      <td>29.070</td>
      <td>0</td>
      <td>yes</td>
      <td>northwest</td>
      <td>29141.36030</td>
      <td>0.0</td>
    </tr>
  </tbody>
</table>
<p>91 rows × 8 columns</p>
</div>




```python
grouped = df['bmi'].groupby(df['sex']).mean()
```


```python
grouped = df.groupby(['sex', 'region'])
grouped
grouped.size()
```




    sex     region   
    female  northeast    161
            northwest    164
            southeast    175
            southwest    162
    male    northeast    163
            northwest    161
            southeast    189
            southwest    163
    dtype: int64




```python

```
