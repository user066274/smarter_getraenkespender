# Literaturübersicht

## Getränkespender: Stand der Technik 
Die Getränkespender spielen gerade im aktuellen Zeitraum eine größere Rolle als vor einigen Jahren. Dieser Anstieg lässt sich vermutlich auf die weiter steigende Schnellebigkeit der Gesellschaft zurückführen. Immer mehr Menschen greifen auf Instant-/Mixgetränke zurück, weil sie ermöglichen  dem Anwender einfach und komfortabel eine große Variation an Getränken zu bieten und dabei weder große Kosten, noch Aufwand verursachen.
Besonders Sirup und Pulver sind eine beliebte Art für die private Nutzung. 
Die Vorteile liegen auf der Hand. Es müssen keine schweren Flaschen transportiert und so mit auch der Pfand nicht zurück gebracht werden. Die Konzentrate zudem sind häufig sehr lange haltbar und sind lediglich mit einfach zugänglichem Leitungswasser zu mischen.
Auch aus der gewerblichen Sicht ist die Variante mit den Konzentraten höchst lukrativ. Die Bereitstellung von vielen verschiedenen Sorten ist deutlich kostensparsamer zu gestalten, als auch die Lagerung ist in kleineren Umgebungen möglich. Besonders gekühlte Getränke benötigen durch den Umstieg auf Konzentrate viel leichter zu handhaben.    
Der aktuellen Markt wird jedoch von den Sirupmixautomaten geführt. Es handelt sich hauptsächlich um die von Fast Food Ketten bekannten Automaten, welche in der Regel Sirup (Konzentrat), Leitungswasser und Kohlensäure miteinander versetzen. Diese Automaten sind gewerblich in verschiedensten Ausführungen verfügbar. 
Im DIY-Segment (Do It Yourself) verbreiten sich Getränkespender mittlerweile auch stark. Es sind immer mehr Artikel und Videos von selbstgebauten Getränkespendern zu finden. Diese basieren meistens auf mehreren Wasser-/Luftpumpen und dem Prinzip die Flüssigkeit aus einer normalen PET Flasche mittels Unter-/Überdruck in ein Glas zu befördern. Diese sind nahezu immer jedoch dadurch beschränkt, dass entweder nur Getränke ohne Kohlensäure ausgegeben werden können, da diese schnell aufgrund des nicht abgedichteten Pumpenmechanismus entflieht, oder die verwendeten Behältnisse nur für kleine Mengen (ca. 3-6 Glasfüllungen) ausreichen, bevor die Zutaten am Automaten nachgefüllt werden muss.
Automaten, welche auf der Ausgabe oder dem Mischen von Instant-Getränkepulver basieren konnten nicht gefunden werden. Alternative gewerbliche Umsetzungen zu den Konzentraten basieren in der Regel auf Kapseln/Pads, wie es sich bereits durch viele Kaffeemaschinen auf dem Markt etabliert hat.

## Mikrocontroller und ESP32 

Mikrocontroller sind besonders im DIY-Segment bei Bastlern beliebt und sind heutzutage auch in Nahezu jedem elektrischen Hasuhaltsgerät zu finden. Dabei haben sich drei Plattformen verschiedener Hersteller auf dem Endverbrauchermarkt durchgesetzt.

* Arduinio
* Raspberry Pi Pico
* ESP

Arduino stellt einerseits die Hardware in Form verschiednster Platinen zur Verfügung, als auch eine Software, die Arduino IDE, welche speziell auf die Programmierung von Mikrocontrollern ausgerichtet ist. Diese bietet auch die Möglichkeit etliche Mikrocontroller externer Hersteller zu programmieren. Da bei Arduino sowohl die Software, wie auch die Pläne für die Hardware open-source vorliegen sind Communitylösungen für verschiedenste Anwendungen und Probleme in Form von Bibliotheken, Codebeispielen und Foren zu finden. Zudem stehen sehr viele Hardware-Shields für die einzelnen Module zur Verfügung. Ein Shield kann passend auf die Pins von Mikrocontroller aufgesteckt werden und erweitert mit kleinen Anpassungen im Code die Funktionalitäten des Hauptmoduls um zum Beispiel WLAN.

Der Raspberry Pi Pico ist ein leistungsstärkeren Mikrocontroller dar, was die Taktfrequenz und den deutlich größeren Speicher (Flash und SRAM) im Vergleich zu dem verbreiteten Arduino Uno betrifft. Der größte Unterschied liegt jedoch in der Programmierung. Diese ist für den Pico in der Sprache MicroPython üblich, während die Arduino-Reihe C/C++ unterstützt. Von dem Pico gibt es mehrere Modelle, eines ist vor kurzem mit integrierter WLAN Schnittstelle auf dem Markt gekommen. Eine Besonderheit ist die Dateisystemfunktion des Pico. Dadurch wird dem Programm der Zugriff auf einen externen Speicher ermöglicht. Zudem ist der Pico auch als USB-Schnittstelle zu programmieren (HID-Anwendungen wie Tastaturen etc. emulieren).

Der ESP ist die Plattform von Espressif Systems und ist durch das Installieren zusätzlicher Pakete auch vollständig mit der Arduino IDE programmierbar. Er unterscheidet sich maßgeblich durch die native WLAN Unterstützung und verfügt in fast allen Fällen noch über eine integrierte Bluetooth Schnittstelle. Seine Leistungsfähigkeit übersteigt den Raspberry Pi Pico nochmals erheblich um knapp das Doppelte. Die Rede ist von der Taktfrequenz (240MHz zu 133MHz), dem Flash Speicher(4MB zu 2MB), dem SRAM (520KB zu 264KB) und mehreren analogen I/O's. Der ESP32 wird durch diese Leistungsfähigkeit und die WLAN/Bluetooth Schnittstelle in vielen Communityforen als die erste Wahl für IoT-Projekte (Internet of Things) empfohlen. Wie auch beim Arduino ist die Verwendung der Arduino IDE und der meist für beide Plattformen kompatiblen Bibliotheken kein Problem.

## Pulvertransport

Die Förderschnecke ist eine Alternative um Schüttgüter, wie auch Flüssigkeiten, zu transportieren. Sie basiert auf dem Funktionsprinzip der archimedischen Schraube. Ziel ist es Material in der Ebene und/oder Höhe zu transportieren. Durch die Drehbewegung der Schnecke in einem seitlich eng abschließenden Rohr und der Schwerkraft/Reibungskraft, wird das Material im Rohr entlang geführt. Die Drehbewegung wird durch einen Motor an mindestens einem Ende der Drehachse der Schnecke erzeugt. Somit lassen sich besonders gut Schüttgüter über einen linearen Weg auch in flacheren Winkeln in die Höhe transportieren. Die Fördermenge dieses Systems lässt sich als nahezu proportional zur Drehgeschwindigkeit des Motors annehmen. Dabei gilt für die meisten Stoffe, dass je höher die Drehzahl ist, desto höher ist auch die Reibungskraft des Transportgutes an den Rohrwänden.

Eine weitere Möglichkeit ist ein Fallklappensystem. Dabei wird eine bestimmte Menge des Schüttgutes auf einer Fallklappe platziert. Dies muss durch einen anderen Transportmechanismus geschehen. Ist die gewünschte Menge erreicht, gemessen durch Füllstand oder Gewicht, wird die Klappe nach unten geöffnet und das Material fällt durch die Schwerkraft nach unten.

Desweiteren können Förderbänder verwendet werden. Das Förderband wird durch einen Motor in eine Richtung angetrieben. Das darauf befindliche Material wird dann bis zur Kante, an der das Förderband umgelenkt wird, gefördert und fällt danach hinunter. Die Motorgeschwindigkeit beeinfluss direkt die Fördergeschwindigkeit, wenn bei der Beschleunigung/Bremsung des Bandes kein Rutschen des Schüttgutes entsteht. Steigungen sind überwindbar, allerdings abhängig vom Winkel des Förderbands, der Reibung des Schüttgutes und weiteren Faktoren. Durch Anbringung von orthogonal zum Förderband befestigten Trennwänden kann die Steigung stark erhöht werden. 

Wird das Konzept der Trennwände an einem Förderband erweitert, entstehen  behälterartige Formen, in denen das Schüttgut ohne Verluste nur noch in der Vertikalen zu transportieren ist.

## Ventil

Bei einem Ventil im Kontext des Getränkeautomaten handelt es sich um die Durchflussregulierung der Wassermenge. Da es sehr viele Arten von Ventilen gibt, wird eine Zuordnung in zwei Übergruppen von Ventilen unterteilt.

* Schaltventile
* Stellventile

Pneumatische und hydraulische Ventile verändern ihren Zustand durch einen Druck über ein Medium (zum Beispiel Luft oder Öl). Da der Druck aufwendig erzeugt werden muss und dies in dem kleinen Gehäuse des Getränkespenders kaum möglich sein wird werden diese Ventilarten, wenn keine Komplikationen mit den elektrisch angetriebenen auftritt, nicht weiter betrachtet.

Bei einem elektrischen Stellventil ist in der Regel ein elektrischer Antrieb auf dem Ventil verbaut. Als Antrieb kommen verschiedenste Formen eines Motors in Frage. Dazu gehören auch Steppermotoren und Servomotoren. Das Stellventil besitzt die Möglichkeit je nach Modell stetige Werte zwischen geöffnet und geschlossen anzunehmen. Das ermöglicht eine 

