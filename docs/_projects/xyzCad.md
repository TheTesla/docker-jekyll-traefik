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

Es ist eine Kugel mit dem Radius `r = 10` mm.

