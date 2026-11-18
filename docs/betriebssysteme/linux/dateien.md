# 📄 Dateien

Dateien enthalten Informationen wie Texte, Programme oder Konfigurationen.

Mit den folgenden Befehlen kannst du Dateien erstellen, bearbeiten, anzeigen, kopieren, verschieben und löschen.

## Übersicht

| Befehl | Bedeutung |
|---------|---------|
| `touch` | Erstellt eine leere Datei |
| `nano` | Bearbeitet eine Datei |
| `cat` | Zeigt den kompletten Inhalt |
| `less` | Zeigt den Inhalt mit Scrollfunktion |
| `head` | Zeigt die ersten Zeilen |
| `tail` | Zeigt die letzten Zeilen |
| `cp` | Kopiert eine Datei |
| `mv` | Verschiebt oder benennt eine Datei um |
| `rm` | Löscht eine Datei |

---

## ✏️ Dateien erstellen und bearbeiten

### touch

Erstellt eine neue leere Datei.

```bash
touch test.txt
```

💡 **Hinweis**

Existiert die Datei bereits, wird sie nicht überschrieben. Linux aktualisiert lediglich das Änderungsdatum.

### nano

Öffnet eine Datei im Terminal zum Bearbeiten.

```bash
nano test.txt
```

Wichtige Tastenkombinationen:

| Tastenkombination | Bedeutung |
|---------|---------|
| `Strg + O` | Speichern |
| `Enter` | Dateiname bestätigen |
| `Strg + X` | Beenden |
| `Strg + W` | Suchen |

---

## 👀 Dateien anzeigen

### cat

Zeigt den gesamten Inhalt einer Datei an.

```bash
cat test.txt
```

💡 **Hinweis**

Für kurze Dateien geeignet.

### less

Zeigt den Inhalt einer Datei seitenweise an.

```bash
less test.txt
```

Nützliche Tasten:

| Taste | Bedeutung |
|---------|---------|
| `Pfeiltasten` | Scrollen |
| `Leertaste` | Eine Seite weiter |
| `/wort` | Nach einem Wort suchen |
| `q` | Beenden |

💡 **Hinweis**

`less` eignet sich besonders für grosse Dateien.

### head

Zeigt die ersten 10 Zeilen einer Datei.

```bash
head test.txt
```

Erste 5 Zeilen anzeigen:

```bash
head -n 5 test.txt
```

### tail

Zeigt die letzten 10 Zeilen einer Datei.

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

💡 **Hinweis**

`tail -f` wird oft bei Log-Dateien verwendet. Neue Einträge erscheinen automatisch auf dem Bildschirm.

---

## 📦 Dateien kopieren, verschieben und löschen

### cp

Kopiert eine Datei.

```bash
cp test.txt kopie.txt
```

Beispiel:

```text
test.txt
↓
kopie.txt
```

Es entstehen zwei Dateien.

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

⚠️ **Warnung**

Gelöschte Dateien landen nicht im Papierkorb und können meist nicht einfach wiederhergestellt werden.

Für eine Sicherheitsabfrage:

```bash
rm -i test.txt
```

⚠️ **Achtung**

`cp` und `mv` können Dateien mit gleichem Namen überschreiben.

Für eine Sicherheitsabfrage:

```bash
cp -i test.txt ziel/
mv -i test.txt ziel/
```
