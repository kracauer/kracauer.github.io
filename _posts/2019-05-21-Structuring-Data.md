---
title: Structuring Data
subtitle: Homework // L09 Structuring Data
---
<b>Task 1:</b> <i>Reformatting the “Dispatch”: generate one TSV-file with the entire content of the “Dispatch”, where each article (or, more broadly—an entry) is a single record; each record should include:</i>
<ol>
  <li><i>date</i></li>
  <li><i>type of an entry (there are articles, advertisements, notices, etc.)</i></li>
  <li><i>header</i></li>
  <li><i>the text of an entry</i></li>
</ol>

<b>Solution 1:</b> Reformatting the Data

The following code excerpt identifies the searched HTML tags from all existing articles and then creates three files: a CSV file, a TSV file, and a JSON object.

```python
import re, os, csv, json

source = "Directory of given files"

lof = os.listdir(source)
counter = 0 

# declaration of list
list = []

# starts loop over all given files
for f in lof:
    if f.startswith("dltext"):
        with open(source + f, "r", encoding="utf8") as f1:
            text = f1.read()

            # searches for the second date tag
            date = re.search(r'<date value="([\d-]+)"', text).group(1)

            # splits each div3 container
            split = re.split("<div3 ", text)

            c = 0 

            # starts loop over all containers
            for s in split[1:]:
                c += 1
                # restores the text from the split function
                s = "<div3 " + s 

                # tries to find the type tag
                try:
                    unitType = re.search(r'type="([^\"]+)"', s).group(1)
                # catches exception from search function and assigns "noType"
                except:
                    unitType = "noType"
                    
                # tries to find a header
                try:
                    header = re.search(r'<head>(.*)</head>', s).group(1)
                    header = re.sub("<[^<]+>", "", header)
                # catches exceptions and assigns "NO HEADER"
                except:
                    header = "NO HEADER"

                # cleans up the text
                text = re.sub("<[^<]+>", "", s)
                text = re.sub(" +\n|\n +", "\n", text)
                text = re.sub("\n+", ";;; ", text)

                # generates unique identifier
                fName = date+"_"+unitType+"_"+str(c)

                # sets the dictionary values
                dict = {
                    'id': fName,
                    'date': date,
                    'type': unitType,
                    'header': header,
                    'text': text
                }
                # appends dictionary to dictionary list
                list.append(dict)

# creates list of dictionary keys
csv_columns =  ['id', 'date', 'type', 'header', 'text']

# creates and opens tsv file
with open('dispatch.tsv', 'w', encoding = "utf8") as f:
    # gets writer object from csv library
    writer = csv.DictWriter(f, delimiter ='\t',fieldnames = csv_columns)
    # writes header into file
    writer.writeheader()
    # writes data into file by each line
    for data in list:
        writer.writerow(data)

# creates and opens csv file
with open('dispatch.csv', 'w', encoding = "utf8") as f:
    # gets writer object from csv library
    writer = csv.DictWriter(f,fieldnames = csv_columns)
    # writes header into file
    writer.writeheader()
    # writes data into file by each line
    for data in list:
        writer.writerow(data)

# and here's how all of it looks with json
with open("dispatch.json", "w", encoding = "utf8") as f:
    json.dump(list, f)

```

