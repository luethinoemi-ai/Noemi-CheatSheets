(linux-dateirechte)=
# Dateirechte

Dateirechte legen fest, wer auf Dateien und Verzeichnisse zugreifen darf und was er damit tun darf.

```{admonition} Auf einen Blick
:class: tip

- Drei Gruppen: **Besitzer**, **Gruppe**, **Andere** → [](#linux-dr-gruppen)
- Drei Rechte: `r`=4, `w`=2, `x`=1 → [](#linux-dr-rechte)
- Rechte lesen mit `ls -l` → [](#linux-dr-anzeigen)
- Rechte ändern mit `chmod` → [](#linux-dr-chmod)
- Besitzer ändern mit `chown` → [](#linux-dr-chown)
```

---

(linux-dr-gruppen)=
## Die drei Benutzergruppen

Jede Datei hat Rechte für drei Gruppen:

| Gruppe | Kürzel | Bedeutung |
| :--- | :---: | :--- |
| Besitzer (Owner) | `u` (user) | Eigentümer der Datei |
| Gruppe (Group) | `g` | Benutzer derselben Gruppe |
| Andere (Others) | `o` | Alle übrigen Benutzer |

Linux prüft **der Reihe nach** und nimmt den ersten Treffer:

```{mermaid}
flowchart TD
    A["Zugriff auf Datei"] --> B{"Bist du<br/>der Besitzer?"}
    B -->|"ja"| C["Rechte des Besitzers"]
    B -->|"nein"| D{"Bist du in<br/>der Gruppe?"}
    D -->|"ja"| E["Rechte der Gruppe"]
    D -->|"nein"| F["Rechte der Anderen"]

    style C fill:#dcfce7,stroke:#16a34a,color:#000
    style E fill:#fef9c3,stroke:#ca8a04,color:#000
    style F fill:#fee2e2,stroke:#dc2626,color:#000
```

```{note}
Ist der Besitzer auch in der Gruppe, gelten trotzdem nur die Rechte des Besitzers.
```

---

(linux-dr-rechte)=
## Die drei Rechte

| Zeichen | Bedeutung | Wert |
| :---: | :--- | :---: |
| {bdg-success}`r` | Lesen (read) | 4 |
| {bdg-warning}`w` | Schreiben (write) | 2 |
| {bdg-danger}`x` | Ausführen (execute) | 1 |

Bei **Verzeichnissen** bedeuten die Rechte etwas anderes:

| Recht | Bei Dateien | Bei Verzeichnissen |
| :---: | :--- | :--- |
| `r` | Inhalt lesen | Inhalt anzeigen (`ls`) |
| `w` | Inhalt ändern | Dateien erstellen, umbenennen, löschen |
| `x` | Datei ausführen | Verzeichnis betreten (`cd`) |

```{warning}
Ohne `x` auf einem Verzeichnis kommst du nicht hinein, auch wenn du `r` hast. Wird ein Ordner aus Versehen mit `chmod 644` versehen, ist er gesperrt.
```

Mehr zu Ordnern: {doc}`ordner`.

---

(linux-dr-anzeigen)=
## Rechte anzeigen

```bash
ls -l
```

```text
-rwxr-xr-x 1 noemi users 1234 Nov 18 script.sh
```

### Der Rechte-Block

| Teil | Bedeutung |
| :---: | :--- |
| `-` | Dateityp (`-` = Datei, `d` = Verzeichnis, `l` = Link) |
| `rwx` | Besitzer: lesen, schreiben, ausführen |
| `r-x` | Gruppe: lesen und ausführen |
| `r-x` | Andere: lesen und ausführen |

### Die ganze Zeile

| Teil | Bedeutung |
| :--- | :--- |
| `-rwxr-xr-x` | Typ und Rechte |
| `1` | Anzahl Links |
| `noemi` | Besitzer |
| `users` | Gruppe |
| `1234` | Grösse in Bytes |
| `Nov 18` | Änderungsdatum |
| `script.sh` | Name |

```{tip}
Eigenen Benutzer und Gruppen anzeigen: `whoami`, `id`, `groups`.
```

---

(linux-dr-zahlen)=
## Zahlenrechte

Pro Gruppe werden die Werte addiert. Drei Ziffern ergeben die Rechte für **Besitzer, Gruppe, Andere**.

| Rechte | Rechnung | Wert |
| :---: | :--- | :---: |
| `rwx` | 4 + 2 + 1 | 7 |
| `rw-` | 4 + 2 | 6 |
| `r-x` | 4 + 1 | 5 |
| `r--` | 4 | 4 |
| `---` | 0 | 0 |

```text
rwx r-x r-x
 7   5   5    →  755
```

---

(linux-dr-chmod)=
## chmod

Ändert die Rechte einer Datei oder eines Verzeichnisses (**ch**ange **mod**e).

### Mit Zahlen

```bash
chmod 755 script.sh
chmod 644 datei.txt
chmod 700 script.sh
```

| Wert | Rechte | Typische Verwendung |
| :---: | :---: | :--- |
| `755` | `rwxr-xr-x` | Skripte und Programme |
| `644` | `rw-r--r--` | Normale Dateien |
| `700` | `rwx------` | Private Skripte |
| `600` | `rw-------` | Vertrauliche Dateien (z. B. SSH-Schlüssel) |

### Mit Buchstaben

Aufbau: **Wer** + **Operator** + **Recht**

| Wer | Operator | Recht |
| :---: | :---: | :---: |
| `u` Besitzer | `+` hinzufügen | `r` |
| `g` Gruppe | `-` entfernen | `w` |
| `o` Andere | `=` genau setzen | `x` |
| `a` Alle | | |

```bash
chmod +x script.sh      # ausführbar machen
chmod u+x script.sh     # nur für den Besitzer ausführbar
chmod go-w datei.txt    # Gruppe und Andere dürfen nicht mehr schreiben
chmod a=r datei.txt     # alle dürfen nur lesen
```

```{tip}
Zahlen sind kürzer, wenn du alles auf einmal setzen willst. Buchstaben sind besser, wenn du nur **ein einzelnes Recht** ändern willst.
```

---

(linux-dr-chown)=
## chown

Ändert den Besitzer und/oder die Gruppe (**ch**ange **own**er).

```bash
chown noemi dokument.txt                  # nur Besitzer
chown noemi:developers projekt.txt        # Besitzer und Gruppe
chown :developers projekt.txt             # nur Gruppe
```

```{note}
Den Besitzer ändern darf normalerweise nur der Administrator, also meist mit `sudo chown ...`. Den Administrator findest du in der {ref}`Verzeichnisstruktur <linux-verzeichnisse>` als `/root`.
```

---

(linux-dr-rekursiv)=
## Rekursiv anwenden

Mit `-R` gilt die Änderung für einen Ordner **und** alles darin.

```bash
chmod -R 755 projekt/
chown -R noemi:developers projekt/
```

```{warning}
`-R` wirkt auf alle Dateien und Unterordner. Vorher mit `pwd` und `ls` prüfen, ob du im richtigen Verzeichnis bist (siehe {doc}`navigation`). Ein falscher Pfad kann das ganze System beschädigen.
```

---

(linux-dr-sicherheit)=
## Sicherheitshinweis

```bash
chmod 777 datei.txt
```

Damit dürfen **alle** Benutzer lesen, schreiben und ausführen.

```{danger}
`777` nur in Ausnahmefällen verwenden. Jeder Benutzer auf dem System bekommt vollen Zugriff. Besser ist es, die Rechte gezielt zu setzen, z. B. `755` oder `644`.
```

---

## Merksätze

```{admonition} Das Wichtigste in Kürze
:class: important

1. Rechte gelten für **Besitzer**, **Gruppe**, **Andere**, in genau dieser Reihenfolge.
2. `r`=4, `w`=2, `x`=1, pro Gruppe addieren.
3. Bei Verzeichnissen heisst `x`: betreten.
4. `chmod` ändert Rechte, `chown` ändert Besitzer und Gruppe.
5. `755` für Skripte, `644` für Dateien, `600` für Vertrauliches.
6. `-R` immer mit Vorsicht, `777` meiden.
```

---

## Weiterführend (offizielle Dokumentation)

- [chmod (GNU Coreutils)](https://www.gnu.org/software/coreutils/manual/html_node/chmod-invocation.html): alle Optionen und Schreibweisen
- [chown (GNU Coreutils)](https://www.gnu.org/software/coreutils/manual/html_node/chown-invocation.html): Besitzer und Gruppe ändern
- [File permissions (GNU Coreutils)](https://www.gnu.org/software/coreutils/manual/html_node/File-permissions.html): Hintergrund zu den Rechten
- [credentials(7) (man7.org)](https://man7.org/linux/man-pages/man7/credentials.7.html): Benutzer, Gruppen und Prozess-Rechte

Zurück zu den Grundlagen: {doc}`basics`. Dateien verwalten: {doc}`dateien`.
