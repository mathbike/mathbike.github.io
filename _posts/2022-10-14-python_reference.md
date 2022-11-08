---
title:  Python Reference
categories: [Python]
tags: [python]
---


### Delete all lines that start with comments and print statements from file:
```python
with open("file_input.py", "r") as file_input:
    with open("file_output.py", "w") as file_output: 
        for line in file_input:
            if line.startswith('#'):
                continue
            if line.startswith('print'):
                continue
            file_output.write(line)
```

### Get number of files in a directory:
```python
import os
folder_path = '/home/mike/directory'
number_of_files = len(os.listdir(folder_path))
```

### Open text file and add each line as an element in a list:
```python
list1 = []
with open('file.txt', 'r') as f:
    for line in f:
        list1.append(line)
# remove \n from list
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
# round 28855.235 to 28855.23
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

### Pandas:
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

### Logging:
```python
import logging

# create logger
logger = logging.getLogger(__name__)
# set level
logger.setLevel(logging.INFO)
# create formatter
formatter = logging.Formatter('%(asctime)s:%(name)s:%(message)s','%Y-%m-%d %H:%M:%S')
# create file handler
file_handler = logging.FileHandler('main.log')
# add formatter to file handler
file_handler.setFormatter(formatter)
# add file handler to logger
logger.addHandler(file_handler)

# code
x = 1
y = 2
z = x + y

# call log method
logger.info('Add: {} + {} = {}'.format(x, y, z))
```

### Threads:
```python
from threading import Thread

def 
```
