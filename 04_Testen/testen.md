## Testen 

### Allgemein 
Das Projekt "Smarter Getränkespender mit Pulver- und Flüssigkeitsausgabe zielt darauf ab, einen steuerbaren Getränkespender zu entwickeln. Der Getränkespender soll Pulver, Sirup und Leitungswasser in variablen Mengen ausgeben können. Die wichtigsten Komponente des Getränkespenders ist der ESP Microcontroller mit dem Messen, Steuern und Regeln. Um die Funktionalität, die Zuverlässigkeit und die Benutzerfreundlichkeit des Systems sicherzustellen, ist die Durchführung umfangreicher Tests während der Entwicklungsphase von entscheidender Bedeutung. 

#### Wichtige Aspekte der Tests 
Für folgende Aspkete sind für die Tests von entscheidender Relevanz: 

1. Funktionalität: Um eine richtige Zusammenarbeit der einzelnen Komponenten zu gewährleisten und sicherzustellen, dass das System die korrekten Ergebnisse liefert, sollen Tests hinsichtlich der Funktionalität durchgeführt werden. Dies beinhaltet die Genaugikeit der Wägezelle, die präzise Steuerung der Pumpe und der Fürderschnecke und die Kommunikation des ESP32 mit den entsprechnenden Diensten des Raspberry Pi Servers. 

2. Zuverlässigkeit: Um sicherzustellen, dass der Getränkespender unter variablen Bedingungen und über einen längeren Zeitraum hinweg zuverlässig funktionert, sollen Belastungs- und Langzeittests durchgeführt werden. So können Schwachstellen im System identifiziert und bearbeitet werden, um die Langlebigkeit und die Robustheit des Getränkespenders zu verbessern. 

3. Benutzerfreundlichkeit: Da der Getränkespender intuitiv bedient werden soll, müssen auch Tests hinsichtlich der Benutzerfreundlichkeit durchgeführt werden. Sogenannte Usability-Test helfen dabei, mögliche Verbesserungen im Design des Interfaces zu identifizieren und die allgemeine Benutzerzufriedenheit zu erhöhen. 

4. Sicherheit: Da dem Thema Sicherheit die höchste Priorität zugewiesen wurden, ist es erfoderlich hier sehr umfangreiche Tests durchzuführen. Das Systen ist mit dem Hauswasseranschluss und Elektronik verbunden. Deswegen sollen Risiken im Zusammenhang mit Wasserlecks, Kurzschlüssen und anderen potenziellen Gefahren minimiert werden. Das Thema Sicherheit ist aus mehreren Gründen von großer Bedeutung: 
    + Schutz der Benutzer: Die Sicherheit des Benutzers stehst an erster Stelle. Elektrische Komponenten und Flüssigkeiten wie Wasser können eine gefährliche Kombination darstellen, wenn Sie nicht ordnungsgemäß behandelt werden. 
    + Schutz der Hardware und Infrastruktur: Durch Minimierung der Risiken von beispielsweise Wasserleks oder Kurzschlüssen wird die Lebensdauer der Komponenten verlängert und Schäden an der umliegenden Infrastruktur verhindert. 

    HIER NACH IEC NORM SCHAUEN, GIBT ES VORSCHRIFTEN, RICHTLINIEN ODER ANDERE REGELN 

5. Integrationstest: Mit den Durchführen von Integrationstest werden Risiken zum Auftreten von Inkompatibilitätsfehlern minimiert. Es soll sichergestellt werden, dass alle Komponenten innerhalb des Systems auch einwandfrei miteinander arbeiten. 
    
Auf Grundlage der zuvor erörterten Apsekte bezüglich der Testanforderungen wurde die Entscheidung für die folgenden Tests getroffen: 
    Mischverhältnis und Reihenfolge der Ausgabe 

    Präzision der Ausgabe

    Reproduzierbarkeit 

    Geschwindigkeit und Engergieverbrauch 

    Fehlererkennung und Behebung 

    Sicherheit 


