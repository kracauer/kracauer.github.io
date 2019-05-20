---
title: Regular Expressions
subtitle: Homework // L06 Regular Expressions
---
Below you will find a data set and corresponding expressions, written with regular expressions, which can uniquely find the respective data sets.

## Part 1

### 1.1 What regular expression matches each of the following?<br>
Data set: `“eat”, “eats”, “ate”, “eaten”, “eating”, “eater”, “eatery”`<br>
Solution: `\b(eat(s|en)?|ate)\b`

### 1.2 Find all Qadhdhafis...<br>
Data set: `Maummar Gaddafi, Moamar AI Kadafi, Moamar al-Gaddafi,
	Moamar el Gaddafi, Moamar El Kadhafi, Moamar Gaddafi,
	Moamar Gadhafi, Moamer El Kazzafi, Moamer Gaddafi,
	Moamer Kadhafi, Moamma Gaddafi, Moammar el Gadhafi,
	Moammar El Kadhafi, Mo'ammar el-Gadhafi, Moammar Gaddafi,
	Moammar Gadhafi, Mo'ammar Gadhafi, Moammar Ghadafi,
	Moammar Kadhafi, Moammar Khadaffy, Moammar Khadafy` <br>

Solution:`\bM[oau']+m+[ae]r? ([aelAIE]+)?[- ]?[GK][h]?a[dhz]+af+[iy]\b`

### 1.3 Find all variations of Iṣbahān (construct the shortest possible regular expression)<br>
Data set: `Iṣbahān, Iṣfahān, Isbahan,
	Isfahan, Esfāhān, Esfahān,
	Esfahan, Hispahan,
	iṣbahān, iṣfahān, isbahan,
	isfahan, esfāhān, esfahān,
	esfahan, hispahan,` <br>

Solution: ´\b()\b´

## Part 2

### 2.1 Conversion: Convert “Askin, Leon” > “Leon Askin” <br>
Data set: `Askin, Leon
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
	Vader, Darth` <br>

Solution: <br>
Find: ´^\t([\w ]+), ([\w ]+)$´ <br>
Replace: ´\t\2 \1´
 

### 2.2 Simple: Construct regular expressions that finds references all Austrian cities. <br>
Data set: `Major cities in Austria are as follows: Vienna, Graz, Linz,
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
	Groß-Enzersdorf, Seekirchen am Wallersee, Sankt Andrä` <br>

Solution: Connect all citynames with a pipe `|`

### 2.3 More Difficult: Construct regular expression that finds only cities from 1) Lower Austria; 2) Salzburg. <br>
Data set: `Vienna (Vienna), Graz (Styria), Linz (Upper Austria),
	Salzburg (Salzburg), Innsbruck (Tyrol), Klagenfurt (Carinthia),
	Villach (Carinthia), Wels (Upper Austria),
	Sankt Pölten (Lower Austria), Dornbirn (Vorarlberg),
	Wiener Neustadt (Lower Austria), Steyr (Upper Austria),
	Feldkirch (Vorarlberg), Bregenz (Vorarlberg),
	Leonding (Upper Austria), Klosterneuburg (Lower Austria),
	Baden bei Wien (Lower Austria), Wolfsberg (Carinthia),
	Leoben (Styria), Krems (Lower Austria), Traun (Upper Austria),
	Amstetten (Lower Austria), Lustenau (Vorarlberg),
	Kapfenberg (Styria), Mödling (Lower Austria),
	Hallein (Salzburg), Kufstein (Tyrol),
	Traiskirchen (Lower Austria), Schwechat (Lower Austria),
	Braunau am Inn (Upper Austria), Stockerau (Lower Austria),
	Saalfelden (Salzburg), Ansfelden (Upper Austria),
	Tulln (Lower Austria), Hohenems (Vorarlberg),
	Spittal an der Drau (Carinthia), Telfs (Tyrol),
	Ternitz (Lower Austria), Perchtoldsdorf (Lower Austria),
	Feldkirchen (Carinthia), Bludenz (Vorarlberg),
	Bad Ischl (Upper Austria), Eisenstadt (Burgenland),
	Schwaz (Tyrol), Hall in Tirol (Tyrol), Gmunden (Upper Austria),
	Wörgl (Tyrol), Wals-Siezenheim (Salzburg),
	Marchtrenk (Upper Austria), Bruck an der Mur (Styria),
	Sankt Veit an der Glan (Carinthia), Korneuburg (Lower Austria),
	Neunkirchen (Lower Austria), Hard (Vorarlberg),
	Vöcklabruck (Upper Austria), Lienz (Tyrol),
	Rankweil (Vorarlberg), Hollabrunn (Lower Austria),
	Enns (Upper Austria), Brunn am Gebirge (Lower Austria),
	Ried im Innkreis (Upper Austria), Bad Vöslau (Lower Austria),
	Waidhofen (Lower Austria), Knittelfeld (Styria),
	Trofaiach (Styria), Mistelbach (Lower Austria),
	Zwettl (Lower Austria), Völkermarkt (Carinthia),
	Götzis (Vorarlberg), Sankt Johann im Pongau (Salzburg),
	Gänserndorf (Lower Austria), Gerasdorf bei Wien (Lower Austria),
	Ebreichsdorf (Lower Austria), Bischofshofen (Salzburg),
	Groß-Enzersdorf (Lower Austria),
	Seekirchen am Wallersee (Salzburg), Sankt Andrä (Carinthia)`

Solution: <br>
Find: `([\w -]+) \(Lower Austria\)\b`  AND <br>
`\b([\w -]+) \(Salzburg\)`


