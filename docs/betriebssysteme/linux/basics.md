(linux-basics)=
# Linux Basics

Kurzer Einstieg: Was Linux ist, wie es aufgebaut ist und wie du dich im Terminal zurechtfindest.

```{admonition} Auf einen Blick
:class: tip

- Linux ist **Open Source** und eigentlich nur der **Kernel** → [](#linux-was-ist)
- Fast alles ist eine **Datei** → [](#linux-alles-datei)
- Das Dateisystem startet bei `/` → [](#linux-verzeichnisse)
- Gesteuert wird per **Terminal** und **Shell** → [](#linux-terminal)
- Zugriff regeln die **Dateirechte** → [](#linux-rechte)
```

---

(linux-was-ist)=
## Was ist Linux?

Linux ist ein **Open-Source-Betriebssystem**. Der Quellcode ist öffentlich und darf von jedem eingesehen, verwendet und verändert werden.

Typische Einsatzgebiete:

- Server und Cloud-Systeme
- Embedded-Systeme (Router, Smart-TVs, Autos)
- Softwareentwicklung
- Container-Plattformen (z. B. Docker)

```{note}
Genau genommen ist Linux nur der **Kernel**. Erst zusammen mit Programmen, Bibliotheken und evtl. einer Desktop-Umgebung entsteht eine **Distribution** wie Ubuntu, Debian, Fedora oder Kali.
```

### Aufbau eines Linux-Systems

Der Kernel sitzt zwischen Hardware und Programmen und verwaltet Speicher, Prozesse und Geräte.

```{mermaid}
flowchart TB
    U["Benutzer"] --> S["Shell / Programme"]
    S --> K["Kernel"]
    K --> H["Hardware"]

    style U fill:#dbeafe,stroke:#2563eb,color:#000
    style S fill:#dcfce7,stroke:#16a34a,color:#000
    style K fill:#fef9c3,stroke:#ca8a04,color:#000
    style H fill:#fee2e2,stroke:#dc2626,color:#000
```

| Schicht | Aufgabe |
| :--- | :--- |
| Benutzer | gibt Befehle ein oder startet Programme |
| Shell / Programme | übersetzt Eingaben und ruft den Kernel auf |
| Kernel | verwaltet {doc}`Prozesse <prozesse>`, Speicher und Geräte |
| Hardware | CPU, RAM, Festplatte, Netzwerkkarte |

---

(linux-konzepte)=
## Wichtige Konzepte

(linux-alles-datei)=
### Alles ist eine Datei

Linux stellt viele Ressourcen wie Dateien dar. Dadurch funktionieren dieselben Werkzeuge für ganz verschiedene Aufgaben.

| Was | Wo | Mehr dazu |
| :--- | :--- | :--- |
| Normale Dateien | überall | {doc}`dateien` |
| Verzeichnisse (Ordner) | überall | {doc}`ordner` |
| Geräte | `/dev` | siehe [](#linux-verzeichnisse) |
| Prozessinformationen | `/proc` | {doc}`prozesse` |

Beispiel: Die CPU-Infos lassen sich wie eine Textdatei lesen.

```bash
cat /proc/cpuinfo
```

(linux-verzeichnisse)=
### Verzeichnisstruktur

Das gesamte Dateisystem ist **ein Baum** und beginnt beim Root-Verzeichnis `/`. Es gibt keine Laufwerksbuchstaben wie `C:`.

```{mermaid}
flowchart LR
    R["/"] --> home["/home"]
    R --> etc["/etc"]
    R --> var["/var"]
    R --> usr["/usr"]
    R --> tmp["/tmp"]
    R --> dev["/dev"]
    R --> root["/root"]

    style R fill:#fef9c3,stroke:#ca8a04,color:#000
    style home fill:#dcfce7,stroke:#16a34a,color:#000
    style etc fill:#dbeafe,stroke:#2563eb,color:#000
    style var fill:#dbeafe,stroke:#2563eb,color:#000
    style usr fill:#dbeafe,stroke:#2563eb,color:#000
    style tmp fill:#f3f4f6,stroke:#6b7280,color:#000
    style dev fill:#f3f4f6,stroke:#6b7280,color:#000
    style root fill:#fee2e2,stroke:#dc2626,color:#000
```

| Verzeichnis | Bedeutung |
| :--- | :--- |
| `/` | Root-Verzeichnis, Ausgangspunkt des Dateisystems |
| `/home` | Benutzerverzeichnisse (z. B. `/home/noemi`) |
| `/etc` | Systemweite Konfigurationsdateien |
| `/var` | Logs und veränderbare Daten |
| `/usr` | Programme und Bibliotheken |
| `/tmp` | Temporäre Dateien |
| `/dev` | Geräte und Hardware |
| `/proc` | Infos zu Prozessen und Kernel (virtuell) |
| `/root` | Home-Verzeichnis des Administrators |

```{warning}
`/` (Root-Verzeichnis) und `/root` (Home des Administrators) sind **nicht dasselbe**.
```

```{note}
Auf modernen Distributionen sind `/bin` und `/sbin` meist nur Verweise (Symlinks) auf `/usr/bin` und `/usr/sbin`.
```

---

(linux-terminal)=
## Terminal und Shell

Diese Begriffe werden oft vermischt:

| Begriff | Bedeutung |
| :--- | :--- |
| **Terminal** | Das Fenster, in dem du tippst |
| **Shell** | Das Programm, das deine Befehle auswertet (meist **Bash**) |
| **Befehl** | Die Anweisung, z. B. `ls` |

```{mermaid}
flowchart LR
    A["Du tippst<br/>ls"] --> B["Terminal"]
    B --> C["Shell (Bash)"]
    C --> D["Kernel"]
    D --> E["Ausgabe im Terminal"]

    style A fill:#dbeafe,stroke:#2563eb,color:#000
    style C fill:#dcfce7,stroke:#16a34a,color:#000
    style D fill:#fef9c3,stroke:#ca8a04,color:#000
    style E fill:#f3f4f6,stroke:#6b7280,color:#000
```

### Die ersten Befehle

| Befehl | Bedeutung |
| :--- | :--- |
| `pwd` | Aktuelles Verzeichnis anzeigen (**p**rint **w**orking **d**irectory) |
| `ls` | Dateien und Ordner anzeigen (**l**i**s**t) |
| `cd Downloads` | In ein Verzeichnis wechseln (**c**hange **d**irectory) |
| `cd ..` | Eine Ebene nach oben |
| `cd ~` | Zum Home-Verzeichnis |

```bash
pwd             # /home/noemi
ls              # Documents  Downloads
cd Downloads    # wechselt in den Ordner
pwd             # /home/noemi/Downloads
```

Mehr zu diesen Befehlen: {doc}`navigation`, {doc}`ordner` und {doc}`dateien`.

```{tip}
- **Tab** vervollständigt Datei- und Ordnernamen.
- **Pfeil hoch** holt den letzten Befehl zurück.
- Hilfe zu jedem Befehl: `man ls` (beenden mit `q`).
```

---

(linux-rechte)=
## Dateirechte

Jede Datei hat Rechte für drei Gruppen: **Besitzer** (Owner), **Gruppe** (Group) und **Andere** (Others).

| Zeichen | Bedeutung | Wert |
| :---: | :--- | :---: |
| {bdg-success}`r` | Lesen (read) | 4 |
| {bdg-warning}`w` | Schreiben (write) | 2 |
| {bdg-danger}`x` | Ausführen (execute) | 1 |

### Rechte lesen

```text
-rwxr-xr-x
```

| Teil | Bedeutung |
| :---: | :--- |
| `-` | Datei (`d` wäre ein Verzeichnis) |
| `rwx` | Besitzer: lesen, schreiben, ausführen |
| `r-x` | Gruppe: lesen und ausführen |
| `r-x` | Andere: lesen und ausführen |

### Zahlen statt Buchstaben

Die Werte werden pro Gruppe addiert:

```text
rwx = 4 + 2 + 1 = 7
r-x = 4 + 0 + 1 = 5
r-x = 4 + 0 + 1 = 5
```

Daraus ergibt sich:

```bash
chmod 755 skript.sh
```

| Zahl | Rechte | Typischer Einsatz |
| :---: | :---: | :--- |
| `644` | `rw-r--r--` | normale Dateien |
| `755` | `rwxr-xr-x` | Skripte und Programme |
| `600` | `rw-------` | private Dateien (z. B. SSH-Schlüssel) |

```{danger}
`777` gibt **allen** Benutzern vollen Zugriff. Nur in Ausnahmefällen verwenden.
```

Alles Weitere (`chown`, `umask`, Sonderrechte): {doc}`dateirechte`.

---

## Merksätze

```{admonition} Das Wichtigste in Kürze
:class: important

1. Linux = **Kernel**, eine Distribution = Kernel + Programme.
2. **Alles ist eine Datei**, auch Geräte (`/dev`) und Prozesse (`/proc`).
3. Das Dateisystem ist ein Baum ab `/`. `/root` ist **nicht** `/`.
4. Terminal = Fenster, Shell = Interpreter (meist Bash).
5. Rechte: `r`=4, `w`=2, `x`=1, vergeben für Besitzer, Gruppe, Andere.
6. `chmod 755` für Skripte, `777` vermeiden.
```

---

## Weiterführend (offizielle Dokumentation)

- [Linux Kernel Documentation](https://www.kernel.org/doc/html/latest/): offizielle Doku zum Kernel
- [Filesystem Hierarchy Standard](https://refspecs.linuxfoundation.org/fhs.shtml): Aufbau der Verzeichnisse
- [man-pages (man7.org)](https://man7.org/linux/man-pages/): Referenz zu Befehlen und Systemaufrufen
- [GNU Bash Reference Manual](https://www.gnu.org/software/bash/manual/): Shell im Detail
- [GNU Coreutils Manual](https://www.gnu.org/software/coreutils/manual/): `ls`, `cd`, `chmod` und weitere
