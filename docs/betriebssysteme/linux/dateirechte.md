# Dateirechte

Dateirechte legen fest, welche Benutzer auf Dateien und Verzeichnisse zugreifen dürfen und welche Aktionen erlaubt sind.

Jede Datei besitzt Berechtigungen für drei Benutzergruppen:

| Gruppe | Bedeutung |
| :--- | :--- |
| Besitzer (Owner) | Eigentümer der Datei |
| Gruppe (Group) | Benutzer derselben Gruppe |
| Andere (Others) | Alle übrigen Benutzer |

---

## Rechte

Linux verwendet drei grundlegende Berechtigungen:

| Zeichen | Bedeutung | Wert |
| :---: | :--- | :---: |
| `r` | Lesen (read) | 4 |
| `w` | Schreiben (write) | 2 |
| `x` | Ausführen (execute) | 1 |

Bei Verzeichnissen haben die Rechte eine leicht andere Bedeutung:

| Recht | Bedeutung |
| :---: | :--- |
| `r` | Inhalt anzeigen |
| `w` | Dateien erstellen oder löschen |
| `x` | Verzeichnis betreten |

---

## Rechte anzeigen

```bash
ls -l
```

Beispiel:

```text
-rwxr-xr-x 1 noemi users 1234 Nov 18 script.sh
```

| Teil | Bedeutung |
| :---: | :--- |
| `-` | Datei (`d` = Verzeichnis) |
| `rwx` | Besitzer darf lesen, schreiben und ausführen |
| `r-x` | Gruppe darf lesen und ausführen |
| `r-x` | Andere dürfen lesen und ausführen |

---

## Zahlenrechte

Dateirechte können auch als Zahlen angegeben werden.

| Rechte | Rechnung | Wert |
| :--- | :--- | :---: |
| `rwx` | 4 + 2 + 1 | 7 |
| `rw-` | 4 + 2 | 6 |
| `r-x` | 4 + 1 | 5 |
| `r--` | 4 | 4 |
| `---` | 0 | 0 |

Beispiel:

```text
rwxr-xr-x
```

entspricht:

```text
755
```

---

## chmod

Ändert die Berechtigungen einer Datei oder eines Verzeichnisses.

```bash
chmod 755 script.sh
```

Datei ausführbar machen:

```bash
chmod +x script.sh
```

Weitere Beispiele:

```bash
chmod 644 datei.txt
chmod 700 script.sh
```

| Wert | Rechte | Typische Verwendung |
| :---: | :--- | :--- |
| `755` | `rwxr-xr-x` | Skripte und Programme |
| `644` | `rw-r--r--` | Normale Dateien |
| `700` | `rwx------` | Private Skripte |
| `600` | `rw-------` | Vertrauliche Dateien |

---

## chown

Ändert den Besitzer einer Datei oder eines Verzeichnisses.

```bash
chown noemi dokument.txt
```

Nach dem Befehl gehört die Datei dem Benutzer `noemi`.

Besitzer und Gruppe gleichzeitig ändern:

```bash
chown noemi:developers projekt.txt
```

---

## Änderungen rekursiv anwenden

Die Option `-R` wendet Änderungen auf einen Ordner sowie dessen gesamten Inhalt an.

Berechtigungen ändern:

```bash
chmod -R 755 projekt/
```

Besitzer ändern:

```bash
chown -R noemi:developers projekt/
```

```{warning}
Die Option `-R` wirkt auf alle Dateien und Unterordner. Vor der Ausführung sollte immer geprüft werden, ob das Zielverzeichnis korrekt ist.
```

---

## Sicherheitshinweis

```bash
chmod 777 datei.txt
```

Mit dieser Berechtigung dürfen alle Benutzer:

- lesen
- schreiben
- ausführen

```{warning}
Die Berechtigung `777` sollte nur in Ausnahmefällen verwendet werden, da jeder Benutzer vollständigen Zugriff auf die Datei erhält.
```
