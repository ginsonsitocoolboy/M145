## Packet Tracer - Navigate the IOS 

### Part 1: Verbindung und CLI

Ich habe PC1 mit S1 über ein Console Kabel verbunden. Danach habe ich im PC das Terminal geöffnet und die Standardeinstellungen verwendet (9600 bits per second). Nach Enter erschien der Prompt S1>.

Mit ? habe ich alle Befehle angezeigt. Der Befehl mit C ist connect. Mit t? und te? habe ich gesehen, wie die Hilfe genauer wird.

---

### Part 2: Modi

Ich habe mit enable in den privilegierten Modus gewechselt (S1#). Mit configure terminal bin ich in den Config Mode gegangen (S1(config)#). Danach bin ich mit exit wieder zurück.

---

### Part 3: Uhr

Mit show clock habe ich die Zeit angezeigt. Mit clock set 15:00:00 31 Jan 2035 habe ich die Uhr gesetzt und danach wieder überprüft.

---

### Fazit

Ich habe gelernt, wie man sich im IOS bewegt, Befehle eingibt, Hilfe benutzt und einfache Einstellungen macht.



## Packet Tracer - Configure Initial Switch Settings 

### Part 1: Default Konfiguration prüfen

Ich habe den Switch geöffnet, in den privilegierten Modus gewechselt (enable) und mit show running-config die aktuelle Konfiguration angeschaut.

Der Switch hat 24 FastEthernet Ports und 2 Gigabit Ports. Die vty lines gehen von 0 bis 15. Die startup-config war nicht vorhanden, da noch nichts gespeichert wurde.

---

### Part 2: Grundkonfiguration

Ich habe den Switchnamen mit hostname S1 gesetzt.

Danach habe ich die Console gesichert mit:

* password letmein
* login (damit das Passwort abgefragt wird)

Ich habe ein enable password gesetzt (c1$c0) und danach ein sicheres enable secret (itsasecret).

Mit show run habe ich gesehen, dass das enable secret verschlüsselt ist.

Danach habe ich mit service password-encryption alle Passwörter verschlüsselt.

---

### Part 3: Banner

Ich habe einen MOTD Banner gesetzt, der beim Login angezeigt wird und unbefugte Benutzer warnt.

---

### Part 4: Speichern

Ich habe die Konfiguration mit copy running-config startup-config gespeichert.

---

### Part 5: S2

Ich habe die gleiche Konfiguration auf S2 gemacht, nur mit dem Namen S2.

---

### Fazit

Ich habe gelernt, wie man einen Switch grundlegend konfiguriert, absichert und die Konfiguration speichert.


## Packet Tracer - Implement Basic Connectivity e

### Part 1: Switch konfigurieren

Ich habe auf S1 und S2 den Hostname gesetzt (S1 und S2). Danach habe ich die Console mit dem Passwort cisco gesichert und ein enable secret Passwort class gesetzt. Anschliessend habe ich einen MOTD Banner gesetzt und die Konfiguration gespeichert.

---

### Part 2: PCs konfigurieren

Ich habe die IP Adressen eingetragen:

* PC1: 192.168.1.1 / 255.255.255.0
* PC2: 192.168.1.2 / 255.255.255.0

---

### Part 3: Switch Management IP

Ich habe auf beiden Switches das Interface VLAN 1 konfiguriert:

* S1: 192.168.1.253 / 255.255.255.0
* S2: 192.168.1.254 / 255.255.255.0

Mit no shutdown habe ich das Interface aktiviert.

---

### Verbindung testen

Ich habe von beiden PCs alle Geräte angepingt (PC1, PC2, S1, S2). Die Verbindungen waren erfolgreich.

---

### Fazit

Ich habe gelernt, wie man Switches und PCs konfiguriert, IP Adressen setzt und die Verbindung mit ping überprüft.
