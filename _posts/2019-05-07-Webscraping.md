---
title: Webscraping
subtitle: Homework // L07 Webscraping
---
<i>Task: Scraping the “The Daily Dispatch”: download issues of “Richmond Times Dispatch” (Years 1860-1865, only!), which are available at: http://www.perseus.tufts.edu/hopper/collection?collection=Perseus:collection:RichTimes)</i>

For the fulfillment of this task I use the program ´wget´. It allows me to automate the downloading of web content by giving the URL.
For this I need three commands:

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight"><code>wget -i file_with_links.txt
wget -i links.txt -P ./folderYouWantToSaveTo/ -nc 
</code></pre></div></div>

As we see in the first line, we first have to create a list of links that can then be downloaded by wget. For this we would have to go to the page of the journal and try to understand the structure of the page and its contents.

### 1. Recognizing the pattern

First we have a look at the homepage of the archive of "The Daily Dispatch":

<img src="/img/the_daily_dispatch_homepage.png" />

And look at some issues:
<img src="/img/the_daily_dispatch_issue1.png" />

A closer look at the page structure reveals two useful clues:
1. There are not only two orange XML buttons, which display the output as XML, there is also a more inconspicuous direct link for download.
<img src="/img/xml_version_download.png" />

2. if you click through further editions, you will quickly see that the URLs of the individual editions follow a pattern.






### 2. Downloading the links

### 3. Cleaning the links

### 4. Downloading the data
