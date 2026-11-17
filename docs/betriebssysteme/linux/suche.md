# Suche

Wichtige Linux-Befehle zum Suchen von Dateien, Ordnern und Inhalten.

---

## find

Dateien und Ordner anhand ihres Namens suchen.

### Syntax

```bash
find <pfad> -name "<name>"
```

### Beispiele

Datei suchen:

```bash
find . -name "station_table.json"
```

Alle JSON-Dateien finden:

```bash
find . -name "*.json"
```

### N*tzliche Optionen

Nur Dateien such*n:

```bash
*ind . -type f
*``

Nur Ordner suchen:

```bash
fi*d . -type*d
```

*ext*ateien suchen:

```bash
find . -ty*e f -name "*.txt"
```

---

## grep

Text innerhalb einer Datei suchen.

### Syntax

```bash
grep "<text>" <datei>
```

### Beispiele

Nach "WebSocket" suchen:

```bash
grep "WebSocket" datei.txt
```

Alle Treffer anzeigen:

```bash
grep "ERROR" logfile.log
```

---

## grep -i

Gross- und Kleinschreibung ignorieren.

### Beispiel

```bash
grep -i "noemi" benutzer.txt
```

Findet:

```text
Noemi
NOEMI
noemi
```

---

## grep -R

Rekursiv in allen Dateien und Unterordnern suchen.

### Beispiel

```bash
grep -R "WebSocket" .
```

Suche im gesamten Projektverzeichnis.

---

## locate

Dateien über eine Datenbank sehr schnell suchen.

### Beispiel

```bash
locate config.json
```

### Datenbank aktualisieren

```bash
sudo updatedb
```

---

## which

Zeigt den Pfad eines Programms.

### Beispiel

```bash
which python3
```

Mögliche Ausgabe:

```text
/usr/bin/python3
```

---

## whereis

Zeigt Programmdateien, Quellcode und Handbuchseiten.

### Beispiel

```bash
whereis ssh
```

Mögliche Ausgabe:

```text
ssh: /usr/bin/ssh /usr/share/man/man1/ssh.1.gz
```

---

## Praktische Kombinationen

Datei finden und Inhalt durchsuchen:

```bash
find . -name "*.txt"
grep -R "Fehler" .
```

Py*hon-Installation prüfen:

```bash
*hich python3
whereis python3
```

*--

## Merken für die Praxis

### *ach Dateien suchen

```bash
find .*-name "datei.txt"
```

### Nach Te*t suchen

```bash
grep "Text" date*.txt
```

### Im ganzen Projekt su*hen

```bash
grep -R "Text" .
```
*### Programm finden

```bash
which*git
```

### Schnell nach Dateien *uchen

```bash
locate config.json
*``

---

## Spickzettel

```text
f*nd      → Dateien und Ordner suche*
grep      → Text in Dateien suche*
grep -R   → Rekursiv suchen
grep *i   → Gross-/Kleinschreibung ignor*eren
locate    → Schnelle Dateisuc*e
which     → Programmpfad anzeige*
whereis   → Programmdateien finde*
```
