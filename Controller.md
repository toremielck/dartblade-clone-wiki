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

## Controller  

Der Controller ist verantwortlich für die gesamte des Spiels. Er ließt und schreibt Werte in das Model (*DartBladegameModel.dart*), welches dann wiederum die View (*DartBladegameView.dart*) updatet.

Im Code des Controllers befindet sich der Game-Loop. Dieser fragt durchgehend ab, ob Win- oder Lost-Bedingungen erfüllt sind. Sollte dies der Fall sein, wird das Spiel gestoppt und das nächste oder das selbe Level geladen. (Abhängig davon, ob man das Level gewonnen hat oder nicht.)  

Über einen *listener* an der *window.onDeviceOrientation* wird durchgehend die Neigung des Smartphones abgefragt. Die neuen Neigungswerte überschreiben dann die aktuelle Position des Spielers. Der Code hierfür sieht folgendermaßen aus:  

```dart
window.onDeviceOrientation.listen((ev) {

      /// Es ist keine device orientation verfügbar. - Zeige entsprechenden Hinweis
      /// in der View an.
      if (ev.alpha == null && ev.beta == null && ev.gamma == null) {
        _view.displayUseSmartphone.style.display = 'block'; // Show QR code
      }

      /// Device orientation ist verfügbar. - Lasse die Hinweise in der View verschwinden
      /// und rufe die [_player.move()]-Funktion mit den Bewegungs-Werten des Sensors auf.
      else {
        _view.displayUseSmartphone.style.display = 'none'; // Hide QR code
        if (_view.getLandscapeMode(_view.width, _view.height) == false) {
          _view.changeView.style.display = 'block';
        } else {
          _view.changeView.style.display = 'none';

          final dx = min(20, max(-20, ev.beta));
          final dy = min(-20, max(-80, ev.gamma)) + 50;

          _player.move(dx, dy);

        }
      }
```

### Game Loop

```dart
/// Haupt Game-Loop hier wird abgefragt, ob die Variblaen [isInitSpinTimerActive],
  /// [isPlayerTimerActive] und eine UND-Bedingung beider aktiv sind.
  /// Je nachdem, welcher der Satus aktiv ist wird ein onClick.listen() Event
  /// an ein Objekt in der View angehängt. Dieses wartet dann auf seine Aktivierung
  /// und startet die entsprechende Handler-Funktion.
  void gameLoop () {

    if(!isInitSpinTimerActive){
      _view.getSpin.onClick.listen((ev) => handlegGetSpin());

    }
    if(!isPlayerTimerActive){
      _view.startLevel.onClick.listen((ev) => handleStartLevel());
      _view.spinDisplay.onClick.listen((ev) => handleSpinDisplay());
    }


    if(!isInitSpinTimerActive && !isPlayerTimerActive){
      _view.displayLevelFailed.onClick.listen((ev)  => handledisplayLevelFailed());
      _view.displayLevelFinished.onClick.listen((ev) => handleDisplayLevelFinished());
    }

  }
```

Der Game Loop fragt während des laufenden Spiels durchgehend ab, ob und welche Timer aktiv sind. Je nachdem ob der Spin-Timer aktiv ist oder nicht mehr, (Spin ist abgelaufen.) hat man das Spiel gewonnen oder verloren.
Die Aktionen, welche nach dem Gewinnen oder Verlieren eines Levels auszuführen sind, werden über verschiedene Handler abgewickelt.  

Als Beispiel ist hier der Handler, welcher ausgeführt wird, wenn ein Level gewonnen wurde.  

```dart
/// Sollte die Sieg-Bedingung des Levels erfüllt werden werden auch hier genau
  /// wie beim erneuten Spielen eines Levels, durch erfülte Lost-Bedingung
  /// alle Variablen neu gesetzt und das Level per JSON vollständig neu geladen.
  void handleDisplayLevelFinished() async{

    /// Alle Timer beenden.
    cancelTimers();
    spinCount = 0;
    _player.spin = 0;
    _model.gameoverTrigger = -1;
    _view.displayLevelFinished.style.display ="none";

    if(_currentLevel <= _lastLevel){

      await _model.loadLevelInModel(_currentLevel);

      _view.getSpin.style.display ="block";
      loadCurrentLevel();

    }

  }
```