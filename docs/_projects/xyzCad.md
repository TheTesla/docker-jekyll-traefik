---
layout: single 
title: "xyzCad"
subtitle: "Konstruktionssoftware zum Entwurf von 3D-Modellen aus Python-Funktionen"
excerpt: "Diese Programm-Bibliothek wandelt den Graphen einer Python-Funktion in Abhängigkeit der drei Raumkoordinaten in einen Volumenkörper in Form einer STL-Datei um."
header:
  teaser: /assets/images/xyzCad_thumb.webp
canonical_url: "https://entroserv.de/Projekte/xyzCad"
categories:
  - Software
tags:
  - Projekt
sidebar:
  - title: "xyzCad"
    image: /assets/images/xyzCad.webp
    image_alt: "Symbolfoto 3D-gedruckte Teile, entworfen mit xyzCad"
    text: "[GitHub](https://github.com/TheTesla/xyzcad){: .btn .btn--info}"
  - text: "[Telegram](https://t.me/xyzcad_de_grp){: .btn .btn--info}"
    
---

Bei der Konstruktion von Maschinenelementen besteht oft die Anforderung, gekrümmte Funktionsoberflächen zu beschreiben. Das können bspw. Gewinde, Zahnräder, Flügel oder Luftschrauben sein. Die Geometrie soll dabei spezifische physikalische Eigenschaften erfüllen. Diese werden üblicherweise in Form mathematischer Gleichungen elegant beschrieben. 

Wünschenswert ist deshalb eine Konstruktionssoftware, welche aus mathematischen Formeln dreidimensionale Geometrien in einem fertigungsfreundlichen Format generieren kann. Das ist beispielsweise mit dem Plugin _XYZ Math Surface_ für _Blender_ möglich. Es sind drei separate Funktionen für die drei Raumkoordinaten in Abhängigkeit der zwei Laufvariablen `u` und `v` anzugeben. Diese Methode ist jedoch mit der Schwierigkeit verbunden, Gleichungen in die drei Koordinaten umzustellen. 

Die _Python_-Bibliothek `xyzcad` vereinfacht die 3D-Konstruktion auf der Basis von (Un-)Gleichungen. Es ist eine Funktion `f(x,y,z)` in Abhängigkeit der drei Raumkoordinaten anzugeben. Der Rückgabewert ist entweder `True` oder `False`. Nur an Punkten im Raum, wo die Funktion `True` zurückgibt ist Material. Dadurch kann die Funktion aus Ungleichungen aufgebaut werden, wobei der Rückgabewert anzeigt, ob die Ungleichung oder Kombination von Ungleichungen an dem jeweiligen Ort im Raum erfüllt ist. 

## Installation

Die _Python_-Bibliothek `xyzcad` und alle ihre Abhängigkeiten können vom _Python Package Index (PyPI)_ bezogen werden:

```bash
python3 -m pip install xyzcad
```

Es wird die Abhängigkeit `numba` installiert. Das ist ein Just-In-Time-Compiler, der unter bestimmten Bedingungen _Python_-Code in nativen Maschinencode umwandeln kann. Dadurch ergibt sich ein Geschwindigkeitsvorteil um den Faktor 100. Eine optimale Geschwindkeitssteigerung wird jedoch nur bei Verwendung von `numpy`-Datentypen erzielt, weshalb auch diese Bibliothek installiert wird. Die STL-Datei wird mit `numpy-stl` erstellt. Das ist ein weiteres separates Paket, das nicht in `numpy` enthalten ist.

Die erstellten STL-Dateien können mit einem geeigneten Slicer angezeigt und für den 3D-Drucker weiterverarbeitet werden. Ist zunächst nur die Darstellung des 3D-Modells ohne 3D-Druck gewünscht, kann dafür auch `view3dscene` installiert werden:

```bash
sudo apt install view3dscene
```

## Benutzung

Für einen ersten Testlauf nach der Installation kann das nachfolgende Minimalbeispiel ausprobiert werden: 

```python
#!/usr/bin/env python3

from numba import jit
from xyzcad import render

@jit(nopython=True)
def f(x,y,z):
    r = 10
    return r**2 > x**2 + y**2 + z**2

render.renderAndSave(f, 'sphere.stl', 0.3)
```

Angenommen dieser _Python_-Code wird als Datei unter dem Namen `sphere.py` abgespeichert, muss er für die Erstellung der STL-Datei nur noch ausgführt werden:

```bash
python3 sphere.py
```

Die Berechnung dauert einige Sekunden. Nach Abschluss ist das 3D-Modell unter dem Namen `sphere.stl` im aktuellen Ordner auffindbar. Es kann mit folgendem Befehl betrachtet werden:

```bash
view3dscene sphere.stl
```

Es ist eine Kugel mit dem Radius `r = 10` mm. Diese wird durch die Ungleichung `r**2 > x**2 + y**2 + z**2` beschrieben. Sie ist für alle Punkte im Raum erfüllt, welche innerhalb des Radius `r` um den Koordinatenursprung liegen. Diese Gleichung wird in die Funktion `f(x,y,z)` gekapselt. Das erlaubt die Übergabe der Ungleichung an `xyzcad`, welches die STL-Datei `sphere.stl` daraus erzeugt. Aufgerufen wird es mit `render.renderAndSave(f, 'sphere.stl', 0.3)`.

Der Wert `0.3` bestimmt die Auflösung. Der Raum wird dadurch in Würfel mit 0,3 mm Kantenlänge eingeteilt. Die Position der Oberfläche, welche den Würfel schneidet kann viel genauer sein. Es ist jedoch nicht möglich eine komplexe Geometrie innerhalb des Würfels unterzubringen. Die Auflösung bestimmt damit eher den Detailgrad als die Maßgenauigkeit. 

Der Decorator `@jit` gibt die Funktion `f(x,y,z)` dem `numba`-Compiler. Nur dadurch läuft die aufwendige Berechnung in annehmbarer Zeit ab. Mit `nopython=True` wird ein eingeschränkter Funktionsfumfang zugunsten einer viel höheren Rechengeschwindigkeit gewählt. Die Einschränkung besteht darin, dass der Compiler alle Datentypen aller Variablen herausfinden kann, bevor der Code ausgeführt wird. Sobald ein Zwischenergebnis den Datentyp einer Variable bzw. eines Elements in einer Liste bestímmt oder bestimmte nicht unterstützte Datentypen verwendet werden, bricht der Compiler mit einer Fehlermeldung ab. 

### Grenzen

Es sind wichtige Einschränkungen zu beachten. Das 3D-Modell muss eine beschränkte Größe haben. Ein unendlich langes Objekt wird ohne Fehlermeldung verarbeitet. Die Rechenzeit und der benötigte Speicherplatz sind in diesem Fall unendlich.

Das Modell muss aus genau einem zusammenhängenden Volumen bestehen. Mehrere nicht miteinander verbundene Elemente können zwar beschrieben werden, es wird jedoch nur eines davon in eine STL-Datei umgewandelt. Welches das ist, ist als zufällig zu betrachten.

Der leere Raum um das Modell herum darf ebenfalls nur exakt ein zusammenhängendes Volumen sein. Ein Hohlraum, welche nicht mit der Umgebung verbunden ist, wird u. U. einfach ausgefüllt. Dieser Hohlraum kann auch die gesamte Umgebung sein. Technisch gesehen, ist es dann ein unendlich großes Objekt ohne äußere Hülle, aber mit einem kleinen Hohlraum. Praktisch ist das Verhalten eines Slicers, welcher die STL-Datei verarbeiten soll, nicht definiert.

STL-Dateien beschreiben nur die Oberflächen von Objekten. Ein geschlossenes Volumen gilt als gefüllt, wenn die Oberfläche konvex ist. Das bedeutet, die Außenseite der Oberfläche ist nach außen gerichtet und die Innenseite zeigt damit in das mit Material gefüllte Volumen hinein. 

Besonders dünne Objekte oder sehr enge Öffnungen können, bei einer grob eingestellten Auflösung, Probleme verursachen. Die Außenseite der einen Objektoberfläche kann vom Algorithmus mit der Innenseite der gegenüberliegenden Objektoberfläche "verwechselt" werden. Es entsteht dann ein beschädigtes STL-Format. Ein Slicer wird versuchen diese STL-Datei zu reparieren und daran scheitern. Das Ergebnis ist moderne Kunst.

### Tipps und Tricks

Um unerwünschte Überraschungen zu vermeiden, können einige Maßnahmen getroffen werden:

Damit nicht versehentlich unendlich große Objekte entstehen, sollten zunächst äußere Schranken definiert werden:

```python
def f(x,y,z):
    if z < 0:
        return False
    if z > 100:
        return False
    if x < -200:
        return False
    if x > 200:
        return False
    if y < -200:
        return False
    if y > 200:
        return False
```

Diese 6 `if`-Bedingungen am Anfang der funktion `f(x,y,z)` beschränken den Bauraum. Ein Objekt, das darüber hinausragt, wird einfach abgeschnitten.

Einzelne Geometrien in Funktionen auszulagern, hilft nicht nur den Überblick zu behalten, sondern auch Elemente wiederzuverwenden und komplexe Modelle mit wenig Code zusammenzubauen:
 
```python
def sphere(x,y,z,r=1):
    return r**2 > x**2 + y**2 + z**2

def f(x,y,z):
   if sphere(x-10,y,z,5):
	return False
   return sphere(x,y,z,10)
```

Das Beispiel zeigt mehrere Entwurfsmuster. Eine parametrisierte Kugel wird durch die Funktion `sphere(x,y,z,r=1)` realisiert. Das Argument `r` bestimmt den Radius. In der Funktion `f(x,y,z)` wird diese Kugel zweimal verwendet. Eine Kugel mit `10` mm Radius befindet sich im Koordinatenursprung. Von ihr wird eine Kugel mit `5` mm Radius ausgeschnitten. Dieser kugelförmige Ausschnitt ist `10` mm entlang der `x`-Achse verschoben.

Die Priorisierung, welches Objekt von welchem weggeschnitten werden soll, wird anhand der Befehlsabfolge festgelegt. Je früher das `return` innerhalb der Funktion ausgeführt wird, um so höher ist die zugehörige Priorität, denn sobald das `return` aufgerufen wurde, wird nachfolgender Code nicht mehr erreicht. Die Kugel wird mit `return False` invertiert. 


