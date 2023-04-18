## Materialien 

### Auswahl der Steuerung 

Allgemein wofür bracuht man die steurung, welche arten von steuerungen, für was haben wir uns entschieden, warum dafür, alternativprodukte? 

### Auswahl der Komponenten zur Ausgabemessung 

Allgemein: welche verfahren gibt es (durchfluss, gewicht, ...?), welche verfahren gibt es für gewicht (wägezelle, ...)





### Auswahl des Servers 

Grundlegend: Ein Server ist Hard- oder Software, die Dienste für andere Hard- oder Software bereitstellt. 
    Quelle 3

**Anforderungen**: 

Für die Betrachtung der Auswahl der Hardwarekomponenten für den Server müssen mehrere Kriterien betrachtet werden. Die folgenden Kriterien wurden für den Server des Getränkespenders berücksichtigt:

+ Leistungsfähigkeit: Die ausgewählte Hardware muss ausreichend Rechenleistung, Netzwerkgeschwindigkeit und Speicherkapazität bieten, um die definierten Aufgaben effizient auszuführen.  

+ Verfügbarkeit: Die ausgewählte Hardware soll ich Deutschland erwerbbar sein, um einen einfach Erwerb und eventuelle Wartungsarbeiten oder Ersatzbeschaffungen zu ermöglichen. 

+ Energieverbrauch: Der Energieverbrauch des Servers sollte möglichst gering sein, um die Betriebskosten und die Belastung auf die Umwelt minimal zu halten.   

+ Preis-Leistungsverhältnis: Ein gutes Preis-Leistungsverhältnis ist zwingend erforderlich um einerseits das Projektbudget nicht zu überschreiten und andererseits die beste Benutzererfahrung zu gewährleisten.  

+ Kompatibilität: Die Hardwarelösung muss mit dem Betriebssystem Linux und dem Softwaretool Docker kompatibel sein.  Docker ist mit den Prozessorarchitekturen x86_64(oder Arm64), armhf, arm64 und s390x kompatibel  (quelle 1)  

+ Zuverlässigkeit: Stabilität und Zuverlässigkeit sind hier notwendig, um die Wahrscheinlichkeit für Ausfälle zu minimieren und die Verfügbarkeit der Serverseite zu gewährleisten Vergleich einfügen  

+ Unterstützung und Community: Für Troubleshooting und allgemeine Problemlösung ist eine aktive Entwickler und Benutzergemeinschaft sowie eine umfassende Dokumentation gewünscht 

+ Größe und Formfaktor: Die Hardware soll einen definierten Formfaktor nicht überschreiten, um in den gewünschten Arbeitsbereich zu passen und den Platzbedarf zu minimieren  

+ Sicherheit: Die Sicherheit der Hardware und der darauf laufenden Anwendung ist ausschlaggebend um unbefugten Zugriff auf Daten und Steuerung des Getränkespenders zu vermeiden. 

Mit der Berücksichtigung dieser Kriterien für die geeignete Server-Hardware eine fundierte Entscheidung getroffen werden. 

**Auswahl**: 

Nach sorgfältiger Abwägung verschiedener Optionen und unter der Berücksichtigung der zuvor genannten Kriterien wurde der Raspberry Pi Model 4 als Serverhardware ausgewählt. 


Der Raspberry Pi zeichnet sich vorallem durch seine kostengünstige Anschaffung, den kleinen und kompakten Formfaktor und den geringen Energieverbrauch aus. Zudem ist er leicht in Deutschland verfügbar und weist eine extrem breite Basis an Unterstützung, Dokumentation und Community auf. Die Kompatibilität mit Linux und Docker stellt sicher, dass die benötigten Softwaretools in der Serverseite des Systems implementiert werden können. 

Als Alternativen im Auswahlprozess wurden der BeagleBone Black, der Ordoid XU4 und der Intel NUC berücksichtigt. Sowohl der BeagleBone Black als auch der Ordoid XU4 sind ähnlich wie der Raspberry Pi Einplatinencomputer, die ebenfalls in den Punkten Leistung, Kompatibilität und Effizienz gut abgeschnitten haben. Jedoch ist die aktive Community deutlich kleiner und aufgrund ihrer vergleichsweisen schlechten Verfügbarkeit in Deutschland sind die für den Entscheidungsprozess ausgeschieden. Der Intel NUC ist eine Mini-PC Lösung, die mehr Rechenleistung und eine höhere Speicherkapazität bietet, jedoch in den Anschaffungskosten zu hoch ist. Ausschlaggebend als Ausschlusskriterium war die vom Hersteller angegebene TDP (Verlustleistung) von 28 Watt. 
    Quelle 4

Nach umfangreicher Analyse dieser Alternativen und Abwägungen der Vor- und Nachteile wurde der Raspberry Pi als Serverhardware für den smarten Getränkespender selektiert.


## Methodiken 

### Auswahl der Methodiken des Servers 

"Unter einem Betriebssystem (engl. operating system) versteht man Software, die zusammen mit dem Hardwareeigenschaften des Computers die Basis zum Betrieb bildet und insbesondere die Abarbeitung von Programmen steuert und überwacht."
    Quelle 5

**Auswahl des Betriebssystems des Servers**: 

Für die Auswahl eines geeigneten Betriebssystems für den Server des smarten Getränkespenders wurden die folgenden Kriterien zur Bewertung potenzieller Betriebssysteme definiert: 

+ Stabilität: Ein stabiles Betriebssystem ist für den Betrieb eines Server essentiell, da ein reibungsloser Betrieb mit hoher Verfügbarkeit gewährleistet werden soll. Die gewähle Plattform soll langfristig zuverlässig arbeiten und unterstützt werden. 

+ Sicherheit: Die Sicherheitsaspekte sind von großer Bedeutung, da die Schutzziele Vertraulichkeit, Integrität und Verfügbarkeit zwingend eingehalten werden müssen. Das Betriebssystem soll regelmäßig Softwareupdates erhalten und entsprechende Sicherheitsmechanismen bieten. 

+ Leichtgewichtigkeit: Da der Server auf einem Einplatinencomputer mit limitierter Hardware läuft, ist es wichtig, dass das entsprechende Betriebssystem geringe Hardwareanforderungen hat. Zudem soll eine effiziente Nutzung der Hardwareressourcen gewährleistet sein, welche unteranderem auch Einfluss auf den Energieverbrauch des Servers nimmt. 

+ Aktive Community und Unterstützung: Eine aktive Community und umfassende Unterstützung sowie Dokumentation ist ähnlich wie der Wahl der Hardware hilfreich, um die Lösungsfindung bei Problemen zu beschleunigen. 

+ Verfügbarkeit von Softwarekomponenten: Das Betriebssystem soll eine umfassende Basis an Softwarekomponenten und -bibliotheken bieten, um die Implementierung der erfoderlichen Funktionen zu ermöglichen 

+ Lizenzen und Kosten: Die Lizenz und Kostenstruktur des enstprechenden Betriebssystems soll berücksichtigt werden. Die finanziellen Rahmenbedingungen des Projekts müssen eingehalten werden. 

Ein Betriebssystem wird unter Berücksichtigung der zuvor genannten Kriterien ausgewählt.

Nach sorgfältiger Abwägung verschiedener Optionen und unter der Berücksichtigung von den oben genannten Kriterien zur Bewertung von Betriebssystemen wurde die Entscheidung auf RaspbianOS getroffen. 

RaspbianOS ist ein Betriebssystem welches auf Debian Linux basiert und speziell für die Raspberry Pi Platform entwickelt wurde: 
"Raspberry Pi OS is a free operating system based on Debian, optimised for the Raspberry Pi hardware, and is the recommended operating system for normal use on a Raspberry Pi. The OS comes with over 35,000 packages: pre-compiled software bundled in a nice format for easy installation on your Raspberry Pi.

Raspberry Pi OS is under active development, with an emphasis on improving the stability and performance of as many Debian packages as possible on Raspberry Pi." 

    Quelle 6

RaspbianOS erfüllt die definierten Anforderungen an ein Betriebssystem. Als Alternativen zu RaspbianOS sind beispielsweise Ubunut Server für den Raspberry Pi oder Arch Linux ARM in Frage gekommen. Bei der genannten Betriebssysteme sind mit der ARM-Archtiektur kompatibel, bieten jedoch nicht hinsichtlich der Aspkete Kompatibilität und Leichtgewichtigkeit eine ausreichend gute Bewertung. Ubuntu Server ist ebenfalls eine beliebte Linux-Distribution, besitzt jedoch höhere Hardwareanforderungen und ist somit weniger optimal für stark begrenzte Systeme. 

## Quellen 

Quelle 1: https://docs.docker.com/engine/install/ubuntu/ 
Quelle 2: https://nodered.org/about/ 
Quelle 3: https://www.researchgate.net/profile/Shakirat-Sulyman/publication/271295146_Client-Server_Model/links/5864e11308ae8fce490c1b01/Client-Server-Model.pdf
Quelle 4: https://www.intel.de/content/www/de/de/products/sku/205600/intel-nuc-11-pro-mini-pc-nuc11tnkv5/specifications.html
Quelle 5: https://www.tu-chemnitz.de/informatik/friz/Grundl-Inf/Betriebssysteme/Script/bs1.html
Quelle 6: https://www.raspberrypi.com/documentation/computers/os.html