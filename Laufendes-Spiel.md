# Inhaltsverzeichnis

1. [Anforderungen an das Spielkonzept](Anforderungen an das Spielkonzept)
2. [Spielkonzept](Spielkonzept)
3. [Architektur und Implementierung](Architektur und Implementierung)  
   3.1 [Model](Model)  
   3.1.1 [Blade Entity](Blade Entity)  
   3.1.2 [Kollisions-Detektion](Kollisions-Detektion)  
   3.2 [View](View)  
   3.2.1 [HTML-Dokument](HTML-Dokument)  
   3.2.2 [DartBladeGameView als Schnittstelle zum HTML-Dokument](DartBladeGameView als Schnittstelle zum HTML-Dokument)  
   3.2.3 [Die verschiedenen Tiles](Die verschiedenen Tiles)  
   3.3 [Controller](Controller)  
   3.3.1 [Laufendes Spiel](Laufendes Spiel)  
4. [Nachweis der Anforderungen](Nachweis der Anforderungen)
5. [Verantwortlichkeiten im Projekt](Verantwortlichkeiten im Projekt)  

## Laufendes Spiel  

Wenn die *Timer* gestartet sind startet auch das Spiel. Es wird durchgehend abgefragt, wie der Wert der Neigung des Smartphones ist. Dieser Bewegungs-Vektor überschreibt dann die aktuelle Position des Kreisels.  

Gleichzeitig findet die Kollisions-Erkennung statt. Diese befindet sich bei uns in der View, da wir die Überschneidung des Mittelpunktes des Spielers, also des Kreisels mit den Rändern der einzelnen Kacheln überprüfen. Ist dies bei einer Kachel, welche eine Aktion beim überqueren ausführt der Fall, so wird eben diese Aktion ausgeführt.

Landet der Spieler außerhalb des Levels oder innerhalb des Levels auf einer *GameOver-Kachel*, so ist das aktuelle Level verloren.  

Landet der Spieler allerdings auf der *Goal-Kachel*, so ist das aktuelle Level gewonnen und es wird das nächste Level geladen.