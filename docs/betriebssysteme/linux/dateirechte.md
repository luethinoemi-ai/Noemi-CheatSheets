# 🔐 Dateirechte

Dateirechte bestimmen, wer eine Datei lesen, bearbeiten oder ausführen darf.

Jede Datei besitzt Rechte für drei verschiedene Gruppen:

| Gruppe | Bedeutung |
|----------|----------|
| Besitzer (Owner) | Der Eigentümer der Datei |
| Gruppe (Group) | Benutzer derselben Gruppe |
| Andere (Others) | Alle übrigen Benutzer |

---

## Rechte

| Zeichen | Bedeutung | Zahl |
|----------|----------|----------|
| `r` | Lesen (read) | 4 |
| `w` | Schreiben (write) | 2 |
| `x` | Ausführen (execute) | 1 |

💡 **Hinweis**

Bei Ordnern bedeutet:

- `r` = Inhalt auflisten
- `w` = Dateien erstellen oder löschen
- `x` = Ordner betreten

【1-d5ed6f】

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
|----------|----------|
| `-` | Datei |
| `rwx` | Besitzer darf lesen, schreiben und ausführen |
| `r-x` | Gruppe darf lesen und ausführen |
| `r-x` | Andere dürfen lesen und ausführen |

---

## Zahlen verstehen

Linux kann Rechte auch als Zahlen darstellen.

| Rechte | Rechnung | Zahl |
|----------|----------|----------|
| `rwx` | 4 + 2 + 1 | 7 |
| `rw-` | 4 + 2 | 6 |
| `r-x` | 4 + 1 | 5 |
| `r--` | 4 | 4 |
| `---` | 0 | 0 |

Beispiel:

```text
rwxr-xr-x
```

wird zu:

```text
755
```

---

## chmod

```bash
chmod 755 script.sh
```

### Bedeutung

Ändert die Zugriffsrechte einer Datei.

【2-40a046】

### Beispiel

Datei ausführbar machen:

```bash
chmod +x script.sh
```

Rechte direkt setzen:

```bash
chmod 755 script.sh
```

Danach:

```text
rwxr-xr-x
```

---

## Häufig verwendete chmod-Werte

| Wert | Rechte | Verwendung |
|----------|----------|----------|
| `755` | `rwxr-xr-x` | Skripte und Programme |
| `644` | `rw-r--r--` | Normale Dateien |
| `700` | `rwx------` | Nur Besitzer darf zugreifen |
| `600` | `rw-------` | Private Dateien |

💡 **Merkhilfe**

```text
7 = rwx
6 = rw-
5 = r-x
4 = r--
```

---

## chown

```bash
chown benutzer datei.txt
```

### Bedeutung

Ändert den Besitzer einer Datei.

【3-c901b3】

### Beispiel

```bash
chown noemi dokument.txt
```

Besitzer wird:

```text
noemi
```

---

## Besitzer und Gruppe ändern

```bash
chown noemi:developers projekt.txt
```

### Bedeutung

Ändert gleichzeitig:

- Besitzer → `noemi`
- Gruppe → `developers`

【3-c901b3】

---

## Rekursiv auf Ordner anwenden

```bash
chmod -R 755 projekt/
```

oder

```bash
chown -R noemi:developers projekt/
```

### Bedeutung

Die Änderung wird auf den gesamten Ordner inklusive Unterordner und Dateien angewendet.

---

⚠️ **Warnung**

Verwende niemals leichtfertig:

```bash
chmod 777 datei.txt
```

Dann dürfen alle Benutzer:

- lesen
- schreiben
- ausführen

Das stellt oft ein Sicherheitsrisiko dar.

【1-d5ed6f】

---

💡 **Für die Praxis**

Die wichtigsten Befehle für Schule, Lehre und Alltag sind:

```bash
ls -l
chmod +x script.sh
chmod 755 script.sh
chmod 644 datei.txt
chown benutzer datei.txt
```

Mit diesen Befehlen lassen sich die meisten Aufgaben zu Dateirechten lösen.
