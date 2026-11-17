# Linux Basics

Kurzer Einstieg in Linux: Was es ist, wie es aufgebaut ist und wie du dich im Terminal zurechtfindest.

---

## 🐧 Was ist Linux?

Linux ist ein **Open-Source-Betriebssystem**. Der Quellcode ist öffentlich und frei nutzbar. Es wird häufig eingesetzt für:

- Server
- Cloud-Systeme
- Embedded-Systeme
- Softwareentwicklung

```{note}
Genau genommen ist "Linux" nur der **Kernel**. Zusammen mit Programmen und Desktop ergibt das eine **Distribution** (z. B. Ubuntu, Debian oder Kali Linux).
```

---

## 💡 Wichtige Konzepte

### Alles ist eine Datei

In Linux werden viele Ressourcen wie Dateien behandelt:

- Normale Dateien
- Ordner
- Geräte (unter `/dev`)
- Prozessinformationen (unter `/proc`)

```{tip}
Weil alles wie eine Datei behandelt wird, kannst du mit denselben Befehlen (`cat`, `ls`, `cp`) sehr unterschiedliche Dinge ansehen.
```

### Verzeichnisstruktur

Alles beginnt beim Root-Verzeichnis `/`. Es gibt keine Laufwerksbuchstaben wie `C:` unter Windows.

```text
/
├── home
├── etc
├── var
├── usr
└── tmp
```

| Ordner | Bedeutung |
| :--- | :--- |
| `/` | Root-Verzeichnis (Startpunkt von allem) |
| `/home` | Benutzerverzeichnisse |
| `/etc` | Konfigurationsdateien |
| `/var` | Logs und veränderbare Daten |
| `/usr` | Programme und Bibliotheken |
| `/tmp` | Temporäre Dateien |
| `/dev` | Geräte (z. B. Festplatten) |
| `/root` | Home-Verzeichnis des Administrators |

```{attention}
`/` (Root-Verzeichnis) und `/root` (Home des Administrators) sind nicht dasselbe.
```

---

## 💻 Terminal

Das Terminal steuert das System über Befehle. Die Shell (meist **Bash**) führt sie aus.

| Befehl | Bedeutung |
| :--- | :--- |
| `pwd` | Zeigt den aktuellen Ordner |
| `ls` | Listet Dateien und Ordner auf |
| `cd Downloads` | Wechselt in einen Ordner |
| `cd ..` | Geht einen Ordner nach oben |
| `cd ~` | Geht ins eigene Home-Verzeichnis |

Beispiel:

```bash
pwd
ls
cd Downloads
```

```{tip}
Mit der **Tab-Taste** vervollständigt das Terminal Namen automatisch. Mit **Pfeil nach oben** holst du den letzten Befehl zurück.
```

---

## 🔐 Dateirechte

Jede Datei hat Rechte für drei Gruppen: **Besitzer**, **Gruppe** und **Andere**.

| Zeichen | Bedeutung | Zahl |
| :-: | :--- | :-: |
| `r` | read (lesen) | 4 |
| `w` | write (schreiben) | 2 |
| `x` | execute (ausführen) | 1 |

Beispiel:

```text
-rwxr-xr-x
```

| Teil | Bedeutung |
| :-: | :--- |
| `-` | Typ: `-` = Datei, `d` = Ordner |
| `rwx` | Besitzer darf lesen, schreiben, ausführen |
| `r-x` | Gruppe darf lesen und ausführen |
| `r-x` | Andere dürfen lesen und ausführen |

Die Rechte lassen sich auch als Zahl schreiben (`rwx` = 4+2+1 = 7, `r-x` = 4+1 = 5):

```bash
chmod 755 skript.sh
```

```{warning}
Vergib nie `chmod 777`. Dann darf jeder alles mit der Datei machen, das ist ein Sicherheitsrisiko.
```

---

## 🗺️ Weitere Linux-Themen

Diese Themen werden in den jeweiligen Cheatsheets genauer erklärt:

- Navigation
- Dateien
- Dateirechte
- Prozesse
- Netzwerk
- Suche
- Informationen
