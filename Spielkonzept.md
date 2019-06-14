# Inhaltsverzeichnis

1. [Anforderungen an das Spielkonzept](Anforderungen an das Spielkonzept)
2. [Spielkonzept](Spielkonzept)
3. [Architektur und Implementierung](Architektur und Implementierung)  
   3.1 [Model](Model)  
   3.1.1 [Blade Entity](Blade Entity)  
   3.2 [View](View)  
   3.2.1 [HTML-Dokument](HTML-Dokument)  
   3.2.2 [DartBladeGameView als Schnittstelle zum HTML-Dokument](DartBladeGameView als Schnittstelle zum HTML-Dokument)  
   3.2.3 [Die verschiedenen Tiles](Die verschiedenen Tiles)  
   3.3 [Controller](Controller)  
   3.3.1 [Laufendes Spiel](Laufendes Spiel)  
4. [Nachweis der Anforderungen](Nachweis der Anforderungen)
5. [Verantwortlichkeiten im Projekt](Verantwortlichkeiten im Projekt)



Der Spieler übernimmt die Steuerung eines Kreisels auf einer schwebenden Plattform. Ziel des Spiels ist es, den Kreisel erfolgreich durch die verschiedenen Level zu führen, ohne, dass er von der Plattform fällt. Am Anfang bekommt der Spieler die Chance dem Kreisel einen Spin mitzugeben, der mit der Zeit immer geringer wird. Sobald der Kreisel stehen bleibt oder von der Plattform fällt, muss der Spieler das Level erneut starten, um weiterzukommen Von Level zu Level erhöht sich der Schwierigkeitsgrad. Das Zeigt sich durch folgende Parameter:

*  Länge des Levels
*  Komplexität des Levels
*  verschiedene Items im Level

Das Level besteht aus einem n x m Feld, welches hardcodiert in einer JSON-Datei geschrieben wird. Diese JSON-Dateien werden im Spielverlauf vom Sever nachgeladen. Das Spiel ist für ein Smartphone konzipiert und die Hauptsteuerung des Kreisel erfolgt durch den Gyroskopsensor.