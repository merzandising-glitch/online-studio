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
   verraten und sollte Browsern keine dauerhafte Weiterleitung beibringen. Sonst sind alle Spoiler-Pfade auf einen
   Schlag lesbar, oder ein späterer Domainwechsel geht ins Leere (W1 bis W3). Ihr Zertifikat und ihre Erreichbarkeit
   brauchen einen Wächter (H10).
2. **Zwei messbare Ziele sind mit üblicher Technik schwer zu erfüllen.** „IP nie in Logs“ schließen viele Hoster aus,
   und „10 Versuche je Leser“ sperrt ganze Schulklassen aus, weil viele Handys dieselbe IP teilen (H3, H4). Das
   entscheidet mit über die Hoster-Wahl, und du entscheidest es im Interview.
3. **„Kostenlos“ heißt bei Wetterdiensten oft „nur privat“.** Bücher verkaufen ist gewerblich (H6).
4. **Vier rechtliche Punkte sind neu:** Das Impressum braucht eine ladungsfähige Anschrift, Jugendschutz im Netz
   kennt keine Stufe „14“, der Hoster braucht einen Auftragsverarbeitungsvertrag, und der Feed könnte als journalistisch
   gelten (R1 bis R3, R6).
5. **Fotos und Stimmen kann Claude nicht erzeugen.** Dafür braucht es ein weiteres Werkzeug mit eigener Lizenz, oder
   du lieferst die Medien selbst (P1).

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
  Fehlerseite. Ob der Hoster der Kurz-Domain Groß- und Kleinschreibung in seinen Weiterleitungsregeln gleich behandelt,
  ist ein Auswahlkriterium für den Hoster.“

### W2. Die Weiterleitungstabelle darf nie als Ganzes beim Leser landen
- **Was:** Der bequemste Weg für W1 wäre eine Liste aller Kurzcodes mit Zielen, die das Handy herunterlädt und dort
  nachschlägt.
- **Warum es dich erwischt:** Dann steht jeder unratbare Zielpfad aller Bücher im Quelltext. Wer die Liste einmal
  öffnet, kann jede Seite vor dem Lesen aufrufen. Der Schutz aus „unratbare Pfade“ wäre weg.
- **Satz für den Auftrag:** „Die Weiterleitungstabelle steht nur in den Weiterleitungsregeln des Hosters, die niemand
  von außen lesen kann. Die Eingabeseite bringt einen abgetippten Code nur in die Normalform (`K7Q3XM`) und ruft dann
  diese Adresse auf. So bleibt die Kurz-Domain rein statisch.“

### W3. Eine „dauerhafte“ Weiterleitung merkt sich der Browser meist dauerhaft
- **Was:** Es gibt zwei Arten von Weiterleitung: „dauerhaft“ (Fachwort 301) und „vorübergehend“ (302 oder 307). Die
  dauerhafte speichert der Browser meist und fragt die Kurz-Domain dann nicht mehr.
- **Warum es dich erwischt:** Die Kurz-Domain gibt es gerade deshalb, damit die Inhalts-Domain wechseln darf (Marke
  abgemahnt, Hoster gewechselt, Archivmodus). Wer schon einmal gescannt hat, landet dann weiter auf der alten Adresse.
- **Satz für den Auftrag:** „Die Kurz-Domain leitet mit echter, vorübergehender Server-Weiterleitung (302 oder 307)
  weiter, ohne Zwischenseite.“

### W4. Die Auflage im QR-Link (`?a=1`) können viele statische Hoster nicht auswerten
- **Was:** Laut 04 trägt der QR-Link die Auflage als Anhang mit Fragezeichen (`/K7Q3XM?a=1`). Viele Anbieter für
  statische Seiten leiten nur nach dem Pfad weiter und ignorieren alles nach dem `?`. Dazu kommt der QR-Code selbst: Er
  hat einen kompakten Modus für Großbuchstaben, Ziffern und wenige Zeichen wie `/` und `:`. Der hilft aber nur, wenn
  der ganze Link großgeschrieben ist (`HTTPS://KURZ.DE/K7Q3XM/1`). Das `?a=1` allein macht den Code nur wenig größer.
- **Warum es dich erwischt:** Eine „rein statische“ Kurz-Domain kann die Auflage dann nicht unterscheiden. Ein klein
  geschriebener Link verschenkt außerdem Platz, und ein dichterer Code scannt schlechter (Blindspot D3).
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
- **Satz für den Auftrag:** „Text und Bedienung jeder Leser-Seite stecken in einer kleinen Datei, die nach dem ersten
  Laden auch ohne Netz vollständig funktioniert. Bilder und Audio laden danach nach. Der Offline-Speicher ist nur ein
  Zusatz. Bis auf Codewort-Prüfung und Live-Wetter läuft alles ohne Server.“

### W7. „noindex“ wirkt nicht, wenn Suchmaschinen gesperrt werden
- **Was:** Die Datei `robots.txt` sagt Suchmaschinen, welche Seiten sie gar nicht erst abrufen sollen. Die Anweisung
  „nicht aufnehmen“ (`noindex`) steht dagegen in der Seite selbst. Wer Suchmaschinen per `robots.txt` aussperrt,
  verhindert also, dass sie das „nicht aufnehmen“ überhaupt lesen. Dann erscheint die Adresse trotzdem in den
  Ergebnissen, nur ohne Beschreibung, sobald sie irgendwo verlinkt ist.
- **Warum es dich erwischt:** Die erste Reddit-Lösung macht deine Zielpfade über Google auffindbar.
- **Satz für den Auftrag:** „‚noindex‘ steht doppelt: in den unsichtbaren Begleitangaben, die der Server mit jeder
  Antwort schickt, und im Kopf jeder Seite; `robots.txt` sperrt die Leser-Seiten nicht.“

### W8. Inhalte aus dem Manifest sind Fremdtext und dürfen nicht als Programmcode laufen
- **Was:** Die Crews und das Manifest liefern Texte, die in Seiten eingesetzt werden. Steht darin versehentlich
  Seiten-Code, führt der Browser ihn aus.
- **Warum es dich erwischt:** Eine einzige kaputte Seite reicht, damit die Domain als gefährlich gilt (Blindspot B5).
- **Satz für den Auftrag:** „Alle Inhalte werden beim Bauen als reiner Text eingesetzt; jede Seite hat eine strenge
  Sicherheitsrichtlinie, die fremde Skripte und Quellen verbietet.“

---

## H. Hosting und Betrieb über 10 Jahre

### H1. „EU-Hoster“ heißt Firmensitz in der EU, nicht nur Rechenzentrum in der EU
- **Was:** Viele große Anbieter werben mit „Region Frankfurt“, sind aber US-Firmen. Für sie gilt ein US-Gesetz (CLOUD
  Act), nach dem US-Behörden Daten auch aus europäischen Rechenzentren verlangen können. Ihr Auslieferungsnetz (viele
  Server weltweit, die Kopien der Seiten nah beim Leser bereithalten) läuft außerdem oft über Länder außerhalb der EU.
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
  Schnittstelle; ein Umzug zu einem anderen Hoster dauert höchstens einen Tag und ist einmal geprobt. Codewörter und
  Extras kommen nach einem Umzug aus dem neu importierten Paket wieder auf den Server, nicht aus einer Sicherung beim
  alten Hoster.“

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
  Stunde selbst löscht. Es kommen nur Hoster in Frage, bei denen die Server-Protokolle nachweislich keine IP enthalten
  (abschaltbar oder gekürzt); eine bloße Zusage reicht nicht, ich prüfe es an echten Protokollen.“
  → **Frage im Interview** und **Bedarf an die Leitstelle**, falls kein passender Hoster das Ziel wörtlich erfüllt.

### H4. Viele Handys teilen sich eine IP, und andere wechseln sie ständig
- **Was:**
  - Mobilfunknetze und Schul-WLANs schicken Hunderte Geräte über dieselbe öffentliche IP-Adresse.
  - Bei der neueren Adressform IPv6 bekommt dagegen ein einzelnes Handy einen ganzen Block an Adressen und kann sie
    beliebig wechseln.
- **Warum es dich erwischt:** „10 Versuche pro Stunde je Leser“ heißt technisch meist „je IP“. Eine Schulklasse, die das
  Buch gemeinsam liest, ist nach zehn Fehlversuchen insgesamt für eine Stunde ausgesperrt. Wer dagegen mit IPv6 raten
  will, umgeht die Grenze durch Adresswechsel.
- **Möglicher Weg (Hypothese, Sicherheitsfrage, deshalb nicht von mir allein entschieden):** zwei Grenzen zugleich.
  Je Lesesitzung (eine Zufallsnummer, die nur im geöffneten Tab lebt) 10 Versuche pro Stunde; je Netz (IPv4-Adresse
  bzw. IPv6-Block) 100 Versuche pro Stunde und Sprungpunkt. **Restrisiko:** Wer bewusst für jede Anfrage eine neue
  Sitzungsnummer erzeugt, kommt auf 100 Versuche pro Stunde, also rund 2.400 am Tag; für ein Wort, das im Buch steht und
  aus einem Wörterbuch geraten werden müsste, halte ich das für vertretbar, aber es ist mehr als „10 je Leser“.
- **Satz für den Auftrag:** „Das Versuchslimit gilt je Lesesitzung (10 pro Stunde) und je Netz (100 pro Stunde und
  Sprungpunkt, bei IPv6 je Adressblock).“ → **Frage im Interview** und **Bedarf an die Leitstelle** (Änderung eines
  messbaren Ziels aus dem Masterplan).

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
  Transfersperre (wo die Endung sie anbietet), Zwei-Faktor-Anmeldung beim Registrar (dem Anbieter, bei dem die Domain
  gemietet ist) und einer Erinnerung im Kalender 60 Tage vor Ablauf.“

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

### H10. Das Sicherheitszertifikat der Kurz-Domain läuft still ab
- **Was:** Jede Adresse mit `https` braucht ein Zertifikat, das alle paar Monate erneuert wird, meist automatisch durch
  den Hoster.
- **Warum es dich erwischt:** Klemmt die Erneuerung einmal (Hosterwechsel, geänderter Domain-Eintrag), zeigt jedes Handy
  eine Sicherheitswarnung statt der Seite, für alle gedruckten Codes gleichzeitig. Niemand merkt es, bis Leser sich
  beschweren.
- **Satz für den Auftrag:** „Ein einfacher Wächter ruft Kurz-Domain und Inhalts-Domain täglich auf, prüft Zertifikat,
  Weiterleitung und eine Testseite und schickt bei einem Fehler sofort einen Alarm.“

### H11. Eine Phishing-Meldung kann den Hoster zum Abschalten bringen
- **Was:** Hoster und Registrare nehmen Meldungen über Phishing ernst und sperren Domains oder Konten teils binnen
  Stunden, oft automatisch und bevor jemand nachfragt.
- **Warum es dich erwischt:** Ein besorgter Elternteil meldet die „gehackte Chatseite“ als Betrug, und das ganze Format
  ist offline, ohne dass du erreichbar warst.
- **Satz für den Auftrag:** „Für Missbrauchsmeldungen gibt es einen festgelegten Notfallweg: Funktions-E-Mail, die
  überwacht wird, beim Hoster hinterlegter Hinweis auf das Buchformat, eine vorbereitete Erklärung samt Belegen
  (Fiktionskennzeichnung, Impressum) und die Anleitung zur Gegendarstellung bei Google Safe Browsing.“

### H12. Automatische Gerätetests sind keine echten Handys
- **Was:** Die Testwerkzeuge (z. B. Playwright, das einen Browser fernsteuert) ahmen Bildschirmgröße und Browser nach. iPhone-Safari, In-App-Browser und vergrößerte
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
- **Unsicher:** Ob die Adresse eines Büro- oder Postservice als ladungsfähige Anschrift reicht, ist rechtlich
  umstritten. Das Gesetz verlangt die Anschrift, unter der man niedergelassen ist. Das gehört in die anwaltliche
  Prüfung.
- **Satz für den Auftrag:** „Impressum und Datenschutz nennen dieselben Angaben wie das Buch-Impressum, mit einer
  eigenen Funktions-E-Mail des Labels. Welche Anschrift zulässig ist, klärt die anwaltliche Prüfung vor der
  Veröffentlichung; für den Technik-Test reicht ein Platzhalter, weil die Seiten nicht öffentlich beworben werden.“
  → **Frage im Interview.**

### R2. Im Jugendmedienschutz gibt es keine Stufe 14
- **Was:** Für Webseiten gilt der Jugendmedienschutz-Staatsvertrag. Er kennt die Altersstufen 0, 6, 12, 16 und 18.
  Inhalte, die für Jüngere ungeeignet sind, muss man sichern, etwa mit einer maschinenlesbaren Altersangabe, die
  Jugendschutzprogramme auf Familien-Geräten auswerten.
- **Warum es dich erwischt:** Die Entscheidung 2 sagt „Webinhalte halten die Altersfreigabe 14 ein“, aber 14 gibt es im
  Netz nicht. Ein Inhalt ist dort entweder „ab 12 unbedenklich“ oder „ab 16“ (mit Kennzeichnung). Der Technik-Test hat
  Altersfreigabe 16.
- **Zwei Wege:** (a) Webinhalte so bauen, dass sie ab 12 unbedenklich sind; Härteres bleibt im Buch. (b) Webinhalte
  „ab 16“ mit maschinenlesbarer Altersangabe; das passt zur dunkleren Mystery aus Entscheidung 2, aber
  Jugendschutzprogramme sperren die Seiten dann für 14- und 15-Jährige, also für einen Teil der Zielgruppe.
- **Satz für den Auftrag:** „Der Prüfer bewertet Webinhalte nach den Stufen 0/6/12/16/18; die Zielstufe für Titel 1
  legst du fest.“ → **Frage im Interview** und **Bedarf an die Leitstelle**.

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
- **Warum es dich erwischt:** Es ist verlockend, für bessere Zahlen eine Geräte-Kennung abzulegen („war schon mal
  hier“). Das bräuchte ein Einwilligungsbanner, und das zerstört die Immersion.
- **Satz für den Auftrag:** „Gemessen wird nur, was ohne Speicherung auf dem Gerät geht: Aufruf, Abschluss und der
  Klick auf ‚Zurück zum Buch‘ (die Rückkehr ins Buch aus dem Masterplan), als Summen je Sprungpunkt und Tag.“

### R5. Lizenzen für alles, was 10 Jahre auf der Seite steht
- **Was:** Schriften, Symbole, Wetterdaten, KI-Bilder und KI-Stimmen haben jeweils eigene Lizenzen. Manche KI-Dienste
  erlauben gewerbliche Nutzung nur im bezahlten Tarif. KI-Bilder sind in der Regel nicht urheberrechtlich geschützt
  (es kommt auf den menschlichen Anteil an), andere dürfen sie dann wiederverwenden.
- **Warum es dich erwischt:** Eine Schrift ohne Web-Lizenz oder eine KI-Stimme aus dem Gratis-Tarif fällt in Jahr 5
  bei einer Prüfung auf, und dann muss jede betroffene Seite neu gebaut werden.
- **Satz für den Auftrag:** „Nur Schriften mit freier Lizenz (z. B. die SIL Open Font License, die gewerbliche Nutzung
  erlaubt), vom eigenen Server ausgeliefert; für jedes Medium stehen Werkzeug, Tarif und Lizenz in der Medienliste der
  Rückmeldung (Feld `quelle`).“

### R6. Ein Feed mit eigenen Texten zu aktuellen Themen kann als journalistisch gelten
- **Was:** Der Medienstaatsvertrag verlangt für Webangebote mit journalistisch-redaktionell gestalteten Inhalten einen
  namentlich genannten Verantwortlichen mit Anschrift (§ 18 Abs. 2 MStV) und Sorgfaltspflichten.
- **Warum es dich erwischt:** Das Modul `feed` greift laut Entscheidung 4 aktuelle Themen in eigener Formulierung auf.
  Ob ein erkennbar fiktiver Feed darunter fällt, ist offen; fällt er darunter, fehlt im Impressum eine Angabe.
- **Satz für den Auftrag:** „Ob der Feed eine Angabe nach § 18 Abs. 2 MStV braucht, klärt die anwaltliche Prüfung; bis
  dahin bleibt der Feed erkennbar fiktiv und ohne Bezug auf echte Personen oder Ereignisse.“ → **Punkt für die
  anwaltliche Prüfung** (Masterplan Abschnitt 9).

---

## P. Produktion im Online-Studio

### P1. Claude erzeugt keine Fotos und keine Stimmen
- **Was:** Die Crews laufen wie im Reihen-Studio über Claude. Claude schreibt Texte, Daten und Seitengestaltung und
  kann Zeichnungen als Vektorgrafik anlegen (das reicht für die Stadt-Illustration im Modul `karte`). Fotorealistische
  Bilder und Sprachaufnahmen erzeugt Claude nicht. Dafür braucht es einen weiteren Dienst mit eigenem Konto, eigenem
  Schlüssel, eigenen Kosten und eigener Lizenz (R5), oder du erzeugst die Medien selbst.
- **Warum es dich erwischt:** Die Module `bildbeweis` und `audio` haben sonst keinen Inhalt, und die Kostenschätzung
  fehlt.
- **Satz für den Auftrag:** „In v1 erzeugt das Studio für Bilder und Audio ein genaues Briefing (Motiv, Länge, Text,
  Alt-Text, Transkript). Die Medien kommen über einen festen Ordner herein; der Prüfer kontrolliert Kennzeichnung und
  Lizenz. Eine direkte Anbindung an einen Bild- oder Stimmdienst ist ein späterer Ausbau.“ → **Frage im Interview.**

### P2. Git als Gedächtnis vergisst nie, auch keine Codewörter
- **Was:** Alles, was einmal in Git steht, bleibt in der Geschichte, auch wenn es später gelöscht wird. Das echte Paket
  enthält privaten Buchtext, Codewörter und den Text des Extras.
- **Warum es dich erwischt:** Ein Repository wird irgendwann geteilt, geforkt oder öffentlich gemacht, und dann liegen
  alle Lösungen aller Bände offen. Außerdem soll laut Briefing privater Text nur über dich kommen.
- **Satz für den Auftrag:** „Das importierte Paket und alle Geheimnisse bleiben außerhalb von Git; versioniert werden
  nur Rückmeldung, Modul-Daten ohne Geheimnisse und Testberichte. Eine Prüfung vor jedem Speichern in Git (Commit)
  stellt sicher, dass kein Codewort und kein Extra-Text im Repository landet.“ → **Frage im Interview.**

### P3. Die Studio-Oberfläche läuft auf Windows
- **Was:** Das Reihen-Studio startet über `.bat`-Dateien unter Windows. Der Tester braucht einen Browser für die
  Gerätetests und ein Programm, das QR-Codes aus dem Druck-PDF liest.
- **Warum es dich erwischt:** Werkzeuge, die nur unter Linux gut laufen, scheitern auf deinem PC, und du bemerkst es
  erst beim ersten echten Lauf.
- **Satz für den Auftrag:** „Das Online-Studio startet unter Windows mit einem Doppelklick wie das Reihen-Studio; alle
  Prüf- und Testwerkzeuge installieren sich mit demselben Befehl wie die übrigen Python-Bausteine, ohne
  Zusatzprogramme, und der Probemodus läuft ohne API-Schlüssel.“

---

## Bedarf an die Leitstelle (Schema und Domain, nicht von mir zu entscheiden)

1. **Auflage im QR-Link (W4):** Bleibt `/<KURZCODE>?a=<N>`, oder wird es `/<KURZCODE>/<N>`? Der Pfad funktioniert bei
   jedem statischen Hoster und ergibt kleinere QR-Codes. Betrifft Grundsatz 4 in 04 und den Satz in Strang C.
2. **Altersfreigabe (R2):** Entscheidung 2 verlangt für Webinhalte „Altersfreigabe 14“; im Jugendmedienschutz gibt es
   nur 0/6/12/16/18. Für die Webinhalte von Titel 1 braucht es die Zielstufe 12 oder 16. Ob dafür ein Feld im Schema
   nötig ist oder eine feste Regel reicht, entscheidet die Leitstelle.
3. **Messbare Ziele zur Codewort-Prüfung (H3, H4):** „10 Versuche je Leser“ und „IP nie in Logs“ in der Fassung, die du
   im Interview festlegst.
4. **Kurz-Domain (H8, H9):** seriöse Endung, früh registrieren, Domain-Einträge gegen Spam-Missbrauch.
5. **Anwaltliche Prüfung (Masterplan Abschnitt 9):** zusätzlich Impressum-Anschrift (R1) und § 18 Abs. 2 MStV für den
   Feed (R6).

## Interview: offene Fragen (einzeln, je mit Hypothese)

1. **Betrieb:** wartungsfrei gegen festen kleinen Monatsbetrag, oder günstiger mit jährlicher Pflege? *Hypothese:
   wartungsfrei, alle Reihen zusammen höchstens 10 € im Monat.*
2. **IP und Protokolle (H3):** Gilt „IP nie in Logs“ wörtlich, auch wenn das die Auswahl an Hostern stark einschränkt?
   *Hypothese: ja, wörtlich; nur Hoster, bei denen ich es an echten Protokollen nachweisen kann.*
3. **Versuchslimit (H4):** zwei Grenzen (10 je Lesesitzung, 100 je Netz und Sprungpunkt pro Stunde) statt „10 je IP“?
   *Hypothese: ja; Restrisiko siehe H4.*
4. **Jugendschutz (R2):** Zielstufe der Webinhalte von Titel 1: 12 oder 16? *Hypothese: ab 12 unbedenklich; was härter
   ist, bleibt im Buch, damit keine Filter 14- und 15-Jährige aussperren.*
5. **Impressum (R1):** Welche Angaben stehen auf den Leser-Seiten? *Hypothese: dieselben wie im Buch-Impressum plus
   Funktions-E-Mail des Labels; für den Technik-Test ein Platzhalter; die Anschrift klärt der Anwalt.*
6. **Fotos und Stimmen (P1):** Woher kommen sie in v1? *Hypothese: Das Studio schreibt die Briefings, du erzeugst die
   Medien mit einem Werkzeug deiner Wahl und legst sie in einen Ordner.*
7. **Git und Geheimnisse (P2):** Paket und Codewörter außerhalb von Git? *Hypothese: ja; die Quelle bleibt das
   Reihen-Studio, das Paket lässt sich jederzeit neu importieren.*
8. **Testgeräte (H12):** Welche echten Handys stehen für Abnahmen bereit? *Hypothese: ein eigenes Handy; das zweite
   System über ein geliehenes Gerät oder einen Testleser.* Die Antwort fließt nur in den Testplan, nie in Webinhalte.

---

## Verbesserter Auftrag für Strang D (mit Reihenfolge und Stopps)

> Baue das Online-Studio laut Briefing D, Masterplan Abschnitt 6 und Manifest-Schema 04 (Kopie unter `schema/`,
> Version 0.1.0).
>
> **Zusätzliche Regeln aus dem Blindspot-Pass:**
> - Kurz-Domain: jede Schreibweise aus der Adresszeile funktioniert; die Tabelle bleibt auf dem Server; vorübergehende
>   Server-Weiterleitung ohne Skript; Auflage im Pfad, falls die Leitstelle zustimmt.
> - Leser-Seiten: neutrale Titel und Vorschaudaten; Teilen über eigene Teaser-Adressen; nach dem ersten Laden ohne Netz
>   vollständig; „noindex“ in Server-Begleitangaben und Seitenkopf; alle Inhalte als reiner Text eingesetzt; strenge Sicherheitsrichtlinie.
> - Hosting: Firmensitz und Server in der EU; Server-Funktionen als kleiner, umziehbarer Dienst; Geheimnisse nach
>   einem Umzug aus dem Paket neu aufgespielt; IP nur mit stündlich wechselndem Geheimschlüssel gehasht; keine IP in
>   Protokollen, an echten Protokollen nachgewiesen; Versuchslimit wie im Interview festgelegt; fester Preis oder
>   Kostendeckel; Wetterdienst mit gewerblich nutzbarer offener Lizenz und Quellenhinweis; täglicher Wächter für
>   Zertifikat und Erreichbarkeit; Notfallweg für Missbrauchsmeldungen.
> - Domains: automatische Verlängerung, Transfersperre (wo möglich), Zwei-Faktor, Anti-Spam-Einträge, seriöse Endung,
>   früh registriert.
> - Recht: Impressum wie im Buch, Anschrift anwaltlich geklärt; Webinhalte nach den Stufen 0/6/12/16/18 geprüft, Zielstufe
>   wie im Interview festgelegt; Auftragsverarbeitungsvertrag; Zählung ohne Speicher auf dem Gerät; Lizenz jedes Mediums
>   in der Medienliste; § 18 MStV für den Feed anwaltlich geklärt.
> - Produktion: Fotos und Audio in v1 über Briefing und Ordner; Paket und Geheimnisse außerhalb von Git mit Prüfung vor
>   jedem Speichern in Git; Start unter Windows per Doppelklick; Abnahme auch auf echten Handys.
>
> **Reihenfolge:**
> 1. Interview zu den acht offenen Fragen, einzeln mit Hypothese. Bedarf an die Leitstelle über dich weitergeben.
> 2. Gesamtplan für Strang D (Bauabschnitte, was hosterneutral vorab entsteht, Testplan).
>    **STOPP Plan: Ich zeige dir den Plan; gebaut wird erst nach deiner Freigabe.**
> 3. Architektur- und Hosting-Vorschlag mit 10-Jahres-Kostenschätzung, je zwei bis drei Hoster und Wetterdienste im
>    Vergleich (Recherche auf Subagenten verteilt), vom Prüfagenten geprüft.
>    **STOPP Hosting: Du gibst Hoster und Wetterdienst frei.** Bis dahin baue ich nur lokal und hosterneutral, wie es
>    das Briefing erlaubt. Gesperrt sind nur Konten, Deployments (das Hochladen auf den Server) und hostergebundener Code.
> 4. Lokal und hosterneutral, parallel zum Hosting-Stopp: Programmgerüst mit Probemodus, Schemaprüfung und alle
>    Prüfungen aus 04, Paket-Import, Modulbibliothek v1 mit Datenschemas, Lesestand-Code.
> 5. Vier Entwürfe für die Studio-Oberfläche und vier für die Leser-Seiten des Technik-Tests.
>    **STOPP Entwürfe: Du wählst je einen.**
> 6. Crews (Modul-Autor, Gestalter, Prüfer, Tester), Rückmeldung mit Handy-Vorschau, Archivmodus.
> 7. Nach der Hosting-Freigabe: Hochladen auf eine Test-Unteradresse des Hosters (z. B. `test.…`), Gerätetests,
>    QR-Scan aus dem Druck-PDF, Abnahme mit dir auf echten Handys.
>    **STOPP Abnahme Technik-Test:** Prüfagent und du nehmen ab, dann übernimmt die Leitstelle.
