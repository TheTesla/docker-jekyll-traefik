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

Ein Ausfall der Regelung kann die Heizung dauerhaft auf 100% Leistung stellen, wodurch so hohe Temperaturen erreicht werden können, dass das Filament, das gedruckte Teil oder Komponenten des 3D-Druckers Feuer fangen. Es gibt viele mögliche Ursachen für eine Störung der Heizungsregelung.

