---
layout: single 
title: "PTC Hotend"
subtitle: "Nie wieder brennende 3D-Drucker wegen fehlerhafter Heizungsregelung"
excerpt: "Tritt ein Fehler in der Hard- oder Software eines FDM-3D-Druckers auf, kann das Hotend zu heiß werden und einen Brand verursachen."
#header:
#  teaser: /assets/images/
#canonical_url: ""
categories:
  - Hardware
tags:
  - Idee
---

3D-Drucker nach dem FDM-Verfahren (Fused Deposition Modeling) funktionieren wie eine Heißklebepistole. Die Düse, in der das Kunststoff-Filament aufschmilzt hat jedoch eine viel höhere Temperatur als die Düse einer gewöhnlichen Heißklebepistole. Die meisten 3D-Drucker erlauben bis zu 290°C. Einige können sogar hochtemperaturfeste Kunststoffe mit über 500°C drucken.

Die Temperatur ist einstellbar. Sie wird durch die Elektronik geregelt. Der Regelalgorithmus ist in Form von Software auf einem Mikrocontroller realisiert. Dieser misst mithilfe eines Temperatursensors die Temperatur an der Düse und schaltet das Heizelement per PWM zyklisch an und aus.

Das Heizelement muss sehr leistungsstark sein, weil der Schmelzvorgang viel Wärmeenergie benötigt. Eine Heizleistung, die geradso ausreicht, um die Temperatur bei schneller Extrusion aufrechtzuhalten, kann sehr hohe Temperaturen verursachen, wenn das Heizelement dauerhaft mit 100% Leistung heizt, aber kein Filament durchfließt.

## Problem

Ein Ausfall der Regelung kann die Heizung dauerhaft auf 100% Leistung stellen, wodurch so hohe Temperaturen erreicht werden können, dass das Filament, das gedruckte Teil oder Komponenten des 3D-Druckers Feuer fangen. Es gibt viele mögliche Ursachen für eine Störung der Heizungsregelung:

Die Heizpatrone kann sich lockern. Dadurch ist der Wärmeübergang zur Düse zu schlecht. Das Heizelement muss viel heißer werden, damit die korrekte Hotendtemperatur erreicht wird. Der 3D-Drucker funktioniert so grundsätzlich noch, obwohl die Temperaturregelung etwas träger wird. Wird das Heizelement zu heiß, kann es beschädigt werden.

Ist der Temperatursensor locker, misst er eine zu niedrige Temperatur. Dadurch steigt die temperatur des gesamten Hotends zu weit an. Die Regelung scheint noch korrekt zu funktionieren, denn der Temperatursensor erreicht gerade noch die Soll-Temperatur. Das Filament in der Düse kann bereits anfangen zu brennen. Es entstehen brennbare Dämpfe und Rauch. Montageelemente am Hotend können schmelzen.

Ein ähnliches Verhalten wie ein lockerer Temperatursensor zeigt sich, wenn sich die elektrischen Eigenschaften der Temperaturmessung verändern. Das kann eine Beschädigung des Kabels, Steckers oder des Temperatursensors selbst sein. Es kann aber auch eine falsch eingestellte Messelektronik oder eine Kalibrierkurve sein, die nicht zum verwendeten Temperatursensor passt. 

Auch ein Ausfall der Schaltelektronik kann dazu führen, dass die Heizpatrone dauerhaft heizt und dabei überhitzt. Das kann z. B. ein Kontaktproblem auf der Leiterplatte sein. Der Halbleiterschalter schaltet dann einfach nicht mehr aus, wenn er kein Signal bekommt. Das Gleiche passiert, wenn die Software einen Fehler aufweist, der Mikrocontroller nicht korrekt arbeitet oder die Spannungsversorgung der Steuerelektronik fehlerhaft arbeitet. 

## Lösung

Das Brandrisiko kann durch Austausch des Heizelements reduziert werden. Das neue Heizelement muss eine obere Abschalttemperatur aufweisen. Eine Art interne Temperaturregelung soll die Temperatur auf z. B. maximal 350°C begrenzen. 

Grundsätzlich könnte eine Schmelzsicherung in die Heizpatrone eingearbeitet werden. Steigt die Temperatur auf ein unzulässiges Niveau, schmilzt ein Draht und unterbricht den Stromfluss. Leider ist das nicht rücksetzbar. Während der Anheizpahse oder wenn das Filament viel Wärme aufnimmt, könnte diese Sicherung auslösen, weil die Heizpatrone zeitweise viel heißer werden muss.

Besser ist der Einbau eines Bimetall-Thermostaten direkt im Heizelement. Wird die Temperatur zu hoch, wird der Stromkreis zeitweise unterbrochen. Dieser mechanische Schalter ist relativ groß und die Kontakte könnten verkleben.

Besser ist ein PTC-Heizelement. Das steht für positiver Temperaturkoeffizient.  Anstatt aus einer Heizwendel besteht es aus einer Halbleiterschicht, die hochohmig wird, wenn die Schwelltemperatur überschritten wird. Dadurch sinkt der Strom. Das Heizelement wird dadurch nie heißer als diese Abregeltemperatur.

Die Düse wird damit im Fehlerfall nie heißer als diese Grenztemperatur. Allerdings schaltet die Heizung auch nicht ab. Die Temperatur kann immernoch zu hoch sein und Schäden verursachen. Das kann z. B. die Zersetzung des Filaments sein. Es entstehen dadurch evtl. Dämpfe und Ruß. Es bricht jedoch kein Feuer aus.

## Herausforderungen

Bei der Umsetzung des Projektes sind folgende Punkte zu beachten:

Die Abregeltemperatur des Heizelements muss höher sein, als die maximale nutzbare Drucktemperatur, aber nicht viel höher, damit die Brandschutz noch gewährleistet wird. Dabei ist der Wärmewiderstand zu beachten. Die gesamte Düsenkonstruktion muss die Wärme möglichst gut vom Heizelement ableiten, damit es nicht viel heißer werden muss als die Düse, sonst müsste die Abregeltemperatur unsicher hoch gewählt oder die maximal Drucktemperatur abgesenkt werden.

Der Temperaturkoeffizient sollte im Abregelbereich sehr hoch sein. Das Heizelement sollte seine Heizleistung minimal unterhalb der Abregeltemperatur kaum absenken, kurz darüber jedoch sehr stark. Das ist technisch anspruchsvoll umzusetzen. Alternativ könnte ein Heizelement mit deutlich höherer Leistung oder höherer Abregeltemperatur eingesetzt werden. Die höhere Temperatur würde die Sicherheit absenken. Die höhere Leistung würde höhere kurzzeitige Belastungen der Stromversorgung und Elektronik bedeuten. 

## Fazit

PTC-Heizungen können die Sicherheit von 3D-Druckern erhöhen. Man sollte ihn trotzdem nicht tagelang unbeobachtet drucken lassen, weil noch weitere Risiken bestehen, z. B. könnte ein Stecker wegen Kontaktproblemen anfangen zu brennen. Außerdem könnte auch der Druck scheitern und es würden große Mengen an Material verschwendet werden. 

