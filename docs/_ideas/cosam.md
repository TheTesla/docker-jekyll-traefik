---
layout: single 
title: "CoSAM"
subtitle: "Constraint oriented System Administration and Management"
excerpt: "Die constraint-orientierte Systemverwaltung konfiguriert Komponenten auf Basis einer deklarativen Anforderungs- oder Problembeschreibung."
#hidden: true
#header:
#  teaser: /assets/images/airbedonbed_thumb.webp
#canonical_url: ""
categories:
  - Software
tags:
  - Idee
---


## aktuelle Situation

Die umständiche und fehleranfällige manuelle Administration von IT-Infrastruktur spielt nur noch eine untergeordnete Rolle. Auf Desktop-Systemen ist sie noch weit verbreitet.

Häufig werden imparative Administrationslösungen eingesetzt. Das können Shellskripte oder Orchestrierungspprogramme, wie bspw. _Ansible_ sein. Doch auch diese Lösungen haben Schwächen. Die Reihenfolge der Konfigurationsanweisungen und damit auch der Ausgangszustand haben einen direkten Einfluss auf das Ergebnis.

Wird ein Skript mehrfach ausgeführt, können Komplikationen auftreten. Bei erneuter Auführung bestehen bereits Dateien und Einträge aus der ersten Ausführung. Soll eine Einstellung geändert werden, ist es daher nicht zu empfehlen das Skript mit den neuen Angaben erneut auszuführen. Das System sollte am besten vorher auf den Ausgangszustand zurückgesetzt werden. 

Das Anwenden mehrere Konfigurationsskripte auf die selbe Resource führt schnell zu Problemen. Das zweite Skript kann dabei eine Einstellung, die vom ersten Skript vorgenommen wurde, verändern. Selbst, wenn es scheinbar funktioniert, hat die Reihenfolge der Anwendung der Skripte u. U. einen Einfluss auf das Endergebnis. Dabei kann es vorkommen, dass das Konfigurationsergebnis in bestimmten Fällen gar nicht mehr funktioniert oder sich eine Sicherheitslücke auftut. 

Besser sind deklarative Konzepte, wie bspw. bei _NixOS_. Dabei wird ein Endzustand beschrieben. Der Weg bzw. die Reihenfolge der Schritte vom gegenwertige Zustand zum Zielzustand ist dabei nicht relevant und wird von der Konfigurationssoftware automatisch bestimmt. Soll die neue Konfiguration angewendet werden, prüft die Konfigurationsverwaltung zunächst die Konfliktfreiheit und vollständigkeit der gesamten Konfiguration. Anschließend wird das System auf Werkseinstellung zurückgesetzt und von da aus neu konfiguriert. 


## Herausforderungen

Die deklarative Konfiguration hat da Grenzen, wo ein Konflikt aus mehreren konkreten Konfigurationsbeschreibungen auftritt. Bspw. kann es zu einem Portkonflikt kommen, wenn zwei Webserver auf dem selben System verwendet werden sollen. Die beiden Konfigurationsbeschreibungen können daher nicht unmittelbar auf das selbe System angewendet werden.

Sie müssen angepasst werden, damit nur ein Webserver für beide Aufgaben genutzt wird oder sie ihre Dienste auf unterschiedlichen Ports bereitstellen, welche über einen Reverse-Proxy zusammengeführt werden. Für diesen Beispielfall wird in der Praxis häufig der Weg gewählt, grundsätzlich einen Reverse-Proxy einzurichten und jeden Dienst jeweils in einen separaten Container unterzubringen. 

Diese Lösung ist nicht sehr effizient. Daten müssen durch mehrere Netzwerkstacks übertragen werden. Des Weiteren gibt es Fälle, die nicht auf diese Weise lösbar sind. Das macht sich spätestens dann bemerkbar, sobald Container in Container gesteckt werden sollen. Auch ein bestehender Nutzdatensatz, der mit dem Folgesetup nicht mehr kompatibel ist, erfordert zusätzliche Maßnahmen.

Ein weiterer Fall, bei dem eine rein deklarative Konfigurationsbeschreibung nur wenige Vorteile bringt, ist die Anpassung einer Konfiguration an gegebene Umstände. Das können verbunde Dienste oder Netzwerktopologien sein. Sobald bei der Konfigurtion eines System viele, sich häufig ändernde Rahmenbedingungen berücksüchtigt werden müssen, werden die vielen Fallunterscheidungen zu unübersichtlich.


## Constraint-orientierter Ansatz

Es gibt eine Möglichkeit diese Herausforderungen elegant zu meisten. Dabei wird die Gesamtheit aller Systeme, Anforderungen und Rahmenbedingungen als Gleichungssystem betrachtet. Diese werden in einer formalen Sprache erfasst. Anschließend berechnet ein Gleichungslöser die notwendigen Anpassungen. Diese werden auf die konfigurierbaren Systeme angewendet. Fertig!

Um _CoSAM_ zu realisieren, müssen Verhaltensmodelle von nutzbaren Systemkomponenten abgeleitet werden. Die gewünschte Konfiguration wird im Vergleich zur deklarativen Beschreibung nicht mehr in Form einer Struktur oder Attributen beschrieben, sondern als Systemverhalten. 

Für ein Webserver-Setup ist im Gegensatz zum rein deklarativen Ansatz nicht die Nennung der zu verwendenden Server-Software erforderlich. Auch möglicherweise erforderliche Reverse-Proxies oder Konfigurationsparameter werden durch den Administrator nicht explizit angegeben.

Die Constraint-orientierte Beschreibung ermöglich völlig neue Wege der Zieldefinition. Das Setup bspw. eines Webservers wird nicht beschrieben, sondern die erwartete Ausgabe unter bestimmten Bedingungen. Es gibt dazu bspw. die Möglichkeit, ein HTML-Dokument mit Platzhaltern zu erstellen und den mit ``sed``, ``grep`` oder ``awk`` gefilterten Inhalt dieser Datei mit der Ausgabe einer ``curl``-Abfrage mit ``==`` gleichzusetzen. _CoSAM_ erstellt aus dieser eher abstrakten Beschreibung eine konkrete Systemkonfiguration.

Für die Interaktion mit der Infrastruktur kann _CoSAM_ auf bestehende Lösungen, wie z. B. _Ansible_ zurückgreifen und so die anzuwendenden Arbeitsschritte in Form von entsprechenden Skripten ausgeben. 

Diese Contraint-orientierte Lösung ermöglicht die kompakte Beschreibung komplexer Sachverhalte. Dabei kann der Aufbau der bestehenden und unabänderlichen Infrastruktur automatisiert ermittelt werden und als zusätzliche Einschränkungen in die Systembeschreibung aufgenommen werden. Die abstrakte Zielbeschreibung muss dabei nicht abgeändert werden. 

Bspw. kann eine Mailserver-Konfiguration automatisch aus u. a. dem Datenbankschema erstellt werden. Soll jedoch das neue Schema verwendet werden, kann das Migrationsskript automatisch ermittelt werden. Die vorhandenen Datenbankeinträge aus dem alten Setup werden automatisch auf das neue Schema migriert.


## Zukunft

Die Hauptschwierigkeit bei der Realisierung des _CoSAM_-Projektes ist die aufwendige Erstellung der Modelle für jede einzelne Systemkomponente. Mit jeder neuen Funktion der jeweiligen Server-Software, muss auch das Modell erweitert werden. Die Modell werden daher auf die wesentliche Funktionalität beschränkt bleiben.

Die Programme, von denen Verhaltensmodelle abgeleitet werden sollen, sind eigentlich schon Verhaltensmodelle, allerdings sehr komplexe, für den gewünschten Zweck ungeeignet Modelle. Grundsätzlich sollte es daher möglich sein aus den vorhandenen Programmen geeignete Verhaltenmodelle abzuleiten.

Dies könnte durch automatisches Zerteilen der jweiligen Software in einzelne Funktionsblöcke und anschließender symbolischen Ausführung erreicht werden. Die erkannten Strukturen werden mit geeigneten Ersatzstrukturen ersetzt. So kann z. B. der Netzwerkstack innerhalb eines Programms automatisch identifiziert und gegen eine abstrakte Schnittstellenbeschreibung getauscht werden. 


## Schwierigkeiten

Das klingt alles sehr spektakulär. Doch so einfach die Anwendung der Constraint-orientierten Beschreibung nicht. Die Beschreibung sollte vollständig sein. Alles, was nicht explizit verboten ist, ist nämlich erlaubt. Wer wichtige Einschränkungen vergisst anzugeben, kann ein System erhalten, welches mehr kann, als geplant. Das schließt Sicherheitslücken mit ein!

Damit das nicht passiert, muss eine Grundspezifikation vorhanden sein, welche die Funktionalität auf das absolute Minimum reduziert, wenn das jeweilige Verhalten nicht explizit gefordert ist. Allerdings kann auch die abstrakte Beschreibung sehr unintuitiv sein, was schnell zu unerwartetem Verhalten führt.


## Fazit

Trotz unintuitiver Arbeitsweise und wenig transparenter Komplexität, kann ein Constraint-orientiertes Vorgehen in bestimmten Fällen das Leben erleichtern.

Es muss nicht zwingend alles Constraint-orientiert umgesetzt werden. Eine klassische deklarative Konfiguration kann um Constraint-orientierte Elemente erweitert werden. Die klassisch beschriebenen Teile fließen als Einschränkung in die Contraint-orientierte Beschriebung ein. Unter diesem Aspekt ist es doch ratsam dem Contraint-orientierten Ansatz eine Chance zu geben.



