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

## Kollisions Detektion

Die Kollisions-Detektion ist ein Herzstück unseres Spiels. Es muss bei jeder Bewegung des Spielers überprüft werden, ob soeben eine Kollision mit einem relevanten Tile stattgefunden hat.  

Dies passiert über folgenden Code:  

```dart
/// Collision detection
  /// Die collision detection geht durchgehend die Liste aller Tiles durch und
  /// überprüft, ob der Mittelpunkt des Players eine der Seiten eines Tiles berührt
  /// hat.
  /// Je nachdem welcher Tile-Typ es ist wird eine oder keine Aktion ausgeführt.
  void collisionDetection() {

    /// Einlesen der Liste aller Tiles
    var tiles = saveAllTilesInList();

    /// Eigentliche collision detection
     tiles.forEach((tile) {

      if (bladeCenterPoint().x >= fieldCenterPoint(tile).x - 25 &&
          bladeCenterPoint().x <= fieldCenterPoint(tile).x + 25 &&
          bladeCenterPoint().y >= fieldCenterPoint(tile).y - 25 &&
          bladeCenterPoint().y <= fieldCenterPoint(tile).y + 25) {

        if(tile.getAttribute("tileType") == "gameover-tile"){

          model.setLevelLost();

        }
        if(tile.getAttribute("tileType") == "goal-tile"){

          model.setLevelWon();

        }
      }
    });
  }
```  

Es wird zunächst eine Liste aller Tiles des aktuellen Levels eingelesen. Dann wird für jedes Tile in dieser Liste überprüft, ob der Spieler den linken, oberen, unteren oder rechten des Tiles überquert hat. Sollte dies der Fall sein, wird das Type-Attribut des entsprechenden Tiles ausgelesen und die dazugehörige Funktion ausgeführt.  
(Es sind hier aus Demonstrationszwecken nicht alle Tile-Typen und deren Aktionen im Code aufgefürt!)