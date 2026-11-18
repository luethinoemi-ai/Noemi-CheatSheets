(linux-navigation)=
# Navigation

Navigation ist die wichtigste Grundlage im Terminal. Mit wenigen Befehlen siehst du, wo du bist, was im Ordner liegt und wie du in andere Verzeichnisse wechselst.

```{admonition} Auf einen Blick
:class: tip

- Wo bin ich? `pwd` → [](#linux-nav-pwd)
- Was liegt hier? `ls` → [](#linux-nav-ls)
- Wohin will ich? `cd` → [](#linux-nav-cd)
- Wie schreibe ich den Weg? Absolut oder relativ → [](#linux-nav-pfade)
```

---

(linux-nav-uebersicht)=
## Übersicht

| Befehl | Bedeutung |
| :--- | :--- |
| `pwd` | Aktuelles Verzeichnis anzeigen |
| `ls` | Inhalt anzeigen |
| `ls -la` | Alles anzeigen, auch versteckte Dateien |
| `cd Ordner` | In einen Ordner wechseln |
| `cd ..` | Eine Ebene nach oben |
| `cd ~` | Ins Home-Verzeichnis |
| `cd -` | Ins vorherige Verzeichnis zurück |

Als Karte, ausgehend vom Home-Verzeichnis `/home/noemi`:

```{mermaid}
flowchart TD
    R["/"] --> H["home"]
    H --> N["noemi (du bist hier)"]
    N --> P["Projects"]
    N --> D["Downloads"]
    P --> W["webseite"]

    style R fill:#f3f4f6,stroke:#6b7280,color:#000
    style H fill:#f3f4f6,stroke:#6b7280,color:#000
    style N fill:#dcfce7,stroke:#16a34a,color:#000
    style P fill:#dbeafe,stroke:#2563eb,color:#000
    style D fill:#dbeafe,stroke:#2563eb,color:#000
    style W fill:#fef9c3,stroke:#ca8a04,color:#000
```

| Ziel | Befehl von `/home/noemi` aus |
| :--- | :--- |
| `Projects` | `cd Projects` |
| `webseite` | `cd Projects/webseite` |
| eine Ebene hoch (`home`) | `cd ..` |
| ganz nach oben (`/`) | `cd /` |

Den Aufbau des Baums erklärt die {ref}`Verzeichnisstruktur <linux-verzeichnisse>`.

---

(linux-nav-pwd)=
## pwd

Zeigt das aktuelle Arbeitsverzeichnis (**p**rint **w**orking **d**irectory).

```bash
pwd
```

```text
/home/noemi/Projects
```

```{tip}
Bist du unsicher, wo du gerade bist, tippe `pwd`. Das lohnt sich besonders vor gefährlichen Befehlen wie `rm -r` oder `chmod -R` (siehe {ref}`Rekursiv anwenden <linux-dr-rekursiv>`).
```

---

(linux-nav-ls)=
## ls

Zeigt den Inhalt eines Verzeichnisses (**l**i**s**t).

```bash
ls
```

```text
Dokumente  Downloads  Projects
```

### Die wichtigsten Optionen

| Befehl | Zeigt |
| :--- | :--- |
| `ls` | Nur Namen |
| `ls -l` | Liste mit Rechten, Besitzer, Grösse, Datum |
| `ls -a` | Auch versteckte Dateien |
| `ls -la` | Liste **und** versteckte Dateien |
| `ls -lh` | Liste mit lesbaren Grössen (KB, MB, GB) |
| `ls Ordner` | Inhalt eines anderen Ordners, ohne hinzuwechseln |

### ls -la

```bash
ls -la
```

```text
.
..
.git
.gitignore
README.md
```

```{note}
Dateien und Ordner, die mit einem Punkt (`.`) beginnen, sind standardmässig **versteckt**. Typische Beispiele sind `.git` und `.gitignore`.
```

Was die Spalten von `ls -l` bedeuten, steht unter {ref}`Rechte anzeigen <linux-dr-anzeigen>`.

---

(linux-nav-cd)=
## cd

Wechselt in ein anderes Verzeichnis (**c**hange **d**irectory).

```bash
cd Projects
```

### Wichtige Varianten

| Befehl | Ziel |
| :--- | :--- |
| `cd Projects` | In den Ordner `Projects` |
| `cd ..` | Eine Ebene nach oben |
| `cd ../..` | Zwei Ebenen nach oben |
| `cd ~` | Ins Home-Verzeichnis |
| `cd` | Ebenfalls ins Home-Verzeichnis |
| `cd -` | Zurück ins vorherige Verzeichnis |
| `cd /` | Ins Root-Verzeichnis |

```text
Vorher:  /home/noemi/Projects
cd ..
Nachher: /home/noemi
```

```{tip}
- **Tab** vervollständigt Ordnernamen. Tippe `cd Pro` und drücke Tab.
- Bei Namen mit Leerzeichen brauchst du Anführungszeichen: `cd "Meine Dokumente"`.
```

---

(linux-nav-pfade)=
## Absolute und relative Pfade

Ein **Pfad** beschreibt den Weg zu einer Datei oder einem Ordner. Es gibt zwei Arten.

| Art | Beginnt mit | Hängt vom Standort ab? |
| :--- | :--- | :---: |
| {bdg-success}`absolut` | `/` | nein |
| {bdg-primary}`relativ` | Ordnername, `.` oder `..` | ja |

### Absoluter Pfad

Beginnt immer beim Root-Verzeichnis `/` und funktioniert von überall.

```bash
cd /home/noemi/Projects
```

### Relativer Pfad

Bezieht sich auf das aktuelle Verzeichnis.

```bash
cd Projects
```

```{note}
Ein absoluter Pfad führt von überall zum selben Ziel. Ein relativer Pfad führt je nach Standort woandershin.
```

### Pfad-Kürzel

| Kürzel | Bedeutung |
| :---: | :--- |
| `/` | Root-Verzeichnis (oder Trenner zwischen Ordnern) |
| `~` | Home-Verzeichnis des Benutzers |
| `.` | Aktuelles Verzeichnis |
| `..` | Übergeordnetes Verzeichnis |

Beispiel: Von `/home/noemi/Projects` aus zeigen diese drei Befehle auf denselben Ort:

```bash
cd /home/noemi/Downloads      # absolut
cd ../Downloads               # relativ
cd ~/Downloads                # über das Home-Verzeichnis
```

```{warning}
`/` ist das Root-Verzeichnis, `/root` das Home des Administrators. Das ist nicht dasselbe (siehe {ref}`Verzeichnisstruktur <linux-verzeichnisse>`).
```

---

(linux-nav-fehler)=
## Häufige Fehler

| Meldung | Ursache | Lösung |
| :--- | :--- | :--- |
| `No such file or directory` | Tippfehler oder falscher Standort | `pwd` und `ls` prüfen, Tab nutzen |
| `Permission denied` | Kein `x`-Recht auf dem Ordner | Rechte prüfen, siehe {ref}`Rechte <linux-dr-rechte>` |
| `Not a directory` | Du willst in eine Datei wechseln | `ls -l` prüfen, mit `cat` oder `nano` öffnen |

```{warning}
Linux unterscheidet **Gross- und Kleinschreibung**. `Downloads` und `downloads` sind zwei verschiedene Ordner.
```

---

## Beispiel: Ein kleiner Ablauf

```bash
pwd                  # /home/noemi
ls                   # Downloads  Projects
cd Projects          # in den Ordner wechseln
ls -la               # alles anzeigen, auch Versteckte
cd ..                # zurück nach oben
cd -                 # zurück nach Projects
cd ~                 # ins Home-Verzeichnis
```

Weiter mit Dateien und Ordnern: {doc}`dateien`, {doc}`ordner`. Dateien finden: {doc}`suche`.

---

## Merksätze

```{admonition} Das Wichtigste in Kürze
:class: important

1. `pwd` = wo bin ich, `ls` = was liegt hier, `cd` = wohin.
2. `ls -la` zeigt auch versteckte Dateien (Punkt am Anfang).
3. `..` = eine Ebene hoch, `~` = Home, `-` = zurück.
4. Absolut beginnt mit `/`, relativ nicht.
5. Gross- und Kleinschreibung zählt.
6. Tab vervollständigt, `pwd` schafft Klarheit.
```

---

## Weiterführend (offizielle Dokumentation)

- [pwd (GNU Coreutils)](https://www.gnu.org/software/coreutils/manual/html_node/pwd-invocation.html): Arbeitsverzeichnis ausgeben
- [ls (GNU Coreutils)](https://www.gnu.org/software/coreutils/manual/html_node/ls-invocation.html): alle Optionen
- [Bourne Shell Builtins (Bash)](https://www.gnu.org/software/bash/manual/html_node/Bourne-Shell-Builtins.html): `cd` und seine Optionen
- [Tilde Expansion (Bash)](https://www.gnu.org/software/bash/manual/html_node/Tilde-Expansion.html): wie `~` funktioniert
- [path_resolution(7) (man7.org)](https://man7.org/linux/man-pages/man7/path_resolution.7.html): wie Linux Pfade auflöst

Zurück zu den Grundlagen: {doc}`basics`
