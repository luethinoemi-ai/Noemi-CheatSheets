# Suche

Linux bietet verschiedene Werkzeuge, um Dateien, Verzeichnisse, Programme und Inhalte schnell zu finden.

---

## find

Sucht Dateien und Verzeichnisse anhand ihres Namens oder anderer Kriterien.

### Syntax

```bash
find <pfad> -name "<name>"
```

### Beispiele

Datei suchen:

```bash
find . -name "station_table.json"
```

Alle JSON-Dateien suchen:

```bash
find . -name "*.json"
```

Nur Dateien *uchen:

```bash
find . -type f
``*

Nur Verzeichnisse suchen:

```ba*h
*ind . -type d
```

Alle Text*ateien suchen:

```bash
find . -*ype f -name "*.txt"
```

```*note}
Der Punkt (`.`) steht für*das aktuelle Verzeichnis.
```

---*
## grep

Sucht*nach Text innerhalb einer Datei.

*##*Syntax

```bash
grep "<text>"*<datei>
```

### Beispiele

Nach "*ebSocket" suchen:

```bash
grep*"WebSocket" datei.txt
```

Nach*Fehlern in einer Log-Date* suchen:

```bash
grep "ERROR"*logfile.log
```

---

## grep -i*
Sucht unter Ignorierung*von Gross- und Kleinschreibung.

#*#*Beispiel

```bash
grep -i "no*mi" benutzer.txt
```

Findet*beispielsweise:

```text
Noemi
NOE**
noemi
```

---

## grep*-R

Durchsucht Dateien*und Unterverzeichnisse rekursiv.

*##*Beispiel

```bash
grep -R "Web*ocket" .
```

Durchsucht das gesam*e*aktuelle Verzeichnis.

---

## loc*te

Sucht*Dateien mithilfe einer Datenbank.
*### Beispiel

```bash
locate confi*.json
```

*``{note}
`locate` ist häufig*schneller als `find`, da nicht dir*kt*das Dateisystem durchsucht wird.
`*`

*atenbank aktualisieren:

```bash
s*do updatedb
```

---

## which

Ze*gt den Speicherort eines Programms*an.

###*Beispiel

```bash
which python3
``*

Mögliche Ausgabe:

```text
/usr*bin/python3
```

---

## whereis*
Zeigt Programmdateien, Handbuchse*ten*und weitere zugehörige Dateien an.*
### Beispiel*
```bash
whereis ssh
```

*ögliche Ausgabe:

```text
ssh:*/usr/bin/ssh /usr/share/man/man*/ssh.1.gz
```

---

*# Praktische Beispiele

Dateien fi*den:

*``bash
find . -name "*.txt"
*``

Text in einem Projekt suchen:
*```bash*grep -R "Fehler" .
``*

Python-Installation prüfen:

```*ash*which python3
whereis python3
*``
