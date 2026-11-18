# Linux Basics

Kurzer Einstieg in Linux: Was es ist, wie es aufgebaut ist und wie du dich im Terminal zurechtfindest.

---

## Was ist Linux?

Linux ist ein Open-Source-Betriebssystem. Der Quellcode ist öffentlich verfügbar und kann von jedem eingesehen, verwendet und verändert werden.

Linux wird häufig eingesetzt für:

- Server
- Cloud-Systeme
- Embedded-Systeme
- Softwareentwicklung
- Container-Plattformen

```{note}
Genau genommen ist Linux nur der Kernel. Zusammen mit Programmen, Bibliotheken und einer Desktop-Umgebung entsteht eine Linux-Distribution wie Ubuntu, Debian oder Fedora.
```

---

## Wichtige Konzepte

### Alles ist eine Datei

In Linux werden viele Ressourcen wie Dateien behandelt:

- Normale Dateien
- Verzeichnisse (Ordner)
- Geräte unter `/dev`
- Prozessinformationen unter `/proc`

```{note}
Da viele Komponenten als Dateien dargestellt werden, können dieselben Werkzeuge für unterschiedliche Aufgaben verwendet werden.
```

### Verzeichnisstruktur

Das gesamte Dateisystem beginnt beim Root-Verzeichnis:

```text
/
├── home
├── etc
├── var
├── usr
└── tmp
```

| Verzeichnis | Bedeutung |
| :--- | :--- |
| `/` | Root-Verzeichnis, Ausgangspunkt des Dateisystems |
| `/home` | Benutzerverzeichnisse |
| `/etc` | Systemweite Konfigurationsdateien |
| `/var` | Logs und veränderbare Daten |
| `/usr` | Programme und Bibliotheken |
| `/tmp` | Temporäre Dateien |
| `/dev` | Geräte und Hardware |
| `/root` | Home-Verzeichnis des Administrators |

```{warning}
Das Root-Verzeichnis `/` und das Verzeichnis `/root` sind nicht dasselbe.
```

---

## Terminal

Das Terminal ermöglicht die Steuerung des Systems über Befehle. Die Eingaben werden von einer Shell, meist Bash, verarbeitet.

| Befehl | Bedeutung |
| :--- | :--- |
| `pwd` | Aktuelles Verzeichnis anzeigen |
| `ls` | Dateien und Ordner anzeigen |
| `cd Downloads` | In ein Verzeichnis wechseln |
| `cd ..` | Eine Ebene nach oben wechseln |
| `cd ~` | Zum Home-Verzeichnis wechseln |

Beispiel:

```bash
pwd
ls
cd Downloads
```

```{note}
Mit der Tab-Taste können Dateinamen und Verzeichnisse automatisch vervollständigt werden. Mit der Pfeiltaste nach oben lassen sich vorherige Befehle erneut aufrufen.
```

---

## Dateirechte

Jede Datei besitzt Berechtigungen für drei Benutzergruppen:

- Besitzer (Owner)
- Gruppe (Group)
- Andere (Others)

| Zeichen | Bedeutung | Wert |
| :---: | :--- | :---: |
| `r` | Lesen (read) | 4 |
| `w` | Schreiben (write) | 2 |
| `x` | Ausführen (execute) | 1 |

Beispiel:

```text
-rwxr-xr-x
```

| Teil | Bedeutung |
| :---: | :--- |
| `-` | Datei (`d` = Verzeichnis) |
| `rwx` | Besitzer darf lesen, schreiben und ausführen |
| `r-x` | Gruppe darf lesen und ausführen |
| `r-x` | Andere dürfen lesen und ausführen |

Die Rechte können auch numerisch dargestellt werden:

```text
rwx = 4 + 2 + 1 = 7
r-x = 4 + 1     = 5
r-x = 4 + 1     = 5
```

Daraus ergibt sich:

```bash
chmod 755 skript.sh
```

```{warning}
Die Berechtigung `777` gibt allen Benutzern vollständigen Zugriff auf eine Datei oder ein Verzeichnis. Sie sollte nur in Ausnahmefällen verwendet werden.
```
