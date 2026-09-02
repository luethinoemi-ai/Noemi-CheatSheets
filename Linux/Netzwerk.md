# Netzwerk

Wichtige Linux-Befehle zur Analyse und Verwaltung von Netzwerken.

---

## ping

```bash
ping google.ch
```

### Bedeutung

Prüft, ob ein Host oder Server erreichbar ist.

### Beispiel

```bash
ping 8.8.8.8
```

Sendet Testpakete an den DNS-Server von Google.

---

## ssh

```bash
ssh user@server
```

### Bedeutung

Stellt eine verschlüsselte Verbindung zu einem anderen Rechner her.

### Beispiel

```bash
ssh noemi@192.168.1.100
```

Verbindet sich mit dem Benutzer `noemi` auf dem Zielsystem.

---

## ip

```bash
ip addr
```

### Bedeutung

Zeigt die Netzwerkinterfaces und IP-Adressen an.

### Beispiel

```bash
ip addr show
```

Zeigt alle verfügbaren Netzwerkadapter.

---

## hostname

```bash
hostname
```

### Bedeutung

Zeigt den Namen des aktuellen Computers an.

### Beispiel

```bash
hostname
```

Ausgabe:

```text
server01
```

---

## nslookup

```bash
nslookup google.ch
```

### Bedeutung

Fragt DNS-Informationen ab.

### Beispiel

```bash
nslookup github.com
```

Zeigt die zugehörige IP-Adresse an.

---

## traceroute

```bash
traceroute google.ch
```

### Bedeutung

Zeigt den Weg der Pakete bis zum Zielserver.

### Beispiel

```bash
traceroute 8.8.8.8
```

Hilft bei der Fehlersuche im Netzwerk.

---

## netstat

```bash
netstat -tuln
```

### Bedeutung

Zeigt offene Netzwerkverbindungen und Ports an.

### Beispiel

```bash
netstat -an
```

Listet aktive Verbindungen auf.

---

## ss

```bash
ss -tuln
```

### Bedeutung

Moderner Ersatz für `netstat`.

### Beispiel

```bash
ss -tuln
```

Zeigt offene TCP- und UDP-Ports an.

---

## curl

```bash
curl https://example.com
```

### Bedeutung

Ruft Daten von Webseiten oder APIs ab.

### Beispiel

```bash
curl https://api.github.com
```

Zeigt die Antwort der GitHub-API an.

---

## wget

```bash
wget https://example.com/datei.zip
```

### Bedeutung

Lädt Dateien aus dem Internet herunter.

### Beispiel

```bash
wget https://example.com/setup.zip
```

Speichert die Datei lokal.

---

## Merken für die Praxis

| Befehl | Zweck |
|---------|---------|
| ping | Erreichbarkeit testen |
| ssh | Remote-Verbindung herstellen |
| ip | Netzwerkinformationen anzeigen |
| hostname | Gerätenamen anzeigen |
| nslookup | DNS-Abfragen durchführen |
| traceroute | Netzwerkpfad analysieren |
| netstat | Verbindungen anzeigen |
| ss | Offene Ports anzeigen |
| curl | Webseiten und APIs abrufen |
| wget | Dateien herunterladen |
