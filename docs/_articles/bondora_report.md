---
layout: single
title: "Bondora Report - P2P-Kredit-Portfolio darstellen"
hidden: true
header:
  teaser: /assets/images/report.svg
categories: jekyll update
tags:
  - project
  - oss
---

# Bondora die P2P-Kredit-Investment-Plattform

Bondora ist eine Investitionsplattform für P2P-Kredite. Als _Peer-to-Peer_-Kredite wird die direkte Vergabe von Krediten zwischen zwei Endkunden ohne Bank bezeichnet. Bondora teilt die Investitionssumme des Anlegers auf viele einzelne Kredite anteilig auf, wodurch das Risiko eines Totalverlustes erheblich reduziert wird. Bondora handelt hierbei nicht als klassische Bank, sondern als Vermittler. 

Die automatische Aufteilung des anzulegenden Geldes erfolgt mit Hilfe des _Portfolio-Managers_. Der Kunde kann eine Risikoklasse einstellen, nach welcher der Portfolio-Manager die Kredite auswählt. _Portfolio Pro_ ist noch feingranularer einstellbar als der Portfolio-Manager. Z. B. können bestimmte Risikoklassen oder Laufzeiten ausgeschlossen werden. Über die API kann alternativ auch eine externe Verwaltungssoftware angebunden werden. Sie stellt auch Daten zur Auswertung zur Verfügung, welche durch die im Folgenden beschriebene Software verarbeitet werden.

# Was macht Bondora Report?

Bondora bietet eine API, über die aktuelle Investitionsdaten, aber auch der historische Verlauf der Investments, Buchungen, Zinszahlungen usw. abgerufen werden können. Ein kleines Python-Programm mit matplotlib-SVG-Export generiert schöne Diagramme, welche die Wertentwicklung des Kontos zeigen:

![Diagramm über den Wertverlauf des Portfolios.](/assets/images/report.svg)

Die grüne Kurve zeigt den Wert der aktuellen Kredite. Die rote Kurve zeigt den Kontostand und die blaue Kurve die Zinszahlungen aus den Krediten. Einzahlungen werden durch gelbe Kreise dargestellt. Die grünen Kreise zeigen die Provisionen aus dem Freunde-Werben-Partnerprogramm.

Du möchtest in P2P-Kredite investieren? Dann besuche Bondora über diesen Link: https://bondora.com/ref/BO563KK66 und erstelle einen Account. Über diesen Link erhältst du 5€ Startbonus und ich 5% Provision auf deine Erstinvestition. Diese wird dann auch als grüner Kreis in dem Diagramm auftauchen. Probier es aus ;)

# Warum das Ganze?

Viele Webseiten sind werbefinanziert. Die Werbung ist meist schelcht umgesetzt: herumblinkende Werbebanner irgendwo an der Seite, Popups, die den eigentlichen Inhalt verdecken oder ein Standardtext mit Affiliate-Link. Doch die relevanten Fragen: "Verwendest du das Produkt auch? Funktioniert das denn überhaupt?" werden nicht beantwortet. Diese Anwendung beweist dagegen anhand von Realdaten die Wertentwicklung des Portfolios. 

# Kann ich die Anwendung auch nutzen?

Du kannst den Quellcode hier einsehen: https://github.com/TheTesla/bondora-marketing-app und diese Anwendung zu privaten Zwecken kostenfrei verwenden. Eine gewerbliche Nutzung erfordert meine Genehmigung.

Du betreibst einen Blog über Finanzthemen  und willst die Anwendung oder deren Ausgaben auf deiner Webseite einbinden um Bondora zu bewerben? Setze dich einfach mit mir in Verbingung: <info@entroserv.de> Wir können uns für dich völlig risikolos auf eine Umsatzbeteiligung einigen. Ich helfe dir auch bei der Einrichtung.

Du würdest gerne weitere Funktionen hinzufügen oder die Darstellung anpassen. Das ist sicher kein Problem. Schreib mich einfach an.

Du möchtest unserer Community beitreten, über Neuigkeiten informatiert werden oder mitdiskutieren? Dann abonniere die Mailingliste: https://www.lists.entroserv.de/listinfo/lounge Aktuell finden noch sehr wenige Diskussionen darüber statt.


