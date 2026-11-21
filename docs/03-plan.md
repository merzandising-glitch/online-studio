# Gesamtplan Strang D: Online-Studio

Stand 21.11.2026 · Grundlage: Briefing D, Masterplan Abschnitt 6, Manifest-Schema 0.1.0 (Kopie unter `schema/`),
[Blindspot-Pass](01-blindspot-pass.md) und [Interview](02-interview.md).
**Status: STOPP Plan. Gebaut wird erst nach deiner Freigabe.**

## 1. Was am Ende auf deinem PC läuft

Ein zweites lokales Programm neben dem Reihen-Studio, gleich aufgebaut:

- **Start per Doppelklick** (`Studio starten.bat`, `Probe starten.bat`), Oberfläche im Browser unter
  `http://localhost:8766`. Port 8766, damit beide Studios gleichzeitig laufen können (8765 ist das Reihen-Studio).
- **Probemodus** ohne API-Schlüssel und ohne Kosten, mit Platzhaltertexten der Crews.
- **Python** mit denselben Bausteinen wie das Reihen-Studio (Crews mit LangGraph, Oberfläche mit FastAPI, Datenmodelle
  mit Pydantic), damit sich beide gleich bedienen und pflegen lassen.
- **Einstellung `REIHEN_STUDIO_PFAD`** in einer eigenen Einstellungsdatei `einstellungen.json` ohne Geheimnisse (nicht
  in der `.env`, die nur den API-Schlüssel enthält und die ich nie lese). So kann ich Pfadfehler prüfen und benennen.
- **Installation unter Windows** mit einem einzigen Befehl wie beim Reihen-Studio. Dazu kommt einmalig der
  Test-Browser für die Gerätetests (Playwright lädt ihn selbst, ohne Administratorrechte). PDF-Seiten werden mit einem
  Python-Baustein in Bilder umgewandelt, QR-Codes mit einem zweiten gelesen; beide gibt es fertig für Windows.

**Ein Klick vom Paket zur Handy-Vorschau:** Paket importieren → Schemaprüfung und alle Prüfungen aus 04 → Seite des
Sprungpunkts bauen → Prüfer → Vorschau-Adresse und QR-Code auf dem Bildschirm, die du mit dem Handy im selben WLAN
scannst. Die Adresse trägt das Studio in die Rückmeldung ein (Feld `vorschau`). Sie gilt nur im eigenen WLAN und nur, solange
der Vorschau-Server läuft; das steht als Hinweis daneben (und als Wunsch an Strang C für dessen Oberfläche).

**Die Handy-Vorschau ist vom Studio getrennt.** Das Studio selbst ist nur auf deinem PC erreichbar. Ins WLAN geht nur
ein eigener kleiner Vorschau-Server, der ausschließlich die gebauten Leser-Seiten aus `ausgabe/` und die lokale Fassung
der Server-Funktionen ausliefert. Codewörter, Paket und Oberfläche sind dort nicht erreichbar. Er läuft nur, solange du
die Vorschau geöffnet hast. Eine Einschränkung: Der Offline-Speicher funktioniert nur über eine verschlüsselte Adresse
(`https`). Im WLAN wird deshalb nur geprüft, dass die Seite nach dem ersten Laden ohne Netz weiterläuft (Blindspot W6).
Den Offline-Speicher selbst prüfe ich erst auf der Test-Unteradresse.

## 2. Bauabschnitte

Jeder Abschnitt endet mit einer Prüfung durch einen unabhängigen Prüfagenten. Wo „STOPP“ steht, entscheidest du.

| Nr. | Abschnitt | Inhalt | Hängt ab von |
|---|---|---|---|
| **1** | **Hosting-Vorschlag** | Je zwei bis drei Wege: verwalteter EU-Anbieter und eigener kleiner Server (Interview 1), jeweils für Inhalts-Domain, Server-Funktionen und Kurz-Domain; zwei bis drei Wetterdienste; 10-Jahres-Kosten. Ausschlusskriterien: IP nie in Protokollen (gekürzt erlaubt), Groß-/Kleinschreibung in Weiterleitungen, vorübergehende Weiterleitung (302/307), Auswertung des Auflagen-Anhangs (nur sofern die Leitstelle den Anhang beibehält), Kostendeckel oder Festpreis, Firmensitz und Auslieferung in der EU, Auftragsverarbeitungsvertrag, Wetter-Lizenz gewerblich nutzbar. Dazu die Anleitung für dich: beide Domains in der Google Search Console anmelden (Blindspot B5), Domain-Einträge gegen Spam, automatische Verlängerung, Transfersperre, Zwei-Faktor-Anmeldung beim Registrar und Kalender-Erinnerung 60 Tage vor Ablauf. Recherche auf Subagenten verteilt. **STOPP Hosting** | – |
| **2** | **Gerüst** (parallel zu 1) | Programmstart, Probemodus, Einstellungen, Ordnerstruktur, `.gitignore` für Paket und Geheimnisse, Sperre vor jedem Commit (Abschnitt 3) | – |
| **3** | **Austausch** | „Paket importieren“ aus `<REIHEN_STUDIO_PFAD>/daten/reihen/<id>/baende/NN/transmedia/export/`, Schemaprüfung gegen `schema/`, die sieben Prüfungen aus 04 („Was JSON-Schema nicht prüfen kann“, Grenzen siehe Abschnitt 3a), „Rückmeldung schreiben“ nach `daten/<reihe-id>/band-NN/<sprache>/rueckmeldung.json` mit `vorschau`-Adresse | 2 |
| **4** | **Modulbibliothek v1** | Acht Module (Abschnitt 4), je Datenschema, Textalternative, dunkler Grundmodus, Notfallinhalt, Serverteil, mehrsprachig angelegt, Share-Karte nach `teilen`; Lesestand-Code (Abschnitt 5). **Bis zum STOPP Entwürfe nur als Funktion mit schlichter Standarddarstellung; die Gestaltung folgt erst deiner Wahl.** | 3 |
| **5** | **Vier Entwürfe Studio-Oberfläche** und **vier Entwürfe Leser-Seiten** des Technik-Tests, als klickbare Seiten mit Screenshots auf 360 px. **STOPP Entwürfe** | 4 (Leser-Seiten brauchen die Module) |
| **6** | **Oberfläche bauen** nach deiner Wahl | 5 |
| **7** | **Crews** | Modul-Autor, Gestalter, Prüfer, Tester (Abschnitt 6) | 4, 6 |
| **8** | **Server-Funktionen** | Codewort-Prüfung mit Versuchslimit 10/100 (Abschnitt 5a), Extras ausliefern, Wetter holen und zwischenspeichern (Quellenhinweis auf der Seite), Zählung: nur Aufruf, Abschluss und „Zurück zum Buch“ als Tagessummen je Sprungpunkt, ohne Speicher auf dem Gerät und ohne Vorschau-Roboter. IP nur mit stündlich wechselndem Geheimschlüssel gehasht, nur im Arbeitsspeicher, höchstens 1 Stunde, nie in Protokollen. Als kleiner, eigenständiger Dienst mit schmaler Schnittstelle; Geheimnisse kommen bei jedem Aufspielen aus dem Paket. Zuerst als lokale Fassung für die Handy-Vorschau, nach der Hosting-Freigabe in der Form des Hosters; der Umzug auf einen anderen Hoster wird einmal geprobt (Ziel: höchstens ein Tag) | 3, STOPP Hosting |
| **9** | **Kurz-Domain** | Weiterleitungstabelle aus `kurzcode` und `ziel`, nur in den Weiterleitungsregeln des Hosters, nie als Liste für das Handy; vorübergehende Weiterleitung ohne Zwischenseite; Eingabeseite (Bindestrich und Groß-/Kleinschreibung egal, Auflagen-Frage bei mehreren Fassungen); jede Schreibweise auch direkt aus der Adresszeile; Format des QR-Links nach Entscheidung der Leitstelle (Auflage im Pfad oder im Anhang, Interview Weitergabe 4); Teaser-Adressen fürs Teilen | 3, STOPP Hosting |
| **10** | **Archivmodus** | Export einer Reihe als rein statisches Paket mit Ersatz für geschützte Inhalte (nach `archiv_ersatz` des Extras) | 4, 8 |
| **11** | **Technik-Test** | Hochladen auf eine nicht verlinkte, für Suchmaschinen gesperrte Test-Unteradresse, möglichst hinter Zugangsschutz und nur so lange wie nötig; für die eigentlichen Abnahme-Durchgänge (QR-Scan, Instagram, Ladezeit) wird der Zugangsschutz kurz abgeschaltet, weil er sie verfälschen würde (das Paket trägt `band.test: true`, „nie veröffentlichen“); Gerätetests; QR-Scan aus dem Druck-PDF von Strang C; Kontrolle der echten Hoster-Protokolle; Abnahme mit dir auf iPhone und Android (je einmal aus Instagram); Wächter für Zertifikat und Erreichbarkeit; Notfallweg für Missbrauchsmeldungen vorbereitet. **STOPP Abnahme** | alles, Druck-PDF aus C |

Bis zum STOPP Hosting entsteht nur, was an keinen Hoster gebunden ist (Abschnitte 2 bis 7 und die lokalen Fassungen
von 8 und 9). Es werden keine Konten angelegt und nichts hochgeladen.

**Warum der Austausch vor den Modulen kommt:** Das Briefing nennt den Austausch als Schritt 6. Ich ziehe Import und
Prüfungen vor, weil jedes Modul gegen echte Manifest-Daten gebaut und getestet werden soll. Die Rückmeldung entsteht
trotzdem erst, wenn es etwas zu melden gibt.

## 3. Ablage im Repository

| Pfad | Inhalt | In Git? |
|---|---|---|
| `studio/` | Programm | ja |
| `studio/module/<modultyp>/` | je Modul: Datenschema, Vorlage, Notfallinhalt, Textalternative | ja |
| `prompts/<crew>/<rolle>.md` | ein Prompt je Rolle, wie im Reihen-Studio | ja |
| `schema/` | Kopie des Manifest-Schemas 0.1.0 mit `VERSION.md` | ja |
| `daten/<reihe-id>/band-NN/<sprache>/rueckmeldung.json` | Rückmeldung an das Reihen-Studio | ja |
| `daten/<reihe-id>/band-NN/<sprache>/module/` | Modul-Daten ohne Geheimnisse | ja |
| `daten/<reihe-id>/band-NN/<sprache>/tests/` | Testberichte (eine Seite) | ja |
| `lokal/pakete/` | importierte Pakete mit Buchtext, Codewörtern, Extras | **nein** |
| `lokal/impressum.json` | echte Impressum-Angaben | **nein** |
| `lokal/medien/` | Fotos und Audios, die du nach Briefing ablegst | **nein**, bis der Prüfer sie freigibt |
| `ausgabe/` | gebaute Leser-Seiten, Server-Daten, Archivpaket | **nein** (wird jederzeit neu gebaut) |

**Sperre vor jedem Commit:** Sie vergleicht alle Dateien mit den Codewörtern und Extra-Texten aus `lokal/pakete/` und
hält den Commit an, wenn etwas davon auftaucht. Verglichen wird nach ganzen Wörtern, damit kurze Codewörter keine
Fehlalarme auslösen.
- Die Sperre liegt im Repository und wird dort eingeschaltet, damit sie nach einem neuen Herunterladen nicht fehlt.
- Das Studio prüft bei jedem Start, ob sie aktiv ist, und meldet es sonst.
- Fehlt `lokal/pakete/`, warnt sie ausdrücklich, statt still alles durchzulassen.
- Dieselbe Prüfung läuft über `ausgabe/` für die Leser-Seiten (Prüfung 6 aus 04).

## 3a. Die sieben Prüfungen aus 04: was das Online-Studio selbst prüfen kann

| Prüfung aus 04 | Im Online-Studio |
|---|---|
| `id` und `kurzcode` eindeutig im Band, im Register, über alle Reihen und Sprachen | im Band und über alle hier importierten Pakete. Das zentrale Register `daten/kurzcodes.json` liegt im Reihen-Studio, und das darf ich laut 04 nicht lesen. Die Prüfung gegen das Register macht deshalb das Reihen-Studio. |
| `fassung.live` ⊆ `welt.live` | vollständig |
| `auflagen.bis` ≥ `auflagen.ab`, keine Überschneidung | vollständig |
| `spoilergrenze` nicht vor `position.szene_id` | nur teilweise. Das Manifest enthält keine Reihenfolge der Szenen. Ich prüfe, ob beide gleich sind; sind sie verschieden, prüft es das Reihen-Studio, und ich zeige einen Hinweis. → **Bedarf an die Leitstelle:** Soll das Manifest die Reihenfolge mitliefern, oder bleibt diese Prüfung beim Reihen-Studio? |
| IDs in `extras.freischaltung.sprungpunkte` existieren und haben `rolle` = `extra_schluessel` | vollständig |
| kein Feld aus `geschuetzt` und kein Extra-Text in statischen Dateien | vollständig, über `ausgabe/` |
| jede `id` der Rückmeldung im Manifest, jedes `auflagen_ab` passt zu einer Fassung | vollständig |

## 4. Modulbibliothek v1

Für alle Module gilt:
- Text und Bedienung stecken in einer kleinen Datei. Medien laden nach.
- Bedienbar ohne Ton und ohne Wischgesten. Keine Information nur über Farbe.
- Dunkler Grundmodus. Neutrale Titel und Vorschaudaten.
- Inhalte werden als reiner Text eingesetzt, und eine strenge Sicherheitsrichtlinie gilt.
- Alle Texte der Oberfläche liegen in einer Sprachdatei (Titel 1: nur `de`).
- Fiktions- und KI-Kennzeichnung und der Link zu Impressum und Datenschutz sitzen in einem festen Rahmen, der auch auf
  Screenshots sichtbar bleibt.
- `noindex` steht in den Server-Begleitangaben und im Seitenkopf; `robots.txt` sperrt nicht.
- Schriften nur mit freier Lizenz, vom eigenen Server ausgeliefert. Der Feed bleibt erkennbar fiktiv, ohne echte
  Personen oder Ereignisse (bis die anwaltliche Prüfung § 18 MStV geklärt hat).

| Modul | Daten (Kern) | Textalternative | Notfallinhalt (ohne Server) | Auf dem Server |
|---|---|---|---|---|
| `akte` | Deckblatt, Seiten, Absätze, Schwärzungen | die Akte als gegliederter Text | vollständig, weil nichts geheim ist | nichts; Geschwärztes wird beim Bauen entfernt, nicht nur verdeckt |
| `chat` | fiktiver Messenger-Name, Teilnehmer, Nachrichten mit fester Zeit | Verlauf als Dialogtext | vollständig | nichts |
| `feed` | Beiträge der Buch-Stadt, Kopfzeile | Liste der Beiträge | vollständig, Kopfzeile ohne Wetter | nichts (Wetter kommt aus dem Wetter-Zwischenspeicher) |
| `bildbeweis` | Bild, Alt-Text, Suchauftrag, Zoomstufen | Bildbeschreibung mit allen relevanten Details | Bild und Auftrag, Prüfen nicht möglich | Lösung des Suchauftrags |
| `audio` | Audiodatei, Länge, Transkript, Kennzeichnung | vollständiges Transkript mit Geräuschbeschreibung | vollständig | nichts |
| `karte` | eigene Illustration (Vektorgrafik), Markierungen | Liste der Orte mit Beschreibung | Karte ohne Wetter, mit Tageszeit aus der Uhr des Handys | Wetter (geholt und zwischengespeichert) |
| `schloss` | Art (Wort oder Kombination), Hinweis nach 3 Fehlversuchen | Beschreibung des Schlosses und des Hinweises | Schloss mit Hinweis „gerade nicht erreichbar“ | Codewort, Lösung, freigeschalteter Inhalt, Versuchszähler |
| `ermittlerakte` | gefundene Beweise, Fortschritt zum Extra | Liste der Beweise | vollständig aus dem Lesestand | Extra-Text, nur nach bestandener Codewort-Prüfung |

Die Datenschemas der Module legen das Feld `fassung.daten` aus dem Manifest fest. Laut 04 gehört dieses Schema dem
Online-Studio. Live-Daten erscheinen nur im Rahmen, und nur solche, die `welt.live` und `fassung.live` erlauben.

## 5. Lesestand-Code

- Format `XXXX-XXXX-XXXX` mit dem Kurzcode-Alphabet. 12 Zeichen aus 31 ergeben rund 59,4 Bit. Weil 31 keine
  Zweierpotenz ist, wird der Inhalt als eine große Zahl zur Basis 31 geschrieben, nicht zeichenweise.
- Inhalt: 32 Bit „gefunden“-Markierungen, 10 Bit Index und 17 Bit Prüfsumme, zusammen 59 Bit. Die Prüfsumme erkennt
  Tippfehler. Vor Fälschung schützt sie nicht, und das muss sie auch nicht (04).
- **Eine Tabelle, in die nur neue Einträge kommen** und in der sich nie etwas ändert, legt fest:
  - welcher Index zu welcher Reihe, welchem Band und welcher Sprachausgabe gehört, und
  - welche Bit-Nummer (0 bis 31) zu welcher `sp_`-ID gehört, in der Reihenfolge der ersten Aufnahme.

  Sonst würde ein alter Code nach Jahren auf einen anderen Band oder Sprungpunkt zeigen. Die Tabelle liegt in Git; jede
  Leser-Seite bekommt nur den Ausschnitt ihres eigenen Bandes, damit niemand sieht, welche Reihen, Bände und
  Sprungpunkte es sonst gibt.
- Berechnet wird er nur auf dem Handy, ohne Server. Gespeichert wird er im Gerät, weil der Leser ihn will
  (§ 25 TDDDG). Zusätzlich wird er dem Leser zum Abschreiben angezeigt.
- **Restrisiko:** Der Code reicht für 1.024 Bandausgaben (Bände mal Sprachen) über alle Reihen und 32 Sprungpunkte je
  Band; danach braucht es eine zweite Code-Generation, die die Leitstelle als Schemaänderung festlegt.

## 5a. Versuchslimit beim Codewort (Interview 3)

- **Je Lesesitzung 10 Versuche pro Stunde und Sprungpunkt.** Die Seite erzeugt beim Öffnen eine Zufallskennung, die
  nur im Arbeitsspeicher des Tabs liegt und beim Schließen verschwindet. Sie ist kein Cookie und nichts, was auf dem
  Gerät gespeichert wird.
- **Je Netz 100 Versuche pro Stunde und Sprungpunkt**: eine IPv4-Adresse bzw. ein IPv6-Block der Größe /64, nur als
  gehashter Wert mit stündlich wechselndem Schlüssel.
- In der Oberfläche erscheint nach 3 Fehlversuchen ein Hinweis auf das Kapitel.
- **Restrisiko:** Wer gezielt rät und jedes Mal eine neue Kennung erzeugt, schafft bis zu 100 Versuche pro Stunde,
  rund 2.400 am Tag je Netz und Sprungpunkt; das hast du für ein Wort aus dem Buch akzeptiert.

## 6. Crews

| Crew | Aufgabe | Modell (wie im Reihen-Studio) |
|---|---|---|
| **Modul-Autor** | füllt die Modul-Daten aus Briefing, erlaubten Fakten und Wissensstand; schreibt Medien-Briefings (Interview 6) und Kanon-Anträge | Sonnet, Opus für Texte mit hohem Anspruch |
| **Gestalter** | wendet das gewählte Design der Reihe an, prüft die Lesbarkeit auf 360 px | Sonnet |
| **Prüfer** | Kanon und Spoilergrenze, Jugendschutz (Ziel ab 12, Stufen 0/6/12/16/18), Namenskollisionen, Fiktionskennzeichnung, Phishing-Optik (keine echten Marken, Behörden, Banken, Logins), KI-Kennzeichnung und Lizenz je Medium | Sonnet |
| **Tester** | Geräteprofile automatisch (iPhone-Safari-Nachbildung, Android-Chrome, kleine Bildschirme, große Schrift, In-App-Browser), Ladezeit unter 2 s bei 4G-Drosselung, QR-Scan aus dem Druck-PDF, Leck-Prüfung; Testbericht auf einer Seite | kein Modell, reine Programme |

Die Prüfer-Befunde haben dieselben Schweregrade wie im Reihen-Studio. `getestet` gibt es nur mit 0 offenen Befunden und
bestandenem QR-Scan (Schema).

## 7. Testplan und Abnahme

| Ziel (Briefing) | Wie gemessen |
|---|---|
| erster Inhalt < 2 s über 4G | automatisch mit gedrosseltem Netz, Wert in `tests.erster_inhalt_ms` |
| „Aha“ < 30 s | automatisch nur näherungsweise: der Kern des Moduls (z. B. die erste Chatnachricht, das Aktendeckblatt) steht ohne Scrollen im ersten Bildschirm und ist nach höchstens einem Tippen erreicht. Endgültig gemessen wird es mit dir per Stoppuhr, ab dem Scan |
| einhändig auf 360 px, ohne Ton, ohne Wischgesten | Screenshots auf 360 px, Prüfung der Tippflächen (mindestens 44 px) und aller Bedienwege per Tippen |
| offline für die Lesesitzung | Test: Seite laden, Netz abschalten, alles außer Codewort und Wetter funktioniert |
| Codewort: Hinweis nach 3, Limit 10/100 | automatischer Test der lokalen Server-Fassung |
| `noindex`, unratbare Pfade | Prüfung der Server-Begleitangaben und Seitenköpfe; Ziel-Pfade mit mindestens 40 Bit Zufall |
| IP nur gehasht, ≤ 1 h, nie in Logs | Code-Prüfung, nach dem Hochladen Kontrolle der echten Hoster-Protokolle (Interview 2) |
| keine Cookies, keine Drittanbieter | automatisch: keine Cookies und keine Anfrage an fremde Adressen während des Tests |
| Impressum und Datenschutz leicht erreichbar | auf jeder Seite im Rahmen, höchstens zwei Klicks |
| ein Klick bis zur Handy-Vorschau | Abnahme mit dir |

Abnahme Technik-Test laut Briefing: Die Seiten laufen auf der Test-Unteradresse, bestehen Prüfer und Gerätetests,
lassen sich aus dem Druck-PDF scannen, die Rückmeldung besteht alle Prüfungen, und der Prüfagent hat abgenommen.
Danach machst du einen Durchgang auf deinem iPhone und deinem Android-Handy.

## 8. Was ich von dir brauche (der Reihe nach)

1. **Jetzt:** Freigabe dieses Plans (STOPP Plan) und Weitergabe der Punkte aus dem Interview an die Leitstelle.
2. **STOPP Hosting:** Auswahl von Hoster und Wetterdienst. Danach legst du die Konten an, schließt den
   Auftragsverarbeitungsvertrag ab und meldest beide Domains in der Google Search Console an (Anleitung von mir).
   Zugänge bekomme ich nur über die sicheren Wege der Umgebung, nie im Chat.
3. **STOPP Entwürfe:** je ein Entwurf für Studio und Leser-Seiten.
4. **Technik-Test:** echtes Paket und Druck-PDF aus Strang C (über dich), die echten Impressum-Angaben auf deinem PC,
   Abnahme auf deinen Handys.

## 9. Was ich bewusst nicht mache

- keine Konten, kein Hochladen und kein hostergebundener Code vor dem STOPP Hosting
- keine Änderung am Schema und am Repo `reihen-studio`
- keine Videos, Mini-Games, Konten oder Freitext-Community (v1)
- keine echten Impressum-Angaben im Chat oder im Repository

Restrisiko (R3): Die Server-Funktionen entstehen zuerst lokal und werden nach der Hosting-Wahl angepasst. Das kostet
etwas Doppelarbeit, verhindert aber, dass vor deiner Freigabe Code an einen Hoster gebunden wird.
