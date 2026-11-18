# Suche

Linux bietet verschiedene Werkzeuge, um Dateien, Verzeichnisse, Programme oder Inhalte schnell zu finden.

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

Nur*Dateien suchen:

```bash
find . -t*pe f
```

Nur Verzeichnisse suchen*

*``bash
find . -type d
``*

Alle Textdateien suchen:

*``bash
find . -type f -name*"*.txt"
```

```{note}
Der*Punkt (`.`) steht für das aktuelle*Verzeichnis*
```

---

## grep

Sucht nach*Text innerhalb einer Datei.

###*Syntax

```bash
grep "<text>"*<datei>
```

### Beispiel

Nach "*ebSocket" suchen:

```bash
grep "*ebSocket" datei.txt
```

In*einer Log-Date* nach Fehlern suchen:

```bash
gre**"ERROR" logfile.log
```

---

##*grep -i

Ignoriert Gross- und*Kleinschreibung.

### Beispiel

``*bash*grep -i "noemi" benutzer*txt
```

Findet beispielsweise*

```text
Noemi
NOEMI*noemi
```

---

## grep -*

Durchsucht alle*Dateien und Unterverzeichnisse.

*## Beispiel

```bash
grep -R "*ebSocket" .
```

Durch*ucht das gesamte aktuelle Verzeich*is rek*rsiv.

---

## locate

Sucht Datei*n*mithilfe einer Daten*ank.

### Beispiel

```bash
locate*config.json
```

```{note}
`*ocate` ist meist deutlich schnelle* als `*ind`, da es nicht direkt das*Dateisystem durchsucht.
```

D*tenbank aktualisieren:

```bash
su*o updated*
```

---

## which

Zeigt*den Speicherort eines Programms an*

### Beispiel*
```bash
which python3
```

*ögliche Ausgabe:

```text
/usr/bin*python3
```

---

## whereis

*eigt Programmdateien, Hand*uchseiten und weitere zugehörige D*teien an*

### Beispiel

```bash
whereis ss**```

Mögliche Ausgabe:

```text*ssh: /usr/bin/ssh /usr*share/man/man1/ssh.1.gz
*``

---

## Praktische Kombination*n

Date*en finden:

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

---

## Häufig verwend*te Befehle

| Befehl |*Verwendung |
| :--- |*:--- |
| `find`*| Dateien und Verzeichnisse suchen*|
|*`grep` | Text in Dateien suchen |
* `grep -R` | Rekursiv suchen*|
| `grep -i` | Gross-*und Kleinschreibung ignorieren |
|*`*ocate` | Dateien über*eine Datenbank suchen |
| `which` **Programmpfad anzeigen |
| `where*s` | Programmdateien und*Dokumentation finden*|
