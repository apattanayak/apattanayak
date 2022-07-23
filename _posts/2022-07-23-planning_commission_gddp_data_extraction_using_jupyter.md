```python
import os
os.getcwd()
os.chdir('C:/Users/anubh/OneDrive/planning-commission-gddp-data')
```


```python
import tabula
# Read pdf into list of DataFrame
dfs = tabula.read_pdf("AP 1999-00.pdf", pages='all', multiple_tables=True)

# convert PDF into CSV file
tabula.convert_into("AP 1999-00.pdf", "AP 1999-00.csv", output_format="csv", pages='all')
```

# Excel


```python
import tabula
import pandas as pd
os.chdir('C:/Users/anubh/OneDrive/planning-commission-gddp-data')
```


```python
df = tabula.read_pdf("AP 1999-00.pdf", pages = 'all')[1]
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
      <th>Sr.</th>
      <th>District</th>
      <th>Transport</th>
      <th>Storage</th>
      <th>Commu-</th>
      <th>Banking &amp;</th>
      <th>Real, Owner</th>
      <th>Public</th>
      <th>Other</th>
      <th>Total</th>
      <th>Population</th>
      <th>Per Capita</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>No.</td>
      <td>Name</td>
      <td>by other</td>
      <td>NaN</td>
      <td>nication</td>
      <td>Insurance</td>
      <td>ship of Dwel.</td>
      <td>Adminis-</td>
      <td>Services</td>
      <td>DDP</td>
      <td>(In '00)</td>
      <td>Income</td>
    </tr>
    <tr>
      <th>1</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>means</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>B.Ser.&amp; Legal</td>
      <td>tration</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>(Rs.)</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>2</td>
      <td>14</td>
      <td>15.0</td>
      <td>16</td>
      <td>17</td>
      <td>18</td>
      <td>19</td>
      <td>20</td>
      <td>21</td>
      <td>22</td>
      <td>23</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1</td>
      <td>Srikakulam</td>
      <td>9917</td>
      <td>122.0</td>
      <td>2489</td>
      <td>15055</td>
      <td>29696</td>
      <td>13088</td>
      <td>38571</td>
      <td>288130</td>
      <td>25297</td>
      <td>11390</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2</td>
      <td>Vizianagaram</td>
      <td>6630</td>
      <td>369.0</td>
      <td>2697</td>
      <td>14728</td>
      <td>25712</td>
      <td>13428</td>
      <td>38413</td>
      <td>263685</td>
      <td>22509</td>
      <td>11714</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.to_excel("AP 1999-00.xlsx")
```

# Tabula


```python
os.chdir('C:/Users/anubh/OneDrive/planning-commission-gddp-data/AP')
import tabula
import pandas as pd
import glob


path = r'C:/Users/anubh/OneDrive/planning-commission-gddp-data/AP'
all_files = glob.glob(path + "/*.pdf")
print (all_files)

df = []

for f1 in all_files:
    df = pd.concat(tabula.read_pdf(f1, pages='all', multiple_tables=True))
    #df = pd.concat(tabula.read_pdf(f1, pages='all', multiple_tables=True) for f1 in all_files)
    df.to_csv("output.csv", index = False)
```

    ['C:/Users/anubh/OneDrive/planning-commission-gddp-data/AP\\AP 1999-00.pdf', 'C:/Users/anubh/OneDrive/planning-commission-gddp-data/AP\\AP 2000-01.pdf', 'C:/Users/anubh/OneDrive/planning-commission-gddp-data/AP\\AP 2001-02.pdf', 'C:/Users/anubh/OneDrive/planning-commission-gddp-data/AP\\AP 2002-03.pdf', 'C:/Users/anubh/OneDrive/planning-commission-gddp-data/AP\\AP 2003-04.pdf', 'C:/Users/anubh/OneDrive/planning-commission-gddp-data/AP\\AP 2004-05.pdf', 'C:/Users/anubh/OneDrive/planning-commission-gddp-data/AP\\AP 2005-06.pdf']
    

# Tabula: Batch Extract


```python
import tabula
tabula.convert_into_by_batch("C:/Users/anubh/OneDrive/planning-commission-gddp-data/AP", output_format='xlsx', pages='all')
```


    ---------------------------------------------------------------------------

    ValueError                                Traceback (most recent call last)

    Input In [2], in <cell line: 2>()
          1 import tabula
    ----> 2 tabula.convert_into_by_batch("C:/Users/anubh/OneDrive/planning-commission-gddp-data/AP", output_format='excel', pages='all')
    

    File ~\AppData\Roaming\Python\Python39\site-packages\tabula\io.py:599, in convert_into_by_batch(input_dir, output_format, java_options, **kwargs)
        596 if input_dir is None or not os.path.isdir(input_dir):
        597     raise ValueError("'input_dir' should be an existing directory path")
    --> 599 kwargs["format"] = _extract_format_for_conversion(output_format)
        601 java_options = _build_java_options(java_options)
        603 # Option for batch
    

    File ~\AppData\Roaming\Python\Python39\site-packages\tabula\io.py:632, in _extract_format_for_conversion(output_format)
        630     return "TSV"
        631 else:
    --> 632     raise ValueError("Unknown 'output_format': '{}'".format(output_format))
    

    ValueError: Unknown 'output_format': 'excel'



```python

```
