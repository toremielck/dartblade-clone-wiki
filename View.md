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

## View

### Füllen des Levels mit den Tiles  

Das Level wird über die Funktion *fillLevelWithEntity* mit den Kacheln des aktuellen Levels befüllt.  

```dart
/// Füllen des HTML-Level-Elements mit den verschiedenen Tile-Typen als Divs
  ///
  /// Es wird jedem Div ein Typ und ein x-, sowie y-Wert mitgegeben.
  void fillLevelWithEntity(List<List<TileTypes>> l ){

    int _row = 0;
    int _col = 0;

    /// Gehe die Liste mit den verschiedenen Typen an Tiles, welche übergeben wird
    /// durch und füge je nachdem, welches es ist eines in das HTML-Level-Element ein.
    for(List<TileTypes> row in l){
      var tileDiv = new DivElement();
      tileDiv.className = "tr";
      level.children.add(tileDiv);
      for(TileTypes s in row){
        switch (s){
          case TileTypes.GROUNDTILE:
            var tileDiv = new DivElement();
            tileDiv.className = "td ground-tile";
            tileDiv.setAttribute("tileType", "ground-tile");
            tileDiv.setAttribute("x", "$_col");
            tileDiv.setAttribute("y", "$_row");
            level.children.add(tileDiv);
            break;
          case TileTypes.GAMEOVERTILE:
            var tileDiv = new DivElement();
            tileDiv.className = "td gameover-tile";
            tileDiv.setAttribute("tileType", "gameover-tile");
            tileDiv.setAttribute("x", "$_col");
            tileDiv.setAttribute("y", "$_row");
            level.children.add(tileDiv);
            break;
          case TileTypes.SPINTILE:
            var tileDiv = new DivElement();
            tileDiv.className = "td spin-tile";
            tileDiv.setAttribute("tileType", "spin-tile");
            tileDiv.setAttribute("x", "$_col");
            tileDiv.setAttribute("y", "$_row");
            level.children.add(tileDiv);
            break;
          case TileTypes.GOALTILE:
            var tileDiv = new DivElement();
            tileDiv.className = "td goal-tile";
            tileDiv.setAttribute("tileType", "goal-tile");
            tileDiv.setAttribute("x", "$_col");
            tileDiv.setAttribute("y", "$_row");
            level.children.add(tileDiv);
            break;
          default:
            break;
        }
        _col++;
      }
      _col = 0;
      _row++;
    }
  }
```  

Wie man sehen kann wird eine Liste von Kacheln als Parameter der Funktion übergeben. Diese erstellt dann mit Hilfe der ersten Schleife jeweils eine Reihe des Levels, welche dann wiederum mit Hilfe der zweiten verschachtelten Schleife, in welcher sich ein *switch* befindet, der die unterschiedlichen Kacheln unterscheidet, jeweils ein Div-Element in Dart erstellt. Diesem Div-Element werden dann die dem Kachel-Typ entsprechenden Attribute (Kachel-Typ) als HTML-Parameter angehängt. Außerdem erhält jede Kachel einen x- und y-Wert, sodass die Position der Kachel im Level ausgelesen werden kann.

### Bewegen des Levels  

```dart
/// Bewegen des Levels in eine [direction] und mit einem [movingSpeed]
  void moveLevel(direction, movingSpeed) {

    switch (direction) {
      case 'up':
        levelPositionTop -= movingSpeed;
        level.style.setProperty("top", "${levelPositionTop}px");
        break;
      case 'down':
        levelPositionTop += movingSpeed;
        level.style.setProperty("top", "${levelPositionTop}px");
        break;
      case 'left':
        levelPositionRight -= movingSpeed;
        level.style.setProperty("right", "${levelPositionRight}px");
        break;
      case 'right':
        levelPositionRight += movingSpeed;
        level.style.setProperty("right", "${levelPositionRight}px");
        break;
      default:
        break;

    }
  }
```  

Über die oben gezeigte Funktion **moveLevel()**, welche aufgerufen wird sobald der Spieler den Rand des Viewports erreicht wird das Level je nachdem, ob der Spieler den Viewport links, oben, unten oder rechts berührt, das Level in die genau entgegengesetzte Richtung bewegt. Die Funktion **moveLevel()** nimmt zwei Parameter entgegen:  

1.  Die Richtung in die das Level bewegt werden soll
2.  Die Geschwindigkeit mit der die Bewegung ausgeführt werden soll (in Pixel pro Timer-Intervall)