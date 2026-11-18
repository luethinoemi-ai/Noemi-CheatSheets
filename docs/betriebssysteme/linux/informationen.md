(linux-informationen)=
# Informationen

Nützliche Befehle, um Informationen über das System, Dateien und Programme abzurufen, Befehle nachzuschlagen und Dateien zu archivieren.

```{admonition} Auf einen Blick
:class: tip

- Hilfe und Verlauf: `man`, `history` → [](#linux-info-hilfe)
- System und Speicher: `uname`, `df`, `du`, `which` → [](#linux-info-system)
- Dateien vergleichen und archivieren: `diff`, `tar` → [](#linux-info-dateien)
- Ausgabe im Terminal: `echo`, `clear` → [](#linux-info-terminal)
```

---

(linux-info-uebersicht)=
## Übersicht

| Befehl | Bedeutung | Kategorie |
| :--- | :--- | :---: |
| `man` | Handbuchseite eines Befehls | {bdg-primary}`Hilfe` |
| `history` | Bisherige Befehle anzeigen | {bdg-primary}`Hilfe` |
| `uname` | Infos zu System und Kernel | {bdg-info}`System` |
| `df` | Auslastung der Dateisysteme | {bdg-info}`System` |
| `du` | Speicherbedarf von Dateien und Ordnern | {bdg-info}`System` |
| `which` | Speicherort eines Programms | {bdg-info}`System` |
| `diff` | Zwei Dateien vergleichen | {bdg-warning}`Dateien` |
| `tar` | Archive erstellen und entpacken | {bdg-warning}`Dateien` |
| `echo` | Text ausgeben | {bdg-secondary}`Terminal` |
| `clear` | Terminal leeren | {bdg-secondary}`Terminal` |

Welcher Befehl passt zu deiner Frage?

```{mermaid}
flowchart TD
    A["Was möchtest du wissen?"] --> B["Wie funktioniert<br/>ein Befehl?"]
    A --> C["Wo liegt ein<br/>Programm?"]
    A --> D["Wie viel Platz<br/>ist belegt?"]
    A --> E["Welches System<br/>läuft?"]
    A --> F["Was ist<br/>anders?"]

    B --> B1["man"]
    C --> C1["which"]
    D --> D1{"Ordner oder<br/>ganze Platte?"}
    D1 -->|"Ordner"| D2["du"]
    D1 -->|"Platte"| D3["df"]
    E --> E1["uname"]
    F --> F1["diff"]

    style B1 fill:#dbeafe,stroke:#2563eb,color:#000
    style C1 fill:#dcfce7,stroke:#16a34a,color:#000
    style D2 fill:#fef9c3,stroke:#ca8a04,color:#000
    style D3 fill:#fef9c3,stroke:#ca8a04,color:#000
    style E1 fill:#dcfce7,stroke:#16a34a,color:#000
    style F1 fill:#fee2e2,stroke:#dc2626,color:#000
```

---

(linux-info-hilfe)=
## Hilfe und Verlauf

(linux-info-man)=
### man

Zeigt die Handbuchseite (**man**ual) eines Befehls an.

```bash
man ls
man cp
```

Die Seite wird wie bei {ref}`less <linux-dateien-less>` bedient:

| Taste | Bedeutung |
| :--- | :--- |
| `Leertaste` | Eine Seite vor |
| `/wort` | Nach einem Begriff suchen |
| `n` | Nächster Treffer |
| `q` | Beenden |

```{tip}
Eine Kurzfassung gibt es bei den meisten Befehlen mit `--help`, zum Beispiel `ls --help`.
```

(linux-info-history)=
### history

Zeigt die bisher ausgeführten Befehle, nummeriert.

```bash
history
```

```text
  101  cd Downloads
  102  ls
  103  nano test.txt
```

| Eingabe | Wirkung |
| :--- | :--- |
| `!103` | Befehl Nummer 103 erneut ausführen |
| `!!` | Letzten Befehl erneut ausführen |
| `Strg + R` | Rückwärts im Verlauf suchen |
| `history \| grep nano` | Verlauf nach einem Wort durchsuchen |

```{note}
Mit der Pfeiltaste nach oben holst du ebenfalls frühere Befehle zurück (siehe {ref}`Tipps zum Terminal <linux-terminal>`). Mehr zu `grep`: {doc}`suche`.
```

---

(linux-info-system)=
## System und Speicher

(linux-info-uname)=
### uname

Zeigt Informationen über Betriebssystem und Kernel.

```bash
uname -a
```

| Option | Zeigt |
| :---: | :--- |
| `-a` | Alle Informationen |
| `-s` | Name des Kernels (`Linux`) |
| `-r` | Kernel-Version |
| `-m` | Architektur (z. B. `x86_64`) |
| `-n` | Hostname |

Der Kernel wird erklärt unter {ref}`Was ist Linux? <linux-was-ist>`.

(linux-info-df)=
### df

Zeigt die Auslastung der **Dateisysteme** (**d**isk **f**ree).

```bash
df -h
```

```text
Filesystem      Size  Used Avail Use%  Mounted on
/dev/sda1        50G   20G   28G  42%  /
```

| Spalte | Bedeutung |
| :--- | :--- |
| `Filesystem` | Gerät, z. B. `/dev/sda1` (siehe {ref}`Verzeichnisstruktur <linux-verzeichnisse>`) |
| `Size` | Gesamtgrösse |
| `Used` / `Avail` | Belegt / frei |
| `Use%` | Auslastung in Prozent |
| `Mounted on` | Wo das Dateisystem eingehängt ist |

(linux-info-du)=
### du

Zeigt den Speicherbedarf von **Dateien und Ordnern** (**d**isk **u**sage).

```bash
du -sh Downloads
```

```text
1.2G    Downloads
```

| Option | Bedeutung |
| :---: | :--- |
| `-h` | Menschenlesbar (KB, MB, GB) |
| `-s` | Nur die Gesamtsumme (summary) |

```{tip}
Merke dir den Unterschied: `df` fragt die **ganze Platte**, `du` fragt **einen Ordner**.
```

Alle Unterordner einzeln anzeigen:

```bash
du -sh *
```

(linux-info-which)=
### which

Zeigt, wo ein Programm liegt.

```bash
which python3
```

```text
/usr/bin/python3
```

```{note}
Gibt `which` nichts aus, wurde das Programm nicht gefunden. Dann ist es nicht installiert oder nicht im Suchpfad (`PATH`). Mehr zum Suchen von Dateien: {doc}`suche`.
```

---

(linux-info-dateien)=
## Dateien vergleichen und archivieren

(linux-info-diff)=
### diff

Vergleicht zwei Dateien und zeigt die Unterschiede.

```bash
diff alt.txt neu.txt
```

```text
2c2
< Hallo Welt
---
> Hallo Noemi
```

| Symbol | Bedeutung |
| :---: | :--- |
| `<` | Zeile steht nur in der **ersten** Datei |
| `>` | Zeile steht nur in der **zweiten** Datei |
| `2c2` | Zeile 2 wurde geändert (**c**hanged) |

```{tip}
Mit `diff -u` bekommst du das übersichtlichere Format, das auch Git verwendet. Praktisch für Konfigurationsdateien und Quellcode.
```

(linux-info-tar)=
### tar

Fasst Dateien zu einem **Archiv** zusammen oder entpackt es.

Archiv erstellen:

```bash
tar -czf projekt.tar.gz Projekt
```

Archiv entpacken:

```bash
tar -xzf projekt.tar.gz
```

Inhalt anzeigen, ohne zu entpacken:

```bash
tar -tzf projekt.tar.gz
```

| Option | Bedeutung |
| :---: | :--- |
| `c` | Archiv erstellen (**c**reate) |
| `x` | Archiv entpacken (e**x**tract) |
| `t` | Inhalt anzeigen (lis**t**) |
| `z` | Mit gzip komprimieren (`.gz`) |
| `f` | Dateiname folgt (**f**ile) |
| `v` | Ausführliche Ausgabe (**v**erbose) |

```{warning}
`f` muss direkt vor dem Archivnamen stehen. Und beim Erstellen kommt der Archivname **zuerst**, danach, was archiviert wird. Sonst kann ein falsches Ziel überschrieben werden (siehe {ref}`Überschreiben verhindern <linux-dateien-ueberschreiben>`).
```

Zielordner beim Entpacken angeben:

```bash
tar -xzf projekt.tar.gz -C Zielordner/
```

---

(linux-info-terminal)=
## Ausgabe im Terminal

(linux-info-echo)=
### echo

Gibt Text im Terminal aus.

```bash
echo "Hallo Noemi"
```

```text
Hallo Noemi
```

Text in eine Datei schreiben:

```bash
echo "Erste Zeile" > notizen.txt     # Datei neu schreiben
echo "Zweite Zeile" >> notizen.txt   # am Ende anhängen
```

```{warning}
`>` **überschreibt** die Datei ohne Rückfrage, `>>` hängt nur an. Mehr zu Dateien: {doc}`dateien`.
```

(linux-info-clear)=
### clear

Leert das Terminalfenster.

```bash
clear
```

```{tip}
Schneller geht es mit `Strg + L`.
```

---

## Merksätze

```{admonition} Das Wichtigste in Kürze
:class: important

1. Hilfe zu einem Befehl: `man <befehl>` oder `<befehl> --help`.
2. `history` zeigt den Verlauf, `!!` wiederholt den letzten Befehl.
3. `df` = ganze Platte, `du` = ein Ordner, beide mit `-h`.
4. `which` zeigt, wo ein Programm liegt.
5. `diff`: `<` erste Datei, `>` zweite Datei.
6. `tar`: `c` erstellen, `x` entpacken, `t` anzeigen, `z` komprimieren, `f` Dateiname.
7. `>` überschreibt, `>>` hängt an.
```

---

## Weiterführend (offizielle Dokumentation)

- [GNU Coreutils Manual](https://www.gnu.org/software/coreutils/manual/): `echo`, `du`, `df`, `uname`
- [GNU tar Manual](https://www.gnu.org/software/tar/manual/): alle Optionen und Formate
- [GNU Diffutils Manual](https://www.gnu.org/software/diffutils/manual/): `diff` im Detail
- [Bash History Facilities](https://www.gnu.org/software/bash/manual/html_node/Bash-History-Facilities.html): `history` und `!!`
- [man-db](https://www.nongnu.org/man-db/): das System hinter `man`
- [clear (ncurses)](https://invisible-island.net/ncurses/man/clear.1.html): `clear` im Detail

Zurück zu den Grundlagen: {doc}`basics`
