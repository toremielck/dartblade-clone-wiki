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

## HTML Dokument 

Die index.html wird als statisches HTML-Dokument vom Browser aufgerufen. Dann wird diese von der **DartBladeGameView.dart** im Verlaufe des Spiels manipuliert. So stellt das HTML-Dokument zu jeder Zeit den aktuellen Status des Spiels grafisch dar.  

```html
<!DOCTYPE html>

<html>

<head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <meta name="scaffolded-by" content="https://github.com/google/stagehand">
    <title></title>
    <link rel="stylesheet" href="styles.css">
    <link rel="icon" href="favicon.ico">
    <script defer src="main.dart.js"></script>
</head>

<body>
    <div id="displayUseSmartphone">Please use your Smartphone</div>
    <div id="changeView">Please use landscape Mode</div>
    <div id="startMenu">
        <h1 id="gameTitle">Dartblade</h1>

        <span id="start" class="menuPoint">start new game</span>
        <span id="entersecret" class="menuPoint">enter secret</span>
        <span class="menuPoint">instructions</span>
    </div>

    <div id="game">
        <div id="getSpin">click to start spin</div>
        <div id="startLevel"></div>
        <div id="debugOutput"></div>
        <div id="spinDisplay">Spin</div>
        <span id="displayLevelFinished"></span>
        <span id="displayLevelFailed"></span>
        <div id="level"></div>
        <div id="blade"></div>
    </div>

</body>

</html>
```  

Das *div* mit der id *level* nimmt hierbei eine besonders wichtige Funktion ein. In ihm werden von der **fillLevelWithEntity** Funktion der **DartBladeGameView.dart** die einzelnen Kacheln des Levels geladen. Dies passiert nachdem das aktuelle Level aus einer JSON-Datei ausgelesen wurde. Danach wird das *level*-Div mit den in der JSON-Datei enthaltenen verschiedenen Kacheln befüllt.  
Es wird also noch nachträglich neuer HTML-Code in das Dokument eingefügt.