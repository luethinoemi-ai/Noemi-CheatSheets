# Suche

Wichtige Linux-Befehle zum Suchen von Dateien, Ordnern und Inhalten.

---

## find

```bash
find . -name "*.json"
```

*##*Bedeutung

Sucht Dateien oder Ordn*r nach Namen.

### Beispiel

```ba*h
find . -name "station_table.json*
```

Findet alle Dateien mit dies*m Namen im aktuellen Verzeichnis u*d seinen Unterordnern.

---

## gr*p

```bash
grep "Hallo" datei.txt*```

### Bedeutung

Sucht nach Tex**innerhalb einer Datei.

### Beispi*l

```bash
grep "WebSocket" datei.*xt
```

Zeigt*alle Zeilen an, die das Wort `WebS*cket` enthalten.

---

## grep -R
*```bash
*rep -R "Canvas" .
```

*##*Bedeutung

Durchs*cht alle Dateien und Unterordner r*kursiv.

### Beispiel

```bash*grep -R "Web*ocket" .
```

*ucht nach dem Begriff `WebSocket` *m gesamten Projekt.

---

## locat*

```bash
loc*te nano
```

### Bedeutung

Sucht*Dateien über eine Datenbank und*ist sehr schnell.

### Beispiel

`*`bash
*ocate config.json*```

Zeigt alle bekannten*Dateien mit diesem Namen an.

---
*## where*s

```bash*whereis python3*```

### Bedeutung

Zeigt*Programm*atei, Qu*llcode und Handbuchseiten*eines Programms.

### Beispiel

``*bash
*hereis*git
```

Mögliche Ausgabe:

```tex*
git: /*sr/bin/git /usr/share/man/man1/git*1.gz
```

*--

##*which

```bash*which*python3
```

### Bedeutung

Zeigt*den*genauen Pfad eines ausführ*aren Programms.

### Beispiel

```*ash
which node
```

*ögliche Ausgabe:

*``text
/usr/bin/node
```

*--

*# Merken für die Praxis

| B*fe*l | Zweck |
|----------|----------*
| find | Dateien suchen |
| grep*| Text in*Dateien suchen |
| grep*-R | Ganze*Ordner durchsuchen |
| locate*| Schn*lle Dateisuche |
| whereis*| Programmdate*en finden |
| which*| Pf*d eines Programms anzeigen |
````*
