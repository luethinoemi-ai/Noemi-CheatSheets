(linux-suche)=
# Suche

Linux bietet verschiedene Werkzeuge, um Dateien, Ordner, Programmpfade und Textinhalte blitzschnell zu finden – egal ob direkt im Dateisystem oder über eine Index-Datenbank.

```{admonition} Kurzcheck: Was willst du finden?
:class: tip

- Bestimmte Datei oder Ordner nach Namen suchen? `find` / `locate` → [](#linux-suche-dateien)
- Nach einem Wort oder Fehler in Dateien suchen? `grep` → [](#linux-suche-inhalt)
- Herausfinden, wo ein Programm installiert ist? `which` / `whereis` → [](#linux-suche-programme)
```

(linux-suche-uebersicht)=
## Übersicht

| Befehl | Sucht nach | Besonderheit |
| :--- | :--- | :--- |
| `find . -name "datei"` | Dateien und Ordnern | Durchsucht das Dateisystem live und exakt |
| `locate datei` | Dateien (über Datenbank) | Extrem schnell, braucht `sudo updatedb` für neue Dateien |
| `grep "text" datei` | Text in einer Datei | Filtert Zeilen mit passendem Suchbegriff |
| `grep -i "text" datei` | Text (Gross/Klein egal) | Findet z. B. `Noemi`, `noemi` und `NOEMI` |
| `grep -R "text" .` | Text in ganzen Ordnern | Durchsucht alle Unterordner rekursiv |
| `which programm` | Ausführbarem Befehl | Zeigt den Pfad im `$PATH` (z. B. `/usr/bin/python3`) |
| `whereis programm` | Programm, Sourcen & Manpages | Zeigt alle zugehörigen Systempfade an |

Welches Suchwerkzeug passt zu deiner Aufgabe?

```{mermaid}
flowchart LR
    A["Was suchst du?"] --> B{"Dateiname, Textinhalt<br>oder Programm?"}
    B -->|Dateiname / Ordner| C{"Sofort aktuell oder<br>sehr schnell?"}
    C -->|Live & flexibel| D["find . -name ..."]
    C -->|Blitzschnell per Index| E["locate ..."]
    B -->|Text in Dateien| F["grep / grep -R"]
    B -->|Installationsort| G["which / whereis"]

    style A fill:#f3f4f6,stroke:#6b7280,color:#000
    style B fill:#fef9c3,stroke:#ca8a04,color:#000
    style C fill:#dbeafe,stroke:#2563eb,color:#000
    style D fill:#dcfce7,stroke:#16a34a,color:#000
    style E fill:#dcfce7,stroke:#16a34a,color:#000
    style F fill:#dbeafe,stroke:#2563eb,color:#000
    style G fill:#f3f4f6,stroke:#6b7280,color:#000
```

(linux-suche-dateien)=
## Dateien & Ordner finden

(linux-suche-find)=
### `find`

Durchsucht ein Verzeichnis und alle Unterordner live nach Dateien oder Ordnern anhand von Namen, Typ oder anderen Kriterien.

```bash
find <pfad> -name "<name>"
```

**Häufige Beispiele:**

```bash
find . -name "station_table.json"       # Exakten Dateinamen ab aktuellem Ordner suchen
find . -name "*.json"                   # Alle JSON-Dateien suchen (Wildcard *)
find . -type f                          # Nur Dateien auflisten (files)
find . -type d                          # Nur Ordner auflisten (directories)
find . -type f -name "*.txt"            # Nur Textdateien suchen
```

| Option | Bedeutung |
| :--- | :--- |
| `.` | Startpunkt ist das aktuelle Verzeichnis (siehe {doc}`navigation`) |
| `-name` | Sucht nach dem exakten Namen (unterscheidet Gross-/Kleinschreibung) |
| `-iname` | Sucht nach dem Namen und ignoriert Gross-/Kleinschreibung |
| `-type f` | Filtert ausschliesslich nach regulären Dateien ({doc}`dateien`) |
| `-type d` | Filtert ausschliesslich nach Verzeichnissen ({doc}`ordner`) |

```{admonition} Tipp: Wildcards in Anführungszeichen
:class: tip

Setze Suchmuster mit `*` wie `"*.json"` immer in Anführungszeichen, damit die Shell das `*` nicht vorzeitig auflöst.
```

(linux-suche-locate)=
### `locate`

Sucht Dateien über eine vorberechnete Index-Datenbank des gesamten Systems.

```bash
locate config.json
```

**Datenbank aktualisieren (falls neue Dateien noch nicht gefunden werden):**

```bash
sudo updatedb
```

| Vergleich | `find` | `locate` |
| :--- | :--- | :--- |
| Geschwindigkeit | {bdg-warning}`langsamer` (durchsucht live) | {bdg-success}`extrem schnell` (nutzt Index) |
| Aktualität | Immer zu 100 % aktuell | Hängt vom letzten `updatedb` ab |
| Filter-Möglichkeiten | Sehr viele (Typ, Grösse, Datum) | Hauptsächlich Dateinamen / Pfade |

(linux-suche-inhalt)=
## Textinhalte in Dateien durchsuchen

(linux-suche-grep)=
### `grep`

Durchsucht Dateien Zeile für Zeile nach einem bestimmten Textmuster (*global regular expression print*).

```bash
grep "<text>" <datei>
```

**Beispiele:**

```bash
grep "WebSocket" datei.txt              # Alle Zeilen mit "WebSocket" anzeigen
grep "ERROR" logfile.log                # Alle Fehlerzeilen in einer Log-Datei finden
```

(linux-suche-grep-optionen)=
### `grep -i` und `grep -R`

Mit Optionen wird [](#linux-suche-grep) deutlich flexibler – besonders beim Durchsuchen ganzer Projekte oder beim Ignorieren von Gross-/Kleinschreibung.

**Gross- und Kleinschreibung ignorieren (`-i`):**

```bash
grep -i "noemi" benutzer.txt
```

```text
Noemi
NOEMI
noemi
```

**Ganze Ordner rekursiv durchsuchen (`-R`):**

```bash
grep -R "WebSocket" .
```

| Option | Bedeutung |
| :--- | :--- |
| `-i` | *ignore case* – ignoriert Gross- und Kleinschreibung |
| `-R` / `-r` | *recursive* – durchsucht alle Dateien im Ordner und in Unterordnern |
| `-n` | Zeigt zusätzlich die genaue Zeilennummer des Treffers an |
| `-v` | Kehrt die Suche um (zeigt alle Zeilen, die den Text **nicht** enthalten) |

```{admonition} Kombination mit anderen Befehlen
:class: note

`grep` wird häufig über eine Pipe (`|`) genutzt, um Ausgaben anderer Befehle zu filtern – zum Beispiel `ps -ef | grep python` (siehe {doc}`prozesse`).
```

(linux-suche-programme)=
## Programme & Befehle lokalisieren

(linux-suche-which)=
### `which`

Zeigt den genauen Speicherort der ausführbaren Datei eines Befehls an.

```bash
which python3
```

```text
/usr/bin/python3
```

(linux-suche-whereis)=
### `whereis`

Zeigt neben der ausführbaren Programmdatei auch den Quellcode und die zugehörigen Handbuchseiten (*Manpages*) an.

```bash
whereis ssh
```

```text
ssh: /usr/bin/ssh /usr/share/man/man1/ssh.1.gz
```

| Befehl | Zeigt |
| :--- | :--- |
| `which` | Den Pfad des Befehls, der beim Eintippen im Terminal ausgeführt wird |
| `whereis` | Programmdatei, Konfigurations-/Quellpfade und Handbuchseiten |

(linux-suche-fehler)=
## Häufige Fehler

| Problem / Meldung | Ursache | Lösung |
| :--- | :--- | :--- |
| `find: Permission denied` | Kein Leserecht auf Systemordner (z. B. unter `/`) | Mit `sudo find ...` ausführen oder Fehler ausblenden (`2>/dev/null`) |
| `locate` findet neue Datei nicht | Datei wurde nach dem letzten Datenbank-Update erstellt | Datenbank mit `sudo updatedb` aktualisieren |
| `grep` findet nichts trotz Treffer | Falsche Gross-/Kleinschreibung im Suchbegriff | Option `-i` ergänzen (`grep -i "suchwort" datei`) |
| `locate: command not found` | Paket `plocate` / `mlocate` ist nicht installiert | Nachinstallieren oder [](#linux-suche-find) verwenden |

(linux-suche-ablauf)=
## Beispiel: Ein kleiner Ablauf

```bash
find . -name "*.txt"                    # Alle Textdateien im aktuellen Ordner finden
grep -Rn "Fehler" .                     # Alle Ordner rekursiv mit Zeilennummer nach "Fehler" durchsuchen
sudo updatedb                           # Such-Datenbank für locate aktualisieren
locate config.json                      # Datei blitzschnell im gesamten System finden
which python3                           # Prüfen, welche Python-Installation aktiv ist
whereis ssh                             # Programm- und Manpage-Pfade von ssh anzeigen
```

Dateien direkt lesen und bearbeiten: {doc}`dateien`. Systeminformationen und Pfade prüfen: {doc}`informationen`.

```{admonition} Merksätze
:class: important

1. `find` sucht Dateien live und exakt (z. B. `find . -name "*.json"`), `locate` sucht blitzschnell über eine Datenbank.
2. `-type f` filtert bei `find` nach Dateien, `-type d` nach Ordnern.
3. `grep` sucht Text **in** Dateien – mit `-i` ohne Gross-/Kleinschreibung, mit `-R` über ganze Ordner.
4. `which` zeigt, wo ein Befehl liegt; `whereis` zeigt zusätzlich die Manpages.
5. Suchmuster mit `*` bei `find` immer in Anführungszeichen (`"*.txt"`) schreiben.
```

## Weiterführend (offizielle Dokumentation)

- [find (GNU Findutils)](https://www.gnu.org/software/findutils/manual/html_node/find_html/index.html): Dateien und Verzeichnisse suchen
- [locate & updatedb (GNU Findutils)](https://www.gnu.org/software/findutils/manual/html_node/find_html/Invoking-locate.html): Dateisuche über die Index-Datenbank
- [GNU Grep Manual](https://www.gnu.org/software/grep/manual/grep.html): Textmuster in Dateien suchen
- [which(1) (linux.die.net)](https://linux.die.net/man/1/which): Pfad ausführbarer Befehle anzeigen
- [whereis(1) (man7.org)](https://man7.org/linux/man-pages/man1/whereis.1.html): Programmdateien und Manpages lokalisieren

Zurück zu den Grundlagen: {doc}`basics`
