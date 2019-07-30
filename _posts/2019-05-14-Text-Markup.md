---
title: Text Markup
subtitle: Homework // L08 Text Markup ([TEI] XML ...)
---
The following steps refer to the "Daily Dispatch" dataset that we webscraped with wget in [Lesson 07](https://kracauer.github.io/2019-05-07-Webscraping/).


<b>Task 1a:</b>
<i>Cleaning the “Dispatch”: write a python script that will create clean copies of text from each issue of the “Dispatch” that you scraped before (make sure to keep the originals intact!).</i>

Note: For the script the library of "Beatiful Soup 4" is used to efficiently recognize HTML elements.

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight"><code>from bs4 import BeautifulSoup
import re
import os
newPathToFolder = "~/Documents/Dh_Tools/lesson8/articles_try_2/"
pathToFolder = "~/Documents/Dh_Tools/lesson7/4th/"
listOfFiles = os.listdir(pathToFolder)

# for loop that opens all files of a defined folder and stores it with BeautifulSoup in variable soup
for f in listOfFiles:
    soup = BeautifulSoup (open(pathToFolder+f, "r", encoding="utf8"), features="html.parser")
    # searches for list items of "date" and return maximum two elemens
    issue_date = soup.find_all("date", limit=2)[1] # only returns the second match
    issue_date = issue_date.get("value")
    # searches for all tags with "div3" and stores it in variable "articles"
    articles = soup.find_all("div3", {"type":"article"})
    # for loop to count each articles with "a"
    # automatically seperates all articles in "item"
    for a, item in enumerate(articles[1:]): # with the latest part after articles the counter starts at 1 instead of 0
        # assiging the counter to a variable
        counter = a
        # cleaning all articles of xml tags
        article = re.sub("&lt;[^&lt;]+&gt;", "", str(item))
        # creates a new file in a target folder with name + article counter + name + issue_date + txt file
        newfile = newPathToFolder  + "dispatch_" + str(issue_date) + "_article_no_" + str(counter) + ".txt"
        # opens the newfile and writes each article into a sperate file
        with open(newfile, "w", encoding="utf8") as f9:
            f9.write(article)
</code></pre></div></div>

<b>Task 1b:</b>
<i>Cleaning the “Dispatch”: write a python script that will create clean copies of articles (!) from all issues of the “Dispatch”. (again, make sure to keep the originals intact!).</i>




