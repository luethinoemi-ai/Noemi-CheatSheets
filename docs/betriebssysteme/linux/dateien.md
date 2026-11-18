# Dateien

Dateien speichern Informationen wie Texte, Programme, Konfigurationen oder Protokolle.

Mit den folgenden Befehlen kannst du Dateien erstellen, bearbeiten, anzeigen, kopieren, verschieben und löschen.

---

## Übersicht

| Befehl | Bedeutung |
| :--- | :--- |
| `touch` | Erstellt eine leere Datei |
| `nano` | Bearbeitet eine Datei im Terminal |
| `cat` | Zeigt den Inhalt einer Datei an |
| `less` | Zeigt den Inhalt seitenweise an |
| `head` | Zeigt die ersten Zeilen einer Datei |
| `tail` | Zeigt die letzten Zeilen einer Datei |
| `cp` | Kopiert Dateien |
| `mv` | Verschiebt oder benennt Dateien um |
| `rm` | Löscht Dateien |

---

## Dateien erstellen und bearbeiten

### touch

Erstellt eine neue leere Datei.

```bash
touch test.txt
```

```{note}
Existiert die Datei bereits, wird sie nicht überschrieben. Stattdessen wird nur das Änderungsdatum aktualisiert.
```

### nano

Öffnet eine Datei im Terminal zur Bearbeitung.

```bash
nano test.txt
```

Wichtige Tastenkombinationen:

| Tastenkombination | Bedeutung |
| :--- | :--- |
| `Strg + O` | Speichern |
| `Enter` | Dateiname bestätigen |
| `Strg + X` | Beenden |
| `Strg + W` | Suchen |

```{note}
Existiert die Datei noch nicht, wird sie beim Speichern automatisch erstellt.
```

---

## Dateien anzeigen

### cat

Zeigt den gesamten Inhalt einer Datei an.

```bash
cat test.txt
```

```{note}
`cat` eignet sich besonders für kurze Dateien.
```

### less

Zeigt eine Datei seitenweise an.

```bash
less test.txt
```

Nützliche Tasten:

| Taste | Bedeutung |
| :--- | :--- |
| `Pfeiltasten` | Scrollen |
| `Leertaste` | Nächste Seite |
| `/wort` | Nach einem Begriff suchen |
| `q` | Beenden |

```{note}
`less` eignet sich für grosse Dateien oder Log-Dateien.
```

### head

Zeigt standardmässig die ersten 10 Zeilen einer Datei an.

```bash
head test.txt
```

Erste 5 Zeilen anzeigen:

```bash
head -n 5 test.txt
```

### tail

Zeigt standardmässig die letzten 10 Zeilen einer Datei an.

```bash
tail test.txt
```

Letzte 5 Zeilen anzeigen:

```bash
tail -n 5 test.txt
```

Datei live überwachen:

```bash
tail -f /var/log/syslog
```

```{note}
`tail -f` wird häufig verwendet, um Log-Dateien in Echtzeit zu beobachten.
```

---

## Dateien kopieren, verschieben und löschen

### cp

Kopiert eine Datei.

```bash
cp test.txt kopie.txt
```

Danach existieren beide Dateien:

```text
test.txt
kopie.txt
```

### mv

Verschiebt eine Datei oder benennt sie um.

Datei verschieben:

```bash
mv test.txt Dokumente/
```

Datei umbenennen:

```bash
mv test.txt neu.txt
```

### rm

Löscht eine Datei.

```bash
rm test.txt
```

```{warning}
Mit `rm` gelöschte Dateien landen normalerweise nicht im Papierkorb.
```

Sicherheitsabfrage vor dem Löschen:

```bash
rm -i test.txt
```

```{warning}
`cp` und `mv` können vorhandene Dateien überschreiben. Mit der Option `-i` wird vor dem Überschreiben nachgefragt.
```

```bash
cp -i test.txt ziel/
mv -i test.txt ziel/
```
