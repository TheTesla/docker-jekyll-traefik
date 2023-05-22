---
layout: single 
title: "smarter Screenshot"
subtitle: "Bildschirmfoto mit Quellennachweis, Metadaten und unveränderten Originaldateien"
excerpt: "Der smarte Screenshot soll neben dem eigentlich Bildinhalt auch die Herkunft erfassen. Abfotografierter Text bleibt auch erhalten."
#header:
#  teaser: /assets/images/airbedonbed_thumb.webp
#canonical_url: ""
categories:
  - Software
tags:
  - Idee
  
---

Es ist einfach bequem, vom Netzfund schnell ein Bildschirmfoto zu erstellen. Leider fehlt diesem Bild der komplette Kontext. Der Rest der Webseite, die URL, der Orginaltext und Mediendaten im Originalformat werden auch nicht mit erfasst.

Ein Webseite kann zwar auch abgespeichert werden, dann fehlt aber die Markierung des interessanten Ausschnitts. Dieser ist nachträglich zu markien, Quellenangaben müssen umständich manuell extrahiert werdeni. Literaturverwaltungssoftware, wie z. B. _Zotero_ erfasst die URL der Webseite automatisch mit und lädt auch die mediendateien mit herunten, soweit dies technisch einfach möglihc ist. Bei dynamisch nachladenden Seite funktioniert es i. d. R. nicht vollständig. Es wird auch nur die Webseite erfasst weiterer Kontext, z. B. Plugin-Einstellungen oder alles außerhalb des Browser, fehlt.

Problematisch sind auch Anwendungsprogramme. Möchte man eine Ansicht innerhalb eines Programms sichern, fehlt dem Bildschirmfoto die Verknüpfung, die es erlaubt, diese Ansicht in diesem Programm wiederherzustellen und an dieser Stelle weiterzuarbeiten. Das ist besonders auf mobilen Geräten wichtig. Dort werden viele Webseiten als deutlich komfortablere App angeboten.

## Beispiel

Die smarte Screenshot-App kann folgendermaßen eingesetzt werden: Auf dem Smartphone ist bspw. die _YouTube_-App geöffnet. Das Video läuft gerade im Miniplayer, während die Suchergebnisse angezeigt werden. Der Nutzer nimmt nun einen Screenshot auf. Neben dem Bildschirminhalt als Bilddatei, werden noch folgende weitere Daten abgespeichert:

| Parameter                              | Wert                                |
| -------------------------------------- | ----------------------------------- |
| __Systemkontext__                      |                                     |
| Betriebssystem                         | Android, Version 13.12              |
| installierte Apps                      | YouTube, Facebook, Twitter, ...     |
| App im Vordergrund                     | YouTube, Version 1.2.34             |
| Apps im Hintergrund                    | Facebook, Twitter, Instagram        |
| laufende Dienste                       | Nextcloud Upload, Search Indexer    |
| Batteriezustand                        | 63%                                 |
| RAM                                    | 80%                                 |
| Flash                                  | 73%                                 |
| WLAN-SSID                              | Telekom Hotspot                     |
| Datentarif                             | Otelo 8 GB                          |
| Datenguthaben                          | 3,2 GB                              |
| __Appkontext__                         |                                     |
| Video geöffnet                         | ja                                  |
| Miniplayer                             | ja                                  |
| Interaktionskontext                    | Suchergbnisse                       |
| geöffnetes Video                       | Video-ID=08151337                   |
| Abspielposition                        | 6:23                                |
| Videodauer                             | 8:37                                |
| Videotitel                             | Einhörner-Flauschen für Einsteiger  |
| Kategorie                              | Lifehacks                           |
| Abspielstatus                          | Play - Video läuft                  |
| Veröffentlichungsdatum                 | 30.02.2020                          |
| Likes                                  | 1337                                |
| Aufrufe                                | 1073456                             |
| Kanal                                  | Einhorn-Tutorials                   |
| Abonnenten                             | 256400                              |
| Suchbegriffe                           | pflege einhorn                      |
| Suchergebnisse                         | Video-IDs=12344, 25511, 23133, ...  |

Diese Tabelle ist nur ein kleiner Auszug möglicher Metadaten. Idealerweise lässt sich der gesamte Zustand aus dem Kontext wiederherstellen. Der Ursprung aller auf dem Bildschirmfoto sichtbaren Elemente ist nachvollsźiehbar, aber auch nicht unmittelbar sichbare Zusammhänge werden mit abgespeichert.

