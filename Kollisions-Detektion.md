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