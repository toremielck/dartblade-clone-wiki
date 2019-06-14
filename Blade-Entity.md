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

## Die Blade Entity  

Die Instanz der Blade Entity stellt das Haupt-Spielerobjekt dart und lässt sich über den in Smartphones enthaltenen Gyroskop-Sensor steuern. Dies passiert über folgende Funktion in der **Blade.dart **.  

```dart
/// Updatet die Position des Players entsprechend der Werte des Gyro-Sensors
  /// und führt die collision detection aus.
  void update() {

    collisionDetection();

    this.position_x += this.direction_x;
    this.position_y += this.direction_y;

    /// Stellt sicher, dass der Blade innerhalb des Viewports bleibt und sich nur das
    /// Level darunter in die entgegengesetzte Richtung bewegt.

    /// BEGRENZUNG OBEN
    if (this.top < 1) {
      this.position_y = this.radius + 1;
      view.moveLevel("down", 5);
    }

    /// BEGRENZUNG UNTEN
    if (this.bottom > this.view.height - 1) {
      this.position_y = this.view.height - this.radius - 1;
      view.moveLevel("up", 5);
    }

    /// BEGRENZUNG LINKS
    if (this.left < 1) {
      this.position_x = this.radius + 1;
      view.moveLevel("left", 5);
    }

    /// BEGRENZUNG RECHTS
    if (this.right > this.view.width - 1) {
      this.position_x = this.view.width - this.radius - 1;
      view.moveLevel("right", 5);
    }

  } 
```  

Es wird durch einen Timer in der **BladeGameController.dart** gesteuert die oben zu sehende Funktion aufgerufen.  

Diese **überschreibt** den aktuellen **Positionswert** des Blades mit der vom Gyroskop-Sensor kommenden **Bewegunsrichtung**. Sollte der Player den Rand des Viewport erreichen, so wird auch die **moveLevel()-Funktion** aus der View aufgerufen, um das Level in die entsprechende Richtung zu bewegen.  

Außerdem befindet sich innerhalb der **move()-Funktion** des Blades die Funktion **collisionDetection()**. Diese wird bei jeder Bewegung des Blades mit aufgerufen und überprüft, ob eine Kollision mit einem relevanten Objekt aufgetreten ist. (siehe [Die verschiedenen Tiles](Die verschiedenen Tiles)). Sollte dies der Fall sein, so wird die entsprechende Funktion des Tiles aufgerufen. Genauere Informationen zur Kollisions-Detektion sind hier zu finden:  

[Kollisions-Detektion](Kollisions-Detektion)