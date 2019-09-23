# Aufbau der Levels  

Die Levels unseres Spiels sind als JSON-Dateien kodiert. Diese werden dann geladen und dekodiert. Fertig dekodiert werden die einzelnen Zeichen der Level-Struktur dann als die Kacheln des Spielfeldes dargestellt.  

Als Beispiel hier das 4. Level (wir fangen bei 0 an zu zählen) kodiert in JSON:  

```json
{
  "levelNumber": 3,
  "size_x": 32,
  "size_y": 14,
  "levelStructur": "XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX|X##############################X|X##############################X|X##############################X|X##############################X|X##############################X|X########~#####################X|X##############################X|X#######X#X####################X|X######XXGXX###################X|X######XXXXX###################X|X##############################X|X##############################X|XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX|"
}
```  

die *levelNumber* gibt die Nummer des Levels an. Die Keys *size_x* und *size_y* geben die Größe des Levels an. Dies ist wichtig damit die Schleifen in denen die geparsde Level-Datei in die View geschrieben wird wissen, wann eine neue Zeile des Levels beginnt und wann die angegebene Höhe des Levels erreicht ist.  

Als letzter Key folgt die *levelStructur*. Diese ist das Level kodiert in ASCII-Zeichen.  

*  "X" steht für das Gameover-Tile.
*  "#" steht für ein Ground-Tile.
*  "G" steht für das Goal-Tile des Levels, welches es zu erreichen gilt.
*  "~" steht für das Spin-Tile, welches das Level zum wackeln bringt, soblad man rüberfährt.
*  "|" ist der Seperator. Dieser sagt dem Parser, dass eine neue Zeile anzufangen ist.

