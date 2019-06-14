# Inhaltsverzeichnis

1. [Anforderungen an das Spielkonzept](Anforderungen an das Spielkonzept)
2. [Spielkonzept](Spielkonzept)
3. [Architektur und Implementierung](Architektur und Implementierung)  
   3.1 Model  
   3.1.1 Blade Entity  
   3.2 View  
   3.2.1 HTML-Dokument  
   3.2.2 DartBladeGameView als Schnittstelle zum HTML-Dokument  
   3.3 Controller  
   3.3.1 Laufendes Spiel  
4. [Nachweis der Anforderungen](Nachweis der Anforderungen)
5. [Verantwortlichkeiten im Projekt](Verantwortlichkeiten im Projekt)


## Anforderungen an das Spielkonzept

*  Das Spiel soll als One-Player-Game konzipiert werden.
*  Es handelt sich bei dem Spiel um eine Single-Page HTML App
*  Das Spiel muss als **eine statische Website** von einem Webserver oder CDNs bereitgestellt werden können.
*  Die Steuerung des Spiels soll über den Gyrokop-Sensor eines Smartphones erfolgen