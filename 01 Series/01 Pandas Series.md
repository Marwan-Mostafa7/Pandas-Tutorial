
# Pandas tutorial

### Series


```python
import pandas as pd
```


```python
l = [1, 5, 10, 8]
```


```python
pd.Series(l)
```




    0     1
    1     5
    2    10
    3     8
    dtype: int64




```python
l[1] = "ASD"
```


```python
l
```




    [1, 'ASD', 10, 8]




```python
pd.Series(l)
```




    0      1
    1    ASD
    2     10
    3      8
    dtype: object




```python
ser = pd.Series(l)
```


```python
type(ser[0])
```




    int




```python
type(ser[1])
```




    str




```python
i = ['A', 'B', 'C', 'D']
```


```python
list('ABCD')
```




    ['A', 'B', 'C', 'D']




```python
ser.set_axis(i, inplace=True)
```


```python
ser
```




    A      1
    B    ASD
    C     10
    D      8
    dtype: object




```python
ser.set_axis(list('XYZL'), inplace= True)
```


```python
ser
```




    X      1
    Y    ASD
    Z     10
    L      8
    dtype: object




```python
ser2 = pd.Series([1, 10,1000, 100, 10, 1], index=list('ABCDEF'))
```


```python
ser2
```




    A       1
    B      10
    C    1000
    D     100
    E      10
    F       1
    dtype: int64




```python
ser2['A'] + ser2['B']
```




    11




```python
ser2.A + ser2.B
```




    11




```python
ser2.values
```




    array([   1,   10, 1000,  100,   10,    1], dtype=int64)




```python
ser2.value_counts()
```




    10      2
    1       2
    100     1
    1000    1
    dtype: int64




```python
ser2.sum()
```




    1122




```python
ser2
```




    A       1
    B      10
    C    1000
    D     100
    E      10
    F       1
    dtype: int64




```python
ser2[2]
```




    1000




```python
ser2.loc['C']
```




    1000




```python
ser2.iloc[2]
```




    1000



### Extra methods


```python
ser2.div(10)
```




    A      0.1
    B      1.0
    C    100.0
    D     10.0
    E      1.0
    F      0.1
    dtype: float64




```python
ser2.mul(100)
```




    A       100
    B      1000
    C    100000
    D     10000
    E      1000
    F       100
    dtype: int64




```python
ser2.add(5)
```




    A       6
    B      15
    C    1005
    D     105
    E      15
    F       6
    dtype: int64




```python
ser2.sub(1)
```




    A      0
    B      9
    C    999
    D     99
    E      9
    F      0
    dtype: int64




```python
ser2.cumsum()
```




    A       1
    B      11
    C    1011
    D    1111
    E    1121
    F    1122
    dtype: int64




```python
ser2.diff()
```




    A      NaN
    B      9.0
    C    990.0
    D   -900.0
    E    -90.0
    F     -9.0
    dtype: float64



### apply


```python
def add5(x):
    return x + 5
```


```python
ser2.apply(add5)
```




    A       6
    B      15
    C    1005
    D     105
    E      15
    F       6
    dtype: int64




```python
add5_l = lambda x: x + 5
```


```python
ser2.apply(add5_l)
```




    A       6
    B      15
    C    1005
    D     105
    E      15
    F       6
    dtype: int64




```python
ser2.apply(lambda x: x + 5)
```




    A       6
    B      15
    C    1005
    D     105
    E      15
    F       6
    dtype: int64




```python
ser2.apply(lambda x: str(x))
```




    A       1
    B      10
    C    1000
    D     100
    E      10
    F       1
    dtype: object




```python
ser2.apply(str)
```




    A       1
    B      10
    C    1000
    D     100
    E      10
    F       1
    dtype: object



### Assignment

Calculate mean of Series `ser2` with 3 ways


```python
ser2.mean()
```




    187.0




```python
ser2.cumsum()[-1] / ser2.count()
```




    187.0




```python
ser2.sum() / ser2.count()
```




    187.0


