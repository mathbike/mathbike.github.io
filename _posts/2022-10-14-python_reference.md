---
title:  Python Reference
categories: [Python]
tags: [python]
---


### Create new file:
```python
t = open('file.txt', 'w')
t.close()
```

### Delete all lines from text file:
```python
t = open('file.txt', 'w')
t.close()
```

### Get number of files in a directory:
```python
import os
folder_path = '/home/mike/directory'
number_of_files = len(os.listdir(folder_path))
```

### Open text file and add each line as an entry in a list:
```python
list1 = []
with open('file.txt', 'r') as f:
    for line in f:
        list1.append(line)
# remove /n from list
list2 = [x.replace('\n', '') for x in list1]
# access entire list
print(list2)
# access specific value in list
print(list2[0])
```

### Create json file:
```python
import json
# function to append data to file.json
def write_json(data, filename="file.json"):
    with open (filename, "w") as f:
        json.dump(data, f, indent=4)
# data to add
data = { "key1": "" }
# or
data = { "key1": [] }
# call function
write_json(data)
```

### Add values to json file:
```python
import json
# create temporary dictionary
tempdict = { "key1":"", "key2":"" }
# temporary variables
key1 = "value1"
key2 = "value2"
# append values from list to values in dictionary
tempdict["key1"] = key1
tempdict["key2"] = key2
# function to append tempdict to file.json
def write_json(data, filename="file.json"):
    with open (filename, "w") as f:
        json.dump(data, f, indent=4)
# append to a specific key
with open ("file.json") as json_file:
    data = json.load(json_file)
    temp = data["key1"]
    temp.append(tempdict)
# call function
write_json(data)
```

### Access values in json file:
```python
import json
# load json data from json file
with open('file.json', 'r') as f:
    data = json.load(f)
# get key1
print(data["key1"])
# get key1, value1, key1
print(data["key1"][0]["key1"])
```

### Save request response to json file:
```python
import requests, json
# first send request, then:
data = response.json()
with open('data.json', 'w') as f:
    json.dump(data, f, indent=4)
```

### Floor then round to a certain number of decimal places:
```python
import math
number = 28855.235
decimal_number = 0.01
# get number of decimal places as a number; e.g. 2
decimal_places = len(str(decimal_number).split(".")[1])
print(decimal_places)
# floor to certain decimal places
floored = math.floor(number / decimal_number) * decimal_number
print(floored)
# round to certain decimal places
rounded = round(28855.234, decimal_places)
print(rounded)
```

###  Pandas:
```python
import pandas as pd
# from csv
df = pd.read_csv('file.csv')
# set index to Time
df.set_index("Time", inplace=True)
# search column equal to, return row
df = df.loc[df['Volume'] == 0]
# get all cells equal to
df = df[df.eq(0)]
# return True/False if values is in df
df = 0 in df.values
print(df)
```

---
<br>
{% include signature.md %}