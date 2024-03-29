---
layout: single
title: "LT3060 LDO BO"
subtitle: "Breakout-Board mit dem robusten und rauscharmen Low-Drop-Spannungsregler LT3060"
excerpt: "Das Spannungsregler-Modul in der Form eines TO220-Gehäuse enthält bereits die erforderliche Außenbeschaltung und einen Überspannungsschutz."
header:
  teaser: /assets/images/LT3060bo.webp
categories:
  - Hardware
tags:
  - Projekt
  - Elektronik
sidebar:
  - title: "LT3060 BO"
    image: /assets/images/LT3060bo.webp
    image_alt: "Foto des Breakout Boards"
---

Die Platine hat die Größe eines Standard-Festspannungsreglers im TO220-Gehäuse. Mit der 3-poligen Stiftleiste ist der elektrische Kontakt und der mechanische Halt bei Verwendungen auf dem Steckbrett deutlich besser und zuverlässiger als er bei Standardspannungsreglern mit normalen Anschlussdrähten ist.

Zum Einsatz kommt der Low-Drop-Regler LT3060 von linear Technologies mit einer Dropout-Spannung von max. 510 mV. Er zeichnet sich durch geringes Rauschen und niedrigem Ruhestrom aus.

Im Gegensatz zu den meisten anderen Reglern ist der LT3060 sehr robust. Beliebige Falschpolung mit Spannungen bis 50 V können das IC nicht zerstören. Der Leckstrom bei Falschpolung ist sehr gering. Die Platine besitzt zusätzlich Überspannungsschutzdioden an allen 3 Pins. Sie werden bei ca. 45 V leitend und verhindern so kurzzeitige Überschreitung der 50-V-Grenze. Die Dioden sind so angeordnet, dass auch bei Falschpolung kein Strom fließt, solange die Spannung unter 45 V bleibt.

Die zum Betrieb erforderlichen Bauelemente, d.h. u. a. Kondensatoren am Ein- und Ausgang sind bereits auf der Platine vorhanden. Sie sind ebenfalls für Spannungen bis 50 V dimensioniert.

Beziehbar über [Watterott](https://www.watterott.com).

## Technische Daten

* Ausgangsspannungen: 1,2 V; 1,5 V; 1,8 V; 2,5 V; 3,3 V; 5,0 V (fest)
* Ausgangsstrom (max.): 100 mA
* Eingangsspannungsbereich: Uo+0,51 - 40 V
* Ruhestrom: 40 uA

![LT3060boBack](/assets/images/LT3060bo.webp)

