---
layout: post
title: PHPStorm in der 64-Bit Variante verwenden
---
1.  **Java SE Development Kit installieren.** [Download-Link](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)

		Darin enthalten:
		1.  Java JDK zum Beispiel unter: C:\Program Files\Java\jdk1.8.0_92
		2.  Java JRE zum Beispiel unter: C:\Program Files\Java\jre1.8.0_92

2.  **JAVA_HOME und JRE_HOME Variable setzen**
	
	1.  JAVA_HOME = C:\Program Files\Java\jdk1.8.0_92
	2.  JRE_HOME = C:\Program Files\Java\jre1.8.0_92

**Sieht dann so aus**

![Java Variables Settings on Windwos](http://www.brocksi.net/images/brocksinet/posts/phpstorm-jre-java-home-setting-variables.PNG "Java Variables Settings on Windwos")

3.  **Neustarten** bzw. sicherstellen das die Variable in der Umgebung gesetzt ist

	> **Tipp fÃ¼r Windows - ohne Neustart:**
	> 
	> CMD Ã¶ffnen / Command Line
	> 
	> AusfÃ¼hren: **taskkill /f /im explorer.exe**
	> 
	> AusfÃ¼hren: **explorer.exe**	

4.  **PHPStorm** z.B. mit C:\Program Files (x86)\JetBrains\PhpStorm 2016.1.2\bin\PhpStorm64.exe **starten**

5.  **Verknüpfung auf dem Desktop anlegen** ;-)