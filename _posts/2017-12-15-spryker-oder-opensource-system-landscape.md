---
layout: post
title: Spryker oder OpenSource System Landscape?
description: OpenSource System Alternativen zu Spryker E-Commerce.
---
Spryker bezeichnet sich selbst als das Betriebssystem für E-Commerce. In Deutschland scheint das Konzept, auch wegen der
fehlenden Präsenz der Konkurenz, an Fahrt zu gewinnen. Wem Spryker komplett neu ist der kann [hier](http://etailment.de/news/stories/Spryker-Die-wichtigsten-Antworten-zur-hippen-Software-2951) die Basics nachlesen.

Neue Systeme und neue Ideen beflügeln den Markt und deshalb kann man wohl sagen das von Spryker folgende Dinge gelernt wurden:
* Echte Trennung von Frontend und Backend
* Performance auch ohne Caching (eigentlich ein alter Schuh)
* Einheitlicher und konsequenter Code-Style (modulare Architektur, OOD)
* Moderne Design Patterns
* Automatische Visualisierung von Geschäftsprozessen
* Nicht nur und nicht immer sind relationale Datenbanken das richtige Werkzeug

Als Spryker 2014 das Licht der Welt erblickte hat es sich zwischen **klassischen Standard-Shopsystemen** und **Marktführern
mit Eigenentwicklungen** positioniert. Ende 2017 stellt sich die Frage ob dies noch der Fall ist? Bei vielen mittleren bis größeren
E-Commerce Projekten stehen Updates oder Relaunches auf dem Programm. Gute Möglichkeit mal Spryker zu testen.

Stellt sich erstmal die Frage nach dem Preis. Am Anfang hat Spryker 100.000 Euro im Jahr verlangt und dann Mitte 2016 das
Preis-Model umgestellt. Jetzt kostet ein Entwickler-Seat 15.000 Euro im Jahr, es kann aber auch monatlich bezahlt werden.
Es können zum Beispiel am Anfang des Projektes mehr Sitze gebucht werden und dann später wenn es in die Wartung geht 
entsprechend reduziert werden. 

Aktuell wird im E-Commerce auch der MVP-Ansatz hochgelebt. Es ist sicherlich gut schnell ein Produkt oder Projekt online zu testen
anstatt in einem Wasserfall-Model zu versinken. Allerdings sollte sich jedes bestehende E-Commerce Projekt genau überlegen ob der 
MVP-Ansatz von der eigenen Kundeschaft für einen Relaunch akzeptiert wird. Nicht das sie mit einem "kleinen neuen Projekt" 
Live gehen und dann einen Shit-Storm ernten, weil eben viele Funktionen nicht mehr gegeben sind. Ein MVP sollte wohl in der 
Regel innerhalb von 3 Monaten bis 6 Monaten umgesetzt sein, ansonsten ist es wohl kein MVP mehr.

2014 hat Spryker also gesagt "Kein E-Commerce Projekt ist wie das andere! Und deshalb macht Standard-Software keinen Sinn!"
Jetzt Ende 2017 möchte Spryker viele Projekte als MVP umsetzen. Kann ein MVP also mit einem System funktionieren welches nicht
von der Stange ist? Und was heißt den eigentlich Standard-Software? Ist es nicht gut wenn Dinge erprobt sind und das von vielen?
Spryker sagt ja Magento oder Shopware wären quasi ein Fertighaus. Und Spryker selbst wäre das individuelle gebaute und passende
Haus in der richtigen Größe mit den richtigen Fenstern, Türen und so weiter. Gute individuelle Häuser können eigentlich nur 
von guten Architekten gebaut werden. Oder?

Wir haben ja schon festgestellt das der Core von Spryker einer modernen Architektur entspricht. Das ist der Vorteil wenn
man auf einer grünen Wiese beginnt und nicht wie Shopware oder Magento auch alte Kunden und alten Code bedienen muss. Stellt
sich die Frage nach den richtigen Architekten. Aktuell scheinen sehr viele Agenturen in Deutschland neben den etablierten
E-Commerce Systemen eben auch Spryker anzubieten. Es könnte also sein das ich eine gute Basis für mein individuell geplantes
Haus von Spryker erhalte und danach bei einer Agentur lande die keine Erfahrungen damit hat wie diese "Materialien" nun 
ordentlich verbaut werden bzw. wie eben noch ein Anbau gemacht wird. 

Klar die Basis ist PHP, HTML5, JavaScript etc. aber jeder weiß dass eben auch Konzepte verinnerlicht werden müssen. Als 
Entwickler muss ich wissen das ich dafür XYZ verwenden kann oder das es dies schon gibt. Der gute Entwickler überlegt
was er wie verwenden kann um ein Ziel zu erreichen. Der *nunja* Entwickler denkt alles selbst bauen zu müssen damit es gut
wird. Ich muss also mindestens 2 Projekte gemacht haben um sagen zu können das ich Spryker verstanden habe. Nur wer hat das
schon in Deutschland? Soweit ich gehört habe werden die großen Spryker Projekte sogar mit dem Core-Team in Berlin umgesetzt.

Gehen wir mal davon aus das ich 4 Entwickler brauche und in 6 Monaten Live sein möchte. Dann bezahle ich 30.000 Euro dafür
das ich den Spryker-Core verwenden darf. Der Entwickler und/oder die Agentur will auch bezahlt werden. Heißt bei 6 Monaten
für die Entwicklung sind das ca. 130 Arbeitstage mit jeweils 8 Stunden sind 1.040 Stunden bis zum Go-Live. Wenn ich nun
einen durchschnittlichen Stundensatz von 100 Euro ansetze komme ich auf Kosten von 104.000 Euro. Rechnen wir noch 20% für 
Kommunikation und Projektmanagement dazu dann wären wir bei 124.800 Euro. Dazu dann die 30.000 Euro für Spryker sind 
aufgerundet 155.000 Euro. Für einen MVP ;-)

Realistisch betrachtet glaube ich nicht das im Markt aktuell ein Spryker Projekt für 155.000 Euro Online gehen würde. Ich schätze
das Spryker Projekte ab 250.000 Euro möglich sind. Das alles hier ist natürlich eine sehr einfache Betrachtung, weil wir 
den Projekt-Scope noch gar nicht definiert haben. Die Komplexität steigt mit jeder Zahlart, jeder Anbindung und jedem Feature. 
Selbst wenn wir nun ein Volumen von 300.000 Euro für unser Projekt unterstellen, dann ist Spryker vom Preis verglichen mit
Hybris doch gar nicht so teuer wie eine Enterprise Software es erwarten lässt.

Hört sich doch alles erstmal gut an. Nur was ist den aktuell die Schwäche von Spryker? Einige sagen es wären die fehlenden
Features. Gut aber eigentlich ja logisch wenn man selbst keine Standard-Software liefern will und sagt jedes Projekt sollte
die individuellen Features auch individuell bauen. Andere sagen "OpenCode" ist leider nicht "OpenSource". Gut der Quellcode
von Spryker ist für alle Online einsehbar. PullRequests oder eine Beteiligung der Community ist soweit ich weiß noch nicht
möglich. Zitat *"Wir brauchen 6 Monate um einen Entwickler auf das Niveau der Spryker Core-Entwickler zu bringen. Es ist deshalb 
schon sehr unwahrscheinlich das ein Agentur Modul in den Core kommt.".* Schade.

Wenn ich Projektleiter wäre und ein ausreichendes Budget hätte dann stellt sich doch die Frage ob ich das was Spryker gemacht hat
nicht auch einfach ohne Spryker tun kann? Die Architektur ist ja bekannt. Redis und/oder ElasticSearch können verwendet werden.
Eine strickte Trennung von Frontend und Backend ist eine Disziplin die konsequent verfolgt werden muss. Wenn ich also ein
individuelles Projekt habe und quasi ein individuelles Frontend möchte z.B. mit Angular oder React, dann kann ich mir 
das ja bauen lassen. Eigentlich doch genau das was Spryker propagandiert.

Irgendwie hat Spryker eine doppelte Persönlichkeit. Ich soll Spryker verwenden weil ich dann schneller zum Ziel komme.
Aber ich soll auch die Features individuell bauen weil ja kein E-Commerce Projekt gleich ist. Große erfolgreiche Projekte 
haben intern ein Team aufgebaut welches sich in der eigenen Systemlandschaft auskennt und diese ohne Agenturen bedienen kann.
Sollte ja irgendwo auch das Ziel sein Unabhängig agieren zu können. Da Frage ich mich dann:

**Welche Alternative Lösung, ohne laufende Lizenzkosten, könnte ich mir vorstellen?**
![OpenSource system landscape](https://raw.githubusercontent.com/bjoern-flagbit/brocksinet.github.io/master/images/_posts/open-source-system-landscape.png "OpenSource system landscape")

Meiner Meinung nach wird sich der Aufwand (aktuell) mit oder ohne Spryker die Waage halten. Für Ihren Erfolg ist die Conversion des
Kunden im Frontend entscheidend. In der Frontend-Entwicklung findet aktuell die meiste Veränderung statt. Schauen Sie sich
Konzepte wie Progressive Web Apps an. Beharren Sie auf Frontend-Style-Tests, nutzen Sie TypeScript für Ihr JavaScript
und verwenden Sie eine JavaScript Testing Framework. Spryker liefert aktuell ein Frontend-Gerüst aus was auf PHP baisert.
Arbeitet aber soweit ich gehört habe auch an einem Skeleton für ein React Frontend. Wenn Sie also den angesagten und modernen 
Frontend Weg mit Angular, React oder vue.js gehen wollen, dann müssen Sie auch bei Spryker erstmal ein Frontend bauen. 
Im übrigens ist Spryker mit der Ausrichtung nicht alleine, auch Magento2 will für das Frontend auf Progressive Web Apps setzen.

Die zukünftige Entwicklungsgeschwindigkeit wird entscheiden welches E-Commerce System sich als Vorreiter platziert.
Die Ausgangslage scheint für Spryker nicht schlecht. Leider vermisse ich eine Community und den OpenSource Gedanken.
Freue mich aber auf die ersten Projekte und Erfahrungen mit Spryker. Mal schauen ob das Marketing hält was es verspricht ;-)
