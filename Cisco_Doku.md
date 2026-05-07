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



## Packet Tracer - Identify MAC and IP Addresses (Doku)

### Ziel

In dieser Übung habe ich den Datenverkehr (PDU) im Simulation Mode analysiert und beobachtet, wie sich MAC und IP Adressen im Netzwerk verhalten.

---

### Vorgehen

Ich habe einen Ping von 172.16.31.5 zu 172.16.31.2 ausgeführt und das Paket Schritt für Schritt verfolgt (PC → Switch → Hub → Ziel-PC). Dabei habe ich bei jedem Gerät die MAC und IP Adressen notiert.

---

### Tabelle (lokale Kommunikation)

| Gerät       | Dest MAC       | Src MAC        | Src IP      | Dest IP     |
| ----------- | -------------- | -------------- | ----------- | ----------- |
| 172.16.31.5 | 000C.85CC.1DA7 | 00D0.D311.C788 | 172.16.31.5 | 172.16.31.2 |
| Switch1     | 000C.85CC.1DA7 | 00D0.D311.C788 | N/A         | N/A         |
| Hub         | N/A            | N/A            | N/A         | N/A         |
| 172.16.31.2 | 00D0.D311.C788 | 000C.85CC.1DA7 | 172.16.31.2 | 172.16.31.5 |

---

### Beobachtungen (lokal)

* Die IP Adressen bleiben gleich
* Die MAC Adressen bleiben im gleichen Netzwerk gleich
* Der Switch leitet das Paket weiter ohne Änderung
* Der Hub sendet das Paket an alle Geräte
* Beim Zielgerät werden die Adressen für die Antwort vertauscht

---

### Remote Kommunikation

Beim Ping zu einem anderen Netzwerk (z.B. 10.10.10.2) habe ich gesehen:

* Die IP Adresse bleibt gleich
* Die MAC Adresse zeigt zuerst auf den Router (Gateway)
* Beim Router ändern sich die MAC Adressen

---

### Geräte Verhalten

* Switch: leitet Pakete gezielt weiter
* Hub: sendet Pakete an alle Ports
* Router: ändert MAC Adressen zwischen Netzwerken

---

### Reflection 

* Hub verliert keine Daten, sondern verteilt alles
* Switch repliziert keine falschen Pakete
* MAC Adressen gelten nur lokal
* IP Adressen bleiben gleich
* Beim Ping Reply werden Source und Destination vertauscht

---

### Fazit

Ich habe gelernt, wie Daten im Netzwerk übertragen werden und den Unterschied zwischen MAC und IP Adressen sowie zwischen lokaler und externer Kommunikation verstanden.


## Packet Tracer - Subnetting und Basic Connectivity

### Ziel

In dieser Aufgabe wurde das Netzwerk 192.168.0.0/24 in mehrere gleich grosse Subnetze aufgeteilt. Danach wurden Router, Switches und PCs mit den passenden IP Adressen konfiguriert und die Verbindung mit Ping getestet.

---

### Subnetting

Für LAN-A werden mindestens 50 Hosts benötigt, für LAN-B mindestens 40 Hosts. Zusätzlich sollen zwei weitere Subnetze für spätere Erweiterungen frei bleiben. Deshalb werden insgesamt mindestens 4 Subnetze benötigt.

Als passende Subnetzmaske wurde /26 gewählt.

* Subnetzmaske: 255.255.255.192
* Hosts pro Subnetz: 62
* Anzahl Subnetze: 4

| Subnetz   | Netzwerkadresse  | Hostbereich                   | Broadcast     |
| --------- | ---------------- | ----------------------------- | ------------- |
| LAN-A     | 192.168.0.0/26   | 192.168.0.1 - 192.168.0.62    | 192.168.0.63  |
| LAN-B     | 192.168.0.64/26  | 192.168.0.65 - 192.168.0.126  | 192.168.0.127 |
| Reserve 1 | 192.168.0.128/26 | 192.168.0.129 - 192.168.0.190 | 192.168.0.191 |
| Reserve 2 | 192.168.0.192/26 | 192.168.0.193 - 192.168.0.254 | 192.168.0.255 |

---

### Verwendete IP Adressen

| Gerät          | Interface | IP Adresse    | Subnetzmaske    | Default Gateway |
| -------------- | --------- | ------------- | --------------- | --------------- |
| CustomerRouter | G0/0      | 192.168.0.1   | 255.255.255.192 | N/A             |
| CustomerRouter | G0/1      | 192.168.0.65  | 255.255.255.192 | N/A             |
| CustomerRouter | S0/1/0    | 209.165.201.2 | 255.255.255.252 | N/A             |
| LAN-A Switch   | VLAN 1    | 192.168.0.2   | 255.255.255.192 | 192.168.0.1     |
| LAN-B Switch   | VLAN 1    | 192.168.0.66  | 255.255.255.192 | 192.168.0.65    |
| PC-A           | NIC       | 192.168.0.62  | 255.255.255.192 | 192.168.0.1     |
| PC-B           | NIC       | 192.168.0.126 | 255.255.255.192 | 192.168.0.65    |

---

### Router Konfiguration

Auf dem CustomerRouter wurden zuerst Hostname und Passwörter gesetzt. Danach wurden die Interfaces G0/0 und G0/1 mit den IP Adressen der beiden LANs konfiguriert und aktiviert.

Verwendete Befehle:

```bash
enable
configure terminal
hostname CustomerRouter
enable secret Class123
line console 0
password Cisco123
login
exit

interface g0/0
ip address 192.168.0.1 255.255.255.192
no shutdown
exit

interface g0/1
ip address 192.168.0.65 255.255.255.192
no shutdown
exit

end
copy running-config startup-config
```

---

### Switch Konfiguration

Auf beiden LAN Switches wurde VLAN 1 als Management Interface konfiguriert. Zusätzlich wurde jeweils das richtige Default Gateway gesetzt.

LAN-A Switch:

```bash
enable
configure terminal
interface vlan 1
ip address 192.168.0.2 255.255.255.192
no shutdown
exit
ip default-gateway 192.168.0.1
end
copy running-config startup-config
```

LAN-B Switch:

```bash
enable
configure terminal
interface vlan 1
ip address 192.168.0.66 255.255.255.192
no shutdown
exit
ip default-gateway 192.168.0.65
end
copy running-config startup-config
```

---

### PC Konfiguration

Die PCs wurden über Desktop → IP Configuration konfiguriert.

PC-A:

* IP Adresse: 192.168.0.62
* Subnetzmaske: 255.255.255.192
* Default Gateway: 192.168.0.1

PC-B:

* IP Adresse: 192.168.0.126
* Subnetzmaske: 255.255.255.192
* Default Gateway: 192.168.0.65

---

### Verbindungstest

Zum Schluss wurde die Verbindung mit Ping überprüft.

Von PC-A:

```bash
ping 192.168.0.1
ping 192.168.0.126
```

Von PC-B:

```bash
ping 192.168.0.65
ping 192.168.0.62
```

Die Pings zum eigenen Gateway und zwischen PC-A und PC-B waren erfolgreich. Damit ist die Grundkonfiguration korrekt.

---

### Fazit

Das Netzwerk wurde in vier /26 Subnetze aufgeteilt. Zwei Subnetze wurden für LAN-A und LAN-B verwendet, zwei bleiben für spätere Erweiterungen frei. Router, Switches und PCs wurden passend adressiert und die Verbindung wurde erfolgreich getestet.
