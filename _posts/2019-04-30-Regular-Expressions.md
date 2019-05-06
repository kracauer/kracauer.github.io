---
title: Regular Expressions
subtitle: Homework // L06 Regular Expressions
---
#Regular Expression Practical Session created by 

Below you will find a data set and corresponding expressions, written with regular expressions, which can uniquely find the respective data sets.

# Part 1

## 1.1 <br>
What regular expression matches each of the following?
	`“eat”, “eats”, “ate”, “eaten”, “eating”, “eater”,
	“eatery”`
Solution: `[ea]t?r?s?y?i?n?g?`

## 1.2 <br>
Solution:`\bM[oau']+m+[ae]r? ([aelAIE]+)?[- ]?[GK][h]?a[dhz]+af+[iy]\b`

## 1.3 <br>
Solution:`\t(\w+), (\w+)?\n`

## 1.4<br>
Solution:`([\w -]+) \(Lower Austria\)\b`  OR <br>
`\b([\w -]+) \(Lower Austria\)\b`
