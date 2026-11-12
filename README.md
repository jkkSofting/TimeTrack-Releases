<!--
  Diese Datei wird nicht von Hand gepflegt: Im Quell-Repo erzeugt Scripts\Update-ReleasesReadme.ps1 sie aus
  ReleasesRepo\README.template.md und traegt Version und Changelog aus Helpers\Changelog.cs ein.
  Aenderungen direkt hier gehen beim naechsten Lauf verloren.
-->

# TimeTrack

**Zeiterfassung für Windows.** Projekte anlegen, Stunden buchen, auswerten – und mit einem Klick zwischen Projekten wechseln. TimeTrack läuft unauffällig im Infobereich der Taskleiste.

Aktuelle Version: **2026.47.1** &nbsp;·&nbsp; [**Zum Download**](https://github.com/jkkSofting/TimeTrack-Releases/releases/latest)

Dieses Repository enthält die fertigen Installer (unter [Releases](https://github.com/jkkSofting/TimeTrack-Releases/releases)), die Anleitung und die Versionshistorie von TimeTrack.

**Inhalt:** [Installation](#installation) · [Updates](#updates) · [Erste Schritte](#erste-schritte) · [Funktionen](#funktionen) · [Deine Daten](#deine-daten) · [Deinstallation](#deinstallation) · [Fragen und Probleme](#fragen-und-probleme) · [Changelog](#changelog)

## Installation

**Voraussetzungen:** Windows 10 (ab Version 1903) oder Windows 11. Das benötigte .NET Framework 4.8 ist dort bereits enthalten.

1. Öffne die [neueste Version](https://github.com/jkkSofting/TimeTrack-Releases/releases/latest) und lade unter **Assets** die Datei `TimeTracker-<Version>.exe` herunter.
2. Starte die heruntergeladene Datei. Windows fragt einmal nach der Administratorfreigabe (UAC), weil TimeTrack nach `Programme` installiert wird.
   Der Installer ist nicht digital signiert, deshalb zeigt Windows SmartScreen unter Umständen „Der Computer wurde durch Windows geschützt“. Wähle dann **Weitere Informationen → Trotzdem ausführen**.
3. Folge dem Installationsassistenten. Optional kannst du ein Desktop-Symbol anlegen lassen und festlegen, dass TimeTrack mit Windows startet.
4. Am Ende startet TimeTrack. Beim ersten Start legt es seine Datenbank selbst an.

## Updates

TimeTrack aktualisiert sich selbst – du musst nichts von Hand herunterladen.

- Die App sucht kurz nach dem Start und danach alle 10 Minuten nach einer neueren Version. Gibt es eine, erscheint ein Hinweis am Tray-Symbol.
- **Einstellungen → Updates → Installieren** lädt die neue Version herunter und spielt sie im Hintergrund ein. TimeTrack beendet sich dafür kurz und startet danach von selbst wieder. Windows fragt dabei einmal nach der Administratorfreigabe.
- „Nach Updates suchen“ prüft sofort, ohne auf die nächste Runde zu warten. Die automatische Suche lässt sich in den Einstellungen abschalten.
- Einstellungen und Buchungen bleiben bei einem Update erhalten.
- Du kannst auch jederzeit den neuesten Installer von Hand herunterladen und über die vorhandene Installation spielen.

Die Updates kommen aus den [Releases](https://github.com/jkkSofting/TimeTrack-Releases/releases) dieses Repositories. Ältere Versionen (bis 2026.45.0) haben früher in einem anderen Repository gesucht und wechseln mit dem nächsten Update von selbst hierher – dafür ist nichts zu tun.

## Erste Schritte

1. Lege unter **Projekte** deine Projekte an – mit Kunde und Kostenträger, und als „extern“ markiert, wenn der Kunde die Zeit bezahlt.
2. Öffne in der Seitenleiste **Quick Switch** und wähle ein Projekt: Die Buchung startet sofort. Mit Pause, Stop und Start wechselst du zwischen Projekten.
3. Jede Buchung landet automatisch in der **Stundenbuchung**, wo du sie korrigieren oder nachtragen kannst.
4. Für den Alltag praktisch: Das kleine **Quick-Switch-Fenster** kann immer sichtbar bleiben.

Eine ausführlichere Erklärung aller Bereiche findest du in TimeTrack selbst unter **Hilfe & Neuigkeiten**.

## Funktionen

| Bereich | Wofür |
| --- | --- |
| **Dashboard** | Heute gebuchte Zeit, Durchschnitt der letzten Werktage, Top-Projekt und eine Aktivitäts-Heatmap der letzten 12 Monate. |
| **Quick Switch** | Kleines Fenster zum Starten, Pausieren und Stoppen von Projekten – bis zu 4 gleichzeitig, auf Wunsch immer sichtbar. Jeder beendete Abschnitt wird sofort als Buchung gespeichert. Bekommt einen roten Rahmen, solange du in Teams deinen Bildschirm teilst. |
| **Stundenbuchung** | Alle Buchungen eines Tages als Zeitstrahl ansehen, nachtragen und korrigieren. Zeigt Pausen (auch die gesetzliche Pause) und die real gearbeitete Zeit. |
| **Fragmentierung** | Wie zersplittert war dein Tag, deine Woche oder dein Monat? |
| **SAP-Verrechnung** | Was am Monatsende wirklich im SAP gebucht werden muss: Externe Zeit deckt parallele interne Zeit ab. |
| **Projektcontrolling** | SAP-Plan- und Ist-Kosten aus einer Excel-Datei zu deinen Kostenträgern ansehen (nur lesend), mit Kostenverlauf nach SAP-Stand. Mit dem Stundensatz, den du je Projekt einträgst, lassen sich die Beträge auch als rechnerische Stunden anzeigen. Daneben der lokale Stundenverlauf aus deinen Buchungen – getrennt von den Geldbeträgen. |
| **Projekte** | Projekte anlegen, bearbeiten und auswerten; festlegen, welche im Quick Switch wählbar sind. |
| **Einstellungen** | Design (hell/dunkel, mehrere Motive, saisonale Designs), Programmstart, Automatisierung, Updates und Datensicherung. |
| **Tray-Symbol** | TimeTrack läuft im Infobereich weiter und meldet sich, wenn eine Buchung automatisch beendet wurde, länger kein Projekt läuft oder ein Update bereitsteht. |
| **Der Pinguin** | Das Maskottchen von TimeTrack. Klick ihn rechtzeitig an, dann wirft er dir einen Fisch zu. |

## Deine Daten

- Die Buchungen liegen lokal in einer Datenbank: `C:\ProgramData\Kaltenmark-Engineering\TimeTracker\timetracker.db`. TimeTrack schickt keine Daten ins Netz; Verbindung zum Internet braucht nur die Suche nach Updates.
- **Datensicherung:** Unter **Einstellungen → Datensicherung** erstellst du Sicherungen und spielst eine vorhandene wieder ein. Sie liegen im Ordner `Backups` neben der Datenbank (`*.timetrack-backup`). Fehlt beim Start die Datenbank, bietet TimeTrack an, die neueste Sicherung zu laden.
- Das **Projektcontrolling** speichert importierte SAP-Kosten ebenfalls in dieser Datenbank (und damit in Sicherungen). Die Excel-Datei wird nur gelesen, nicht verändert oder behalten, und es werden nur Zeilen zu deinen eigenen Kostenträgern übernommen.
- Updates und Deinstallation löschen die Datenbank nicht.

## Deinstallation

**Windows-Einstellungen → Apps → Installierte Apps → TimeTracker → Deinstallieren.** Deine Daten bleiben dabei bewusst erhalten. Wenn du sie nicht mehr brauchst, kannst du den Ordner `C:\ProgramData\Kaltenmark-Engineering\TimeTracker` anschließend selbst löschen.

## Fragen und Probleme

- **Windows blockiert den Installer** → siehe Hinweis zu SmartScreen unter [Installation](#installation).
- **Das Update lässt sich nicht installieren** → lade den neuesten Installer von Hand herunter und starte ihn; er aktualisiert die vorhandene Installation.
- **Die Datenbank ist weg** → starte TimeTrack neu und lade die angebotene Sicherung, oder spiele eine Sicherung unter Einstellungen → Datensicherung ein.
- Weitere Fragen: [Kontakt und Support](https://sites.google.com/view/janick-kaltenmark/startseite).

## Changelog

Die Einträge entsprechen der Seite **Hilfe & Neuigkeiten** in der App. Die neueste Version steht oben.

### 2026.47.1 - To-Do und Notizen

*12. November 2026*

- **Neu:** „To-Do“ in der Seitenleiste (Gruppe „Organisation“): ein Board wie bei Trello oder Jira, und zwar je Projekt ein eigenes. Oben wählst du unter „Board von“ das Projekt; „Ohne Projekt“ ist für alles, was zu keinem Projekt gehört. Du legst Tickets mit Titel und Beschreibung an und ordnest sie in Spalten.
- **Neu:** Jedes Board startet mit den Spalten „To Do“, „In Arbeit“ und „Erledigt“. Spalten legst du mit „Neue Spalte“ oder „Spalte hinzufügen“ am Ende des Boards an, benennst sie um, schiebst sie nach links oder rechts und löschst sie mit dem Papierkorb im Spaltenkopf. Hat die Spalte Tickets, fragt TimeTrack vorher nach, denn die Tickets gehen mit.
- **Neu:** Tickets verschiebst du mit der Maus per Ziehen, in eine andere Spalte oder an eine andere Stelle derselben Spalte; ein farbiger Strich zeigt, wo das Ticket landet. Ein Klick auf ein Ticket öffnet es zum Bearbeiten, dort kannst du es auch einer anderen Spalte zuordnen oder löschen.
- **Neu:** „Notizen“ in der Seitenleiste: Notizen mit Titel, Text und auf Wunsch einem Projekt. Die Liste ist durchsuchbar und nach Projekt filterbar; wählst du ein Projekt als Filter, gehört eine neue Notiz gleich dazu. TimeTrack speichert Änderungen kurz nach dem Tippen von selbst.
- **Neu:** Boards und Notizen liegen in der TimeTrack-Datenbank und sind in jeder Datensicherung enthalten. Löschst du ein Projekt, verschwindet sein Board mit; seine Notizen bleiben erhalten, nur ohne Projekt.

### 2026.47.0 - Plugins

*12. November 2026*

- **Neu:** TimeTrack lässt sich mit Plugins erweitern. Ein Plugin bringt eigene Seiten mit, die in der Seitenleiste unter „Plugins“ erscheinen, und kann Einstellungen ergänzen. Ohne Plugin ändert sich nichts.
- **Neu:** Einstellungen → Plugins zeigt alle gefundenen Plugins mit Version und Status. Ein neu gefundenes Plugin ist zunächst aus und wird erst geladen, wenn du es einschaltest und TimeTrack neu startest. „Plugin-Ordner öffnen“ führt direkt zum Ordner, „Nach Plugins suchen“ findet neu abgelegte Plugins ohne Neustart (das passiert auch bei jedem Öffnen der Einstellungen) und erkennt ausgetauschte Dateien laufender Plugins.
- **Neu:** Ein fehlerhaftes Plugin verhindert den Start nicht: Es bleibt aus, und die Einstellungen nennen den Grund, zum Beispiel eine aus dem Internet geladene, von Windows blockierte Datei.
- **Neu:** Was ein Plugin speichert, liegt in der TimeTrack-Datenbank und ist in jeder Datensicherung enthalten. Zugangsdaten verschlüsselt Windows für deinen Benutzer; nach dem Wiederherstellen auf einem anderen Rechner musst du sie neu eingeben.
- **Behoben:** Tätigkeitsnachweis, „Nach Tag“: Die Tagessumme stand nur unter Tagen mit mehreren Buchungen und las sich dadurch wie eine zu niedrige Summe über mehrere Tage. Jetzt hat jeder Tag seine eigene Tagessumme.
- **Verbessert:** Tätigkeitsnachweis: Die Zusammenfassung im PDF (Gesamtzeit, Buchungen, Arbeitstage, Durchschnitt) lässt sich unter „Dokument“ mit „Zusammenfassung zeigen“ ausblenden.

### 2026.46.1 - Tätigkeitsnachweis

*11. November 2026*

- **Neu:** „Tätigkeitsnachweis“ in der Seitenleiste: Du wählst einen Zeitraum (Schnellwahl wie „Letzter Monat“, „Alle Buchungen“ der gewählten Projekte oder Von/Bis) und deine Projekte und exportierst die Buchungen als PDF oder CSV. Eine Vorschau zeigt vorher, was im Nachweis steht, mit Gesamtzeit, Arbeitstagen und jeder Buchung.
- **Neu:** Das PDF ist ein A4-Dokument: Titel und Zeitraum, Auftragnehmer und Auftraggeber, Eckdaten mit Kostenträger, Zusammenfassung (bei mehreren Projekten mit Stunden und Kostenträger je Projekt), Einzelnachweis mit Zwischen- und Gesamtsumme und eine Bemerkung. Die Tabellenkopfzeile wiederholt sich auf jeder Seite, die Fußzeile nennt die Seitenzahl.
- **Neu:** Gliederung nach Tag (die Tagessumme lässt sich abschalten), Projekt oder Kalenderwoche, Dauer dezimal (1,50), als h:mm (1:30) oder beides, Uhrzeiten sowie Projekt- und Kostenträger-Spalte nach Wunsch, auf Wunsch im Querformat. Dein Name und deine Anschrift als Auftragnehmer bleiben für den nächsten Nachweis gespeichert.
- **Neu:** Standard ist die minutengenaue Dauer: Es wird nichts gerundet. Nur auf ausdrücklichen Wunsch rundet der Nachweis die Dauer jeder Buchung kaufmännisch auf 5, 10, 15 oder 30 Minuten und nennt dann die ungerundete Summe. Die Rundung wird nie gemerkt, jeder Nachweis beginnt wieder ohne.
- **Neu:** Die CSV-Datei hat eine Zeile je Buchung und passt zum deutschen Excel (UTF-8, Semikolon, Dezimalkomma); alternativ international mit Komma und Dezimalpunkt. Text, der mit = + - oder @ beginnt, wird entschärft, damit Excel ihn nicht als Formel ausführt.
- **Neu:** „PDF-Vorschau“ erzeugt den Nachweis als temporäre Datei und öffnet ihn im PDF-Programm, ohne zu speichern. So prüfst du das Aussehen, bevor du den Nachweis ablegst.
- **Neu:** Auftrags-/Bestellnummer und Auftraggeber (Name, Anschrift) trägst du einmal ein; TimeTrack merkt sie für das Projekt und füllt sie beim nächsten Nachweis wieder ein. Auftragnehmer und Auftraggeber sind optional: Der Auftraggeber steht nur im PDF, wenn du „Auftraggeber im Dokument zeigen“ wählst. Optional steht ein eigenes Logo oben rechts im PDF.
- **Neu:** TimeTrack merkt sich deine letzte Auswahl: Optionen, Projekte und die Schnellwahl des Zeitraums. „Letzter Monat“ gilt beim nächsten Mal für den dann letzten Monat.
- **Neu:** Unter „Projekte“ öffnet ein Symbol in der Zeile den Tätigkeitsnachweis mit diesem Projekt.
- **Neu:** Vor dem Export prüft TimeTrack die Buchungen und warnt vor fehlenden Beschreibungen, Überschneidungen im selben Projekt, nicht lesbaren Zeiten (diese Buchungen fehlen im Nachweis, sie werden nie mit erfundener Dauer gezählt), Dauer 0 und mehr als 12 Stunden an einem Tag. Betroffene Zeilen sind in der Vorschau hinterlegt.
- **Neu:** Projektcontrolling: Ein Standard-Stundensatz in der Kopfzeile gilt für jedes Projekt ohne eigenen Satz (je Währung des Imports). Der Stundensatz in den Details eines Projekts überschreibt ihn nur für dieses Projekt, ein leeres Feld nimmt den Standard. Ohne Standard bleibt alles wie bisher.
- **Verbessert:** Buttons, Eingabefelder, Auswahllisten und ihre Aufklapp-Fenster haben nur noch einen sehr kleinen Eckenradius und wirken eckiger. Ebenso Karten und Innenflächen; nur kleine Kapseln (Status, „Neu“-Marken) bleiben rund.

### 2026.46.0 - Projektcontrolling

*10. November 2026*

- **Neu:** „Projektcontrolling“ in der Seitenleiste: „Excel importieren“ liest Plan- und Ist-Kosten aus einer SAP-Projektcontrolling-Datei (.xlsx) – nur lesend. Importiert werden nur PSP-Elemente, die in einem Kostenträger deiner Projekte enthalten sind; der Kostenträger muss die PSP-Element-ID enthalten, aber nicht genau so heißen.
- **Neu:** Die Vorschau zeigt vor dem Speichern, was übernommen wird, samt Warnungen und Fehlern mit Blatt und Zelle. Der SAP-Stand kommt aus der Datei (fehlt er, gibst du ihn an), die Währung ist optional.
- **Neu:** Jeder Import ist ein Stand: Der Kostenverlauf zeigt die Stände nach SAP-Datum. Ein erneuter Import desselben Stands wird nicht doppelt gespeichert, eine Korrektur wird als Revision abgelegt.
- **Neu:** Lokaler Stundenverlauf je Kostenträger (Tag, Woche, Monat) aus deinen Buchungen. Er steht getrennt von den SAP-Geldbeträgen und ist nicht mit SAP abgestimmt.
- **Neu:** Stundensatz je Projekt: In den Details trägst du für jedes Projekt seinen Stundensatz ein (je Währung des Imports). Damit rechnet TimeTrack Plan, Ist und Rest zusätzlich in rechnerische Stunden um (Betrag ÷ Stundensatz). Haben Projekte am selben Kostenträger unterschiedliche Sätze, wird nicht umgerechnet. Die Stunden sind eine Schätzung aus Geld, keine gebuchte Zeit.
- **Neu:** Die erste Spalte der Übersicht, „Stand“, zeigt den Budgetverbrauch in Prozent mit einem kleinen Fortschrittsbalken. Sie bleibt beim horizontalen Scrollen stehen, sodass der Stand immer sichtbar ist.
- **Neu:** Berechnete Stunden (aus Geld umgerechnet) lassen sich mit „Berechnete Stunden (h) zeigen“ ein- und ausblenden. Die Wahl bleibt gespeichert.
- **Neu:** Diagramm: Im Projektcontrolling schaltest du zwischen „Tabelle“ und „Diagramm“ um. Das Diagramm zeigt den Stand je PSP-Element über die SAP-Daten – relativ in Prozent des Plans oder in Stunden (aus Geld umgerechnet, dazu für die gewählte Zeile Plan in Stunden und deine lokal gebuchten Stunden, kumuliert). Fährst du mit der Maus über einen Punkt, siehst du den Stand dort; neben einem Punkt zeigt eine Linie alle Werte zum nächsten SAP-Datum. Mit „Kostenträger“ blendest du einzelne Kostenträger im Diagramm ein und aus (mit Suche, „Alle einblenden“ und „Alle ausblenden“).
- **Verbessert:** Unter „Projekte“ öffnet ein Symbol in der Zeile das Projektcontrolling mit dem Kostenträger des Projekts.

### 2026.45.3 - Quick Switch statt Quick Select

*5. November 2026*

- **Neu:** „Quick Switch“ in der Seitenleiste öffnet das Quick-Switch-Fenster direkt, ebenso „Quick Switch öffnen“ im Menü des Tray-Symbols.
- **Verbessert:** Die Seite „Quick Select“ entfällt: Welche Projekte im Quick Switch wählbar sind, bestimmt allein der Schalter unter „Projekte“. Er heißt jetzt „Quick Switch“.

### 2026.45.2

*5. November 2026*

- **Behoben:** Der Schalter „Quick Select“ unter „Projekte“ wurde nicht übernommen: Ein ausgeschaltetes Projekt blieb im Quick Switch und im Quick Select wählbar. Der Schalter wirkt jetzt sofort.

### 2026.45.1

*4. November 2026*

- **Verbessert:** Updates kommen jetzt aus einem eigenen Release-Repository (github.com/jkkSofting/TimeTrack-Releases), in dem auch eine Anleitung und alle Neuigkeiten stehen. Für dich ändert sich nichts.

### 2026.45.0 - Alle Projekte im Quick Select

*4. November 2026*

- **Neu:** Unter „Projekte“ legt der Schalter „Quick Select“ fest, ob ein Projekt im Quick Select und im Quick Switch wählbar ist. Standardmäßig sind alle Projekte dabei.
- **Verbessert:** Das Quick-Switch-Fenster bietet jetzt alle Projekte zum Starten an, nicht mehr nur die im Quick Select eingerichteten.
- **Behoben:** Neu angelegte, umbenannte oder gelöschte Projekte erscheinen sofort im Quick Select und im Quick Switch, nicht erst nach einem Neustart.

### 2026.44.0 - Designs, Hilfe & Neuigkeiten

*30. Oktober 2026*

- **Neu:** Hilfe & Neuigkeiten: Diese Seite erklärt alle Bereiche von TimeTrack und zeigt, was sich mit jeder Version geändert hat. Nach einem Update weist ein „Neu“ in der Seitenleiste darauf hin.
- **Neu:** Designs: Standard, Wald, Ozean, Halloween, Weihnachten, Ostern, VfB Stuttgart und Werder Bremen – jedes in einer hellen und einer dunklen Variante. Auswahl in den Einstellungen, wird sofort übernommen.
- **Neu:** Rund um Halloween, Weihnachten und Ostern schaltet sich das passende Design automatisch ein (abschaltbar).
- **Neu:** Hell/Dunkel-Schalter unten in der Seitenleiste.
- **Neu:** Der Pinguin zieht sich passend zum Design an: Hexenhut, Weihnachtsmütze, Hasenohren, Bommelmütze, Matrosenmütze oder Fanschal.
- **Neu:** Den Fisch, den der Pinguin wirft, kannst du jetzt fangen. Die Einstellungen zeigen deine Fangstatistik.
- **Neu:** Wie oft der Pinguin auftaucht, lässt sich in den Einstellungen festlegen (Standard: alle 60 bis 90 Minuten).
- **Verbessert:** Neues Aussehen: gruppierte Navigation mit Icons, Uhr und Datum in der Seitenleiste und einheitliche Karten, Schaltflächen und Eingabefelder auf allen Seiten.
- **Verbessert:** Diagramme, Heatmap und Zeitstrahl nutzen zum Design passende Farben, die auch bei Farbsehschwäche gut unterscheidbar sind.
- **Verbessert:** Quick Select zeigt pro Zeile Laufzeit und Status.
- **Verbessert:** Einstellungen mit Design-Vorschau und einer immer sichtbaren Leiste zum Speichern und Verwerfen.
- **Verbessert:** Der Pinguin ist jetzt ein Kaiserpinguin.

### 2026.43.0 - Der Pinguin ist da

*22. Oktober 2026*

- **Neu:** Maskottchen: ein Pinguin mit einer Uhr auf dem Bauch – im App-Icon, in der Seitenleiste, im Quick Switch und im Dashboard, dort mit einer Sprechblase passend zu Tageszeit und gebuchten Stunden.
- **Neu:** Ab und zu schaut ein Pinguin hinter der Taskleiste hervor. Wer ihn rechtzeitig anklickt, bekommt einen Fisch zugeworfen. Lässt sich in den Einstellungen abschalten.
- **Neu:** Solange du in Teams deinen Bildschirm teilst, hat das Quick-Switch-Fenster einen roten Rahmen – zur Erinnerung, dass es im Meeting zu sehen ist.
- **Verbessert:** Das Projekt einer laufenden Quick-Select-Zeile lässt sich nicht mehr versehentlich ändern.

### 2026.42.3

*22. Oktober 2026*

- **Verbessert:** „Projekt starten“ im Quick Switch ist alphabetisch sortiert.

### 2026.42.1

*14. Oktober 2026*

- **Verbessert:** Die SAP-Verrechnung zeigt Kostenträger statt Projektnamen.

### 2026.42.0

*14. Oktober 2026*

- **Verbessert:** SAP-Verrechnung: Laufen ohne externes Projekt mehrere interne Projekte parallel, zählt nur das Projekt mit weniger Stunden an diesem Tag, die parallele Zeit der anderen wird verworfen.
- **Verbessert:** Die Stundenbuchung zeigt in Klammern die real gearbeitete Zeit (ohne Pausen, parallele Buchungen nur einmal gezählt).

### 2026.40.1 - SAP-Verrechnung

*30. September 2026*

- **Neu:** SAP-Verrechnung: zeigt pro Monat und Kostenträger, was wirklich im SAP gebucht werden muss. Externe Zeit deckt parallele interne Zeit ab, Überschuss wird bis Monatsende mit freien internen Zeiten verrechnet.
- **Neu:** Projekte lassen sich als „extern (vom Kunden bezahlt)“ markieren.

### 2026.40.0

*28. September 2026*

- **Neu:** Buchungen in Quick Select und Quick Switch lassen sich pausieren und fortsetzen.

### 2026.39.12

*24. September 2026*

- **Verbessert:** Übersichtlichere Anzeige des Arbeitstags in der Stundenbuchung.

### 2026.39.11

*23. September 2026*

- **Neu:** Die Buchungen eines Tages erscheinen als Zeitstrahl statt als Tabelle, parallele Buchungen nebeneinander.

### 2026.39.10

*23. September 2026*

- **Verbessert:** Auch im Quick Switch startet die Buchung sofort, sobald ein Projekt gewählt ist.

### 2026.39.9

*23. September 2026*

- **Verbessert:** Im Quick Select startet die Buchung sofort, sobald ein Projekt gewählt ist.

### 2026.39.8

*22. September 2026*

- **Neu:** Die Stundenbuchung berechnet die gesetzliche Pause (30 Minuten ab 6 Stunden, 45 Minuten ab 9 Stunden) und warnt, wenn der Arbeitstag zu lang wird.

### 2026.39.7

*22. September 2026*

- **Verbessert:** Nach Updates wird alle 10 Minuten statt alle 6 Stunden gesucht.

### 2026.39.6

*22. September 2026*

- **Neu:** Quick Select hat beliebig viele Zeilen, bis zu 4 Buchungen laufen gleichzeitig.
- **Behoben:** Einstellungen gingen bei einem Update verloren.

### 2026.39.2

*22. September 2026*

- **Verbessert:** Updates installieren sich komplett im Hintergrund, ohne Assistent.

### 2026.39.0 - Updates, Dashboard & Automatik

*22. September 2026*

- **Neu:** Automatische Updates: TimeTrack sucht neue Versionen und installiert sie per Klick in den Einstellungen.
- **Neu:** Dashboard mit Aktivitäts-Heatmap der letzten 12 Monate und Vergleichen, wie lange du schon gearbeitet hast.
- **Neu:** Buchungen werden bei Sperrbildschirm oder Ruhemodus automatisch beendet, und TimeTrack erinnert dich, wenn kein Projekt läuft.
- **Neu:** Pausen zwischen Buchungen werden berechnet und angezeigt.
- **Neu:** Unplausible Buchungen werden markiert, Überschneidungen beim Eintragen gemeldet.
- **Neu:** Datensicherung: Sicherungen erstellen und wiederherstellen.
- **Verbessert:** Der Installer kommt ohne Lizenz- und Infoseiten aus.

### 2026.29.2

*14. Juli 2026*

- **Behoben:** Das Quick-Switch-Fenster erscheint zuverlässig mittig.

### 2026.29.1

*14. Juli 2026*

- **Neu:** Einstellungen für den Programmstart (normal oder minimiert, auf Wunsch mit Quick Switch).
- **Neu:** TimeTrack kann mit Windows starten, auch direkt im Installer wählbar.

### 2026.29.0 - Quick Switch & Fragmentierung

*14. Juli 2026*

- **Neu:** Quick Switch: ein kleines, immer sichtbares Fenster zum schnellen Projektwechsel.
- **Neu:** Fragmentierung: zeigt, wie zersplittert ein Tag war, mit Details zu jedem Abschnitt.
- **Verbessert:** Buchungen werden genauer geprüft (Ende nach Start), Fehlermeldungen sind verständlicher.
- **Behoben:** Fehler bei der Zuordnung von Buchungen und beim Tageswechsel um Mitternacht.

### 2026.22.1

*29. Mai 2026*

- **Verbessert:** Lange Beschreibungen werden in der Stundenbuchung gekürzt.

### 2026.22.0 - Die erste Version

*29. Mai 2026*

- **Neu:** Projekte anlegen, Stunden buchen und im Dashboard auswerten.
- **Neu:** Quick Select zum schnellen Wechseln zwischen Projekten.
- **Verbessert:** Stunden werden als Stunden:Minuten angezeigt.

---

© Janick Kaltenmark 2026 · Kaltenmark-Engineering
