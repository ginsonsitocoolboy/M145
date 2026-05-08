# Antworten zur Netzwerkdokumentation

## 1. Wie lautet die Netzwerkadresse vom Standort Samedan?

Die Netzwerkadresse vom Standort Samedan lautet:
192.168.3.0/24

## 2. Auf welcher IP-Adresse befindet sich der AccessPoint in Bellinzona?

Der Access Point in Bellinzona befindet sich auf der IP-Adresse:
192.168.4.30

## 3. In welchem VLAN befinden sich die Arbeitsplatz-PCs?

Die Arbeitsplatz-PCs befinden sich im VLAN-2 Office.

## 4. Über welche IP-Adresse erreicht man den Manageable-Switch am Standort Chur?

Den Manageable-Switch am Standort Chur erreicht man über:
192.168.2.253

## 5. Welche IP-Adressen LAN-seitig und tunnelseitig ist der VPN-Gateway am Standort Bellinzona konfiguriert?

VPN-Gateway Bellinzona:

* LAN-seitig: 192.168.4.1
* Tunnelseitig: 172.200.4.2/24

## 6. Wie lautet der am Standort Samedan an den Arbeitsplatz-PCs eingetragene Standardgateway?

Der Standardgateway der Arbeitsplatz-PCs in Samedan lautet:
192.168.3.1

## 7. Ein Aussendienstmitarbeiter benötigt Zugriff auf das Firmennetzwerk. Wie muss er seine VPN-SW IP-mässig konfigurieren?

Der Aussendienstmitarbeiter muss seine VPN-Software wie folgt konfigurieren:

* VPN-C verwenden (RAS = Remote Access)
* Verbindung über die öffentliche Adresse bzw. Domain ingcaprez.ch
* Tunnelnetz: 172.200.5.x/24

## 8. Wer hat im Büro CAD Wasserbau die VoIP-Telefone installiert?

Die VoIP-Telefone im Büro CAD Wasserbau wurden von abisang installiert.

## 9. Wann wurde im Bistro der AccessPoint installiert?

Der Access Point im Bistro wurde am 23.07.2014 installiert.

## 10. Der IT-Mitarbeiter Rene Sauter (rsauter) verlässt die Firma. Welche Arbeiten bzw. Verantwortlichkeiten sind davon betroffen? Wen würden sie als zukünftigen Ansprechpartner bei Problemen vorschlagen?

Von Rene Sauter betreute Installationen:

* Arbeitsplatz-PC Empfang
* CAD Workstation CAD Tiefbau
* MF-Kopierer Bauleiterbüro
* Access Point Bistro

Als zukünftigen Ansprechpartner würde ich blaeuchli oder rkundert vorschlagen, da diese bereits mehrere Installationen betreuen.

## 11. Wieviele RJ45-Steckdosen stehen ihnen im Bauleiterbüro zur Verfügung und wieviele davon sind zurzeit noch nicht belegt?

Im Bauleiterbüro stehen insgesamt 8 RJ45-Steckdosen zur Verfügung.

Verfügbare Anschlüsse:

* E3 = 2 Anschlüsse
* E4 = 2 Anschlüsse
* E5 = 2 Anschlüsse
* E6 = 2 Anschlüsse

Noch frei sind:

* E3/1
* E6/2

Somit sind 2 Anschlüsse noch nicht belegt.

## 12. Im Büro CAD Tiefbau muss ein weiteres VoIP-Telefon zur Verfügung stehen. Wie soll diese Verbindung gepatched werden? Verlangt wird die Patchpanelbelegung und der Switch-Port.

Für das zusätzliche VoIP-Telefon kann der freie Anschluss E2/2 verwendet werden.

Patchpanelbelegung:

* E2/2

Switch-Port:

* VLAN-1 Telefon
* Ports 24 bis 47

## 13. Im Bistro soll eine Projektpräsentation stattfinden. Dafür muss eine Ethernetkabelverbindung bereitgestellt werden.

Im Bistro können folgende freie Anschlüsse verwendet werden:

* E8/2
* E9/1
* E9/2

## 14. Im Büro CAD Wasserbau soll temporär ein weiterer Arbeitsplatz eingerichtet werden. Wie werden sie diese Aufgabe lösen?

Da alle Anschlüsse im Büro CAD Wasserbau bereits belegt sind, würde ich:

* einen kleinen zusätzlichen Switch einsetzen oder
* ein bestehendes Gerät temporär umpatchen

## 15. Wieviele Switchs stehen ihnen am Standort Chur zur Verfügung?

Am Standort Chur stehen 2 Switches zur Verfügung.

## 16. Frau Sommer arbeitet an der CAD-Workstation und meldet ihnen, dass sie keine Verbindung ins Internet mehr hat. Was werden sie überprüfen?

Folgende Punkte würde ich überprüfen:

* Netzwerkkabel
* Link am Switch
* IP-Adresse
* DHCP-Konfiguration
* Standardgateway
* DNS
* VLAN-Zuweisung
* Patchpanel-Verbindung
* Firewall bzw. Internetverbindung

## 17. Wie lautet die SSID des Churer-AccessPoint?

Die SSID des Churer Access Points ist in der Dokumentation nicht angegeben.
