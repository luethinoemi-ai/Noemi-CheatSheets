# Prozesse

Prozesse sind laufende Programme oder Befehle. Linux weist jedem Prozess eine eindeutige Prozess-ID (PID) zu.

Mit den folgenden Befehlen lassen sich Prozesse anzeigen, überwachen und beenden.

---

## ps

Zeigt Informationen über laufende Prozesse an.

```bash
ps -ef
```

Beispiel:

```bash
ps -ef | grep main.py
```

Zeigt Prozesse an, die `main.py` enthalten.

```{note}
Jeder Prozess besitzt eine PID (Process ID), die zum Identifizieren und Beenden eines Prozesses verwendet werden kann.
```

---

## kill

Beendet einen laufenden Prozess anhand seiner PID.

```bash
kill PID
```

Beispiel:

```bash
kill 4809
```

Beendet den Prozess mit der PID `4809`.

Falls ein Prozess nicht reagiert:

```bash
kill -9 4809
```

```{warning}
Die Option `-9` beendet einen Prozess sofort. Dabei kann der Prozess keine Aufräumarbeiten oder das Speichern von Daten mehr durchführen.
```

---

## top

Zeigt laufende Prozesse und die aktuelle Systemauslastung in Echtzeit an.

```bash
top
```

Beispiel:

```bash
top
```

Angezeigt werden unter anderem:

- CPU-Auslastung
- Arbeitsspeicher (RAM)
- Laufende Prozesse
- Prozess-IDs (PID)

```{note}
Mit der Taste `q` wird `top` beendet.
```

---

## Prozessinformationen finden

Oft wird `ps` zusammen mit `grep` verwendet, um bestimmte Prozesse zu suchen.

```bash
ps -ef | grep python
```

Beispielausgabe:

```text
noemi     4809  1  0 14:20 ?  00:00:01 python main.py
```

Hier ist:

| Wert | Bedeutung |
| :--- | :--- |
| `noemi` | Benutzer |
| `4809` | Prozess-ID (PID) |
| `python main.py` | Gestartetes Programm |

---

## Häufige Befehle

| Befehl | Bedeutung |
| :--- | :--- |
| `ps -ef` | Alle Prozesse anzeigen |
| `ps -ef \| grep name` | Nach einem Prozess suchen |
| `kill PID` | Prozess beenden |
| `kill -9 PID` | Prozess sofort beenden |
| `top` | Prozesse und Systemauslastung anzeigen |
