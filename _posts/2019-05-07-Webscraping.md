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

A closer look at the page structure reveals three useful clues:
1. There are not only two orange XML buttons, which display the output as XML, there is also a more inconspicuous direct link for download.

<img src="/img/xml_version_download.png" />

2. In addition, if you compare the download links of different isses, you can quickly see that they follow a pattern.

3. If you click through further editions, you will quickly see that the URLs of the individual issues also follow a pattern, which is very similar to the XML links.

These three observations we make use of to create a list of XML files to download.

### 2. Downloading the links
We go back to the home page of "The Daily Dispatch" and look at the source code. It already contains the links to all single issues from 1860 to 1865. We download the source and clean it with the regular expression `text\?doc[^"]+` from all unnecessary page elements. What remains are 1349 URLs, which we collect in a document.

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight"><code>text?doc=Perseus%3atext%3a2006.05.0001
text?doc=Perseus%3atext%3a2006.05.0002
text?doc=Perseus%3atext%3a2006.05.0003
text?doc=Perseus%3atext%3a2006.05.0004
text?doc=Perseus%3atext%3a2006.05.0154
text?doc=Perseus%3atext%3a2006.05.0005
[...]
text?doc=Perseus%3atext%3a2006.05.1348
text?doc=Perseus%3atext%3a2006.05.1349
text?doc=Perseus%3atext%3a2006.05.1350
text?doc=Perseus%3atext%3a2006.05.1351
text?doc=Perseus%3atext%3a2006.05.1352
text?doc=Perseus%3atext%3a2006.05.1353
</code></pre></div></div>

### 3. Adapting the links

Now it's almost done. In the comparison of the now received links to the XML-download, a detail is noticeable:
Apart from the beginning, which can be added later (and As in upper and lower case, which doesn't matter for us), there is a missing <b>dl</b> in our current link list:
<div class="highlighter-rouge"><div class="highlight"><pre class="highlight"><code> www.perseus.tufts.edu/hopper/<b>dl</b>text?doc=Perseus%3Atext%3A2006.05.0001
                                text?doc=Perseus%3atext%3a2006.05.0001
</code></pre></div></div>

Finally we add the prefix `www.perseus.tufts.edu/hopper/dl` to all our links and save the list in a common document.
### 4. Downloading the data
