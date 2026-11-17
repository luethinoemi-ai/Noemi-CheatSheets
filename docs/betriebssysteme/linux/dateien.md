# Dateien

Befehle zum Erstellen, Anzeigen und Bearbeiten von Dateien im Terminal.

---

## Übersicht

| Befehl | Bedeutung |
| :--- | :--- |
| `touch` | Erstellt eine leere Datei |
| `nano` | Bearbeitet eine Datei im Terminal |
| `cat` | Zeigt den ganzen Inhalt an |
| `less` | Zeigt den Inhalt mit Scrollfunktion an |
| `head` | Zeigt die ersten Zeilen |
| `tail` | Zeigt die letzten Zeilen |
| `cp` | Kopiert eine Datei |
| `mv` | Verschiebt oder benennt eine Datei um |
| `rm` | Löscht eine Datei |

---

## Erstellen und bearbeiten

### touch

Erstellt eine neue leere Datei.

```bash
touch test.txt
```

```{note}
Existiert die Datei schon, ändert `touch` nur das Änderungsdatum. Der Inhalt bleibt erhalten.
```

### nano

Bearbeitet eine Datei im Terminal. Gibt es sie noch nicht, wird sie beim Speichern erstellt.

```bash
nano test.txt
```

| Tastenkombination | Aktion |
| :--- | :--- |
| `Strg + O`, dann `Enter` | Speichern |
| `Strg + X` | Beenden |
| `Strg + W` | Suchen |

---

## Anzeigen

### cat

Zeigt den ganzen Inhalt einer Datei an.

```bash
cat test.txt
```

```{tip}
`cat` eignet sich für kurze Dateien. Bei langen Dateien ist `less` besser.
```

### less

Zeigt eine Datei seitenweise mit Scrollfunktion an.

```bash
less test.txt
```

| Taste | Aktion |
| :--- | :--- |
| `Pfeiltasten` oder `Leertaste` | Scrollen |
| `/wort` | Nach einem Wort suchen |
| `q` | Beenden |

### head

Zeigt die ersten 10 Zeilen einer Datei.

```bash
head test.txt
```

Eine andere Anzahl an Zeilen gibst du mit `-n` an:

```bash
head -n 5 test.txt
```

### tail

Zeigt die letzten 10 Zeilen einer Datei.

```bash
tail test.txt
```

Auch hier funktioniert `-n`:

```bash
tail -n 5 test.txt
```

Mit `-f` wird die Datei live verfolgt. Neue Zeilen erscheinen sofort. Beenden mit `Strg + C`.

```bash
tail -f /var/log/syslog
```

```{tip}
`tail -f` wird oft bei Log-Dateien benutzt, um zu sehen, was gerade passiert.
```

---

## Kopieren, verschieben, löschen

### cp

Kopiert eine Datei.

```bash
cp test.txt kopie.txt
```

### mv

Verschiebt eine Datei in einen anderen Ordner oder benennt sie um.

```bash
mv test.txt Dokumente/
mv test.txt neu.txt
```

### rm

Löscht eine Datei.

```bash
rm test.txt
```

```{warning}
Gelöschte Dateien landen **nicht** im Papierkorb. Sie sind weg. Mit `rm -i` fragt Linux vor dem Löschen nach.
```

```{attention}
Mit `mv` und `cp` kann eine Datei mit gleichem Namen ohne Nachfrage überschrieben werden. Mit der Option `-i` fragt Linux vorher nach.
```
