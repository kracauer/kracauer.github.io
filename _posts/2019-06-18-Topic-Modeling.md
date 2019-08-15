---
title: Topic Modeling
subtitle: Homework // L12 Topic Modeling
---
<b>Task 1:</b> <i>Topic modeling the “Dispatch”: using the provided R-script, run topic modeling on the “Dispatch”.</i><br>
<b>Task 2:</b> <i>Change the number of topics to 30 and compare new results with the results for 40 topics. Record your observations.</i><br>
<b>Task 3:</b> <i>Publish your observations as a blogpost on your website; compare your results with those of Rob Nelson’s Mining the Dispatch (http://dsl.richmond.edu/dispatch/).</i><br>

## Solution 1: Running the Model

In order to get the script to work, some libraries are needed, which can be downloaded with the command `pip install nltk gensim spacy pyLDAvis matplotlib numpy pandas plotly pprint` in one go.

# Solution 2: Running the Script with Different Number of Topics

The number of topics to be generated is set in lines 32 to 35. Here it is important to note that the desired number of topics in all lines must be adjusted manually. 

<img src="/img/line_32-35_jupyter_notebook.png"/>

In the example image, the number of topics is set to 30 and is applied to the year 1864 of the "Dispatch".

It is also important to know that the running time of the script is significantly extended with each topic increase, which is especially relevant for low-performance computers. For me, the calculation of 20 topics only takes a few minutes, whereas 30 takes half an hour and 40 over 60 minutes.

The generated topics look as follows.

### 20 Topics
<img src="/img/20.png"/>

### 30 Topics
<img src="/img/30.png"/>

### 40 Topics
<img src="/img/40.png"/>

### Observations:
In contrast to T30 and T40, the graphs for T20 are much closer to each other, so the topics generated seem denser in themselves, i.e. more congruent. Interestingly, T30 has the strongest outbreaks, whereas T40 seems to form more congruent topics.

From the end of August 1864, T20 shows a particularly high density of recurring themes dominated by concepts of the money economy. In 1864, the (Un)United States of America were in the third of four years of civil war. From the end of the year onwards, it can be read from the data that there seem to have been more calls to finance the war. 
`Bonds` and `certificates` in particular seem to have played a role in this. It is also interesting to note that the unit of currency `cent` appears but not the dollar, which could stand for the focus on smaller amounts of money. According to the ["Inflation Calculator"](http://www.in2013dollars.com/us/inflation/1864?amount=1), 1 dollar in 1865 today equals 16.34 dollars.
