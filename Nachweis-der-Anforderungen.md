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

## Nachweis der Anforderungen  

| ID    | Kurztitel                              | Erfüllt | Teilw. erfüllt | Nicht erfüllt | Erläuterung |
| ------| -------------------------------------- | ------- | -------------- | ------------- | ----------- |
| AF-1  | Single-Player-Game als Single-Page-App | X       |                |               |             |
| AF-2  | Balance zwischen technischer Komplexität und Spielkonzept | X       |                |               |             |
| AF-3  | DOM-Tree-basiert                       | X       |                |               |             |
| AF-4  | Target Device: SmartPhone und Gyroskop-Steuerung | X              |               |              |             |
| AF-5  | Mobile First Prinzip                   | X       |                |               |             |
| AF-6  | Intuitive Spielfreude                  | X       |                |               |             |
| AF-7  | Das Spiel muss ein Levelkonzept vorsehen | X       |                |               |             |
| AF-8  | Ggf. erforderliche Speicherkonzepte sind Client-seitig zu realisieren | X       |                |               |Speicherkonzept ist über Level-Secrets realisiert|
| AF-9  | Basic Libraries                        | X       |                |               |             |
| AF-10 | Keine Spielereien                      | X       |                |               |             |
| AF-11 | Dokumentation                          |         | X              |               | Die Dokumentation ist evtl. nicht so umfangreich, wie von Ihnen erwartet            |