---
title: Webscraping
subtitle: Homework // L07 Webscraping
---
<i>Task: Scraping the “The Daily Dispatch”: download issues of “Richmond Times Dispatch” (Years 1860-1865, only!), which are available at: http://www.perseus.tufts.edu/hopper/collection?collection=Perseus:collection:RichTimes)</i>

For the fulfillment of this task I use the program ´wget´. It allows me to automate the downloading of web content by giving the URL.
For this I need three commands:

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight"><code> wget -i file_with_links.txt
wget -i links.txt -P ./folderYouWantToSaveTo/ -nc 
</code></pre></div></div>

As we see in the first line, we first have to create a list of links that can then be downloaded by wget. For this we would have to go to the page of the journal and try to understand the structure of the page and its contents.

### 1. Recognizing the pattern

<img src="/img/the_daily_dispatch_issue1.png"/>
<img src="/img/the_daily_dispatch_isssue1_xml.png"/>
<img src="/img/the_daily_dispatch_homepage.png"/>



### 2. Downloading the links

### 3. Cleaning the links

### 4. Downloading the data
