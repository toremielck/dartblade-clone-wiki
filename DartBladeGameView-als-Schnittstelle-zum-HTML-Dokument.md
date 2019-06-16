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

## DartBladeGameView als Schnittstelle zum HTML-Dokument  

Die *DartBladeGameView.dart* ist die zentrale Schnittstelle zur *index.html*. Mit Hilfe ihrer Funktionen wird das HTML-Dokument befüllt und abgeändert während das Spiel läuft.  

Es wird beispielsweise die Position des Spielers, welcher in der *index.html* ein reines Div-Element ist von der *DartBladeGameView.dart* in die *index.html* übertragen. Dafür zuständig ist folgender Code:  

```dart
/// Updatet die Positionswerte des Players
  void update (Blade player){
    player.update();

    final round = "${this.size}px";

    this.blade.style.top = "${player.top}px";
    this.blade.style.left = "${player.left}px";
    this.blade.style.width = "${player.width}px";
    this.blade.style.height = "${player.width}px";
    this.blade.style.borderRadius = round;
  }
```  

Die Links-Rechts-Position des Spieler-Divs entspricht im Model *player.top*. Die Oben-Unten-Position des Spielers entspricht *player.left*.