# Stata Tutorial


```python
import os
os.getcwd()
os.chdir('C:/Users/anubh/OneDrive/planning-commission-gddp-data/AP/')
```


```python
import tabula
# Read pdf into list of DataFrame
dfs = tabula.read_pdf("AP 1999-00.pdf", pages='all', multiple_tables=True)

# convert PDF into CSV file
tabula.convert_into("AP 1999-00.pdf", "AP 1999-00.csv", output_format="csv", pages='all')
```

<a id='another_cell'></a>
# Excel


```python
import os
import tabula
import pandas as pd
os.chdir('C:/Users/anubh/OneDrive/planning-commission-gddp-data/AP/')
```


```python
df = tabula.read_pdf("AP 1999-00.pdf", pages = 'all')[1]
# df.head()
```


```python
# df.to_excel("AP 1999-00.xlsx")
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
    

#  [Tabula: Batch Extract](#another_cell)


```python
import tabula
tabula.convert_into_by_batch("C:/Users/anubh/OneDrive/planning-commission-gddp-data/AP", output_format='csv', pages='all')
```
