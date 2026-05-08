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

