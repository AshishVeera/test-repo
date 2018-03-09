
import csv
import MySQLdb
import pandas as pd
from sqlalchemy import create_engine


```python
DATABASE = 'testdb'
engine = create_engine("mysql+mysqldb://root:"+'root'+"@localhost/"+DATABASE)
connection = engine.connect()
```


```python
iris = pd.read_csv('iris.data', header=None)
```


```python
iris[:5]
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
      <th>0</th>
      <th>1</th>
      <th>2</th>
      <th>3</th>
      <th>4</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>5.1</td>
      <td>3.5</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>Iris-setosa</td>
    </tr>
    <tr>
      <th>1</th>
      <td>4.9</td>
      <td>3.0</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>Iris-setosa</td>
    </tr>
    <tr>
      <th>2</th>
      <td>4.7</td>
      <td>3.2</td>
      <td>1.3</td>
      <td>0.2</td>
      <td>Iris-setosa</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4.6</td>
      <td>3.1</td>
      <td>1.5</td>
      <td>0.2</td>
      <td>Iris-setosa</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5.0</td>
      <td>3.6</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>Iris-setosa</td>
    </tr>
  </tbody>
</table>
</div>




```python
iris.to_sql('iris_data', con=engine, if_exists='append', index=False)
```


```python
iris.to_sql('iris_data', con=engine, if_exists='replace', index=False)
```


```python
result = connection.execute("select * from iris_data")
```


```python
for row in result:
    print(row)
```

    (5.1, 3.5, 1.4, 0.2, 'Iris-setosa')
    (4.9, 3.0, 1.4, 0.2, 'Iris-setosa')
    (4.7, 3.2, 1.3, 0.2, 'Iris-setosa')
    (4.6, 3.1, 1.5, 0.2, 'Iris-setosa')
    (5.0, 3.6, 1.4, 0.2, 'Iris-setosa')
    (5.4, 3.9, 1.7, 0.4, 'Iris-setosa')
    (4.6, 3.4, 1.4, 0.3, 'Iris-setosa')
    (5.0, 3.4, 1.5, 0.2, 'Iris-setosa')
    (4.4, 2.9, 1.4, 0.2, 'Iris-setosa')
    (4.9, 3.1, 1.5, 0.1, 'Iris-setosa')
    (5.4, 3.7, 1.5, 0.2, 'Iris-setosa')
    (4.8, 3.4, 1.6, 0.2, 'Iris-setosa')
    (4.8, 3.0, 1.4, 0.1, 'Iris-setosa')
    (4.3, 3.0, 1.1, 0.1, 'Iris-setosa')
    (5.8, 4.0, 1.2, 0.2, 'Iris-setosa')
    (5.7, 4.4, 1.5, 0.4, 'Iris-setosa')
    (5.4, 3.9, 1.3, 0.4, 'Iris-setosa')
    (5.1, 3.5, 1.4, 0.3, 'Iris-setosa')
    (5.7, 3.8, 1.7, 0.3, 'Iris-setosa')
    (5.1, 3.8, 1.5, 0.3, 'Iris-setosa')
    (5.4, 3.4, 1.7, 0.2, 'Iris-setosa')
    (5.1, 3.7, 1.5, 0.4, 'Iris-setosa')
    (4.6, 3.6, 1.0, 0.2, 'Iris-setosa')
    (5.1, 3.3, 1.7, 0.5, 'Iris-setosa')
    (4.8, 3.4, 1.9, 0.2, 'Iris-setosa')
    (5.0, 3.0, 1.6, 0.2, 'Iris-setosa')
    (5.0, 3.4, 1.6, 0.4, 'Iris-setosa')
    (5.2, 3.5, 1.5, 0.2, 'Iris-setosa')
    (5.2, 3.4, 1.4, 0.2, 'Iris-setosa')
    (4.7, 3.2, 1.6, 0.2, 'Iris-setosa')
    (4.8, 3.1, 1.6, 0.2, 'Iris-setosa')
    (5.4, 3.4, 1.5, 0.4, 'Iris-setosa')
    (5.2, 4.1, 1.5, 0.1, 'Iris-setosa')
    (5.5, 4.2, 1.4, 0.2, 'Iris-setosa')
    (4.9, 3.1, 1.5, 0.1, 'Iris-setosa')
    (5.0, 3.2, 1.2, 0.2, 'Iris-setosa')
    (5.5, 3.5, 1.3, 0.2, 'Iris-setosa')
    (4.9, 3.1, 1.5, 0.1, 'Iris-setosa')
    (4.4, 3.0, 1.3, 0.2, 'Iris-setosa')
    (5.1, 3.4, 1.5, 0.2, 'Iris-setosa')
    (5.0, 3.5, 1.3, 0.3, 'Iris-setosa')
    (4.5, 2.3, 1.3, 0.3, 'Iris-setosa')
    (4.4, 3.2, 1.3, 0.2, 'Iris-setosa')
    (5.0, 3.5, 1.6, 0.6, 'Iris-setosa')
    (5.1, 3.8, 1.9, 0.4, 'Iris-setosa')
    (4.8, 3.0, 1.4, 0.3, 'Iris-setosa')
    (5.1, 3.8, 1.6, 0.2, 'Iris-setosa')
    (4.6, 3.2, 1.4, 0.2, 'Iris-setosa')
    (5.3, 3.7, 1.5, 0.2, 'Iris-setosa')
    (5.0, 3.3, 1.4, 0.2, 'Iris-setosa')
    (7.0, 3.2, 4.7, 1.4, 'Iris-versicolor')
    (6.4, 3.2, 4.5, 1.5, 'Iris-versicolor')
    (6.9, 3.1, 4.9, 1.5, 'Iris-versicolor')
    (5.5, 2.3, 4.0, 1.3, 'Iris-versicolor')
    (6.5, 2.8, 4.6, 1.5, 'Iris-versicolor')
    (5.7, 2.8, 4.5, 1.3, 'Iris-versicolor')
    (6.3, 3.3, 4.7, 1.6, 'Iris-versicolor')
    (4.9, 2.4, 3.3, 1.0, 'Iris-versicolor')
    (6.6, 2.9, 4.6, 1.3, 'Iris-versicolor')
    (5.2, 2.7, 3.9, 1.4, 'Iris-versicolor')
    (5.0, 2.0, 3.5, 1.0, 'Iris-versicolor')
    (5.9, 3.0, 4.2, 1.5, 'Iris-versicolor')
    (6.0, 2.2, 4.0, 1.0, 'Iris-versicolor')
    (6.1, 2.9, 4.7, 1.4, 'Iris-versicolor')
    (5.6, 2.9, 3.6, 1.3, 'Iris-versicolor')
    (6.7, 3.1, 4.4, 1.4, 'Iris-versicolor')
    (5.6, 3.0, 4.5, 1.5, 'Iris-versicolor')
    (5.8, 2.7, 4.1, 1.0, 'Iris-versicolor')
    (6.2, 2.2, 4.5, 1.5, 'Iris-versicolor')
    (5.6, 2.5, 3.9, 1.1, 'Iris-versicolor')
    (5.9, 3.2, 4.8, 1.8, 'Iris-versicolor')
    (6.1, 2.8, 4.0, 1.3, 'Iris-versicolor')
    (6.3, 2.5, 4.9, 1.5, 'Iris-versicolor')
    (6.1, 2.8, 4.7, 1.2, 'Iris-versicolor')
    (6.4, 2.9, 4.3, 1.3, 'Iris-versicolor')
    (6.6, 3.0, 4.4, 1.4, 'Iris-versicolor')
    (6.8, 2.8, 4.8, 1.4, 'Iris-versicolor')
    (6.7, 3.0, 5.0, 1.7, 'Iris-versicolor')
    (6.0, 2.9, 4.5, 1.5, 'Iris-versicolor')
    (5.7, 2.6, 3.5, 1.0, 'Iris-versicolor')
    (5.5, 2.4, 3.8, 1.1, 'Iris-versicolor')
    (5.5, 2.4, 3.7, 1.0, 'Iris-versicolor')
    (5.8, 2.7, 3.9, 1.2, 'Iris-versicolor')
    (6.0, 2.7, 5.1, 1.6, 'Iris-versicolor')
    (5.4, 3.0, 4.5, 1.5, 'Iris-versicolor')
    (6.0, 3.4, 4.5, 1.6, 'Iris-versicolor')
    (6.7, 3.1, 4.7, 1.5, 'Iris-versicolor')
    (6.3, 2.3, 4.4, 1.3, 'Iris-versicolor')
    (5.6, 3.0, 4.1, 1.3, 'Iris-versicolor')
    (5.5, 2.5, 4.0, 1.3, 'Iris-versicolor')
    (5.5, 2.6, 4.4, 1.2, 'Iris-versicolor')
    (6.1, 3.0, 4.6, 1.4, 'Iris-versicolor')
    (5.8, 2.6, 4.0, 1.2, 'Iris-versicolor')
    (5.0, 2.3, 3.3, 1.0, 'Iris-versicolor')
    (5.6, 2.7, 4.2, 1.3, 'Iris-versicolor')
    (5.7, 3.0, 4.2, 1.2, 'Iris-versicolor')
    (5.7, 2.9, 4.2, 1.3, 'Iris-versicolor')
    (6.2, 2.9, 4.3, 1.3, 'Iris-versicolor')
    (5.1, 2.5, 3.0, 1.1, 'Iris-versicolor')
    (5.7, 2.8, 4.1, 1.3, 'Iris-versicolor')
    (6.3, 3.3, 6.0, 2.5, 'Iris-virginica')
    (5.8, 2.7, 5.1, 1.9, 'Iris-virginica')
    (7.1, 3.0, 5.9, 2.1, 'Iris-virginica')
    (6.3, 2.9, 5.6, 1.8, 'Iris-virginica')
    (6.5, 3.0, 5.8, 2.2, 'Iris-virginica')
    (7.6, 3.0, 6.6, 2.1, 'Iris-virginica')
    (4.9, 2.5, 4.5, 1.7, 'Iris-virginica')
    (7.3, 2.9, 6.3, 1.8, 'Iris-virginica')
    (6.7, 2.5, 5.8, 1.8, 'Iris-virginica')
    (7.2, 3.6, 6.1, 2.5, 'Iris-virginica')
    (6.5, 3.2, 5.1, 2.0, 'Iris-virginica')
    (6.4, 2.7, 5.3, 1.9, 'Iris-virginica')
    (6.8, 3.0, 5.5, 2.1, 'Iris-virginica')
    (5.7, 2.5, 5.0, 2.0, 'Iris-virginica')
    (5.8, 2.8, 5.1, 2.4, 'Iris-virginica')
    (6.4, 3.2, 5.3, 2.3, 'Iris-virginica')
    (6.5, 3.0, 5.5, 1.8, 'Iris-virginica')
    (7.7, 3.8, 6.7, 2.2, 'Iris-virginica')
    (7.7, 2.6, 6.9, 2.3, 'Iris-virginica')
    (6.0, 2.2, 5.0, 1.5, 'Iris-virginica')
    (6.9, 3.2, 5.7, 2.3, 'Iris-virginica')
    (5.6, 2.8, 4.9, 2.0, 'Iris-virginica')
    (7.7, 2.8, 6.7, 2.0, 'Iris-virginica')
    (6.3, 2.7, 4.9, 1.8, 'Iris-virginica')
    (6.7, 3.3, 5.7, 2.1, 'Iris-virginica')
    (7.2, 3.2, 6.0, 1.8, 'Iris-virginica')
    (6.2, 2.8, 4.8, 1.8, 'Iris-virginica')
    (6.1, 3.0, 4.9, 1.8, 'Iris-virginica')
    (6.4, 2.8, 5.6, 2.1, 'Iris-virginica')
    (7.2, 3.0, 5.8, 1.6, 'Iris-virginica')
    (7.4, 2.8, 6.1, 1.9, 'Iris-virginica')
    (7.9, 3.8, 6.4, 2.0, 'Iris-virginica')
    (6.4, 2.8, 5.6, 2.2, 'Iris-virginica')
    (6.3, 2.8, 5.1, 1.5, 'Iris-virginica')
    (6.1, 2.6, 5.6, 1.4, 'Iris-virginica')
    (7.7, 3.0, 6.1, 2.3, 'Iris-virginica')
    (6.3, 3.4, 5.6, 2.4, 'Iris-virginica')
    (6.4, 3.1, 5.5, 1.8, 'Iris-virginica')
    (6.0, 3.0, 4.8, 1.8, 'Iris-virginica')
    (6.9, 3.1, 5.4, 2.1, 'Iris-virginica')
    (6.7, 3.1, 5.6, 2.4, 'Iris-virginica')
    (6.9, 3.1, 5.1, 2.3, 'Iris-virginica')
    (5.8, 2.7, 5.1, 1.9, 'Iris-virginica')
    (6.8, 3.2, 5.9, 2.3, 'Iris-virginica')
    (6.7, 3.3, 5.7, 2.5, 'Iris-virginica')
    (6.7, 3.0, 5.2, 2.3, 'Iris-virginica')
    (6.3, 2.5, 5.0, 1.9, 'Iris-virginica')
    (6.5, 3.0, 5.2, 2.0, 'Iris-virginica')
    (6.2, 3.4, 5.4, 2.3, 'Iris-virginica')
    (5.9, 3.0, 5.1, 1.8, 'Iris-virginica')



```python
result = connection.execute("select * from iris_data")
pd.DataFrame.from_records(result)
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
      <th>0</th>
      <th>1</th>
      <th>2</th>
      <th>3</th>
      <th>4</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>5.1</td>
      <td>3.5</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>Iris-setosa</td>
    </tr>
    <tr>
      <th>1</th>
      <td>4.9</td>
      <td>3.0</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>Iris-setosa</td>
    </tr>
    <tr>
      <th>2</th>
      <td>4.7</td>
      <td>3.2</td>
      <td>1.3</td>
      <td>0.2</td>
      <td>Iris-setosa</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4.6</td>
      <td>3.1</td>
      <td>1.5</td>
      <td>0.2</td>
      <td>Iris-setosa</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5.0</td>
      <td>3.6</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>Iris-setosa</td>
    </tr>
    <tr>
      <th>5</th>
      <td>5.4</td>
      <td>3.9</td>
      <td>1.7</td>
      <td>0.4</td>
      <td>Iris-setosa</td>
    </tr>
    <tr>
      <th>6</th>
      <td>4.6</td>
      <td>3.4</td>
      <td>1.4</td>
      <td>0.3</td>
      <td>Iris-setosa</td>
    </tr>
    <tr>
      <th>7</th>
      <td>5.0</td>
      <td>3.4</td>
      <td>1.5</td>
      <td>0.2</td>
      <td>Iris-setosa</td>
    </tr>
    <tr>
      <th>8</th>
      <td>4.4</td>
      <td>2.9</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>Iris-setosa</td>
    </tr>
    <tr>
      <th>9</th>
      <td>4.9</td>
      <td>3.1</td>
      <td>1.5</td>
      <td>0.1</td>
      <td>Iris-setosa</td>
    </tr>
    <tr>
      <th>10</th>
      <td>5.4</td>
      <td>3.7</td>
      <td>1.5</td>
      <td>0.2</td>
      <td>Iris-setosa</td>
    </tr>
    <tr>
      <th>11</th>
      <td>4.8</td>
      <td>3.4</td>
      <td>1.6</td>
      <td>0.2</td>
      <td>Iris-setosa</td>
    </tr>
    <tr>
      <th>12</th>
      <td>4.8</td>
      <td>3.0</td>
      <td>1.4</td>
      <td>0.1</td>
      <td>Iris-setosa</td>
    </tr>
    <tr>
      <th>13</th>
      <td>4.3</td>
      <td>3.0</td>
      <td>1.1</td>
      <td>0.1</td>
      <td>Iris-setosa</td>
    </tr>
    <tr>
      <th>14</th>
      <td>5.8</td>
      <td>4.0</td>
      <td>1.2</td>
      <td>0.2</td>
      <td>Iris-setosa</td>
    </tr>
    <tr>
      <th>15</th>
      <td>5.7</td>
      <td>4.4</td>
      <td>1.5</td>
      <td>0.4</td>
      <td>Iris-setosa</td>
    </tr>
    <tr>
      <th>16</th>
      <td>5.4</td>
      <td>3.9</td>
      <td>1.3</td>
      <td>0.4</td>
      <td>Iris-setosa</td>
    </tr>
    <tr>
      <th>17</th>
      <td>5.1</td>
      <td>3.5</td>
      <td>1.4</td>
      <td>0.3</td>
      <td>Iris-setosa</td>
    </tr>
    <tr>
      <th>18</th>
      <td>5.7</td>
      <td>3.8</td>
      <td>1.7</td>
      <td>0.3</td>
      <td>Iris-setosa</td>
    </tr>
    <tr>
      <th>19</th>
      <td>5.1</td>
      <td>3.8</td>
      <td>1.5</td>
      <td>0.3</td>
      <td>Iris-setosa</td>
    </tr>
    <tr>
      <th>20</th>
      <td>5.4</td>
      <td>3.4</td>
      <td>1.7</td>
      <td>0.2</td>
      <td>Iris-setosa</td>
    </tr>
    <tr>
      <th>21</th>
      <td>5.1</td>
      <td>3.7</td>
      <td>1.5</td>
      <td>0.4</td>
      <td>Iris-setosa</td>
    </tr>
    <tr>
      <th>22</th>
      <td>4.6</td>
      <td>3.6</td>
      <td>1.0</td>
      <td>0.2</td>
      <td>Iris-setosa</td>
    </tr>
    <tr>
      <th>23</th>
      <td>5.1</td>
      <td>3.3</td>
      <td>1.7</td>
      <td>0.5</td>
      <td>Iris-setosa</td>
    </tr>
    <tr>
      <th>24</th>
      <td>4.8</td>
      <td>3.4</td>
      <td>1.9</td>
      <td>0.2</td>
      <td>Iris-setosa</td>
    </tr>
    <tr>
      <th>25</th>
      <td>5.0</td>
      <td>3.0</td>
      <td>1.6</td>
      <td>0.2</td>
      <td>Iris-setosa</td>
    </tr>
    <tr>
      <th>26</th>
      <td>5.0</td>
      <td>3.4</td>
      <td>1.6</td>
      <td>0.4</td>
      <td>Iris-setosa</td>
    </tr>
    <tr>
      <th>27</th>
      <td>5.2</td>
      <td>3.5</td>
      <td>1.5</td>
      <td>0.2</td>
      <td>Iris-setosa</td>
    </tr>
    <tr>
      <th>28</th>
      <td>5.2</td>
      <td>3.4</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>Iris-setosa</td>
    </tr>
    <tr>
      <th>29</th>
      <td>4.7</td>
      <td>3.2</td>
      <td>1.6</td>
      <td>0.2</td>
      <td>Iris-setosa</td>
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
      <th>120</th>
      <td>6.9</td>
      <td>3.2</td>
      <td>5.7</td>
      <td>2.3</td>
      <td>Iris-virginica</td>
    </tr>
    <tr>
      <th>121</th>
      <td>5.6</td>
      <td>2.8</td>
      <td>4.9</td>
      <td>2.0</td>
      <td>Iris-virginica</td>
    </tr>
    <tr>
      <th>122</th>
      <td>7.7</td>
      <td>2.8</td>
      <td>6.7</td>
      <td>2.0</td>
      <td>Iris-virginica</td>
    </tr>
    <tr>
      <th>123</th>
      <td>6.3</td>
      <td>2.7</td>
      <td>4.9</td>
      <td>1.8</td>
      <td>Iris-virginica</td>
    </tr>
    <tr>
      <th>124</th>
      <td>6.7</td>
      <td>3.3</td>
      <td>5.7</td>
      <td>2.1</td>
      <td>Iris-virginica</td>
    </tr>
    <tr>
      <th>125</th>
      <td>7.2</td>
      <td>3.2</td>
      <td>6.0</td>
      <td>1.8</td>
      <td>Iris-virginica</td>
    </tr>
    <tr>
      <th>126</th>
      <td>6.2</td>
      <td>2.8</td>
      <td>4.8</td>
      <td>1.8</td>
      <td>Iris-virginica</td>
    </tr>
    <tr>
      <th>127</th>
      <td>6.1</td>
      <td>3.0</td>
      <td>4.9</td>
      <td>1.8</td>
      <td>Iris-virginica</td>
    </tr>
    <tr>
      <th>128</th>
      <td>6.4</td>
      <td>2.8</td>
      <td>5.6</td>
      <td>2.1</td>
      <td>Iris-virginica</td>
    </tr>
    <tr>
      <th>129</th>
      <td>7.2</td>
      <td>3.0</td>
      <td>5.8</td>
      <td>1.6</td>
      <td>Iris-virginica</td>
    </tr>
    <tr>
      <th>130</th>
      <td>7.4</td>
      <td>2.8</td>
      <td>6.1</td>
      <td>1.9</td>
      <td>Iris-virginica</td>
    </tr>
    <tr>
      <th>131</th>
      <td>7.9</td>
      <td>3.8</td>
      <td>6.4</td>
      <td>2.0</td>
      <td>Iris-virginica</td>
    </tr>
    <tr>
      <th>132</th>
      <td>6.4</td>
      <td>2.8</td>
      <td>5.6</td>
      <td>2.2</td>
      <td>Iris-virginica</td>
    </tr>
    <tr>
      <th>133</th>
      <td>6.3</td>
      <td>2.8</td>
      <td>5.1</td>
      <td>1.5</td>
      <td>Iris-virginica</td>
    </tr>
    <tr>
      <th>134</th>
      <td>6.1</td>
      <td>2.6</td>
      <td>5.6</td>
      <td>1.4</td>
      <td>Iris-virginica</td>
    </tr>
    <tr>
      <th>135</th>
      <td>7.7</td>
      <td>3.0</td>
      <td>6.1</td>
      <td>2.3</td>
      <td>Iris-virginica</td>
    </tr>
    <tr>
      <th>136</th>
      <td>6.3</td>
      <td>3.4</td>
      <td>5.6</td>
      <td>2.4</td>
      <td>Iris-virginica</td>
    </tr>
    <tr>
      <th>137</th>
      <td>6.4</td>
      <td>3.1</td>
      <td>5.5</td>
      <td>1.8</td>
      <td>Iris-virginica</td>
    </tr>
    <tr>
      <th>138</th>
      <td>6.0</td>
      <td>3.0</td>
      <td>4.8</td>
      <td>1.8</td>
      <td>Iris-virginica</td>
    </tr>
    <tr>
      <th>139</th>
      <td>6.9</td>
      <td>3.1</td>
      <td>5.4</td>
      <td>2.1</td>
      <td>Iris-virginica</td>
    </tr>
    <tr>
      <th>140</th>
      <td>6.7</td>
      <td>3.1</td>
      <td>5.6</td>
      <td>2.4</td>
      <td>Iris-virginica</td>
    </tr>
    <tr>
      <th>141</th>
      <td>6.9</td>
      <td>3.1</td>
      <td>5.1</td>
      <td>2.3</td>
      <td>Iris-virginica</td>
    </tr>
    <tr>
      <th>142</th>
      <td>5.8</td>
      <td>2.7</td>
      <td>5.1</td>
      <td>1.9</td>
      <td>Iris-virginica</td>
    </tr>
    <tr>
      <th>143</th>
      <td>6.8</td>
      <td>3.2</td>
      <td>5.9</td>
      <td>2.3</td>
      <td>Iris-virginica</td>
    </tr>
    <tr>
      <th>144</th>
      <td>6.7</td>
      <td>3.3</td>
      <td>5.7</td>
      <td>2.5</td>
      <td>Iris-virginica</td>
    </tr>
    <tr>
      <th>145</th>
      <td>6.7</td>
      <td>3.0</td>
      <td>5.2</td>
      <td>2.3</td>
      <td>Iris-virginica</td>
    </tr>
    <tr>
      <th>146</th>
      <td>6.3</td>
      <td>2.5</td>
      <td>5.0</td>
      <td>1.9</td>
      <td>Iris-virginica</td>
    </tr>
    <tr>
      <th>147</th>
      <td>6.5</td>
      <td>3.0</td>
      <td>5.2</td>
      <td>2.0</td>
      <td>Iris-virginica</td>
    </tr>
    <tr>
      <th>148</th>
      <td>6.2</td>
      <td>3.4</td>
      <td>5.4</td>
      <td>2.3</td>
      <td>Iris-virginica</td>
    </tr>
    <tr>
      <th>149</th>
      <td>5.9</td>
      <td>3.0</td>
      <td>5.1</td>
      <td>1.8</td>
      <td>Iris-virginica</td>
    </tr>
  </tbody>
</table>
<p>150 rows × 5 columns</p>
</div>


