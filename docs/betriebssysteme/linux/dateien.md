(linux-dateien)=
# Dateien

Dateien speichern Informationen wie Texte, Programme, Konfigurationen oder Logs. Hier lernst du, sie zu erstellen, anzuzeigen, zu kopieren, zu verschieben und zu löschen.

```{admonition} Auf einen Blick
:class: tip

- Erstellen und bearbeiten: `touch`, `nano` → [](#linux-dateien-erstellen)
- Anzeigen: `cat`, `less`, `head`, `tail` → [](#linux-dateien-anzeigen)
- Kopieren, verschieben, löschen: `cp`, `mv`, `rm` → [](#linux-dateien-verwalten)
- Ordner statt Dateien? Siehe {doc}`ordner`
```

---

(linux-dateien-uebersicht)=
## Übersicht

| Befehl | Bedeutung | Risiko |
| :--- | :--- | :---: |
| `touch` | Erstellt eine leere Datei | {bdg-success}`harmlos` |
| `nano` | Bearbeitet eine Datei im Terminal | {bdg-success}`harmlos` |
| `cat` | Zeigt den ganzen Inhalt an | {bdg-success}`harmlos` |
| `less` | Zeigt den Inhalt seitenweise an | {bdg-success}`harmlos` |
| `head` | Zeigt die ersten Zeilen | {bdg-success}`harmlos` |
| `tail` | Zeigt die letzten Zeilen | {bdg-success}`harmlos` |
| `cp` | Kopiert Dateien | {bdg-warning}`überschreibt` |
| `mv` | Verschiebt oder benennt um | {bdg-warning}`überschreibt` |
| `rm` | Löscht Dateien | {bdg-danger}`endgültig` |

```{note}
Welche Rechte du für diese Befehle brauchst, steht unter {doc}`dateirechte`. Pfade und Wechsel zwischen Ordnern: {doc}`navigation`.
```

---

(linux-dateien-erstellen)=
## Dateien erstellen und bearbeiten

(linux-dateien-touch)=
### touch

Erstellt eine neue, leere Datei.

```bash
touch test.txt
```

```{note}
Existiert die Datei schon, wird sie **nicht** überschrieben. Nur das Änderungsdatum wird aktualisiert.
```

(linux-dateien-nano)=
### nano

Öffnet eine Datei im Terminal zur Bearbeitung.

```bash
nano test.txt
```

| Tastenkombination | Bedeutung |
| :--- | :--- |
| `Strg + O` | Speichern (mit `Enter` den Dateinamen bestätigen) |
| `Strg + W` | Suchen |
| `Strg + X` | Beenden |

```{tip}
Existiert die Datei noch nicht, wird sie beim Speichern automatisch erstellt. Unten im Fenster zeigt nano alle Tastenkombinationen an (`^` bedeutet `Strg`).
```

---

(linux-dateien-anzeigen)=
## Dateien anzeigen

Welcher Befehl passt?

```{mermaid}
flowchart TD
    A["Datei anzeigen"] --> B{"Wie gross ist<br/>die Datei?"}
    B -->|"kurz"| C["cat"]
    B -->|"gross"| D{"Was brauchst du?"}
    D -->|"alles durchblättern"| E["less"]
    D -->|"nur den Anfang"| F["head"]
    D -->|"nur das Ende"| G["tail"]
    G -->|"live mitlesen"| H["tail -f"]

    style C fill:#dcfce7,stroke:#16a34a,color:#000
    style E fill:#dbeafe,stroke:#2563eb,color:#000
    style F fill:#fef9c3,stroke:#ca8a04,color:#000
    style G fill:#fef9c3,stroke:#ca8a04,color:#000
    style H fill:#fee2e2,stroke:#dc2626,color:#000
```

(linux-dateien-cat)=
### cat

Gibt den gesamten Inhalt einer Datei aus.

```bash
cat test.txt
```

```{note}
`cat` eignet sich für **kurze** Dateien. Bei langen Dateien scrollt alles an dir vorbei, dann nimmst du [](#linux-dateien-less).
```

(linux-dateien-less)=
### less

Zeigt eine Datei seitenweise an.

```bash
less test.txt
```

| Taste | Bedeutung |
| :--- | :--- |
| `Pfeiltasten` | Zeile für Zeile scrollen |
| `Leertaste` | Eine Seite vor |
| `b` | Eine Seite zurück |
| `/wort` | Nach einem Begriff suchen |
| `n` | Nächster Treffer |
| `q` | Beenden |

```{tip}
Ideal für grosse Dateien und Logs. Mehr zum Suchen in Dateien: {doc}`suche`.
```

(linux-dateien-head)=
### head

Zeigt die **ersten** 10 Zeilen.

```bash
head test.txt          # erste 10 Zeilen
head -n 5 test.txt     # erste 5 Zeilen
```

(linux-dateien-tail)=
### tail

Zeigt die **letzten** 10 Zeilen.

```bash
tail test.txt          # letzte 10 Zeilen
tail -n 5 test.txt     # letzte 5 Zeilen
tail -f /var/log/syslog   # live mitlesen
```

```{note}
`tail -f` zeigt neue Zeilen sofort an und wird oft für Logs genutzt. Beenden mit `Strg + C`. Zum Ordner `/var` siehe {ref}`Verzeichnisstruktur <linux-verzeichnisse>`.
```

---

(linux-dateien-verwalten)=
## Dateien kopieren, verschieben und löschen

(linux-dateien-cp)=
### cp

Kopiert eine Datei. Das Original bleibt bestehen.

```bash
cp test.txt kopie.txt
```

```text
Vorher:  test.txt
Nachher: test.txt  kopie.txt
```

```{note}
Ganze Ordner kopierst du mit `cp -r`. Details dazu in {doc}`ordner`.
```

(linux-dateien-mv)=
### mv

Verschiebt eine Datei **oder** benennt sie um.

```bash
mv test.txt Dokumente/     # verschieben
mv test.txt neu.txt        # umbenennen
```

```{tip}
Verschieben und Umbenennen sind in Linux derselbe Befehl: Ändert sich der Pfad oder der Name, nutzt du `mv`.
```

(linux-dateien-rm)=
### rm

Löscht eine Datei.

```bash
rm test.txt
```

```{danger}
Mit `rm` gelöschte Dateien landen **nicht** im Papierkorb und lassen sich normalerweise nicht wiederherstellen.
```

Mit Rückfrage vor dem Löschen:

```bash
rm -i test.txt
```

(linux-dateien-ueberschreiben)=
### Überschreiben verhindern

```{warning}
`cp` und `mv` überschreiben vorhandene Dateien ohne Warnung. Mit `-i` fragt der Befehl vorher nach.
```

```bash
cp -i test.txt ziel/
mv -i test.txt ziel/
```

| Option | Bedeutung | Gilt für |
| :---: | :--- | :--- |
| `-i` | Vor dem Überschreiben oder Löschen nachfragen | `cp`, `mv`, `rm` |
| `-n` | Vorhandene Dateien nicht überschreiben | `cp`, `mv` |

---

## Beispiel: Ein kleiner Ablauf

```bash
touch notizen.txt           # Datei erstellen
nano notizen.txt            # Text schreiben und speichern
cat notizen.txt             # Inhalt prüfen
cp notizen.txt backup.txt   # Sicherung anlegen
mv notizen.txt Dokumente/   # in einen Ordner verschieben
rm backup.txt               # Sicherung wieder löschen
```

---

## Merksätze

```{admonition} Das Wichtigste in Kürze
:class: important

1. `touch` erstellt, `nano` bearbeitet.
2. Kurz = `cat`, lang = `less`, Anfang = `head`, Ende = `tail`.
3. `tail -f` liest Logs live mit.
4. `mv` verschiebt **und** benennt um.
5. `rm` ist endgültig, im Zweifel `rm -i`.
6. `cp -i` und `mv -i` schützen vor Überschreiben.
```

---

## Weiterführend (offizielle Dokumentation)

- [GNU Coreutils Manual](https://www.gnu.org/software/coreutils/manual/): `touch`, `cat`, `head`, `tail`, `cp`, `mv`, `rm`
- [GNU nano Dokumentation](https://www.nano-editor.org/docs.php): alle Tastenkombinationen
- [less (offizielle Seite)](https://www.greenwoodsoftware.com/less/): Befehle und Optionen
- [man-pages (man7.org)](https://man7.org/linux/man-pages/): Referenz im Browser, im Terminal mit `man <befehl>`

Zurück zu den Grundlagen: {doc}`basics`
