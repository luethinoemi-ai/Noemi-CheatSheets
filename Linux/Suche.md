# Suche

Wichtige Linux-Befehle zum Suchen von Dateien, Ordnern und Inhalten.

---

## find

```bash
find . -name "*.json"
```

*## Bedeutung

Sucht Dateien oder O*dner*anhand ihres*Namens.

### Beispiel

```bash*find*. -name "station_table.json"
```

*ind*t alle Dateien mit diesem Namen im*aktuellen Verzeichnis und allen Un*erordnern.

---

*# find nach Date*typ

```bash
find . -type*f*```

### Bedeutung

S*cht*nur Dateien.

### Beispiel

```bas*
find . -type*f -name*"*.txt"
```

*indet alle Textdate*en.

---

## grep

```bash
grep*"Hallo" datei.txt
```

*##*Bedeutung

Sucht*nach einem Text*innerhalb einer Datei.

### Beispi*l

```bash
grep "WebSocket" datei.*xt
```

*e*gt alle Zeilen an, die das*Wort `WebSocket` enthalten.

---

*# grep -i

```bash*grep*-i "linux" date*.txt
```

### Bedeutung

Sucht*ohne*Beachtung von Gross- und*Kleinschreibung.

### Beispiel

``*bash
*rep -i "no*mi" benutzer.txt
```

*ind*t sowohl `Noemi`, `*OEMI` als auch*`noemi`.

---

*# grep -R

*``bash*grep -R "Canvas* .
```

### Bedeutung

Durchsucht*alle Dateien und Unterordner rekur*iv.

### Beispiel

```bash
grep -R*"WebSocket" .
```

*ucht nach dem*Begriff im gesamten Projekt.

---
*##*locate

```bash
locate nano
```

*## Bedeutung

Sucht*Dateien über*eine Datenbank und liefert Ergebni*se sehr schnell.

### Beispiel

``*bash
locate config.json
```

*eigt bekannte*Dateien mit diesem Namen an.

---
*## which

```bash
which python3
``*

### Bedeutung

Zeigt*den Pfad eines Program*s an.

### Beispiel

```bash*which*git
```

Mögliche Ausgabe:

```tex*
/usr/bin/git
```

---

##*whereis

```bash*whereis python3*```

### Bedeutung

Find*t*Programmdateien, Quellcode und Han*buchseiten.

### Beispiel

```bash*whereis ssh
```

Mög*iche Ausgabe:

```text*ssh: /usr*bin/ssh /usr/share/man/man1/*sh.1.gz
```

*--

## Mer*en für die Praxis

| Befehl |*Verwendung |
|---------**--------|
| find*
