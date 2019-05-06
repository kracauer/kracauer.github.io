---
title: Regular Expressions
subtitle: Homework // L06 Regular Expressions
---
Below you will find a data set and corresponding expressions, written with regular expressions, which can uniquely find the respective data sets.

# Part 1

## 1.1 What regular expression matches each of the following?<br>
Dataset: `“eat”, “eats”, “ate”, “eaten”, “eating”, “eater”, “eatery”`
Solution: `[ea]t?r?s?y?i?n?g?`

## 1.2 Find all Qadhdhafis...<br>
Solution:`\bM[oau']+m+[ae]r? ([aelAIE]+)?[- ]?[GK][h]?a[dhz]+af+[iy]\b`

## 1.3 Find all variations of Iṣbahān (construct the shortest possible regular expression)<br>
Dataset: `Iṣbahān, Iṣfahān, Isbahan,
	Isfahan, Esfāhān, Esfahān,
	Esfahan, Hispahan,
	iṣbahān, iṣfahān, isbahan,
	isfahan, esfāhān, esfahān,
	esfahan, hispahan,`
Solution: ???

# Part 2

## 2.1 Conversion: Convert “Askin, Leon” > “Leon Askin” <br>
Dataset: `Askin, Leon
	Berger, Helmut
	Berger, Senta
	Gold, Käthe
	Haid, Liane
	Hörbiger, Attila
	Hörbiger, Christiane\
	Hörbiger, Paul
	Kogler, Melanie
	Lamarr, Hedy
	Merkatz, Karl
	Minichmayr, Birgit
	Moser, Hans
	Nalder, Reggie
	Schell, Maximilian
	Schneider, Romy
	Schwarzenegger, Arnold
	Waltz, Christoph
	Werner, Oskar
	Vader, Darth`

Solution: Find `\t(\w+), (\w+)?\n`
	Replace: ????
 

## 2.2 Simple: Construct regular expressions that finds references all Austrian cities. <br>
Dataset: `Major cities in Austria are as follows: Vienna, Graz, Linz,
	Salzburg, Innsbruck, Klagenfurt, Villach, Wels, Sankt Pölten,
	Dornbirn, Wiener Neustadt, Steyr, Feldkirch, Bregenz, Leonding,
	Klosterneuburg, Baden bei Wien, Wolfsberg, Leoben, Krems, Traun,
	Amstetten, Lustenau, Kapfenberg, Mödling, Hallein, Kufstein,
	Traiskirchen, Schwechat, Braunau am Inn, Stockerau, Saalfelden,
	Ansfelden, Tulln, Hohenems, Spittal an der Drau, Telfs, Ternitz,
	Perchtoldsdorf, Feldkirchen, Bludenz, Bad Ischl, Eisenstadt,
	Schwaz, Hall in Tirol, Gmunden, Wörgl, Wals-Siezenheim,
	Marchtrenk, Bruck an der Mur, Sankt Veit an der Glan,
	Korneuburg, Neunkirchen, Hard, Vöcklabruck, Lienz, Rankweil,
	Hollabrunn, Enns, Brunn am Gebirge, Ried im Innkreis,
	Bad Vöslau, Waidhofen, Knittelfeld, Trofaiach, Mistelbach,	
	Zwettl, Völkermarkt, Götzis, Sankt Johann im Pongau,
	Gänserndorf, Gerasdorf bei Wien, Ebreichsdorf, Bischofshofen,
	Groß-Enzersdorf, Seekirchen am Wallersee, Sankt Andrä`

Solution: ???

## 2.3 More Difficult: Construct regular expression that finds only cities from 1) Lower Austria; 2) Salzburg. <br>
Solution: Find: `([\w -]+) \(Lower Austria\)\b`  OR <br>
`\b([\w -]+) \(Lower Austria\)\b` + Salzburg ???
Replace: ???

