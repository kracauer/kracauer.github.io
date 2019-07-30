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

```python
import re, os, csv, json

source = "C:/Users/bkoschicek/Desktop/tnt/dispatch/dispatch-small/"
#target = "C:/Users/bkoschicek/Desktop/tnt/dispatch/dispatch/modified/"

lof = os.listdir(source)
counter = 0 # general counter to keep track of the progress

# a list to hold all the dictionaries
list = []

for f in lof:
    if f.startswith("dltext"): # fileName test
        with open(source + f, "r", encoding="utf8") as f1:
            text = f1.read()

            # try to find the date
            date = re.search(r'<date value="([\d-]+)"', text).group(1)

            # splitting the issue into articles/items
            split = re.split("<div3 ", text)

            c = 0 # item counter
            for s in split[1:]:
                c += 1
                s = "<div3 " + s # a step to restore the integrity of items
                #input(s)

                # try to find a unitType, if not then there will bei "noType"
                try:
                    unitType = re.search(r'type="([^\"]+)"', s).group(1)
                except:
                    unitType = "noType"
                    print(s)

                # try to find a header, if not then there will be "NO HEADER"
                try:
                    header = re.search(r'<head>(.*)</head>', s).group(1)
                    header = re.sub("<[^<]+>", "", header)
                except:
                    header = "NO HEADER"
                    print("\nNo header found!\n")

                # cleaing the file of all the tags
                text = re.sub("<[^<]+>", "", s)
                text = re.sub(" +\n|\n +", "\n", text)
                text = re.sub("\n+", ";;; ", text)

                # generating necessary bits
                fName = date+"_"+unitType+"_"+str(c)

                # creating a dictionary with all the needed entries
                dict = {
                    'id': fName,
                    'date': date,
                    'type': unitType,
                    'header': header,
                    'text': text
                }
                # appending the dict to a list
                list.append(dict)

## Writing the whole thing
# column header names for the csv/tsv
csv_columns =  ['id', 'date', 'type', 'header', 'text']

# writing tsv with the csv library
with open('dipatch.tsv', 'w', encoding="utf8") as f:
    writer = csv.DictWriter(f, delimiter ='\t',fieldnames=csv_columns)
    writer.writeheader()
    for data in list:
        writer.writerow(data)

# writing csv with the csv library
with open('dipatch.csv', 'w', encoding="utf8") as f:
    writer = csv.DictWriter(f,fieldnames=csv_columns)
    writer.writeheader()
    for data in list:
        writer.writerow(data)

# writing json with the jason library
with open("dispatch.json", "w", encoding="utf8") as f:
    json.dump(list, f)


```
