---
layout: single
title: "ATXMega128a4u USB"
subtitle: "Breakout-Board für Atmel-XMega-USB"
header:
  teaser: /assets/images/XMega128a4u_USB_BO.jpg
categories:
  - Hardware
tags:
  - Projekt
  - Elektronik
sidebar:
  - image: /assets/images/XMega128a4u_USB_BO.jpg
    image_alt: "Foto des Breakout Boards"
    text: "[Auf Amazon bestellen](https://amzn.to/3oBWHUM){: .btn .btn--success}"
    nav: side

gallery:
  - url: /assets/images/XMega128a4u_USB_BO.jpg
    image_path: /assets/images/XMega128a4u_USB_BO.jpg
    alt: "Foto des Breakout Boards schräg von der Seite"
  - url: /assets/images/Xmega128a4u_USB_BO_f.jpg
    image_path: /assets/images/Xmega128a4u_USB_BO_f.jpg
    alt: "Foto des Breakout Boards von oben"
---


{% include gallery caption="Fertig bestückte Platine aus der Serienproduktion" %}

Endlich kann der ATXMega ohne Löten zum Experimentieren verwendet werden. Der Abstand der beiden Pinreihen des Breakout-Boards beträgt 22,86 mm. Damit passt es ideal auf ein Breadboard.

Der Controller ist ein ATXMega128a4u. Er kann als USB-Device verwendet werde. Über die Micro-USB-Buchse wird das Board bspw. mit dem PC verbunden.

Selbstverständlich ist für die USB-Buchse ein ESD-Schutz vorhanden. Eine blaue LED zeigt an, wenn USB mit Strom versorgt wird. So soll verhindert werden, dass das USB-Kabel versehentlich angesteckt bleibt, wenn man an der Schaltung weiterarbeitet.

Über diesen USB-Anschluss kann ohne externem Programmieradapter das Progamm auf den Controller geladen werden. Der Atmel USB-DFU-Loader ist bereits vorinstalliert. Alternativ kann die Firmware auch über den PDI-Anschluss auf dem Board übertragen werden.

Das Board wird extern mit 1,6 - 3,6 V versorgt. Da alle erforderlichen Abblockkondesatoren und Filterspulen sowie ein Quartz (4 MHz) und Kontroll-LEDs für die serielle Schnittstelle vorhanden sind, ist das Board mit geringster Außenbeschaltung nutzbar.

Alle Details sind auf Github verfügbar. Die Inhalte sind urheberrechtlich geschützt.

Das Produkt kann bei Seeedstudio bestellt werden. Schneller und einfacher, d. h. ohne Zoll, Einfuhrumsatzsteuer und Auslandsüberweisung, geht es direkt aus Deutschland bei [Watterott](https://www.watterott.com).



