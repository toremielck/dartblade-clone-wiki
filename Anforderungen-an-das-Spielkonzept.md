# Inhaltsverzeichnis

1. [Anforderungen an das Spielkonzept](Anforderungen an das Spielkonzept)
2. [Spielkonzept](Spielkonzept)
3. [Architektur und Implementierung](Architektur und Implementierung)  
   3.1 [Model](Model)  
   3.1.1 [Blade Entity](Blade Entity)  
   3.1.2 [Kollisions-Detektion](Kollisions-Detektion)  
   3.2.3 [Aufbau der Levels](Aufbau der Levels)  
   3.2 [View](View)  
   3.2.1 [HTML-Dokument](HTML-Dokument)  
   3.2.2 [DartBladeGameView als Schnittstelle zum HTML-Dokument](DartBladeGameView als Schnittstelle zum HTML-Dokument)  
   3.2.3 [Die verschiedenen Tiles](Die verschiedenen Tiles)  
   3.3 [Controller](Controller)  
   3.3.1 [Laufendes Spiel](Laufendes Spiel)  
4. [Nachweis der Anforderungen](Nachweis der Anforderungen)
5. [Verantwortlichkeiten im Projekt](Verantwortlichkeiten im Projekt)


## Anforderungen an das Spielkonzept

*  Das Spiel soll als One-Player-Game konzipiert werden.
*  Es handelt sich bei dem Spiel um eine Single-Page HTML App.  
*  Das Spiel muss als **eine statische Website** von einem Webserver oder CDNs bereitgestellt werden können.
*  Die Steuerung des Spiels soll über den **Gyrokop-Sensor** eines Smartphones erfolgen  
*  Das Spiel soll zwischen technischer Komplexität und der Komplexität des Spielkonzeptes ausbalanciert sein.  
*  Das Spiel folgt dem **MVC- (Model, View, Controller) Prinzip**.  
*  Die View des Spiels ist der DOM-Tree  
*  Das Spiel ist für das Spielen auf einem Smartphone konzipiert (iOS oder Android).  
*  Das Spiel muss schnell und intuitiv erfassbar sein und Spielfreude erzeugen.  
*  Es gibt ein Levelkonzept.  
*  Das Spiel muss ausreichend dokumentiert sein.