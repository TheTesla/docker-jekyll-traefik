---
layout: single
title: "ATXmega128a4u USB Beschreibung"
subtitle: "Breakout-Board für Atmel-XMega-USB"
#hidden: true
header:
  teaser: /assets/images/XMega128a4u_USB_BO.jpg
categories:
  - Hardware
tags:
  - Projekt
  - Elektronik
sidebar:
  - title: "ATXmega128a4u USB"
    image: /assets/images/XMega128a4u_USB_BO.jpg
    image_alt: "Foto des Breakout Boards"
    text: "[Auf Amazon bestellen](https://amzn.to/3oBWHUM){: .btn .btn--success}"
gallery:
  - url: /assets/images/XMega128a4u_USB_BO.jpg
    image_path: /assets/images/XMega128a4u_USB_BO.jpg
    alt: "Foto des Breakout Boards schräg von der Seite"
  - url: /assets/images/Xmega128a4u_USB_BO_f.jpg
    image_path: /assets/images/Xmega128a4u_USB_BO_f.jpg
    alt: "Foto des Breakout Boards von oben"
---

[[Datei:Xmega128a4uBOf.png |thumb|upright=1.5|Vorderseite der Platine, OSH-Park-Vorschau]]

[[Datei:Xmega128a4uBOb.png |thumb|upright=1.5|Rückseite der Platine, OSH-Park-Vorschau]]


Bisher gab es nur sehr selten Breakout-Boards für die ATXMegas von Atmel zu kaufen, meist in ungeeigneter Bauform und ohne ESD-Schutz. Deshalb wurde ein neues Board entworfen. Der Abstand zwischen den beiden Pinreihen beträgt 0,9 Zoll (22,86 mm), wodurch das Board direkt auf das [http://www.pollin.de/shop/dt/MTI4OTg0OTk-/Werkstatt/Werkstattbedarf/Sonstiges/Labor_Steckboard.html Labor-Steckboard] passt.

Es ist eine micro-USB-Buchse direkt am Board angebracht. Diese Schnittstelle ist mit einem ESD-Schutz (BAS70 + 6,2 V Z-Diode) ausgestattet. Die Datenleitung sind mit dem USB-fähigen Xmega verbunden. USB und Board haben eine gemeinsame Masse. Der VUSB ist separat herausgeführt. Es ist kein Spannungsregler eingebaut. Da VUSB, GND und V+ direkt nebeneinander herausgeführt werden, kann ein geeigneter Spannungsregler bzw. Schaltregler ohne großen Aufwand direkt an die Stiftleiste angeschlossen werden.

Das Board ist nicht nur ein Adapter um das SMD-Bauteil auf ein Experimentierboard zu stecken. Es sind auch bereits Abblockkondensatoren (10 µF) und eine Filterspule (100 nH) für die Betriebsspannung nahe am Xmega angebracht. Auch die Spannungsversorgung für die Analogkomponenten ist separat (10 µF, 100 nH) gefiltert. 

Es befinden sich Abblock-Kondensatoren (10 µF) an PORTA.0 und PORTB.0, da diese Pins als Referenzspannungseingang verwendet werden können.

Der PDI-Anschluss auf der Oberseite des Boards besitzt bereits einen 10 kΩ pullup-Widerstand am Reset.

'''Testplan für die Massenfertigung (englisch):''' [[Xmega128a4u BO Testplan]]

'''github:''' [https://github.com/TheTesla/ATXMega32a4u-USB-Breakout/tree/Xmega128a4u Xmega128a4u]

Fragen? [mailto:support@entroserv.de support@entroserv.de]

== Linux ==
Programmierung mit avr-gcc:

avr-gcc -mmcu=atxmega128a4u ...

Klappt auch mit -mmcu=atxmega128a3. (Meistens wird der atxmega nicht explizit unterstützt.)

Hochladen mit

avrdude -p xmega128a4u ...

Auch hier ist der xmega128a4u oft nicht explizit unterstützt, da tut's ebenfalls der xmega128a[\d][a-z].

Happy Hacking.

