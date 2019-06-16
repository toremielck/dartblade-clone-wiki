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

## Verantwortlichkeiten im Projekt

| Komponente | Detail | Asset                                 | Verantwortlichkeit | Unterstützung | Anmerkungen | 
| ---------- | ------ | ------------------------------------- | ------------------ | ------------- | ----------- |
| Model      | Level | lib/src/model/DartBladeGameModel.dart | Mario Odzga         | Tore Mielck | Anmerkungen* |
|            | Blade | lib/src/model/DartBladeGameModel.dart |Tore Mielck         | Mario Odzga  | Anmerkungen* |
|            | Level-Secrets | lib/src/model/DartBladeGameModel.dart | Mario Odzga | Tore Mielck | Anmerkungen* |
|            | Laden der Level | lib/src/model/LoadingLevel.dart | Mario Odzga     | Tore Mielck | Anmerkungen* |
| View       | HTML-Dokument | web/index.html | Tore Mielck                       |  Mario Odzga | Anmerkungen*|
|            | Gestaltung | web/style.css |    Tore Mielck                         | Mario Odzga | Anmerkungen* |
|            | Bild Dateien | web/img/* |             Mario Odzga            |  Tore Mielck       | Anmerkungen* |
|            | Logik der View | lib/src/model/DartBladeGameView.dart |Tore Mielck  |  Mario Odzga| Anmerkungen* |
| Controller | Eventhandling | lib/src/model/DartBladeGameController.dart | Mario Odzga | Tore Mielck | Anmerkungen* |
|            | Level-Logik | lib/src/model/DartBladeGameController.dart | Mario Odzga | Tore Mielck | Anmerkungen* |
|            | Kollisionserkennung | lib/src/model/DartBladeGameController.dart | Tore Mielck |Mario Odzga  | Anmerkungen* |
|            | Timer-Handling | lib/src/model/DartBladeGameController.dart | Mario Odzga | Tore Mielck | Anmerkungen* |
| Level-JSONs |  | web/levels/* |                     Tore Mielck                | Mario Odzga   | Anmerkungen* |
| Dokumentation |  | doc/* |                   Tore Mielck                        |Mario Odzga   | Anmerkungen* |


*Anmerkung:   Jegliche Arbeit, Ideenfindung und Reflektion am Spiel erfolgte grundsätzlich zu zweit.
