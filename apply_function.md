# Code used :


```python
import pandas as pd 

data = pd.DataFrame({"power_level": [12000, 16000, 4000, 1500, 3000, 
                                     2000, 1600, 2000, 300],
                     "uniform color": ["orange", "blue", "black", "orange",
                                       "purple", "green", "orange", "orange","orange"],
                     "species": ["saiyan","saiyan","saiyan","half saiyan",
                                 "namak","human","human","human","human"]}, 
                     index = ["Goku","Vegeta", "Nappa","Gohan",
                                   "Piccolo","Tien","Yamcha", "Krillin","Roshi"])

data

# Use .apply() to apply a function to a Series (single column)


def my_function(x, h, l):
    if x ＞  h:
        return("high")
    if x ＞  l:
        return("med")
    return ("low")

data["power_level"].apply(my_function, args = [10000, 2000])
```

# Apply a function to each column with axis = 0
# Can be used to create new rows/summary rows

```python
def mode(x):
    return x.mode()

data.apply(mode, axis = 0)
```
### Apply a function to each row with axis = 1
### Can be used to create new columns/summary columns

```python
def max_str_len(x):
    return max([len(str(v)) for v in x])

data.apply(max_str_len, axis = 1)
```
### Apply a function to each row, referencing column names:

```python
def make_char_string(x):
    return(f"{x.species} with power level: {x.power_level}")

data.apply(make_char_string, axis = 1 )
```
