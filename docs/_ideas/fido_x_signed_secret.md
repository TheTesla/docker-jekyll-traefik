---
layout: single 
title: "signiertes Secret"
subtitle: "Zero-Knowledge-Proof basierte Signatur des Secrets für Pairwise Public Keys"
excerpt: "Die Kombination der Vorteile von X.509 und FIDO2 erlaubt die Signierung des Identitätsnachweises durch eine CA ohne Pseudonymität einer Pairwise-ID aufzugeben."
hidden: true
#header:
#  teaser: /assets/images/airbedonbed_thumb.webp
#canonical_url: ""
categories:
  - Software
tags:
  - Idee
---

Asymmetrische Kryptoverfahren haben den großen Vorteil __nicht__ auf ein geteiltes Geheimnis zu beruhen. Der private Schlüssel verlässt nie die sich authentifizierende Entität. Der private Schlüssel kann unmittelbar gespeichert oder aus einem Geheimnis abgeleitet werden.

Wichtig ist die Authentizität: Das Gegenüber benötigt einen Nachweis über die eindeutige Zuordnung des öffentlichen Schlüssels zu der korrekten Entität bzw. Person. Das ermöglicht u. a. der Standard X.509. Eine CA signiert den öffentlichen Schlüssel und Angaben zur eindutigen Identifikation der Entität mit ihrem eigenen privaten schlüssel. Der Kommunikationspartner kann die Korrektheit der Signatur prüfen, um festzustellen, ob es sich bspw. um den öffentlichen Schlüssel dieser einen Person mit dem Namen, Adresse und Telefonnumer handelt.

Damit möglichst sparsam mit personenbezogenen Daten umgegangen werden kann, gibt es die Möglichkeit auf die Angabe dieser Attribute zu verzichten und stattdessen eine eindeutige Identifikationsnummer zu verwenden, die dem Vertragspartner erlaubt den Nutzer wiederzuerkennen um ein Nutzerkonto zurodnen zu können. Das Signieren durch die CA ist weiterhin erforderlich, damit niemand die identifikationsnummer fälschen kann.

Der selbe Nutzer kann Nutzerkonten bei mehreren Diensten haben. Nutzt er für alle Dienste die selbe ID, können sich die Dienstebetreiber untereinander absprechen und personenbezogene Daten zusammenführen. Das stellt ein Sicherheitsrisiko dar.

Der Nutzer könnte sich mehrere X.509-Zertifikate mit unterschiedlichen IDs und unterschiedlichen öffentlichen Schlüsseln von der CA ausstellen lassen, ein Zertifikat pro Dienst. Das skaliert nicht, ist umständlich und erfordert die Aufbewahrung vieler privater Schlüssel durch den Nutzer.

Die Alternative nach dem Standard FIDO2 löst dieses Problem, indem aus einem Secret beliebig viele Schlüsselpaare abgeleitet werden können.

