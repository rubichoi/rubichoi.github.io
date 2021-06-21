---
layout: single
title:  "주가분석실습"
---

```python
%conda install pandas-datareader
```

    Collecting package metadata (current_repodata.json): ...working... done
    Solving environment: ...working... done
    
    ## Package Plan ##
    
      environment location: C:\Users\user\anaconda3
    
      added / updated specs:
        - pandas-datareader
    
    
    The following packages will be downloaded:
    
        package                    |            build
        ---------------------------|-----------------
        conda-4.10.1               |   py38haa95532_1         2.9 MB
        ------------------------------------------------------------
                                               Total:         2.9 MB
    
    The following packages will be UPDATED:
    
      conda              conda-forge::conda-4.10.1-py38haa244f~ --> pkgs/main::conda-4.10.1-py38haa95532_1
    
    
    
    Downloading and Extracting Packages
    
    conda-4.10.1         | 2.9 MB    |            |   0% 
    conda-4.10.1         | 2.9 MB    | 5          |   6% 
    conda-4.10.1         | 2.9 MB    | ##5        |  26% 
    conda-4.10.1         | 2.9 MB    | ####4      |  45% 
    conda-4.10.1         | 2.9 MB    | ######6    |  67% 
    conda-4.10.1         | 2.9 MB    | ########4  |  85% 
    conda-4.10.1         | 2.9 MB    | ########## | 100% 
    conda-4.10.1         | 2.9 MB    | ########## | 100% 
    Preparing transaction: ...working... done
    Verifying transaction: ...working... done
    Executing transaction: ...working... done
    
    Note: you may need to restart the kernel to use updated packages.
    


```python
import pandas as pd
import numpy as np
from pandas_datareader import data
```


```python
df = data.get_data_yahoo('005930.KS',"2020-01-01" )
```


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
      <th>High</th>
      <th>Low</th>
      <th>Open</th>
      <th>Close</th>
      <th>Volume</th>
      <th>Adj Close</th>
    </tr>
    <tr>
      <th>Date</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2020-01-02</th>
      <td>56000.0</td>
      <td>55000.0</td>
      <td>55500.0</td>
      <td>55200.0</td>
      <td>12993228.0</td>
      <td>52537.179688</td>
    </tr>
    <tr>
      <th>2020-01-03</th>
      <td>56600.0</td>
      <td>54900.0</td>
      <td>56000.0</td>
      <td>55500.0</td>
      <td>15422255.0</td>
      <td>52822.707031</td>
    </tr>
    <tr>
      <th>2020-01-06</th>
      <td>55600.0</td>
      <td>54600.0</td>
      <td>54900.0</td>
      <td>55500.0</td>
      <td>10278951.0</td>
      <td>52822.707031</td>
    </tr>
    <tr>
      <th>2020-01-07</th>
      <td>56400.0</td>
      <td>55600.0</td>
      <td>55700.0</td>
      <td>55800.0</td>
      <td>10009778.0</td>
      <td>53108.238281</td>
    </tr>
    <tr>
      <th>2020-01-08</th>
      <td>57400.0</td>
      <td>55900.0</td>
      <td>56200.0</td>
      <td>56800.0</td>
      <td>23501171.0</td>
      <td>54059.992188</td>
    </tr>
  </tbody>
</table>
</div>



#### Close 컬럼 삭제


```python
df = df.drop('Close',axis=1)
#del df['Close']
```

#### 컬럼명 변경(고가, 저가, 시작가, Adj Close(수정된 종가), 거래량)


```python
df.columns = ["고가","저가","시작가","거래량","수정된 종가"]
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
      <th>고가</th>
      <th>저가</th>
      <th>시작가</th>
      <th>거래량</th>
      <th>수정된 종가</th>
    </tr>
    <tr>
      <th>Date</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2020-01-02</th>
      <td>56000.0</td>
      <td>55000.0</td>
      <td>55500.0</td>
      <td>12993228.0</td>
      <td>52537.179688</td>
    </tr>
    <tr>
      <th>2020-01-03</th>
      <td>56600.0</td>
      <td>54900.0</td>
      <td>56000.0</td>
      <td>15422255.0</td>
      <td>52822.707031</td>
    </tr>
    <tr>
      <th>2020-01-06</th>
      <td>55600.0</td>
      <td>54600.0</td>
      <td>54900.0</td>
      <td>10278951.0</td>
      <td>52822.707031</td>
    </tr>
    <tr>
      <th>2020-01-07</th>
      <td>56400.0</td>
      <td>55600.0</td>
      <td>55700.0</td>
      <td>10009778.0</td>
      <td>53108.238281</td>
    </tr>
    <tr>
      <th>2020-01-08</th>
      <td>57400.0</td>
      <td>55900.0</td>
      <td>56200.0</td>
      <td>23501171.0</td>
      <td>54059.992188</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>2021-06-15</th>
      <td>81200.0</td>
      <td>80600.0</td>
      <td>80900.0</td>
      <td>10075685.0</td>
      <td>80900.000000</td>
    </tr>
    <tr>
      <th>2021-06-16</th>
      <td>81900.0</td>
      <td>81100.0</td>
      <td>81500.0</td>
      <td>14999855.0</td>
      <td>81800.000000</td>
    </tr>
    <tr>
      <th>2021-06-17</th>
      <td>81300.0</td>
      <td>80700.0</td>
      <td>81100.0</td>
      <td>14007385.0</td>
      <td>80900.000000</td>
    </tr>
    <tr>
      <th>2021-06-18</th>
      <td>81100.0</td>
      <td>80500.0</td>
      <td>81100.0</td>
      <td>14916721.0</td>
      <td>80500.000000</td>
    </tr>
    <tr>
      <th>2021-06-21</th>
      <td>79900.0</td>
      <td>79600.0</td>
      <td>79700.0</td>
      <td>1528067.0</td>
      <td>79900.000000</td>
    </tr>
  </tbody>
</table>
<p>364 rows × 5 columns</p>
</div>



#### 상위 3개 데이터 선택


```python
df.head(3)
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
      <th>고가</th>
      <th>저가</th>
      <th>시작가</th>
      <th>거래량</th>
      <th>수정된 종가</th>
    </tr>
    <tr>
      <th>Date</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2020-01-02</th>
      <td>56000.0</td>
      <td>55000.0</td>
      <td>55500.0</td>
      <td>12993228.0</td>
      <td>52537.179688</td>
    </tr>
    <tr>
      <th>2020-01-03</th>
      <td>56600.0</td>
      <td>54900.0</td>
      <td>56000.0</td>
      <td>15422255.0</td>
      <td>52822.707031</td>
    </tr>
    <tr>
      <th>2020-01-06</th>
      <td>55600.0</td>
      <td>54600.0</td>
      <td>54900.0</td>
      <td>10278951.0</td>
      <td>52822.707031</td>
    </tr>
  </tbody>
</table>
</div>



#### 하위 3개 데이터 선택


```python
df.tail(3)
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
      <th>고가</th>
      <th>저가</th>
      <th>시작가</th>
      <th>거래량</th>
      <th>수정된 종가</th>
    </tr>
    <tr>
      <th>Date</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2021-06-17</th>
      <td>81300.0</td>
      <td>80700.0</td>
      <td>81100.0</td>
      <td>14007385.0</td>
      <td>80900.0</td>
    </tr>
    <tr>
      <th>2021-06-18</th>
      <td>81100.0</td>
      <td>80500.0</td>
      <td>81100.0</td>
      <td>14916721.0</td>
      <td>80500.0</td>
    </tr>
    <tr>
      <th>2021-06-21</th>
      <td>79900.0</td>
      <td>79600.0</td>
      <td>79700.0</td>
      <td>1528067.0</td>
      <td>79900.0</td>
    </tr>
  </tbody>
</table>
</div>



#### 종가 데이터 선택


```python
df['수정된 종가']
```




    Date
    2020-01-02    52537.179688
    2020-01-03    52822.707031
    2020-01-06    52822.707031
    2020-01-07    53108.238281
    2020-01-08    54059.992188
                      ...     
    2021-06-15    80900.000000
    2021-06-16    81800.000000
    2021-06-17    80900.000000
    2021-06-18    80500.000000
    2021-06-21    79900.000000
    Name: 수정된 종가, Length: 364, dtype: float64




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
      <th>고가</th>
      <th>저가</th>
      <th>시작가</th>
      <th>거래량</th>
      <th>수정된 종가</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>364.000000</td>
      <td>364.000000</td>
      <td>364.000000</td>
      <td>3.640000e+02</td>
      <td>364.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>66107.417582</td>
      <td>64710.302198</td>
      <td>65385.439560</td>
      <td>2.177086e+07</td>
      <td>63862.361521</td>
    </tr>
    <tr>
      <th>std</th>
      <td>13532.998134</td>
      <td>13381.609627</td>
      <td>13414.690441</td>
      <td>9.814952e+06</td>
      <td>14255.590204</td>
    </tr>
    <tr>
      <th>min</th>
      <td>43550.000000</td>
      <td>42300.000000</td>
      <td>42600.000000</td>
      <td>0.000000e+00</td>
      <td>40449.824219</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>55500.000000</td>
      <td>54100.000000</td>
      <td>54800.000000</td>
      <td>1.540158e+07</td>
      <td>52506.777344</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>60450.000000</td>
      <td>59500.000000</td>
      <td>60150.000000</td>
      <td>1.924594e+07</td>
      <td>57676.681641</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>81750.000000</td>
      <td>80725.000000</td>
      <td>81100.000000</td>
      <td>2.534348e+07</td>
      <td>81009.970703</td>
    </tr>
    <tr>
      <th>max</th>
      <td>96800.000000</td>
      <td>89500.000000</td>
      <td>90300.000000</td>
      <td>9.030618e+07</td>
      <td>90597.414062</td>
    </tr>
  </tbody>
</table>
</div>



#### 2021년 1월 15일의 데이터


```python
df.loc['2021-01-15']
```




    High         9.180000e+04
    Low          8.800000e+04
    Open         8.980000e+04
    Close        8.800000e+04
    Volume       3.343181e+07
    Adj Close    8.761069e+04
    Name: 2021-01-15 00:00:00, dtype: float64



#### 시작가 대비 종가가 높았던 날의 데이터


```python
df [ df['시작가'] < df['수정된 종가'] ]
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
      <th>고가</th>
      <th>저가</th>
      <th>시작가</th>
      <th>거래량</th>
      <th>수정된 종가</th>
    </tr>
    <tr>
      <th>Date</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2020-03-13</th>
      <td>51600.0</td>
      <td>46850.0</td>
      <td>47450.0</td>
      <td>59462933.0</td>
      <td>47540.437500</td>
    </tr>
    <tr>
      <th>2020-03-24</th>
      <td>46950.0</td>
      <td>43050.0</td>
      <td>43850.0</td>
      <td>49801908.0</td>
      <td>44685.156250</td>
    </tr>
    <tr>
      <th>2020-06-03</th>
      <td>55000.0</td>
      <td>51700.0</td>
      <td>51800.0</td>
      <td>49257814.0</td>
      <td>52253.925781</td>
    </tr>
    <tr>
      <th>2020-11-13</th>
      <td>63200.0</td>
      <td>61000.0</td>
      <td>61300.0</td>
      <td>31508829.0</td>
      <td>61375.773438</td>
    </tr>
    <tr>
      <th>2020-11-16</th>
      <td>66700.0</td>
      <td>63900.0</td>
      <td>64000.0</td>
      <td>36354334.0</td>
      <td>64386.292969</td>
    </tr>
    <tr>
      <th>2020-11-23</th>
      <td>67800.0</td>
      <td>64700.0</td>
      <td>64800.0</td>
      <td>27134398.0</td>
      <td>65551.656250</td>
    </tr>
    <tr>
      <th>2020-12-24</th>
      <td>78800.0</td>
      <td>74000.0</td>
      <td>74100.0</td>
      <td>32502870.0</td>
      <td>75554.351562</td>
    </tr>
    <tr>
      <th>2020-12-30</th>
      <td>81300.0</td>
      <td>77300.0</td>
      <td>77400.0</td>
      <td>29417421.0</td>
      <td>80641.656250</td>
    </tr>
    <tr>
      <th>2021-01-04</th>
      <td>84400.0</td>
      <td>80200.0</td>
      <td>81000.0</td>
      <td>38655276.0</td>
      <td>82632.804688</td>
    </tr>
    <tr>
      <th>2021-01-05</th>
      <td>83900.0</td>
      <td>81600.0</td>
      <td>81600.0</td>
      <td>35335669.0</td>
      <td>83528.820312</td>
    </tr>
    <tr>
      <th>2021-01-08</th>
      <td>90000.0</td>
      <td>83000.0</td>
      <td>83300.0</td>
      <td>59013307.0</td>
      <td>88407.148438</td>
    </tr>
    <tr>
      <th>2021-01-11</th>
      <td>96800.0</td>
      <td>89500.0</td>
      <td>90000.0</td>
      <td>90306177.0</td>
      <td>90597.414062</td>
    </tr>
    <tr>
      <th>2021-01-14</th>
      <td>90000.0</td>
      <td>88700.0</td>
      <td>88700.0</td>
      <td>26393970.0</td>
      <td>89303.164062</td>
    </tr>
    <tr>
      <th>2021-01-19</th>
      <td>88000.0</td>
      <td>83600.0</td>
      <td>84500.0</td>
      <td>39895044.0</td>
      <td>86615.109375</td>
    </tr>
    <tr>
      <th>2021-01-21</th>
      <td>88600.0</td>
      <td>86500.0</td>
      <td>87500.0</td>
      <td>25318011.0</td>
      <td>87710.242188</td>
    </tr>
    <tr>
      <th>2021-01-25</th>
      <td>89900.0</td>
      <td>86300.0</td>
      <td>87000.0</td>
      <td>27258534.0</td>
      <td>89004.492188</td>
    </tr>
    <tr>
      <th>2021-01-28</th>
      <td>85600.0</td>
      <td>83200.0</td>
      <td>83200.0</td>
      <td>31859808.0</td>
      <td>83329.710938</td>
    </tr>
    <tr>
      <th>2021-02-01</th>
      <td>83400.0</td>
      <td>81000.0</td>
      <td>81700.0</td>
      <td>28046832.0</td>
      <td>82632.804688</td>
    </tr>
    <tr>
      <th>2021-02-05</th>
      <td>84000.0</td>
      <td>82500.0</td>
      <td>83100.0</td>
      <td>18036835.0</td>
      <td>83130.593750</td>
    </tr>
    <tr>
      <th>2021-02-15</th>
      <td>84500.0</td>
      <td>83300.0</td>
      <td>83800.0</td>
      <td>23529706.0</td>
      <td>83827.500000</td>
    </tr>
    <tr>
      <th>2021-02-16</th>
      <td>86000.0</td>
      <td>84200.0</td>
      <td>84500.0</td>
      <td>20483100.0</td>
      <td>84524.398438</td>
    </tr>
    <tr>
      <th>2021-02-23</th>
      <td>82900.0</td>
      <td>81100.0</td>
      <td>81200.0</td>
      <td>20587314.0</td>
      <td>81637.226562</td>
    </tr>
    <tr>
      <th>2021-02-25</th>
      <td>85400.0</td>
      <td>83000.0</td>
      <td>84000.0</td>
      <td>34155986.0</td>
      <td>84922.632812</td>
    </tr>
    <tr>
      <th>2021-03-03</th>
      <td>84000.0</td>
      <td>82800.0</td>
      <td>83500.0</td>
      <td>19882132.0</td>
      <td>83628.382812</td>
    </tr>
    <tr>
      <th>2021-03-05</th>
      <td>82600.0</td>
      <td>81100.0</td>
      <td>81100.0</td>
      <td>20508971.0</td>
      <td>81736.789062</td>
    </tr>
    <tr>
      <th>2021-03-11</th>
      <td>82500.0</td>
      <td>81000.0</td>
      <td>81000.0</td>
      <td>23818297.0</td>
      <td>81637.226562</td>
    </tr>
    <tr>
      <th>2021-03-16</th>
      <td>83000.0</td>
      <td>82100.0</td>
      <td>82200.0</td>
      <td>12293537.0</td>
      <td>82433.687500</td>
    </tr>
    <tr>
      <th>2021-03-30</th>
      <td>82300.0</td>
      <td>81300.0</td>
      <td>81600.0</td>
      <td>13121698.0</td>
      <td>82200.000000</td>
    </tr>
    <tr>
      <th>2021-04-01</th>
      <td>83000.0</td>
      <td>82000.0</td>
      <td>82500.0</td>
      <td>18676461.0</td>
      <td>82900.000000</td>
    </tr>
    <tr>
      <th>2021-04-02</th>
      <td>85200.0</td>
      <td>83900.0</td>
      <td>84000.0</td>
      <td>22997538.0</td>
      <td>84800.000000</td>
    </tr>
    <tr>
      <th>2021-04-13</th>
      <td>84500.0</td>
      <td>82800.0</td>
      <td>83000.0</td>
      <td>15238206.0</td>
      <td>84000.000000</td>
    </tr>
    <tr>
      <th>2021-04-15</th>
      <td>84500.0</td>
      <td>83400.0</td>
      <td>83700.0</td>
      <td>16377412.0</td>
      <td>84100.000000</td>
    </tr>
    <tr>
      <th>2021-04-20</th>
      <td>84000.0</td>
      <td>83100.0</td>
      <td>83300.0</td>
      <td>15521965.0</td>
      <td>83900.000000</td>
    </tr>
    <tr>
      <th>2021-04-23</th>
      <td>82900.0</td>
      <td>81600.0</td>
      <td>81900.0</td>
      <td>17805080.0</td>
      <td>82800.000000</td>
    </tr>
    <tr>
      <th>2021-04-26</th>
      <td>83500.0</td>
      <td>82600.0</td>
      <td>82900.0</td>
      <td>15489938.0</td>
      <td>83500.000000</td>
    </tr>
    <tr>
      <th>2021-05-03</th>
      <td>82400.0</td>
      <td>81000.0</td>
      <td>81000.0</td>
      <td>15710336.0</td>
      <td>81700.000000</td>
    </tr>
    <tr>
      <th>2021-05-04</th>
      <td>82600.0</td>
      <td>81800.0</td>
      <td>81900.0</td>
      <td>12532550.0</td>
      <td>82600.000000</td>
    </tr>
    <tr>
      <th>2021-05-06</th>
      <td>82300.0</td>
      <td>81700.0</td>
      <td>81700.0</td>
      <td>17047511.0</td>
      <td>82300.000000</td>
    </tr>
    <tr>
      <th>2021-05-07</th>
      <td>82100.0</td>
      <td>81500.0</td>
      <td>81800.0</td>
      <td>14154882.0</td>
      <td>81900.000000</td>
    </tr>
    <tr>
      <th>2021-05-10</th>
      <td>83500.0</td>
      <td>81800.0</td>
      <td>82300.0</td>
      <td>19385027.0</td>
      <td>83200.000000</td>
    </tr>
    <tr>
      <th>2021-05-14</th>
      <td>80300.0</td>
      <td>78900.0</td>
      <td>79000.0</td>
      <td>16450920.0</td>
      <td>80100.000000</td>
    </tr>
    <tr>
      <th>2021-05-20</th>
      <td>79700.0</td>
      <td>79100.0</td>
      <td>79400.0</td>
      <td>16541828.0</td>
      <td>79500.000000</td>
    </tr>
    <tr>
      <th>2021-05-28</th>
      <td>80400.0</td>
      <td>79400.0</td>
      <td>79800.0</td>
      <td>12360199.0</td>
      <td>80100.000000</td>
    </tr>
    <tr>
      <th>2021-05-31</th>
      <td>80600.0</td>
      <td>79600.0</td>
      <td>80300.0</td>
      <td>13321324.0</td>
      <td>80500.000000</td>
    </tr>
    <tr>
      <th>2021-06-01</th>
      <td>81300.0</td>
      <td>80100.0</td>
      <td>80500.0</td>
      <td>14058401.0</td>
      <td>80600.000000</td>
    </tr>
    <tr>
      <th>2021-06-02</th>
      <td>81400.0</td>
      <td>80300.0</td>
      <td>80400.0</td>
      <td>16414644.0</td>
      <td>80800.000000</td>
    </tr>
    <tr>
      <th>2021-06-03</th>
      <td>83000.0</td>
      <td>81100.0</td>
      <td>81300.0</td>
      <td>29546007.0</td>
      <td>82800.000000</td>
    </tr>
    <tr>
      <th>2021-06-16</th>
      <td>81900.0</td>
      <td>81100.0</td>
      <td>81500.0</td>
      <td>14999855.0</td>
      <td>81800.000000</td>
    </tr>
    <tr>
      <th>2021-06-21</th>
      <td>79900.0</td>
      <td>79600.0</td>
      <td>79700.0</td>
      <td>1528067.0</td>
      <td>79900.000000</td>
    </tr>
  </tbody>
</table>
</div>



#### 종가 기준 주가가 90,000원 이상이 데이터


```python
df [ df['수정된 종가'] >= 90000 ]
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
      <th>고가</th>
      <th>저가</th>
      <th>시작가</th>
      <th>거래량</th>
      <th>수정된 종가</th>
    </tr>
    <tr>
      <th>Date</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2021-01-11</th>
      <td>96800.0</td>
      <td>89500.0</td>
      <td>90000.0</td>
      <td>90306177.0</td>
      <td>90597.414062</td>
    </tr>
    <tr>
      <th>2021-01-12</th>
      <td>91400.0</td>
      <td>87800.0</td>
      <td>90300.0</td>
      <td>48682416.0</td>
      <td>90199.179688</td>
    </tr>
  </tbody>
</table>
</div>



#### 100번째 데이터


```python
df.iloc[99]
```




    고가        5.120000e+04
    저가        4.990000e+04
    시작가       5.110000e+04
    거래량       3.130932e+07
    수정된 종가    4.832290e+04
    Name: 2020-05-28 00:00:00, dtype: float64




```python

```
