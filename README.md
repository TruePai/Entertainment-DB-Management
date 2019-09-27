# Entertainment DB Management

Entertainment database contains large amount of real data and reference data in csv file format from different live entertainment sites.

Also it has some reference files for the live data.

It can not be read and written at one time. This can be implemented by reading rows one by one and using multi-threading.

![banner](https://raw.githubusercontent.com/TruePai/Entertainment-DB-Management/master/screenshot/1.png)

## Run

```bash
python dataproc.py
```

## Main part

```python
maxInt = sys.maxsize
while True:
    # decrease the maxInt value by factor 10
    # as long as the OverflowError occurs.
    try:
        csv.field_size_limit(maxInt)
        break
    except OverflowError:
        maxInt = int(maxInt / 10)
......

# read entertainment db
def readEntertainDB(filename):
    try:
        with open(filename, mode='rt', encoding='UTF8') as file:
            datareader = csv.reader(file)
            for row in datareader:
......

# read csv.gz file
with gzip.open(inputname, 'rt', encoding='UTF8') as readFile:
    datareader = csv.reader(readFile)
......

# using multi-threading
thread = threading.Thread(target=thread_function, args=(INPUT_DIR + file, datawriter))
```

#### Feel free to update me with any issues or directly contact to [truepai@outloook.com](mailto:truepai@outlook.com)
