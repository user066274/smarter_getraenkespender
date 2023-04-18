
# Systemarchitektur

Die gesamte Systemarichtektur des Projekts "smarter Getränkespender" lässt sich logisch in zwei Beschreibungen unterteilen. Die erste Beschreibung "Aufbau des Getränkespenders" umfasst nur den Getränkespender. Alle Komponenten, die sich physisch in den Getränkespender befinden, werden in der ersten Beschreibung erfasst. Dazu gehören die Themenbereiche Hardware, kabelgebundene Kommunikation und Sesoren & Aktoren. Die zweite Beschreibung defninert den Getränkespender als Blackbox, welcher Schnittstellen nach außen exponiert. Die zweite Beschreibung "Systemübersich" schaut von außen auf das gesamte System und umfasst die Kommunikation zwischen dem Getränkespender und dem Server. Der Fokus liegt hier auf dem Server und dessen Konfiguration. 

## Aufbau des Getränkespenders 


**Hier deine Beschreibung NIKLAS**
------------------------------------

## Systempübersicht 

Die allgemeine Systemarchitektur basiert auf dem Client-Server Prinzip. Das Client-Server-Modell ist grundsätzlich eine Möglichkeit, um die Verteilung von Dienstleistungen und Aufgaben innerhalb eines Netzwerks zu realisieren. 

    Quelle 1

Die Kommunikation zwischen dem Getränkespender und dem Server wird mit Hilfe des "Message Queuing Telemetry Transport (MQTT)" Protokolls realisiert. In Kapitel 03 Methodik und Materialien wird diskutiert, warum das MQTT Protokoll für die Kommunikation verwendet wird und welche möglichen Alternativen dafür in Betracht gezogen wurden. Der Raspberry Pi übernimmt mehrere Funktionen innerhalb der Systemarchitektur. Er fungiert als Webserver, um eine Benutzeroberfläche zur Verwaltung und Steuerung des Getränkespenders bereitzustellen. Zudem dient der Raspberry Pi als Datenbank Server, um langfristig Konfigurationsdaten und Statistiken zu speichern. Neben dem Service des Datenbankservers übernimmt der Raspberry Pi noch den Service des MQTT Brokers. Da das MQTT Protokoll eventbasiert arbeitet, ist ein MQTT für die Kommunikation zwingend erforderlich. 

    Quelle 2

Innerhalb des Getränkespenders ist der EPS32 für die Ansteuerung von Pumpen, Förderschnecken und zum Auslesen der Wägezelle zuständig. Die Kommunikation zwischen Raspberry Pi und ESP32 erfolgt via MQTT-Protokoll.

Folgende Grafik soll die Systemübersicht vereinfacht darstellen. Auf der linken Seite ist der Raspberry Pi dargestellt, auf dem mit Hilfe von Docker die einzelnen Services verwaltet und ausgeführt werden. Jeder Service hat einen oder mehrere Ports nach "außen" freigegeben, um für andere Teilnehmer innerhalb des Netzwerks erreichbar zu sein. In der rechten Seite der Grafik ist der Getränkespender als Blackbox dargestellt (grau), welche in diesem Fall der MQTT-Client ist. 

!["alt text"](/ressources/systemuebersicht.jpeg)

## Quellen
Quelle 1: https://books.google.de/books?hl=de&lr=&id=A9LPBgAAQBAJ&oi=fnd&pg=PA1&dq=client+server+architektur&ots=HoXk-kRJMU&sig=ywR2YH7JrqyxWwzbRL4DrUR-920#v=onepage&q=client%20server%20architektur&f=false

Quelle 2: https://www.hivemq.com/mqtt-essentials/
