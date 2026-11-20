# Blindspot-Pass Online-Studio: Web, Hosting und Recht der Leser-Seiten

Stand 20.11.2026 · Strang D · Noch nichts umgesetzt. Grundlage sind die verbindlichen Dokumente im Repo
`reihen-studio`, Branch `claude/transmedia-integration`, Ordner `docs/transmedia/` (01 bis 04 und das Briefing D).

Was dort schon entschieden ist, wiederhole ich hier nicht: Bonus statt Pflicht, Codewort auf dem Server, getrennte
Kurz- und Inhalts-Domain, keine Drittanbieter, Fiktions- und KI-Kennzeichnung, Lesestand-Code, Archivmodus. Hier
stehen nur die Fallen, die beim Bauen und Betreiben der Leser-Seiten zusätzlich zuschnappen. Je Punkt: **Was ist es?**
**Warum würde es dich erwischen?** **Welchen Satz solltest du in den Auftrag schreiben?**

Kein Rechtsrat. Die Punkte unter R gehören zur anwaltlichen Prüfung (Masterplan Abschnitt 9, Punkt 6).

## Kurzfazit

1. **Die Kurz-Domain ist heikler als gedacht.** Sie muss jede Schreibweise verstehen, darf ihre Tabelle nicht
   verraten und darf Browsern keine „ewige“ Weiterleitung beibringen. Sonst sind alle Spoiler-Pfade auf einen Schlag
   lesbar, oder ein späterer Domainwechsel geht ins Leere (W1 bis W3).
2. **Zwei messbare Ziele widersprechen sich mit üblicher Technik.** „IP nur gehasht im Arbeitsspeicher“ passt nicht zu
   den meisten Server-Funktions-Angeboten, und „10 Versuche je Leser“ sperrt ganze Schulklassen aus, weil viele Handys
   dieselbe IP teilen (H3, H4). Das entscheidet mit über die Hoster-Wahl.
3. **„Kostenlos“ heißt bei Wetterdiensten oft „nur privat“.** Bücher verkaufen ist gewerblich (H6).
4. **Drei rechtliche Punkte sind neu:** Das Impressum braucht eine ladungsfähige Anschrift, Jugendschutz im Netz
   kennt keine Stufe „14“, und der Hoster braucht einen Auftragsverarbeitungsvertrag ohne IP-Protokolle (R1 bis R3).
5. **Bilder und Stimmen kann Claude nicht erzeugen.** Für KI-Bilder und KI-Audio braucht es ein weiteres Werkzeug mit
   eigener Lizenz, oder du lieferst die Medien selbst (P1).

---

## W. Leser-Seiten und Kurz-Domain

### W1. Abgetippte Kurzcodes landen in der Adresszeile, nicht auf der Eingabeseite
- **Was:** Im Hörbuch heißt es „Kurzdomain Schrägstrich K7Q3XM“. Die meisten tippen das direkt in die Adresszeile,
  klein geschrieben, mal mit, mal ohne Bindestrich: `kurz.de/k7q-3xm`. Statische Webserver unterscheiden Groß- und
  Kleinschreibung.
- **Warum es dich erwischt:** Wer nicht über das Eingabefeld kommt, sieht „Seite nicht gefunden“. Gerade Hörbuch- und
  E-Book-Leser geben dann auf.
- **Satz für den Auftrag:** „Jede Schreibweise eines Kurzcodes führt direkt aus der Adresszeile zum Ziel: groß, klein,
  mit oder ohne Bindestrich. Unbekannte Codes landen auf der Eingabeseite mit freundlicher Hilfe statt auf einer
  Fehlerseite.“

### W2. Die Weiterleitungstabelle darf nie als Ganzes beim Leser landen
- **Was:** Der bequemste Weg für W1 wäre eine Liste aller Kurzcodes mit Zielen, die das Handy herunterlädt und dort
  nachschlägt.
- **Warum es dich erwischt:** Dann steht jeder unratbare Zielpfad aller Bücher im Quelltext. Wer die Liste einmal
  öffnet, kann jede Seite vor dem Lesen aufrufen. Der Schutz aus „unratbare Pfade“ wäre weg.
- **Satz für den Auftrag:** „Die Weiterleitungstabelle bleibt auf dem Server. Das Handy schickt nur den normalisierten
  Code und bekommt nur dieses eine Ziel zurück.“

### W3. Eine „dauerhafte“ Weiterleitung merkt sich der Browser für immer
- **Was:** Es gibt zwei Arten von Weiterleitung: „dauerhaft“ (301) und „vorübergehend“ (302). Die dauerhafte speichert
  der Browser und fragt die Kurz-Domain nie wieder.
- **Warum es dich erwischt:** Die Kurz-Domain gibt es gerade deshalb, damit die Inhalts-Domain wechseln darf (Marke
  abgemahnt, Hoster gewechselt, Archivmodus). Wer schon einmal gescannt hat, landet dann weiter auf der alten Adresse.
  Ebenso falsch wären Weiterleitungen per Skript oder Zwischenseite: Sie sehen für Phishing-Filter verdächtig aus.
- **Satz für den Auftrag:** „Die Kurz-Domain leitet mit echter, vorübergehender Server-Weiterleitung (302 oder 307)
  weiter, ohne Skript und ohne Zwischenseite.“

### W4. Die Auflage im QR-Link (`?a=1`) können viele statische Hoster nicht auswerten
- **Was:** Laut 04 trägt der QR-Link die Auflage als Anhang mit Fragezeichen (`/K7Q3XM?a=1`). Viele Anbieter für
  statische Seiten leiten nur nach dem Pfad weiter und ignorieren alles nach dem `?`. Außerdem vergrößern `?`, `=` und
  Kleinbuchstaben den QR-Code: Nur Großbuchstaben, Ziffern und wenige Zeichen wie `/` passen in den kompakten
  QR-Modus.
- **Warum es dich erwischt:** Eine „rein statische“ Kurz-Domain kann die Auflage dann nicht unterscheiden, und der Code
  im Buch wird dichter und damit schlechter scannbar (Blindspot D3).
- **Satz für den Auftrag:** „Die Auflage steht im Pfad statt im Anhang (z. B. `/K7Q3XM/1`), wenn der Hoster der
  Kurz-Domain den Anhang nicht auswerten kann. Das entscheidet die Leitstelle.“ → **Bedarf an die Leitstelle** (siehe
  unten), ich erfinde kein Format.

### W5. Link-Vorschauen verraten Spoiler und blähen die Zählung auf
- **Was:** Wird ein Link in WhatsApp, iMessage oder Discord geteilt, ruft die App die Seite selbst ab und zeigt Titel,
  Beschreibung und Bild als Vorschau.
- **Warum es dich erwischt:** Ein Seitentitel wie „Lenas gelöschter Chat“ steht dann in jedem Gruppenchat. Jeder Abruf
  der Vorschau-Roboter zählt als Aufruf, die Messdaten (B7) stimmen nicht mehr. Wer teilt, verbreitet außerdem den
  unratbaren Zielpfad.
- **Satz für den Auftrag:** „Zielseiten tragen neutrale Titel und Vorschaudaten ohne Spoiler. ‚Teilen‘ führt immer auf
  eine eigene Teaser-Adresse mit der Share-Karte, nie auf den Zielpfad. Die Zählung zählt nur echte Leser-Aktionen,
  keine Vorschau-Roboter.“

### W6. Offline klappt nicht in jedem Browser, in dem Leser landen
- **Was:** Der übliche Offline-Baustein (Service Worker) fehlt in vielen In-App-Browsern auf dem iPhone, etwa in
  Instagram oder TikTok. Safari löscht ihn nach 7 Tagen ohne Besuch (Blindspot B3).
- **Warum es dich erwischt:** Das Ziel „offline für die laufende Lesesitzung“ wäre ausgerechnet in den
  YA-Hauptkanälen nicht erfüllt.
- **Satz für den Auftrag:** „Jede Leser-Seite ist nach dem ersten Laden vollständig, auch ohne Netz: alles Nötige in
  einer kleinen Datei, der Offline-Speicher ist nur ein Zusatz. Bis auf Codewort-Prüfung und Live-Wetter funktioniert
  alles ohne Server.“

### W7. „noindex“ wirkt nicht, wenn Suchmaschinen gesperrt werden
- **Was:** Wer Suchmaschinen per `robots.txt` aussperrt, verhindert, dass sie die Anweisung „nicht aufnehmen“
  überhaupt lesen. Dann erscheint die Adresse trotzdem in den Ergebnissen, nur ohne Beschreibung, sobald sie irgendwo
  verlinkt ist.
- **Warum es dich erwischt:** Die erste Reddit-Lösung macht deine Zielpfade über Google auffindbar.
- **Satz für den Auftrag:** „‚noindex‘ steht im Server-Kopf jeder Antwort und im Seitenkopf; `robots.txt` sperrt die
  Leser-Seiten nicht.“

### W8. Inhalte aus dem Manifest sind Fremdtext und dürfen nicht als Programmcode laufen
- **Was:** Die Crews und das Manifest liefern Texte, die in Seiten eingesetzt werden. Steht darin versehentlich
  Seiten-Code, führt der Browser ihn aus.
- **Warum es dich erwischt:** Eine einzige kaputte Seite reicht, damit die Domain als gefährlich gilt (Blindspot B5).
- **Satz für den Auftrag:** „Alle Inhalte werden beim Bauen als reiner Text eingesetzt; jede Seite hat eine strenge
  Sicherheitsrichtlinie, die fremde Skripte und Quellen verbietet.“

---

## H. Hosting und Betrieb über 10 Jahre

### H1. „EU-Hoster“ heißt Firmensitz in der EU, nicht nur Rechenzentrum in der EU
- **Was:** Viele große Anbieter werben mit „Region Frankfurt“, sind aber US-Firmen. Für sie gilt der US CLOUD Act, und
  ihr weltweites Auslieferungsnetz läuft oft über Server außerhalb der EU.
- **Warum es dich erwischt:** Die Datenschutzerklärung muss dann eine Übermittlung in Drittländer erklären, und das
  Versprechen „Hosting in der EU“ (Blindspot C2) stimmt nicht.
- **Satz für den Auftrag:** „Hoster mit Firmensitz und Servern in der EU, auch für das Auslieferungsnetz; Unteranbieter
  stehen im Vertrag.“

### H2. Server-Funktionen sind beim Hoster eingesperrt
- **Was:** Jeder Anbieter hat sein eigenes Format für kleine Server-Funktionen.
- **Warum es dich erwischt:** In 10 Jahren wechselt oder verschwindet ein Anbieter mit hoher Wahrscheinlichkeit. Ist
  der Code an ihn gebunden, ist der Umzug ein Projekt, und das fällt in die Zeit, in der der Titel kaum noch Geld
  bringt.
- **Satz für den Auftrag:** „Die Server-Funktionen sind ein kleiner, eigenständiger Dienst mit einer schmalen
  Schnittstelle; ein Umzug zu einem anderen Hoster dauert höchstens einen Tag und ist einmal geprobt.“

### H3. „IP nur gehasht im Arbeitsspeicher“ passt nicht zu jedem Server-Modell
- **Was:**
  - Eine IP-Adresse einfach zu „hashen“ (in eine Prüfzahl umrechnen) reicht nicht. Es gibt nur etwa 4 Milliarden
    IPv4-Adressen, ein Rechner probiert sie in Minuten durch. Der Hash wäre damit weiter ein personenbezogenes Datum.
  - Viele Server-Funktions-Angebote starten für jede Anfrage eine neue Kopie ohne gemeinsamen Arbeitsspeicher. Ein
    Versuchszähler „im Speicher“ funktioniert dort nicht, er bräuchte eine Datenbank.
  - Fast alle Hoster schreiben Zugriffsprotokolle mit voller IP, oft 7 bis 30 Tage lang, und das lässt sich nicht
    überall abschalten.
- **Warum es dich erwischt:** Das messbare Ziel „nie in Logs“ wäre schon am ersten Tag verletzt, ohne dass du davon
  weißt.
- **Satz für den Auftrag:** „Gehasht wird mit einem geheimen Schlüssel, der stündlich wechselt und nur im Speicher
  liegt. Der Versuchszähler läuft in einem einzigen kleinen Dienst oder in einem Speicher, der Einträge nach einer
  Stunde selbst löscht. Der Hoster bestätigt schriftlich, dass er keine IPs protokolliert oder sie kürzt.“

### H4. Viele Handys teilen sich eine IP
- **Was:** Mobilfunknetze und Schul-WLANs schicken Hunderte Geräte über dieselbe öffentliche IP-Adresse.
- **Warum es dich erwischt:** „10 Versuche pro Stunde je Leser“ heißt technisch meist „je IP“. Eine Schulklasse, die das
  Buch gemeinsam liest, ist nach zehn Fehlversuchen insgesamt für eine Stunde ausgesperrt.
- **Satz für den Auftrag:** „‚Je Leser‘ heißt: je Lesesitzung, nicht je IP. Die Seite schickt dazu eine zufällige
  Sitzungsnummer mit, die nur im Speicher des Tabs liegt; je IP gilt nur eine großzügige Obergrenze gegen Missbrauch.“

### H5. Eine Rechnung ohne Deckel
- **Was:** Server-Funktionen werden oft je Aufruf abgerechnet.
- **Warum es dich erwischt:** Ein Skript, das die Codewort-Prüfung millionenfach aufruft, oder ein viraler BookTok-Clip
  kann aus 2 € im Monat einen dreistelligen Betrag machen.
- **Satz für den Auftrag:** „Fester Monatspreis oder harte Kostenobergrenze beim Hoster; bei Überlast drosseln die
  Server-Funktionen, statt mitzuwachsen. Die statischen Seiten bleiben dabei erreichbar.“

### H6. Kostenlose Wetterdienste sind oft nur privat kostenlos
- **Was:** Bekannte freie Wetter-Schnittstellen erlauben die Gratis-Nutzung nur nicht-kommerziell. Andere verlangen
  einen Quellenhinweis auf der Seite (Lizenz „CC BY“) oder eine Kontaktangabe in jeder Anfrage. Staatliche
  Wetterdienste (z. B. der Deutsche Wetterdienst) haben die langlebigsten offenen Lizenzen, decken aber nicht jede
  Stadt der Welt gleich gut ab.
- **Warum es dich erwischt:** Bücher verkaufen ist gewerblich. Eine Lizenz, die das nicht erlaubt, ist in Jahr 3 eine
  Abmahnung oder eine plötzliche Rechnung. Ein fehlender Quellenhinweis verletzt die Lizenz.
- **Satz für den Auftrag:** „Wetterdienst mit offener Lizenz, die gewerbliche Nutzung erlaubt, bevorzugt ein staatlicher
  Dienst; der Quellenhinweis steht auf der Seite; die Kontaktangabe in der Anfrage ist eine Funktionsadresse des
  Labels, keine persönliche.“

### H7. Domains sterben an abgelaufenen Kreditkarten
- **Was:** Domains werden jährlich verlängert. Scheitert die Zahlung, wird die Domain nach einer Frist frei. Händler
  ersteigern abgelaufene Domains mit Besucherverkehr gezielt.
- **Warum es dich erwischt:** Hinter jedem gedruckten QR-Code stünde dann fremder Inhalt, im schlimmsten Fall Betrug.
  Das wäre der größte denkbare Schaden für die Marke.
- **Satz für den Auftrag:** „Beide Domains mit automatischer Verlängerung, Vorauszahlung für mehrere Jahre,
  Transfersperre, Zwei-Faktor-Anmeldung beim Registrar und einer Erinnerung im Kalender 60 Tage vor Ablauf.“

### H8. Domains ohne E-Mail werden zum Absender von Spam
- **Was:** Eine Domain, die keine E-Mails verschickt, muss das ausdrücklich im Domain-Eintrag sagen (Einträge namens
  SPF, DMARC und „Null-MX“).
- **Warum es dich erwischt:** Sonst fälschen Spammer Absender mit deiner Kurz-Domain. Die Domain landet auf Sperrlisten,
  und Schul- und Jugendschutzfilter blockieren sie.
- **Satz für den Auftrag:** „Beide Domains erklären im Domain-Eintrag, dass sie keine Post versenden, solange es dort
  kein Postfach gibt.“

### H9. Neue Domains und billige Endungen werden von Filtern geblockt
- **Was:** Schul-WLANs, Firmen-Netze und Kinderschutz-Filter sperren oft „neu registrierte Domains“ und Endungen mit
  schlechtem Ruf (etwa `.xyz`, `.top`, `.click`).
- **Warum es dich erwischt:** Ausgerechnet die YA-Leser im Schul-WLAN sehen dann eine Sperrseite.
- **Satz für den Auftrag:** „Kurz-Domain mit seriöser Endung (z. B. `.de`), mindestens drei Monate vor dem ersten Druck
  registriert und mit einer schlichten Startseite versehen.“ → **Hinweis an die Leitstelle** (Domainwahl).

### H10. Automatische Gerätetests sind keine echten Handys
- **Was:** Die Testwerkzeuge ahmen Bildschirmgröße und Browser nach. iPhone-Safari, In-App-Browser und vergrößerte
  Systemschrift verhalten sich auf echten Geräten anders.
- **Warum es dich erwischt:** Der Testbericht ist grün, und auf dem ersten echten iPhone hängt das Codewort-Feld hinter
  der Tastatur.
- **Satz für den Auftrag:** „Neben den automatischen Profilen wird jede Abnahme auf mindestens einem echten iPhone und
  einem echten Android-Handy gemacht, einmal aus Instagram heraus; der Testbericht vermerkt beides.“

---

## R. Recht (kein Rechtsrat)

### R1. Das Impressum braucht eine ladungsfähige Anschrift
- **Was:** § 5 DDG verlangt Name, eine Anschrift, an die man Post zustellen kann (kein Postfach), und eine E-Mail für
  schnellen Kontakt. Die Regel „keine persönlichen Informationen in Webinhalten“ kollidiert damit, wenn kein Unternehmen
  mit eigener Adresse dahinter steht.
- **Warum es dich erwischt:** Ohne gültiges Impressum drohen Abmahnungen. Eine Privatadresse auf jeder Leser-Seite
  eines Jugendbuchs ist für dich ein echtes Risiko.
- **Satz für den Auftrag:** „Impressum und Datenschutz nennen eine Geschäftsanschrift (z. B. Büro- oder Postservice mit
  echter Zustellung) und eine eigene Funktions-E-Mail des Labels, dieselben Angaben wie im Buch-Impressum.“
  → **Frage im Interview.**

### R2. Im Jugendmedienschutz gibt es keine Stufe 14
- **Was:** Für Webseiten gilt der Jugendmedienschutz-Staatsvertrag. Er kennt die Altersstufen 0, 6, 12, 16 und 18.
  Inhalte, die für Jüngere ungeeignet sind, braucht man nur zu kennzeichnen (etwa mit einer maschinenlesbaren
  Altersangabe für Filterprogramme) oder anders zu sichern, wenn sie über „ab 12“ hinausgehen.
- **Warum es dich erwischt:** Die Entscheidung 2 sagt „Webinhalte halten die Altersfreigabe 14 ein“, aber 14 gibt es im
  Netz nicht. Ein Inhalt ist dort entweder „ab 12 unbedenklich“ oder „ab 16“. Der Technik-Test hat Altersfreigabe 16.
- **Satz für den Auftrag:** „Webinhalte von Titel 1 werden so gebaut, dass sie ab 12 unbedenklich sind. Was darüber
  hinausgeht, bleibt im Buch. Der Prüfer bewertet nach den Stufen 0/6/12/16/18.“ → **Frage im Interview.**

### R3. Der Hoster verarbeitet Leserdaten in deinem Auftrag
- **Was:** Auch ohne Konten sieht der Hoster bei jedem Aufruf die IP-Adresse. Dafür braucht es einen Vertrag zur
  Auftragsverarbeitung (Art. 28 DSGVO). Die Datenschutzerklärung muss die Server-Protokolle, die Zählung und den
  Speicher auf dem Handy (Fortschritt, Offline) erklären.
- **Warum es dich erwischt:** Fehlt der Vertrag, ist das ein Bußgeld-Thema, obwohl du gar nichts sammelst.
- **Satz für den Auftrag:** „Mit dem Hoster wird ein Auftragsverarbeitungsvertrag geschlossen; die
  Datenschutzerklärung beschreibt genau die tatsächlich laufenden Vorgänge und wird bei jeder Änderung daran angepasst.“

### R4. Speicher auf dem Handy nur für das, was der Leser will
- **Was:** Fortschritt und Offline-Kopie sind „für den gewünschten Dienst nötig“ und damit ohne Einwilligung erlaubt
  (§ 25 TDDDG). „Wiederkehrender Besucher“, Geräte-Kennungen oder Messwerte im Speicher sind es nicht.
- **Warum es dich erwischt:** Der Masterplan will „Rückkehr“ messen. Mit einer gespeicherten Kennung bräuchte das ein
  Einwilligungsbanner, und das zerstört die Immersion.
- **Satz für den Auftrag:** „Gemessen wird nur, was ohne Speicherung auf dem Gerät geht: Aufruf, Abschluss und der
  Klick auf ‚Zurück zum Buch‘, als Summen je Sprungpunkt und Tag.“

### R5. Lizenzen für alles, was 10 Jahre auf der Seite steht
- **Was:** Schriften, Symbole, Wetterdaten, KI-Bilder und KI-Stimmen haben jeweils eigene Lizenzen. Manche KI-Dienste
  erlauben gewerbliche Nutzung nur im bezahlten Tarif und nur für Inhalte, die während des Abos entstanden sind. KI-Bilder
  sind selbst nicht urheberrechtlich geschützt, andere dürfen sie also wiederverwenden.
- **Warum es dich erwischt:** Eine Schrift ohne Web-Lizenz oder eine KI-Stimme aus dem Gratis-Tarif fällt in Jahr 5
  bei einer Prüfung auf, und dann muss jede betroffene Seite neu gebaut werden.
- **Satz für den Auftrag:** „Nur Schriften mit freier Lizenz (z. B. SIL OFL) und selbst ausgeliefert; für jedes Medium
  stehen Werkzeug, Tarif und Lizenz in der Medienliste der Rückmeldung (Feld `quelle`).“

---

## P. Produktion im Online-Studio

### P1. Claude erzeugt keine Bilder und keine Stimmen
- **Was:** Die Crews laufen wie im Reihen-Studio über Claude. Claude schreibt Texte, Daten und Seitengestaltung, aber
  keine Fotos, Illustrationen oder Sprachaufnahmen. Dafür braucht es einen weiteren Dienst mit eigenem Konto, eigenem
  Schlüssel, eigenen Kosten und eigener Lizenz (R5), oder du erzeugst die Medien selbst.
- **Warum es dich erwischt:** Die Module `bildbeweis`, `audio` und `karte` haben sonst keinen Inhalt, und die
  Kostenschätzung fehlt.
- **Satz für den Auftrag:** „In v1 erzeugt das Studio für Bilder und Audio ein genaues Briefing (Motiv, Länge, Text,
  Alt-Text, Transkript). Die Medien kommen über einen festen Ordner herein; der Prüfer kontrolliert Kennzeichnung und
  Lizenz. Eine direkte Anbindung an einen Bild- oder Stimmdienst ist ein späterer Ausbau.“ → **Frage im Interview.**

### P2. Git als Gedächtnis vergisst nie, auch keine Codewörter
- **Was:** Alles, was einmal in Git steht, bleibt in der Geschichte, auch wenn es später gelöscht wird. Das echte Paket
  enthält privaten Buchtext, Codewörter und den Text des Extras.
- **Warum es dich erwischt:** Ein Repository wird irgendwann geteilt, geforkt oder öffentlich gemacht, und dann liegen
  alle Lösungen aller Bände offen. Außerdem soll laut Briefing privater Text nur über dich kommen.
- **Satz für den Auftrag:** „Das importierte Paket und alle Geheimnisse bleiben außerhalb von Git; versioniert werden
  nur Rückmeldung, Modul-Daten ohne Geheimnisse und Testberichte. Eine Prüfung vor jedem Commit stellt sicher, dass kein
  Codewort und kein Extra-Text im Repository landet.“ → **Frage im Interview.**

### P3. Die Studio-Oberfläche läuft auf Windows
- **Was:** Das Reihen-Studio startet über `.bat`-Dateien unter Windows. Der Tester braucht einen Browser für die
  Gerätetests und ein Programm, das QR-Codes aus dem Druck-PDF liest.
- **Warum es dich erwischt:** Werkzeuge, die nur unter Linux gut laufen, scheitern auf deinem PC, und du bemerkst es
  erst beim ersten echten Lauf.
- **Satz für den Auftrag:** „Das Online-Studio startet unter Windows mit einem Doppelklick wie das Reihen-Studio; alle
  Prüf- und Testwerkzeuge installieren sich über `pip` ohne Zusatzprogramme, und der Probemodus läuft ohne API-Schlüssel.“

---

## Bedarf an die Leitstelle (Schema und Domain, nicht von mir zu entscheiden)

1. **Auflage im QR-Link (W4):** Bleibt `/<KURZCODE>?a=<N>`, oder wird es `/<KURZCODE>/<N>`? Der Pfad funktioniert bei
   jedem statischen Hoster und ergibt kleinere QR-Codes. Betrifft Grundsatz 4 in 04 und den Satz in Strang C.
2. **Altersfreigabe (R2):** Das Feld `reihe.altersfreigabe` erlaubt jede Zahl von 0 bis 18. Für die Webinhalte brauche
   ich die Stufe nach Jugendmedienschutz (0/6/12/16/18). Das leite ich ab, ein neues Feld ist nicht nötig, solange die
   Regel „Web eine Stufe unter dem Buch, mindestens ab 12“ gilt. Die Leitstelle soll das bestätigen.
3. **Kurz-Domain (H8, H9):** seriöse Endung, früh registrieren, Domain-Einträge gegen Spam-Missbrauch.

## Interview: offene Fragen (einzeln, je mit Hypothese)

1. **Betrieb:** wartungsfrei gegen festen kleinen Monatsbetrag, oder günstiger mit jährlicher Pflege? *Hypothese:
   wartungsfrei, alle Reihen zusammen höchstens 10 € im Monat.*
2. **Impressum (R1):** Welche Anschrift und welche E-Mail stehen auf den Leser-Seiten? *Hypothese: eine
   Geschäftsanschrift über einen Büro- oder Postservice und eine Funktions-E-Mail des Labels, wie im Buch-Impressum.*
3. **Bilder und Stimmen (P1):** Woher kommen sie in v1? *Hypothese: Das Studio schreibt die Briefings, du erzeugst die
   Medien mit einem Werkzeug deiner Wahl und legst sie in einen Ordner.*
4. **Jugendschutz (R2):** Webinhalte von Titel 1 „ab 12 unbedenklich“? *Hypothese: ja; was härter ist, bleibt im
   Buch.*
5. **Git und Geheimnisse (P2):** Paket und Codewörter außerhalb von Git? *Hypothese: ja; die Quelle bleibt das
   Reihen-Studio, das Paket lässt sich jederzeit neu importieren.*
6. **Testgeräte (H10):** Welche echten Handys stehen für Abnahmen bereit? *Hypothese: ein eigenes Handy; das zweite
   System über ein geliehenes Gerät oder einen Testleser.*

---

## Verbesserter Auftrag für Strang D (mit Reihenfolge und Stopps)

> Baue das Online-Studio laut Briefing D, Masterplan Abschnitt 6 und Manifest-Schema 04 (Kopie unter `schema/`,
> Version 0.1.0).
>
> **Zusätzliche Regeln aus dem Blindspot-Pass:**
> - Kurz-Domain: jede Schreibweise aus der Adresszeile funktioniert; die Tabelle bleibt auf dem Server; vorübergehende
>   Server-Weiterleitung ohne Skript; Auflage im Pfad, falls die Leitstelle zustimmt.
> - Leser-Seiten: neutrale Titel und Vorschaudaten; Teilen über eigene Teaser-Adressen; nach dem ersten Laden ohne Netz
>   vollständig; „noindex“ im Server-Kopf; alle Inhalte als reiner Text eingesetzt; strenge Sicherheitsrichtlinie.
> - Hosting: Firmensitz und Server in der EU; Server-Funktionen als kleiner, umziehbarer Dienst; IP nur mit stündlich
>   wechselndem Geheimschlüssel gehasht; keine IP in Protokollen, schriftlich bestätigt; Versuchslimit je Lesesitzung;
>   fester Preis oder Kostendeckel; Wetterdienst mit gewerblich nutzbarer offener Lizenz und Quellenhinweis.
> - Domains: automatische Verlängerung, Transfersperre, Zwei-Faktor, Anti-Spam-Einträge, seriöse Endung, früh
>   registriert.
> - Recht: Geschäftsanschrift im Impressum; Webinhalte nach den Stufen 0/6/12/16/18 geprüft; Auftragsverarbeitungsvertrag;
>   Zählung ohne Speicher auf dem Gerät; Lizenz jedes Mediums in der Medienliste.
> - Produktion: Medien in v1 über Briefing und Ordner; Paket und Geheimnisse außerhalb von Git mit Prüfung vor jedem
>   Commit; Start unter Windows per Doppelklick; Abnahme auch auf echten Handys.
>
> **Reihenfolge:**
> 1. Interview zu den sechs offenen Fragen, einzeln mit Hypothese. Bedarf an die Leitstelle über dich weitergeben.
> 2. Architektur- und Hosting-Vorschlag mit 10-Jahres-Kostenschätzung, je zwei bis drei Hoster und Wetterdienste im
>    Vergleich (Recherche auf Subagenten verteilt), vom Prüfagenten geprüft.
>    **STOPP Hosting: Du gibst Hoster und Wetterdienst frei.** Bis dahin baue ich nur lokal und hosterneutral.
> 3. Lokal und hosterneutral, parallel zum Stopp: Programmgerüst mit Probemodus, Schemaprüfung und alle Prüfungen aus
>    04, Paket-Import, Modulbibliothek v1 mit Datenschemas, Lesestand-Code.
> 4. Vier Entwürfe für die Studio-Oberfläche und vier für die Leser-Seiten des Technik-Tests.
>    **STOPP Entwürfe: Du wählst je einen.**
> 5. Crews (Modul-Autor, Gestalter, Prüfer, Tester), Rückmeldung mit Handy-Vorschau, Archivmodus.
> 6. Nach der Hosting-Freigabe: Deployment auf eine Test-Subdomain, Gerätetests, QR-Scan aus dem Druck-PDF, Abnahme mit
>    dir auf echten Handys.
>    **STOPP Abnahme Technik-Test:** Prüfagent und du nehmen ab, dann übernimmt die Leitstelle.
