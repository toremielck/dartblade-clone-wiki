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