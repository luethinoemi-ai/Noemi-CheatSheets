# Informationen

Nützliche Linux-Befehle für Informationen über System, Dateien und Befehle.

---

## echo

```bash
echo Hallo
```

### Bedeutung

Gibt Text im Terminal aus.

### Beispiel

```bash
echo "Hallo Noemi"
```

Ausgabe:

```text
Hallo Noemi
```

---

## history

```bash
history
```

### Bedeutung

Zeigt die bisher ausgeführten Befehle an.

### Beispiel

```bash
history
```

Nützlich, um ältere Befehle wiederzufinden.

---

## man

```bash
man ls
```

### Bedeutung

Zeigt die Handbuchseite (Manual) eines Befehls an.

### Beispiel

```bash
man cp
```

Zeigt die Dokumentation des Befehls `cp`.

---

## which

```bash
which nano
```

### Bedeutung

Zeigt den Speicherort eines Programms an.

### Beispiel

```bash
which python3
```

Mögliche Ausgabe:

```text
/usr/bin/python3
```

---

## diff

```bash
diff datei1.txt datei2.txt
```

### Bedeutung

Vergleicht zwei Dateien und zeigt Unterschiede an.

### Beispiel

```bash
diff alt.txt neu.txt
```

Nützlich zum Vergleichen von Konfigurationsdateien oder Quellcode.

---

## du

```bash
du -sh Ordner
```

### Bedeutung

Zeigt die Grösse eines Ordners an.

### Beispiel

```bash
du -sh Downloads
```

Mögliche Ausgabe:

```text
1.2G Downloads
```

---

## df

```bash
df -h
```

### Bedeutung

Zeigt den verfügbaren und belegten Speicherplatz an.

### Beispiel

```bash
df -h
```

Mögliche Ausgabe:

```text
Filesystem      Size  Used Avail Use%
/dev/sda1        50G   20G   28G  42%
```

---

## tar

```bash
tar -czf backup.tar.gz Ordner
```

### Bedeutung

Archiviert und komprimiert Dateien oder Ordner.

### Beispiel

```bash
tar -czf projekt.tar.gz Projekt
```

Erstellt ein komprimiertes Archiv des Ordners `Projekt`.

---

## uname

```bash
uname -a
```

### Bedeutung

Zeigt Informationen über das Betriebssystem und den Kernel an.

### Beispiel

```bash
uname -a
```

Nützlich für Systemanalysen und Supportfälle.

---

## clear

```bash
clear
```

### Bedeutung

Leert das Terminalfenster.

### Beispiel

```bash
clear
```

Sorgt für eine übersichtliche Terminalansicht.

---

## Merken für die Praxis

| Befehl | Zweck |
|----------|----------|
| echo | Text ausgeben |
| history | Befehlsverlauf anzeigen |
| man | Handbuch anzeigen |
| which | Programmpfad finden |
| diff | Dateien vergleichen |
| du | Ordnergrösse anzeigen |
| df | Speicherplatz anzeigen |
| tar | Dateien archivieren |
| uname | Systeminformationen anzeigen |
| clear | Terminal leeren |

