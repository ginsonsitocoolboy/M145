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


## Packet Tracer - VLAN Configuration

### Ziel

In dieser Übung wurden VLANs auf mehreren Switches erstellt, benannt und den richtigen Ports zugewiesen. Danach wurde getestet, ob PCs im gleichen VLAN miteinander kommunizieren können.

---

### VLANs erstellen

Auf S1, S2 und S3 wurden die gleichen VLANs erstellt:

| VLAN | Name              |
| ---- | ----------------- |
| 10   | Faculty/Staff     |
| 20   | Students          |
| 30   | Guest(Default)    |
| 99   | Management&Native |
| 150  | VOICE             |

Zur Kontrolle wurde der Befehl verwendet:

```bash
show vlan brief
```

---

### Ports zuweisen

Auf S2 und S3 wurden die aktiven Ports den passenden VLANs zugewiesen:

| Port  | VLAN    | Zweck         |
| ----- | ------- | ------------- |
| F0/11 | VLAN 10 | Faculty/Staff |
| F0/18 | VLAN 20 | Students      |
| F0/6  | VLAN 30 | Guest         |

Die Ports wurden als Access Ports konfiguriert.

---

### Voice VLAN

Auf S3 wurde zusätzlich auf F0/11 das Voice VLAN 150 konfiguriert, weil dort ein IP Phone angeschlossen ist. Der PC bleibt im VLAN 10, das Telefon verwendet VLAN 150.

---

### Verbindungstest

Danach wurde ein Ping von PC1 zu PC4 getestet. Beide PCs sind im VLAN 10, aber der Ping war nicht erfolgreich.

Der Grund ist, dass PC1 und PC4 an unterschiedlichen Switches angeschlossen sind. Die Verbindung zwischen den Switches ist noch kein Trunk und transportiert deshalb VLAN 10 nicht. Der Port Gig0/1 ist noch in VLAN 1.

---

### Lösung

Damit der Ping funktionieren kann, müssen die Verbindungen zwischen den Switches als Trunk Ports konfiguriert werden. Erst dann können mehrere VLANs zwischen den Switches übertragen werden.

---

### Fazit

Ich habe gelernt, wie man VLANs erstellt, Ports VLANs zuweist und warum VLANs über mehrere Switches nur mit Trunk Ports funktionieren.

## Packet Tracer - Configure Trunks

### Ziel

In dieser Übung wurden Trunk Ports zwischen den Switches konfiguriert, damit mehrere VLANs über die Switch-Verbindungen übertragen werden können.

---

### Ausgangslage

Die VLANs waren bereits auf den Switches vorhanden. Auf S2 und S3 waren die PC Ports den richtigen VLANs zugewiesen:

| VLAN | PCs         | Ports |
| ---- | ----------- | ----- |
| 10   | PC1 und PC4 | F0/11 |
| 20   | PC2 und PC5 | F0/18 |
| 30   | PC3 und PC6 | F0/6  |

Vor der Trunk Konfiguration konnten PCs im gleichen VLAN auf verschiedenen Switches nicht miteinander kommunizieren. Der Grund war, dass die Verbindungen zwischen den Switches noch normale Access Ports in VLAN 1 waren.

---

### Trunk Konfiguration auf S1

Auf S1 wurden die Ports G0/1 und G0/2 als Trunk Ports konfiguriert. Zusätzlich wurde VLAN 99 als Native VLAN gesetzt.

```bash
enable
configure terminal
interface range g0/1 - 2
switchport mode trunk
switchport trunk native vlan 99
end
```

Nach dieser Konfiguration erschien zuerst eine Native VLAN Mismatch Meldung, weil S2 und S3 noch VLAN 1 als Native VLAN verwendeten.

---

### Native VLAN auf S2 und S3 korrigieren

Damit alle Switches dasselbe Native VLAN verwenden, wurde VLAN 99 auch auf den Trunk Ports von S2 und S3 gesetzt.

S2:

```bash
enable
configure terminal
interface g0/1
switchport trunk native vlan 99
end
```

S3:

```bash
enable
configure terminal
interface g0/2
switchport trunk native vlan 99
end
```

---

### Kontrolle

Die Trunk Konfiguration wurde mit folgendem Befehl überprüft:

```bash
show interface trunk
```

Dabei wurde kontrolliert, ob die Trunk Ports aktiv sind und ob VLAN 99 als Native VLAN eingetragen ist.

Zusätzlich kann man mit folgendem Befehl prüfen, ob der Port wirklich als Trunk arbeitet:

```bash
show interface g0/1 switchport
```

---

### Verbindungstest

Nach der Trunk Konfiguration konnten PCs im gleichen VLAN wieder miteinander kommunizieren:

* PC1 kann PC4 erreichen
* PC2 kann PC5 erreichen
* PC3 kann PC6 erreichen

Pings zwischen verschiedenen VLANs funktionieren nicht, weil dafür ein Router oder Layer 3 Switch nötig wäre.

---

### Antworten auf die Fragen

**Warum funktionieren Pings trotz Native VLAN Mismatch zuerst teilweise?**
Die VLANs 10, 20 und 30 werden als getaggter Traffic über den Trunk übertragen. Die Native VLAN Mismatch Meldung betrifft vor allem ungetaggten Traffic.

**Welche VLANs dürfen über den Trunk?**
Standardmässig sind die VLANs 1 bis 1005 erlaubt. Damit können auch VLAN 10, 20, 30, 99 und 150 über den Trunk übertragen werden.

**Warum ist G0/1 auf S2 nicht mehr VLAN 1 zugeordnet?**
G0/1 ist jetzt ein Trunk Port. Ein Trunk Port ist kein normaler Access Port mehr, sondern transportiert mehrere VLANs gleichzeitig.

---

### Fazit

Ich habe gelernt, dass VLANs über mehrere Switches nur funktionieren, wenn die Switch-Verbindungen als Trunk Ports konfiguriert sind. Ausserdem muss das Native VLAN auf beiden Seiten eines Trunks gleich sein.

## Packet Tracer - Implement VLANs and Trunking

### Ziel

In dieser Übung wurden VLANs erstellt, Access Ports konfiguriert und Trunk Verbindungen zwischen den Switches eingerichtet. Zusätzlich wurde ein Voice VLAN und ein Management VLAN konfiguriert.

---

### VLAN Konfiguration

Auf allen drei Switches wurden folgende VLANs erstellt:

| VLAN | Name       |
| ---- | ---------- |
| 10   | Admin      |
| 20   | Accounts   |
| 30   | HR         |
| 40   | Voice      |
| 99   | Management |
| 100  | Native     |

Die VLAN Konfiguration wurde mit folgendem Befehl überprüft:

```bash
show vlan brief
```

---

### Access Ports konfigurieren

Auf SWB und SWC wurden die Ports den passenden VLANs zugewiesen.

| Port | VLAN    |
| ---- | ------- |
| F0/1 | VLAN 10 |
| F0/2 | VLAN 20 |
| F0/3 | VLAN 30 |

Zusätzlich wurde auf SWC der Port F0/4 für PC7 in VLAN 10 konfiguriert.

---

### Voice VLAN konfigurieren

Da an SWC F0/4 zusätzlich ein IP Telefon angeschlossen ist, wurde dort das Voice VLAN 40 gesetzt.

```bash
interface f0/4
switchport voice vlan 40
```

Dadurch kann derselbe Port gleichzeitig Datenverkehr für den PC und Sprachverkehr für das Telefon transportieren.

---

### Management VLAN konfigurieren

Auf allen Switches wurde VLAN 99 als Management VLAN verwendet.

| Switch | IP Adresse     |
| ------ | -------------- |
| SWA    | 192.168.99.252 |
| SWB    | 192.168.99.253 |
| SWC    | 192.168.99.254 |

Die Management Interfaces wurden über Interface VLAN 99 konfiguriert.

---

### Statischer Trunk

Zwischen SWA und SWB wurde ein statischer Trunk eingerichtet.

```bash
interface g0/1
switchport mode trunk
switchport nonegotiate
switchport trunk native vlan 100
```

Dabei wurde DTP deaktiviert und VLAN 100 als Native VLAN gesetzt.

---

### Dynamischer Trunk

Zwischen SWA und SWC wurde ein dynamischer Trunk eingerichtet.

```bash
interface g0/2
switchport mode dynamic desirable
switchport trunk native vlan 100
```

Dadurch konnte automatisch ein Trunk mit SWC ausgehandelt werden.

---

### Kontrolle

Die Trunk Konfiguration wurde mit folgendem Befehl überprüft:

```bash
show interfaces trunk
```

Zusätzlich wurde mit Ping getestet, ob Geräte im gleichen VLAN miteinander kommunizieren können.

Beispiele:

* PC1 kann PC4 und PC7 erreichen
* PC2 kann PC5 erreichen
* PC3 kann PC6 erreichen

Pings zwischen unterschiedlichen VLANs funktionieren nicht, da kein Routing zwischen den VLANs konfiguriert wurde.

---

### Fazit

Ich habe gelernt, wie VLANs erstellt und Access Ports zugewiesen werden. Ausserdem habe ich statische und dynamische Trunks konfiguriert und verstanden, wie VLAN Verkehr zwischen mehreren Switches übertragen wird.


## Packet Tracer - Inter-VLAN Routing Challenge

### Ziel

In dieser Übung wurde Inter-VLAN Routing mit einem Router-on-a-Stick aufgebaut. Dazu wurden VLANs erstellt, Access Ports konfiguriert, ein Trunk eingerichtet und auf dem Router Subinterfaces für die einzelnen VLANs erstellt.

---

### VLAN Konfiguration

Auf dem Switch S1 wurden folgende VLANs erstellt:

| VLAN | Name           |
| ---- | -------------- |
| 10   | Faculty/Staff  |
| 20   | Students       |
| 30   | Guest(Default) |
| 88   | Native         |
| 99   | Management     |

Die VLANs wurden anschliessend den passenden Ports zugewiesen.

| VLAN    | Ports         |
| ------- | ------------- |
| VLAN 10 | F0/11 - F0/17 |
| VLAN 20 | F0/18 - F0/24 |
| VLAN 30 | F0/6 - F0/10  |

Alle Ports wurden als Access Ports konfiguriert.

---

### Management VLAN

Für die Verwaltung des Switches wurde VLAN 99 verwendet.

Die virtuelle Management Schnittstelle wurde wie folgt konfiguriert:

```bash
interface vlan 99
ip address 172.17.99.10 255.255.255.0
no shutdown
```

Zusätzlich wurde das Default Gateway gesetzt:

```bash
ip default-gateway 172.17.99.1
```

---

### Trunk Konfiguration

Die Verbindung zwischen S1 und R1 wurde als statischer Trunk konfiguriert.

```bash
interface g0/1
switchport mode trunk
switchport trunk native vlan 88
```

Dabei wurde VLAN 88 als Native VLAN verwendet.

---

### Nicht verwendete Ports deaktivieren

Nicht benutzte Ports wurden aus Sicherheitsgründen deaktiviert.

```bash
interface range f0/1 - 5
shutdown
```

Zusätzlich wurde G0/2 deaktiviert.

---

### Router-on-a-Stick Konfiguration

Auf R1 wurden mehrere Subinterfaces erstellt.

| Interface | VLAN    | IP Adresse  |
| --------- | ------- | ----------- |
| G0/1.10   | VLAN 10 | 172.17.10.1 |
| G0/1.20   | VLAN 20 | 172.17.20.1 |
| G0/1.30   | VLAN 30 | 172.17.30.1 |
| G0/1.88   | VLAN 88 | 172.17.88.1 |
| G0/1.99   | VLAN 99 | 172.17.99.1 |

Beispiel einer Subinterface Konfiguration:

```bash
interface g0/1.10
encapsulation dot1Q 10
ip address 172.17.10.1 255.255.255.0
```

Für das Native VLAN wurde folgende Konfiguration verwendet:

```bash
interface g0/1.88
encapsulation dot1Q 88 native
ip address 172.17.88.1 255.255.255.0
```

---

### Verbindungstest

Nach der Konfiguration wurden verschiedene Ping Tests durchgeführt.

Beispiele:

* PC1 konnte PC2 und PC3 erreichen
* Die PCs konnten den Switch S1 erreichen
* Die PCs konnten den Router R1 erreichen
* Die VLANs konnten über den Router miteinander kommunizieren

Dadurch wurde bestätigt, dass das Inter-VLAN Routing korrekt funktioniert.

---

### Fazit

Ich habe gelernt, wie Inter-VLAN Routing mit Router-on-a-Stick funktioniert. Ausserdem habe ich VLANs, Trunks und Router Subinterfaces konfiguriert und getestet.
