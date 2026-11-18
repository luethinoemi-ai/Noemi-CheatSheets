# Informationen

Nützliche Befehle, um Informationen über das System, Dateien und installierte Programme abzurufen.

---

## echo

Gibt Text im Terminal aus.

```bash
echo Hallo
```

Beispiel:

```bash
echo "Hallo Noemi"
```

Ausgabe:

```text
Hallo Noemi
```

---

## history

Zeigt die bisher ausgeführten Befehle an.

```bash
history
```

Beispiel:

```bash
history
```

Nützlich, um bereits verwendete Befehle nachzuschlagen.

---

## man

Zeigt die Handbuchseite eines Befehls an.

```bash
man ls
```

Beispiel:

```bash
man cp
```

Öffnet die Dokumentation des Befehls `cp`.

```{note}
Mit `q` wird die Handbuchseite wieder verlassen.
```

---

## which

Zeigt den Speicherort eines Programms an.

```bash
which nano
```

Beispiel:

```bash
which python3
```

Mögliche Ausgabe:

```text
/usr/bin/python3
```

---

## diff

Vergleicht zwei Dateien und zeigt Unterschiede an.

```bash
diff datei1.txt datei2.txt
```

Beispiel:

```bash
diff alt.txt neu.txt
```

Wird häufig verwendet, um Konfigurationsdateien oder Quellcode zu vergleichen.

---

## du

Zeigt den belegten Speicherplatz von Dateien oder Verzeichnissen an.

```bash
du -sh Ordner
```

Beispiel:

```bash
du -sh Downloads
```

Mögliche Ausgabe:

```text
1.2G Downloads
```

```{note}
Die Option `-h` sorgt für eine menschenlesbare Ausgabe (KB, MB, GB).
```

---

## df

Zeigt die Auslastung der Dateisysteme an.

```bash
df -h
```

Beispiel:

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

Erstellt oder entpackt Archive.

Archiv erstellen:

```bash
tar -czf backup.tar.gz Ordner
```

Beispiel:

```bash
tar -czf projekt.tar.gz Projekt
```

Extrahieren:

```bash
tar -xzf projekt.tar.gz
```

---

## uname

Zeigt Informationen über das Betriebssystem und den Kernel an.

```bash
uname -a
```

Beispiel:

```bash
uname -a
```

Typische Informationen:

- Kernel-Version
- Hostname
- Architektur
- Betriebssystem

---

## clear

Leert das Terminalfenster.

```bash
clear
```

Beispiel:

```bash
clear
```

Entfernt die aktuelle Ausgabe vom Bildschirm und sorgt für eine übersichtliche Ansicht.
