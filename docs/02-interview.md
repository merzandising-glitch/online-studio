# Interview Strang D: Entscheidungen des Herausgebers

Grundlage: offene Fragen aus [01-blindspot-pass.md](01-blindspot-pass.md). Jede Frage einzeln, mit Hypothese.

| Nr. | Frage | Hypothese | Entscheidung | Folgen |
|---|---|---|---|---|
| 1 | Betrieb der Leser-Seiten | wartungsfrei, alle Reihen zusammen ≤ 10 €/Monat | **Beide Wege vergleichen** (21.11.2026): verwalteter Anbieter und eigener kleiner Server, je mit 10-Jahres-Kosten; Entscheidung am STOPP Hosting | Hosting-Vorschlag enthält beide Wege mit Pflegeaufwand, Kosten und Erfüllung der Datenschutzziele (H3) |
| 2 | „IP nie in Logs“: nur eigene Funktionen oder auch Hoster-Protokolle? (Herkunft: Masterplan Abschnitt 6, Zeile Datenschutz; Begründung aus Leser ab 14, keine personenbezogenen Daten, kein Einwilligungsbanner) | beide, nachgewiesen | **Beide, nachgewiesen** (21.11.2026): weder eigene Funktionen noch der Hoster speichern volle IPs; gekürzte IP beim Hoster erlaubt; Nachweis an echten Protokollen | Ausschlusskriterium im Hoster-Vergleich; gekürzte IP im Hoster-Protokoll an die Leitstelle melden (Präzisierung des Masterplan-Ziels) |
| 3 | Versuchslimit Codewort | zwei Grenzen: 10 je Tab, 100 je Netz pro Stunde und Sprungpunkt | **Zwei Grenzen 10/100** (21.11.2026) | Restrisiko bis ca. 2.400 Rateversuche am Tag je Netz und Sprungpunkt, akzeptiert; IPv6 je /64-Block; Präzisierung an die Leitstelle |
| 4 | Jugendschutz-Stufe der Webinhalte von Titel 1 | ab 12 unbedenklich | **Ab 12 unbedenklich** (21.11.2026) | Prüfer bewertet nach 0/6/12/16/18 mit Ziel 12; dunklere Inhalte bleiben im Buch; keine Alterskennzeichnung nötig; Präzisierung von Entscheidung 2 an die Leitstelle. Technik-Test (Freigabe 16) nur auf nicht verlinkter Test-Unteradresse |
| 5 | Impressum der Leser-Seiten | wie Buch-Impressum plus Funktions-E-Mail des Labels | **Wie Buch + Label-Mail** (21.11.2026) | Angaben kommen aus einer lokalen Datei, die nie ins Repository gelangt (wie `daten/verlag.json` im Reihen-Studio); im Technik-Test Platzhalter; Zulässigkeit der Anschrift klärt die anwaltliche Prüfung |
| 6 | Fotos und Stimmen in v1 | Studio schreibt Briefing, Herausgeber erzeugt Medium und legt es in einen Ordner | **Briefing + Ordner** (21.11.2026) | Kein weiterer KI-Dienst und Schlüssel in v1; Medien-Briefing mit Motiv, Text, Länge, Alt-Text, Transkript; Prüfer kontrolliert Kennzeichnung und Lizenz (`quelle`); im Probemodus Platzhalter |
| 7 | Paket und Geheimnisse in Git? | außerhalb von Git, Sperre vor jedem Commit | **Außerhalb von Git** (21.11.2026) | Importiertes Paket, Codewörter, Extra-Texte nur lokal (in `.gitignore`); Prüfung vor jedem Commit; Sicherung über Neu-Export aus dem Reihen-Studio |
| 8 | Echte Testgeräte für die Abnahme | eigenes Handy, das andere System geliehen | **iPhone und Android vorhanden** (21.11.2026) | Abnahme vollständig mit dem Herausgeber: iPhone-Safari, Android-Chrome, je einmal aus Instagram; nur im Testplan vermerkt |

## Weitergabe an die Leitstelle (über den Herausgeber)

1. **Datenschutz-Ziel präzisiert (Frage 2):** „IP nie in Logs“ gilt auch für die Zugriffsprotokolle des Hosters; erlaubt ist dort höchstens eine gekürzte IP.
2. **Versuchslimit präzisiert (Frage 3):** 10 Versuche pro Stunde je Lesesitzung (Tab) und 100 je Netz (IPv4-Adresse bzw. IPv6-/64-Block) und Sprungpunkt.
3. **Altersfreigabe der Webinhalte (Frage 4):** Entscheidung 2 („Altersfreigabe 14“) wird für das Web als Stufe „ab 12 unbedenklich“ umgesetzt, weil der Jugendmedienschutz keine Stufe 14 kennt.
4. **QR-Link-Format (Blindspot W4):** `/<KURZCODE>/<AUFLAGE>` statt `/<KURZCODE>?a=<AUFLAGE>`, wenn der Hoster der Kurz-Domain Anhänge nicht auswerten kann; ganzer Link in Großbuchstaben für kleinere QR-Codes. Entscheidung der Leitstelle.
5. **Kurz-Domain (Blindspot H8, H9):** seriöse Endung, früh registrieren, Domain-Einträge gegen Spam-Missbrauch.
6. **Anwaltliche Prüfung:** zusätzlich Impressum-Anschrift und § 18 Abs. 2 MStV für den Feed.
7. **Prüfung „Spoilergrenze nicht vor Position“ (Plan 3a):** Das Manifest enthält keine Reihenfolge der Szenen. Soll es sie mitliefern, oder bleibt diese Prüfung beim Reihen-Studio? Ebenso prüft nur das Reihen-Studio gegen das Kurzcode-Register.
