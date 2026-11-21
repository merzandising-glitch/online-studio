# Interview Strang D: Entscheidungen des Herausgebers

Grundlage: offene Fragen aus [01-blindspot-pass.md](01-blindspot-pass.md). Jede Frage einzeln, mit Hypothese.

| Nr. | Frage | Hypothese | Entscheidung | Folgen |
|---|---|---|---|---|
| 1 | Betrieb der Leser-Seiten | wartungsfrei, alle Reihen zusammen ≤ 10 €/Monat | **Beide Wege vergleichen** (21.11.2026): verwalteter Anbieter und eigener kleiner Server, je mit 10-Jahres-Kosten; Entscheidung am STOPP Hosting | Hosting-Vorschlag enthält beide Wege mit Pflegeaufwand, Kosten und Erfüllung der Datenschutzziele (H3) |
| 2 | „IP nie in Logs“: nur eigene Funktionen oder auch Hoster-Protokolle? (Herkunft: Masterplan Abschnitt 6, Zeile Datenschutz; Begründung aus Leser ab 14, keine personenbezogenen Daten, kein Einwilligungsbanner) | beide, nachgewiesen | **Beide, nachgewiesen** (21.11.2026): weder eigene Funktionen noch der Hoster speichern volle IPs; gekürzte IP beim Hoster erlaubt; Nachweis an echten Protokollen | Ausschlusskriterium im Hoster-Vergleich; gekürzte IP im Hoster-Protokoll an die Leitstelle melden (Präzisierung des Masterplan-Ziels) |
| 3 | Versuchslimit Codewort | zwei Grenzen: 10 je Tab, 100 je Netz pro Stunde und Sprungpunkt | **Zwei Grenzen 10/100** (21.11.2026) | Restrisiko bis ca. 2.400 Rateversuche am Tag je Netz und Sprungpunkt, akzeptiert; IPv6 je /64-Block; Präzisierung an die Leitstelle |
