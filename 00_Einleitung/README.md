# Einleitung 
Heutzutage sind intelligente Geräte und Automatisierungstechnologien im Vormarsch und dringen immer weiter in das tägliche Leben ein. Mit diesem Hintergrund wurde das Projekt des smarten Getränkespenders durchgeführt. Der Getränkespender soll moderne Technologien mit alltäglichen, wiederkehrenden Handlungen vereinen. 

Das Projekt besteht grundlegened aus einem selbstgebauten Getränkespender, der sowohl Pulver und Sirup als auch Wasser ausgeben kann. Mit dem Einsatz von Microcontrollern, Sensoren, Aktoren und Datenbanktechnologien wird die Steuerung teilweise automatisiert und bietet dem Benutzer eine intuitive Schnittelstelle zur Interaktion. Die folgende wissenschaftliche Arbeit soll technische Details des Projekts erläutern, die Durchführung von Tests und deren Ergebnisse analysieren und mögliche Anwendungsbereiche und Verbesserungen aufzeigen. 

## Hintergrund und Motivation 

Die Entwicklung eines smarten Getränkespenders mit Sirup- und Pulverausgabe ist ein iderdisziplinäres Projekt, welches im Rahmen einer Studienarbeit an der dualen Hochschule Mannheim durchgeführt wurde. 

**Hintergrund**: 

Grundsätzlich ist das Konzept eines automatisierten Getränkespenders nicht neu. Viele Unternehmen und Foschungsgruppen haben bereits Systeme zur automatisierten Getränkezubereitung entwickelt und vermarktet. Eine vielzahl dieser Systeme sind jedoch auf bestimmte Getränkearten beschränkt oder erfordern den Einsatz von speziellen Hülsen oder Patronen für die Zubereitung. Die Idee des smarten Getränkespenders besteht also darin, ein variablen und vielseitiges System zu entwickeln, welches aus generischem Pulver und Sirup Getränke zubereiten kann, ohne auf die Form und Art der Verpackungen angewiesen zu sein. 

**Motivation**: 

Die Motivation der Umsetzung des Getränkespenders als Studienarbeit lässt sich mit mehreren Faktoren begründen. Einerseits bietet das Projekt die Möglichkeit erworbene Kenntnisse aus unterschiedlichen Kursen wie Elektrotechnik, Informatik und Sensorik & Aktorik praktisch anzuwenden und zu vertiefen. Andererseits ist es möglich, einen funktionalen Prototypen für das Projekt zu entwickeln, der den Anfoderungen gerecht wird. 

Abgesehen von der Zeitersparnis, die das feritge Projekt mit sich bringt, hat das Projekt auch Potential positive gesellschaftliche und ökologische Auswirkungen zu erzielen. Der Getränkespender kann dazu beitragen, die Verwendung von Einwegverpackungen zu reduzieren und somit den Plastikmüll zu verringern. Abgesehen davon kann ein solches System für Personen mit eingeschränkter Mobilität oder für Personen mit Behinderungen die Zubereitung und Aufnahme von Getränken erleichtern.  

Insgesamt dient die Entwicklung des Projektes als Studienarbeit an einer Hochschule dazu, das erlernte theoretische Wisen in einem praktischen Konsens anzuwenden und zusätzlich ein nützliches System zu entwickeln, das sowohl den Benutzern als auch der Umwelt zugute kommen kann. 


## Zielsetzung des Projekts 

Das Ziel der vorliegenden Arbeit ist es, eine moderne und kostengünstige Lösung eines Getränkespenders zu entwickeln, das dem Benutzer Zeit einspart und zugleich leicht reproduzierbar ist. Mit der Untersuchung der technischen Komponenten und Prozesse soll ein allgemeines Verständnis für die Funktionsweise und vorallem die Anwendbarkeit einer solchen Technologie im alltäglichen Leben gemacht werden. Der Weg für die Entwicklung praktischer und leicht reproduzierbarer Technologien soll geebnet werden, damit diese den Alltag erleichtern und effizienter gestalten. 

## Abgrenzung des Themas und Definitionen: 

In der vorliegenden Arbeit wird der Schwerpunkt auf die Entwicklung gesetzt. Im das Thema präzise und verständlich abgerenzen zu können, sind einige zentrale Begriffe und Definitionen wichtig. 

1. Smarter Getränkespender: 
    Ein Smarter Getränkespender ist eine Lösung, die eine automatisierte Getränkezubereitung bereitstellt, sodass variable Mengen an Pulver und Flüssigkeitn ausgegeben werden können. Basierend auf dem Zitat "A smart device is a context-aware electronic device capable of performing autonomous computing and connecting to other devices wire or wirelessly for data exchange." kann der Getränkespender als intelligenten Gerät bezeichnet werden. 
        ***Zitat markieren***!
    
    Laut Definition ist ein smarter Getränkespender in der Lage, sowohl die Umgebung als auch Benutzerpräferenzen zu erkennen und auf diese zu reagieren. Für eine autonome Verarbeitung ist der verbaute Mikrocontroller zuständig, der verschiedene Sensoren liest und mehrere Aktoren steuert. Die Kommunikation der einzelnen Komponenten des Projekts erfolgt kabelgebunden als auch drahtlos. 

    Zudem kann der "smarte" Getränkespender mit anderen Geräte wie dem Raspberry Pi kommunizieren und Daten austauschen. Ein Benutzer kann mit Schnittstellen in Form von Tasten an dem Getränkespender oder über eine Weboberfläche mit dem Gerät interagieren. 

2. Förderschnecke 
    Die sogenannte Förderschnecke ist eine essenzielle Komponente in der Entwicklung des smarten Getränkespenders. Im Zusammenhang mit dem Getränkespender wird die Förderschnecke verwendet, um eine präzise und kontrollierte Menge an Pulver ausszugeben. Allgemein besteht die Förderschnecke aus einem spirlförmigen Gewinde, das sich in einem Rohr oder Trog um eine zentrale Welle dreht und dabei Material entlang der Achse befördert. 
    
    Das ausgegebene Pulver löst sich beim Vermengen mit Wasser auf und kann konsumiert werden. Die trägt maßgeblich zur Reduzierung von Verschwendung bei und ermöglicht gleichzeitig eine einfache Reinigung und Wartung des gesamten Systems. 
    
    Später wird die Funktionsweise, das Design und die Anwenduung der Förderschnecke genauer diskutiert. 

3. Wägezelle 
    Unter wissenschaftlicher Betrachtung im Kontext des Getränkespenders ist die Wägezelle ein entscheidender Bestandteil des System, indem sie präzise Messungen der ausgegebenen Pulver-, Sirup- und Wassermenge ermöglicht. Grundsätzlich ist eine Wägezelle ein elektronischer Sensor, welcher auf dem Prinzip der Dehnungsmessstreifen basiert. Hierbei wird die auf die Wägezelle wirkende Kraft in ein elektrisches Signal umgewandelt, das (ideal) proportianl zur Größe der Kraft ist. Somit kann das Gewicht, das auf die Wägestelle wirkt, berechnet werden. 

    Durch die Integration der Wägezelle soll eine konstante und wiederholbare Qualität des Getränks sichergestellt werden. Die Qulität entspricht in diesem Zusammenhang dem Mischverhältnis von Pulver oder Sirup zu Wasser. 

4. Mikrocontroller (ESP32)
    Der Mikrocontroller ist im Rahmen des Projekts die wichtigste Komponente. Der Mikrocontroller ist für die Steuerung der einzelenen Komponenten im System verantwortlicht. Fällt der Mikrocontroller aus, ist keine Ausgabe von Getränken mehr möglich. 

    Allgemein ist ein Mikrocontroller ein integrierter Schaltkreis, welcher mindestens einen Prozessor, Speicher und programmierbare Ein- und Ausgänge enthält. Basierend auf den von Entwicklern geschriebenen Programmen ist er in der Lage eine Vielzahl von Aufgaben auszuführen.

    "Mikrocontroller (µC) sind aus modernen technischen Systemen nicht mehr wegzudenken. Unbemerkt verrichten sie in den Bereichen Unterhaltungselektronik, Mobiltelefone, Chipkarten und PCPeripherie-Geräte ihren Dienst. In einem aktuellen Mittelklassewagen sorgen bis zu 80 Mikrocontrollersysteme unter anderem für die korrekte Funktion von Fahrassistenzsystemen, Multimediaanwendungen und der Klimaautomatik. Innovationen und Neuheiten im Automobilbereich basieren zum großen Teil auf mikrocontrollerbasierten Sensor-Aktor-Systemen.". Das genannte Zitat verdeutlicht die entscheidende Rolle von Mikrocontrollern in modernen technischen Systemen. Bezogen auf den "smarten" Getränkespenders verdeutlicht das Zitat die Relevanz und den Einfluss von Mikrocontrollern in der Steuerung von komplexen technischen Systemen. 

    ***Zitat markieren***

    Der in diesem Projekt eingesetzte ESP32 ist nur ein Beispiel von dafür, wie Mikrocontroller Technologien revolutionieren und neue, schlanke Lösungen für verschiedenste Herausforderungen bereitstellen. 


5. Raspberry Pi
    Eine andere Komponete des Systems ist der RaspberryPi. Der Raspberry Pi dient als zentrale Schnittstelle für die generelle Datenverarbeitung und Benutzerinteraktion. 
    Der Raspberry Pi ist ein kostengünstiger Einplatinencomputer, der trotz seiner geringen Größe genug Rechenleistung mitsich bringt, um vielen Einsatzmöglichkeiten in komplexen Projekten gerecht zu werden. 

    Im Kontext des Projekts fungiert der Raspberry Pi als Server, um benötigte Dienste und Services auszuführen. Ein Beispiel eines solchen Dienstes ist der Webserver. Um Benutzern eine Schnittstelle zur Interaktion mit dem System zu bieten, hostet der Raspberry Pi einen Webserver, während die Datenbank für die Speicherung von Statistiken, Rezepten und weiteren Konfigurationen zuständig ist. Durch die Integration des Raspberry Pis wird eine flexible und erweiterbare Plattform für den Getränkespender geschaffen.  


## Allgemeiner Aufbau der Arbeit

In dieser wissenschaftlichen Arbeit zur Entwicklung eines smarten Getränkespenders wird der allgemeine Aufbau so gestaltet, dass sowohl eine klare Struktur als auch eine logische Darstellung und Reihenfolge der wichtigsten Aspekte des Projekts gewährleistet werden kann. Der gesamte Inhalt der Arbeit gliedert sich in sieben Hauptabschnitte: 

**Einleitung**:    

Die Einleitung soll ein groben Überblick über die Themenstellung des Projekts, dessen Hintergrund und Motivation und dessen Ziele bieten. Das Projekt wird in einem größeren Kontext dargestllt und erläutert die Bedeutung des Themas 

**Literaturübersicht**: 

Der Abschnitt Literaturübersicht bietet eine vereinfachte Übersicht den aktuellen Stand der Technik im Bereich des Getränkespenders sowie in den Bereichen der verwandten Technologien. 

**Material und Methodik**: 

Hier werden alle verschiedenen Techniken, Werkzeuge und Ansätze beschrieben, die für die Entwicklung des Getränkespenders angewendet wurden. Hierzu gehört auch die Auswahl der Komponenten, die Programmierung des Mikrocontrollers und die Entwicklung der Benutzeroberfläche. 

**Testen**

Im Abschnitt Testen werden die angewendeten Testverfahren beschrieben. Nachdem die Tests theoretisch untermauert wurden, werden diese durchgeführt und dokumentiert. 

**Ergebnisse und Ausblick** 

Der Schlussfolgerungsteil wertet die Testergebnisse aus und analysiert diese. Allgemein werden die wichtigsten Ergebnisse der Arbeit zusammengefasst und interpretiert. Zudem bietet dieser Abschnitt einen Ausblick auf mögliche zukünftige Verbesserungen des Getränkespenders und bewertet die erzielten Fortschritte im Kontext der ursprünglichen Projektziele und -motivationen. 

**Literaturverzeichnis**

Das Literaturverzeichnis listet alle verwendeten Quellen, die im Laufe der Arbeit zitiert oder refernziert wurden, auf. 
## Quellen 

+ https://viejournal.springeropen.com/articles/10.1186/s40327-018-0063-8
+ https://www.lmt.uni-saarland.de/sitemedia/lehre/Modulbeschreibungen/kript_uC_Praktikum.pdf