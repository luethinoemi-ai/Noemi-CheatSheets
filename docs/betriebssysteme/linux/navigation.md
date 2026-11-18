# Navigation

Navigation gehört zu den wichtigsten Grundlagen in Linux. Mit den folgenden Befehlen kannst du deinen aktuellen Standort anzeigen, Ordnerinhalte auflisten und zwischen Verzeichnissen wechseln.

---

## pwd

Zeigt das aktuelle Arbeitsverzeichnis an.

```bash
pwd
```

Beispiel:

```bash
pwd
```

Ausgabe:

```text
/home/user/Projects
```

---

## ls

Zeigt den Inhalt eines Verzeichnisses an.

```bash
ls
```

Beispiel:

```bash
ls
```

Mögliche Ausgabe:

```text
Dokumente
Downloads
Projekte
```

---

## ls -la

Zeigt alle Dateien und Verzeichnisse an, einschliesslich versteckter Dateien.

```bash
ls -la
```

Beispiel:

```bash
ls -la
```

Mögliche Ausgabe:

```text
.
..
.git
.gitignore
README.md
```

```{note}
Dateien und Verzeichnisse, die mit einem Punkt (`.`) beginnen, sind standardmässig versteckt.
```

---

## cd

Wechselt in ein anderes Verzeichnis.

```bash
cd Ordnername
```

Beispiel:

```bash
cd Projects
```

---

## cd ..

Wechselt eine Ebene nach oben.

```bash
cd ..
```

Beispiel:

```text
/home/user/Projects
```

wird zu:

```text
/home/user
```

---

## cd ~

Wechselt in das Home-Verzeichnis des aktuellen Benutzers.

```bash
cd ~
```

Beispiel:

```text
/home/user
```

---

## Absolute und relative Pfade

### Absoluter Pfad

Beginnt immer beim Root-Verzeichnis `/`.

```bash
cd /home/user/Projects
```

### Relativer Pfad

Bezieht sich auf das aktuelle Verzeichnis.

```bash
cd Projects
```

```{note}
Absolute Pfade funktionieren unabhängig vom aktuellen Standort. Relative Pfade hängen vom aktuellen Verzeichnis ab.
```
