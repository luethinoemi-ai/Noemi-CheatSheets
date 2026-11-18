# Netzwerk

Wichtige Befehle zur Analyse, Überprüfung und Verwaltung von Netzwerkverbindungen unter Linux.

---

## ping

Prüft, ob ein Host oder Server erreichbar ist.

```bash
ping google.ch
```

Beispiel:

```bash
ping 8.8.8.8
```

Sendet Testpakete an den öffentlichen DNS-Server von Google.

```{note}
Mit `Strg + C` wird der laufende Ping beendet.
```

---

## ssh

Stellt eine verschlüsselte Verbindung zu einem anderen System her.

```bash
ssh user@server
```

Beispiel:

```bash
ssh noemi@192.168.1.100
```

Verbindet sich mit dem Benutzer `noemi` auf dem Zielsystem.

```{note}
SSH wird häufig für die Fernverwaltung von Linux-Servern verwendet.
```

---

## ip

Zeigt Netzwerkinformationen und IP-Adressen an.

```bash
ip addr
```

Beispiel:

```bash
ip addr show
```

Zeigt alle verfügbaren Netzwerkinterfaces und deren Konfiguration an.

---

## hostname

Zeigt den Hostnamen des aktuellen Systems an.

```bash
hostname
```

Beispiel:

```bash
hostname
```

Ausgabe:

```text
server01
```

---

## nslookup

Fragt DNS-Informationen zu einem Hostnamen ab.

```bash
nslookup google.ch
```

Beispiel:

```bash
nslookup github.com
```

Zeigt die zugehörigen DNS-Einträge und IP-Adressen an.

---

## traceroute

Zeigt den Weg der Netzwerkpakete bis zum Zielsystem.

```bash
traceroute google.ch
```

Beispiel:

```bash
traceroute 8.8.8.8
```

Hilft bei der Analyse von Netzwerkproblemen und Verbindungswegen.

```{note}
Auf einigen Distributionen muss `traceroute` zuerst installiert werden.
```

---

## netstat

Zeigt Netzwerkverbindungen und offene Ports an.

```bash
netstat -tuln
```

Beispiel:

```bash
netstat -an
```

Listet aktive Verbindungen und offene Ports auf.

```{note}
Auf modernen Linux-Systemen wird häufig `ss` anstelle von `netstat` verwendet.
```

---

## ss

Moderner Ersatz für `netstat`.

```bash
ss -tuln
```

Beispiel:

```bash
ss -tuln
```

Zeigt offene TCP- und UDP-Ports an.

---

## curl

Ruft Daten von Webseiten oder APIs ab.

```bash
curl https://example.com
```

Beispiel:

```bash
curl https://api.github.com
```

Zeigt die Antwort der GitHub-API direkt im Terminal an.

---

## wget

Lädt Dateien aus dem Internet herunter.

```bash
wget https://example.com/datei.zip
```

Beispiel:

```bash
wget https://example.com/setup.zip
```

Speichert die Datei im aktuellen Verzeichnis.

```{note}
Mit `wget` können Downloads bei Bedarf fortgesetzt werden.
```
