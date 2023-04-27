## Materialien 

### Auswahl der Steuerung 


Die Steuerung muss folgende grundlegende Aufgaben übernehmen:
* Benutzereingaben verwalten (Drehencoder, Start-Taster auslesen)
* Ausgänge schalten (Ventil, Motor, Button LED)
* UI Darstellen (OLED Display ansteuern)
* Logik zur Ausgabe (Zeitberechnung, Reaktivität der Wägezelle, ...)
* Parametrierung (Wägezelle, Wasserfluss, ...)
* Kommunikation mit Raspberry Pi Server

Die Wahl ist auf einen Mikrocontroller gefallen. Günde dafür waren:
* Sehr kompaktes Format (passt in den kleinen Automaten)
* Ausreichend Leistung für Berechnungen
* Einfache Programmierung durch Vorkenntnisse in "Arduino"
* Sehr günstiger Anschaffungspreis
* Alle nötigen Schnittstellen (Bsp. WLAN, I²C, GPIO's, Interrupts, ...)
* Geringe Stromaufnahme
* Passende Bibliotheken für Drehencoder, Wägezelle, MQTT, ...

Die Auswahl an Alternativen war nicht groß. Zur Option standen nur noch ein Mikroprozessor (Raspberry Pi o.ä.) und diverse Kleinststeuerungen (z.B. Siemens LOGO! oder ABB CL-LSR). Der Mikroprozessor Raspberry Pi ist durch die folgenden Kriterien für die Getränkeautomaten ausgeschieden:
* Größe
* Preis deutlich höher
* Abwärme

Die erwähnten Kleinststeuerungen stammen aus dem industriellem Sektor und sind darum sowohl auf Hutschienenmontage als auch die Protokolle angepasst. Folgende Aspekte sprechen gegen die Verwendung im Rahmen dieses Projekts:
* Größe
* Preis deutlich höher
* Stromversorgung (meist 24V)
* Fehlende Schnittstellen für WLAN, MQTT, I²C, ...
* geringfügige Vorkenntnisse

Die Wahl des Mikrocontrollers ist für das Projekt unter den gegebenen Rahmenbedingungen alternativlos, wie die Erläuterungen in der Literaturübersicht darlegen. Die Arduinos sind im Verhältnis eher auf einer größeren Platine zu erwerben. Hinzu kommt die fehlende native WLAN Schnittstelle und die geringere Rechenleistung. Der Raspberry Pi Pico ist aufgrund seiner Programmierung in MicroPython aus persönlichen Präferenzen ausgeschieden. Zudem sind viele Bibliotheken ausschließlich für die Arduino/ESP Plattform in C/C++ verfügbar. Der ESP vereint alle Anforderungen und ist aus durch mehrere private Projekte bereits gut bekannt. 
Anhand der oben genannten Gründe für diese Art der Steuerung wird ein explizites Modell aus der ESP-Familie ausgewählt. Die am stärksten vertretenen Chips haben den ESP32 oder den ESP8266 verbaut.
Der ESP8266 wurde für den Versuchsaufbau verwendet, da dieser noch im privaten Lager vorhanden war. Das Board ist ein D1 Mini, welcher mit 3,3V Logik arbeitet. Er besitzt 11 I/O Pins und kann über die verbaute MicroUSB Schnittstelle zum Flashen mit einem PC verbunden werden.
Nach einigen Tests der Hardware im Bereich des Drehencoders und der Displayvisualisierung wurde ein ESP32 für den weiteren Bau des Automaten verwendet. Die Tests mit dem ESP32, welcher eine leistungsstärkere und funktionsreichere Version auf Basis des ESP8266 ist, ergaben ein flüssigeres Gesamtbild in der Bedienung. Nachforschungen zu diesem Verhalten sind keine weiteren erfolgt, jedoch ist dies vermutlich auf die höhere Taktfrequenz und eine andere Interruptsteuerung der verwendeten Bibliothek zurück zu führen.

#### Benutzerschnittstelle

Für den Benutzer der Maschine muss es sowohl schnell und intuitiv sein seinen Getränkewunsch am Gerät einzugeben und auch eine entsprechende Rückmeldung zu erhalten. Im Versuchsaufbau wurde dabei auch eine Eingabe über einen einzelnen Touchsensor realisiert und die Ausgabe von Informationen mit drei RGB LED's umgesetzt. Gerade für außenstehende ist die höchst irritierend. Darum kamen die Steuerung über einen Touchscreen oder einen Bildschirm mit zusätzlichen Knöpfen oder ähnlichem in Frage. Da im Bereich der Küche die Bedienung mit nassen/dreckigen Händen nicht unwahrscheinlich ist, wurde der Touchscreen nicht in die nähere Auswahl einbezogen. Interessant ist ein kleiner Bildschirm und eine Eingabemethode. Bildschirmtechnologien die sich im Microcontrollerbereich durchgesetzt haben sind LCD-, TFT- und OLED-Displays. Die meisten LCD-Displays basieren dabei meistens auf der Ausgabe von sechzehn Zeichen auf zwei Reihen. Für den Endanwender und die Darstellung von variablen Informationen, gar Grafiken, lässt sich nur bedingt umsetzen. Die TFT-Displays, wie auch die nicht zeichenbasierten LCD-Displays, benötigen meistens viele der Pin des ESP's zur Ansteuerung. Erwähnenswert ist für die TFT-Displays jedoch, dass eine farbliche Darstellung möglich ist. Da dies im Dauerbetrieb jedoch auch mehr Energie verbraucht, wurde sich in Kombination mit der einfachen Verdrahtung über die I²C Schnittstelle für ein 1,3 Zoll großes OLED-Display mit einer Auflösung von 128x64 Pixeln entschieden.
Für die Benutzereingabe bewährte sich ein Drehencoder mit Push-Funktion für die Navigation durch die Menüs auf dem Display und ein zusätzlicher Taster mit steuerbarer Beleuchtung und einer "Start"-Beschriftung zum finalen Beginnen der Wasser-/Pulverausgabe.



### Auswahl der Komponenten zur Ausgabemessung 


#### Wassermenge

Um die Mixgetränke auszugeben ist es nötig die Wassermenge und die Pulvermenge möglichst genau zu bestimmen. Die Messung der Wassermenge ist über mehrere Verfahren möglich. Eines davon ist die Bestimmung über die Zeit. Dabei wird angenommen, dass ein parametrierter Wasserfluss (z.B. in l/min) in allen Fällen am Ventil anliegt. Verrechnet man dieses nun mit der Zeit erhält man die ausgegebene Menge. Eine anderes Verfahren ist die Verwendung eines Tachogenerators in Kmbination mit einem Flügelrad in der Messstelle. Dieser misst Impulse, welche durch ausgelagerte Elektronik oder interruptgesteuert über den ESP verarbeitet wird. Ein Impuls entspricht dabei immer einer im Datenblatt festgelegten Wassermenge.
Der Versuchsaufbau lieferte bereits gute Werte, wie es im Abschnitt Testen zu erkennen ist. Der Aufbau arbeitete mit der zeitbasierten Messmethode. Da die Dichtigkeit der Leitungen im Automaten große Probleme bereitet hatte, wurde auf das Hinzufügen einer zusätzlichen Schwachstelle, an welcher Undichtigkeiten auftreten könnten, verzichtet. Zudem konnte auch nach langer Recherche keine, an die verwendeten 1/4 Zoll Schlauchverbindungen, passende Messapparatur gefunden werden, welche sowohl das richtige Gewinde besitzt, als auch für die geforderte Durchflussgeschwindigkeit und den Wasserdruck ausgelegt ist.
Die Entschiedung fiel somit aus Gründen der Einfachheit und der guten Zwischenergebnisse auf die zeitbasierte Messung.

#### Pulvervorrat

Für die Bestimmung der Menge des im Behälter befindlichen Pulvers standen einige Verfahren zur Verfügung. Die Schwierigkeiten der Füllstandsbestimmung lagen dabei hauptsächlich darin, dass es sich um Schüttgut handelt. Schüttgut bietet im Vergleich zur beispielsweise Wasser oder Gasen keine einfache Möglichkeit den Bestand über Druck oder Schwimmer zu lösen. Zudem verhindert die ungleichmäßige Oberflächenstruktur eine genaue Messung über den Abstand.

Die erste Idee ergab die Verwendung der im Microcontrollerbereich weit verbreiten Ultraschallsensoren, wie man sie auch aus der Parkhilfe im Auto kennt. Für die Messung des Pulverbestandes sind sie allerding aus folgenden Gründen nicht geeignet:

* Anfällige und ungenaue Ergebnisse auf sehr kurze Entfernung
* Müsste im Deckel des Behälters befestigt werden (Kabelverlegung, Platzeinnahme)
* Kontakt mit Sensor sehr wahrscheinlich => Verschmutzung
* Ungleichmäßige Oberfläche => ungenauer/schwankender Messwert

Eine weitere Möglichkeit stellte die Verwendung von Licht-/Laserdioden dar. Diese könnten durch kleine Löcher seitlich im Behälter strahlen und im Falle der unterschrittenen Füllhöhe auf der gegenüberliegenden Seite durch Fotowiderstände erkannt werden. Ist das Schüttgut dazwischen wird dementsprechen kein aktives Signal erkannt. Nachteile ergeben sich durch:

* Keine kontinuierliche Messung möglich, nur Schrittweise
* Höherer Stromverbrauch durch die Dioden
* Undichtigkeiten im Behälter => feines Pulver, Feuchtigkeit problematisch
* Verstopfung der Sichtlöcher wahrscheinlich

Die Wägezelle schien der beste Lösungsansatz zu sein. Eine Wägezelle ist in der Größenordnung von wenigen Kilogramm in der Regel ein Aluminiumstab. An diesem sind mindestens an den Seiten der Kraftauswirkung Dehnungsmessstreifen angebracht. Durch die minimale Dehnung des Aluminiums kann an den Dehnungsmessstreifen eine Widerstandsabweichung gemessen werden. Die Abweichung gibt die Dehnung des Materials und somit die Ausübung einer Kraft an. Somit wird eine Messung des Gewichts der durch die durch Schwerkraft ausgelöste Wegänderung durchgeführt. Die Wiederstandsänderungen sind dabei so minimal, dass der intern verbauten Analog-Digital Wandler des ESP's nicht genau genug ist. Die ADC (analog to digital converter) haben nur eine Auflösung von 12bit. Damit die Änderung des Widerstandes der Dehnungsmessstreifen ausgewertet werden kann, wird auf basis einer Wheatstone Messbrücke ein externer 24 bit ADC zur Messung des Spannungsabfalls an den Widerständen verwendet. Der Chip nennt sich HX711. Über zwei Drähte und der Spannungsversorgung lässt er sich mit einer passenden Bibliothek leicht auslesen und zur Messung von Gewichten verwenden. Die Kalibrierung basiert dabei auf dem Prinzip einen Nullzustand zu speichern, ein bekanntes Gewicht aufzulegen und die Werte dazwischen, wie auch darüber hinaus, linear zu skalieren. Das bekannte Gewicht kann dabei auch relativ sein, sprich dem vollen Vorratsbehälter wird der Wert 100 zugeordnet und dem leeren der Wert 0. Somit erhält man einen Füllstand 0-100%. Die Kalibrierung wurde jedoch in Gramm vorgenommen, um keine Informationen zu verwerfen. 
Mit der Auswahl der Wägezelle gehen auch einige Schwierigkeiten einher. Zum Einen muss nur der komplette Behälter inklusive der Fördervorrichtung und dem Antrieb frei schwebend, abgekoppelt von dem restlichen Gehäuse sein. Zum Anderen erzeugt der Antrieb einen Schwingung auf der Wägezelle, welche die Messung während eines aktiven Ausgabevorgangs beeinflusst. Ein weiterer Faktor ist die Temperaturempfindlichkeit der Dehnungsmessstreifen. Für dieses Projekt hat die Temperatur jedoch nur geringfügige Auswirkungen, da sich der Automat in der Wohnung bei relativ konstanter Raumtemperatur befindet.
Die Wägezelle bietet dabei so genaue Messergebnisse, dass eine Ausgaberegulierung über das Gewicht denkbar ist. Diese konnte leider aufgrund der Zeit nicht mehr implementiert werden und ist bei der zeitgesteuerten Ausgabe geblieben.

#### Pulverausgabe

Für die Pulverausgabe soll kontrolliert über den ESP eine Menge an Schüttgut in den Endbehälter ausgeben (z.B. ein Wasserglas). Infrage kommen hierfür verschiedenste Technologien, wobei viele nach kürzester Planungsphase bereits ausgeschieden sind:

* Kippmechanismus
* Fälltür

Die größte Problematik besteht in der kontrollierten Mengenregulierung. Durch jegliche Kippmechanismen wird in kurzer Zeit eine große Menge an Schüttgut ausgegeben. Dabei sind kleine stetige Menge ohne Umstände nicht umzusetzen. Hinzu kommt die komplexere Programmierung und der Platzbedarf im Gehäuse. Auch vibrationsgesteuerte Ausgabeverfahren kommen durch starke Schwankungen in der Ausgabegeschwindigkeit (abhängig vom Füllstand) nicht in Frage.

Übrig bleiben Verfahren mit einer linearen Ausgabe. Ein Beispiel hierfür ist die Verwendung eines Förderbandes. Die Verwendung einer Förderschnecke, deren Funktionsweise in der Literaturübersicht genauer beschrieben ist, biete den anderen Verfahren klare Vorteile:

* Lineare Ausgabemenge 
* Skalierbare Geschwindigkeit
* Entnahme aus dem Vorratsbehälter einfach umsetzbar

Zu den Nachteilen gehören dennoch die erschwerten Reinigungsmöglichkeiten und bei einem Leerlauf/ersten Inbetriebnahme muss die "Luft" aus dem System entfernt werden, bis das Schüttgut die Ausgabe erreicht hat.



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

### Auswahl der Programmierumgebung

Bei der Programmierumgebung standen sowohl die Arduino IDE, als auch die Erweiterung PlatformIO für Visual Studio Code zur Auswahl. Beide sind kostenlos zu nutzen und haben einen ähnlichen Funktionsumfang. Während die Arduino IDE mit Benutzerfreundlichkeit, besonders für Anfänger, glänzt und eine große Community mit vielen Beispielen hat, bietet PlatformIO ein deutlich einfacheres Konfigurationspaket für Projekte mit mehr als einer Programmdatei. Zu den Vorteilen gehört die automatische Bibliotheksverwaltung über die Platform.ini. Diese ermöglicht es ohne großen Aufwand Bibliotheken einzubinden. Dabei kann auf die gleichen Bibliothenken zugegriffen werden, wie die Arduino IDE. Desweiteren kann ein Verzeichis strukturiert aufgebaut werden. Mit der Auto-Complete Funktion von Visual Studio Code ist das Programmieren auch deutlich angenehmer und effizienter. Die endgültige Entscheidung wurde für PlatformIO getroffen, da durch den Aufbau der Projektstruktur, im Vergleich zu den Projekten der Arduino IDE, einfach der Projektordner im Zip Format an andere PC's übertragen werden kann, ohne dass Bibliotheken, Konfigurationen oder Abhängigkeiten vorher installiert werden müssen. Zudem bietet wird der build der Datei automatisch gespeichert, was für eine zukünftige Implementation von OTA-Flashing (over the air) interessant ist.


### Programmierkonzept

Die Programmierung des Getränkespenders basiert auf der Setup- und der Loop-Schleife. Das sind die grundlegenden Funktionen der meisten Microcontroller, wie auch der ESP einer ist. Die Setup-Schleife wird einmalig bei Booten ausgeführt. Anschließend wird zyklisch die Loop-Schleife ausgeführt.
Für das Programm wurden viele Bibliotheken verweden, da es den Aufwand für die Ansteuerung z.B. des Bildschirms auf ein Minimum beschränkt. Der Code wurde möglichst Modular aufgebaut, sprich es gibt eine eigene Datei, welche sich um den WLAN Verbindungsaufbau kümmert, eine welche die Menüführung des Displays übernimmt und so weiter.
Um die Vorgehensweise beim Start einer Getränkeausgabe genauer zu erläutern, gilt es die zeitliche Abhängigkeit des gesteurten Ausgangspins und der z.B. Wassermenge zu verstehen. Bei der Inbetriebnahme wird einmalig eine Flowrate (Durchflussrate) der geöffneten Ventils ermittelt und gespeichert. Die Einheit dafür ist l/min. Wird jetzt eine Ausgabe von einer Wassermenge verlangt, berechnet der ESP mit der Flowrate eine Zeit in der Einheit ms. Mit dem Aktivieren des Ausgangs und somit dem Öffnen des Ventils, startet intern ein Timer.
Der Timer ist mit der millis()-Funktion umgesetzt. Der ESP zählt ab dem Start jede Millisekunde eine Variable vom Datentyp unsigned long hoch. Mit der millis()-Funktion kann der aktuelle Stand abgefragt werden. Durch setzen eines Zeitstempels beim Beginn der Ausgabe und dem zyklischen Vergleichen in der Loop-Funktion, ob die berechnete Zeit bereits abgelaufen ist, wird die Ausgabe beim Erreichen wieder gestoppt. Das Gleiche passiert bei der Ausgabe von Pulver. Beim Vergleichen der Werte muss der Überlauf der long Variable bedacht werden. Hier gibt es unterschiedliche Herangehensweisen, keinen Fehler hervorzurufen.
Die Verwundung einer Bibliothek vereinfacht das Auslesen der Eingaben über den Drehencoder, sowie den Startknopf enorm, durch einstellbare Callback-Funktionen.
Verwendete Pins des ESP's zur Kommunikation mit den anderen Bauteilen sind den bei Systemarchitektur beschrieben und im Anhang beigefügten Plänen zu entnehmen.

Der Code wird bei der Fertigstellung der Anlage in Zukunft (siehe Ergebnisse und Ausblick) in dem im Anhang genannten GitHub Repository hochgeladen.

### Auswahl der Methodiken des Servers 

"Unter einem Betriebssystem (engl. operating system) versteht man Software, die zusammen mit dem Hardwareeigenschaften des Computers die Basis zum Betrieb bildet und insbesondere die Abarbeitung von Programmen steuert und überwacht."
    Quelle 5

### Auswahl des Betriebssystems des Servers: 

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