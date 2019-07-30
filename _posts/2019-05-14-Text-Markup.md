---
title: Text Markup
subtitle: Homework // L08 Text Markup ([TEI] XML ...)
---
The following steps refer to the "Daily Dispatch" dataset that we webscraped with wget in [Lesson 07](https://kracauer.github.io/2019-05-07-Webscraping/).


<b>Task 1a:</b>
<i>Cleaning the “Dispatch”: write a python script that will create clean copies of text from each issue of the “Dispatch” that you scraped before (make sure to keep the originals intact!).</i>

```python
import re
import os
pathToFolder = "Directory in which the dataset of the "Daily Dispatch" is located"
newPathToFolder = "Directory where the modified dataset is to be stored"

# retrieves all files in the given directory
listOfFiles = os.listdir(pathToFolder)

# loop over files
for f in listOfFiles:
  with open(pathToFolder+f, "r", encoding="utf8") as f1:
     data = f1.read()
     # deletes all xml tags (=in between < and >)
     text = re.sub("&lt;[^&lt;]+&gt;"," ", data)
     # sets name for processed file
     newfile = "_" + pathToFolder + f + "_processed.txt"
     # creates, opens and fills processed file
     with open(newfile, "w", encoding="utf8") as f9:
         f9.write(text)
</code></pre></div></div>

<b>Task 1b:</b>
<i>Cleaning the “Dispatch”: write a python script that will create clean copies of articles (!) from all issues of the “Dispatch”. (again, make sure to keep the originals intact!).</i>

Note: For the script the library of "Beautiful Soup 4" is used to efficiently recognize XML elements.

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight"><code>from bs4 import BeautifulSoup
import re
import os
pathToFolder = "Directory in which the dataset of the "Daily Dispatch" is located"
newPathToFolder = "Directory where the modified dataset is to be stored"

listOfFiles = os.listdir(pathToFolder)
#
# loop over given files
for f in listOfFiles:
    # opens file to parse input
    file_handle = open(pathToFolder+f, "r", encoding="utf8")
    # parse text using bs4
    soup = BeautifulSoup (file_handle, features="html.parser")
    # looks for list items of "date" and return maximum two elemens
    # only returns the second match
    issue_date = soup.find_all("date", limit=2)[1] 
    issue_date = issue_date.get("value")
    # searches for all tags with "div3" and stores it in variable "articles"
    articles = soup.find_all("div3", {"type":"article"})
    # for loop to count each articles with "a"
    # seperates all articles in "item"
    # with the latest part after articles the counter starts at 1 instead of 0
    for a, item in enumerate(articles[1:]): 
        # assigins counter to a variable
        counter = a
        # removes all xml tags
        article = re.sub("&lt;[^&lt;]+&gt;", "", str(item))
        # sets name for the parsed file
        newfile = newPathToFolder  + "dispatch_" + str(issue_date) + "_article_no_" + str(counter) + ".txt"
        # creates and opens new file and appends the parsed text
        with open(newfile, "w", encoding="utf8") as f9:
            f9.write(article)
```






