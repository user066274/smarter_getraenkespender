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

## Quellen 

Quelle 1: https://docs.docker.com/engine/install/ubuntu/ 
Quelle 2: https://nodered.org/about/ 
Quelle 3: https://www.researchgate.net/profile/Shakirat-Sulyman/publication/271295146_Client-Server_Model/links/5864e11308ae8fce490c1b01/Client-Server-Model.pdf
Quelle 4: https://www.intel.de/content/www/de/de/products/sku/205600/intel-nuc-11-pro-mini-pc-nuc11tnkv5/specifications.html