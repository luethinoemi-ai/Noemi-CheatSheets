# Ordner

Verzeichnisse (Ordner) werden verwendet, um Dateien zu organisieren und zu strukturieren.

Mit den folgenden Befehlen kannst du Ordner erstellen, löschen, kopieren und verschieben.

---

## mkdir

Erstellt ein neues Verzeichnis.

```bash
mkdir test
```

Beispiel:

```bash
mkdir Projekte
```

Erstellt den Ordner `Projekte`.

```{note}
Mit der Option `-p` können mehrere Verzeichnisse gleichzeitig erstellt werden.
```

```bash
mkdir -p Schule/Linux/Befehle
```

---

## rmdir

Löscht ein leeres Verzeichnis.

```bash
rmdir test
```

Beispiel:

```bash
rmdir Projekte
```

```{warning}
`rmdir` funktioniert nur bei leeren Verzeichnissen.
```

---

## cp

Kopiert Dateien oder Verzeichnisse.

Datei kopieren:

```bash
cp a.txt b.txt
```

Beispiel:

```bash
cp bericht.txt kopie.txt
```

Verzeichnis kopieren:

```bash
cp -r Projekte Backup
```

```{note}
Für Verzeichnisse wird die Option `-r` benötigt.
```

---

## mv

Verschiebt Dateien oder Verzeichnisse oder benennt sie um.

Datei umbenennen:

```bash
mv alt.txt neu.txt
```

Beispiel:

```bash
mv Projekt Projekt_Alt
```

Verzeichnis verschieben:

```bash
mv Projekt Dokumente/
```

---

## rm

Löscht Dateien.

```bash
rm test.txt
```

Beispiel:

```bash
rm bericht.txt
```

```{warning}
Gelöschte Dateien werden normalerweise nicht in den Papierkorb verschoben.
```

---

## rm -r

Löscht ein Verzeichnis inklusive seines Inhalts.

```bash
rm -r test
```

Beispiel:

```bash
rm -r Projekte
```

Dadurch werden der Ordner `Projekte` und alle enthaltenen Dateien und Unterordner gelöscht.

```{warning}
Vor der Verwendung von `rm -r` sollte immer geprüft werden, ob das richtige Verzeichnis gelöscht wird.
```
