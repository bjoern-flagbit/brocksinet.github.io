---
layout: post
title: Memory für PHPStorm erhöhen
---
1.  Bevor du die Einstellungen machst starte PHPStorm und öffne deine Settings

	>	Suche nach "Memory" und klicke auf "Appearance"
	>		
	>	Aktiviere die Option "Show memory indicator"
	>		
	>	Rechts unten in der Taskleiste siehst du nun wie viel Memory für PHPStorm maximal reserviert sind
	>		
	>	Merke dir den Wert damit du auch die richtige Zeile bearbeitest

2.  Das PHPStorm **bin** Verzeichnis Öffnen 
	
	>	z.B. C:\Program Files (x86)\JetBrains\PhpStorm 2016.1.2\bin\

3.  Datei mit der Endung .vmoptions suchen
	
	>	PhpStorm.exe.vmoptions (32-Bit)	*oder*
	
	>  	PhpStorm64.exe.vmoptions (64-Bit)
	
4.  In der Datei steht ganz oben z.B.

	>	-Xms128m
	
	>	-Xmx750m

5.  Den Wert für -Xmx von 750m auf z.B. 1024m erhöhen also so:
	
	>	-Xmx1024m
	
6.	Datei speichern und PHPStorm neustarten

7.	Prüfe den maximalen Memory-Wert rechts unten in der Taskleiste von PHPStorm ;-)