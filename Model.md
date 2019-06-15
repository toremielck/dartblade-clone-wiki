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

## Model  

Im Model wird der aktuelle Zustand des Spiels gespeichert. Der Zustand wird von *Events* aus dem Controller geändert.  

Zu Beginn des Spiels wird das erste Level aus einer JSON-Datei geladen. Dies passiert über die Funktion **loadLevelInModel**, welche hier zu sehen ist:  

```dart
Future<bool> loadLevelInModel(int levelNumber) async {
    _player = null;
    _level = null;
    if(!await LoadingLevel.getLevelDataFromJSON(levelNumber)) return false;
    _currentLevel = LoadingLevel._levelNumber;
    _levelSecret = getLevelSecretFromLevelNumber(_currentLevel);
    _level = new Level(LoadingLevel._levelStructur, LoadingLevel._levelNumber, LoadingLevel._size_x, LoadingLevel._size_y, this);
    return true;
  }
```  

Die Funktion bekommt das zu ladene Level als Integer-Wert übergeben. Danach werden das Spieler-Objekt und das Level-Objekt auf *null* gesetzt. Dies ist erforderlich, damit der Spieler beim Neustart des Levels nicht am Punkt startet, an dem er beim Beenden des Levels war. Außerdem wird das Level zurückgesetzt, um auch hier nicht den vorherigen Status im neuen Level bzw. Versuch zu erhalten.  

Innerhalb der Funktion bedienen wir uns der Funktion **getLevelDataFromJSON(levelNumber))** aus der Helfer-Klasse **LoadingLevel**. Diese läuft asynchron, da gewartet werden muss, bis die gesamte JSON-Datei eingelesen ist. Dann werden die Werte aus der entsprechenden JSON-Datei in die Model-Variablen übertragen.

