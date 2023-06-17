# subnetcalculator

```
Usage:
        sc.exe -c <ip> <netmask> --> show network info
        sc.exe -s <ip> <netmask> <n> --> split network into <n> subnets
        sc.exe -v <ip> <netmask> <subnets/hosts per subnet> --> split network into several subnets, define the hosts like 100,40,10
```

Der Parameter -c gibt all Informationen zu dem Netzwerk aus, in dem sich eine IP Adresse befindet.

```
sc -c 192.168.0.30 24

Netzwerk:
        Netzwerkadresse: 192.168.0.0/24
        Erste Host-Adresse: 192.168.0.1
        Letzte Host-Adresse: 192.168.0.254
        Broadcast-Adresse: 192.168.0.255
        Verfuegbare Hosts: 254
        Subnetzmaske: 255.255.255.0
```

Der Parameter -s teilt ein gegebenes Netzwerk in eine bestimmte Anzahl Subnetze gleicher Länge.

```
sc -s 192.168.0.0 24 4

Netzwerk 1:
        Netzwerkadresse: 192.168.0.0/26
        Erste Host-Adresse: 192.168.0.1
        Letzte Host-Adresse: 192.168.0.62
        Broadcast-Adresse: 192.168.0.63
        Verfuegbare Hosts: 62
        Subnetzmaske: 255.255.255.192

Netzwerk 2:
        Netzwerkadresse: 192.168.0.64/26
        Erste Host-Adresse: 192.168.0.65
        Letzte Host-Adresse: 192.168.0.126
        Broadcast-Adresse: 192.168.0.127
        Verfuegbare Hosts: 62
        Subnetzmaske: 255.255.255.192

Netzwerk 3:
        Netzwerkadresse: 192.168.0.128/26
        Erste Host-Adresse: 192.168.0.129
        Letzte Host-Adresse: 192.168.0.190
        Broadcast-Adresse: 192.168.0.191
        Verfuegbare Hosts: 62
        Subnetzmaske: 255.255.255.192

Netzwerk 4:
        Netzwerkadresse: 192.168.0.192/26
        Erste Host-Adresse: 192.168.0.193
        Letzte Host-Adresse: 192.168.0.254
        Broadcast-Adresse: 192.168.0.255
        Verfuegbare Hosts: 62
        Subnetzmaske: 255.255.255.192

Host Adressen: 248/254 (97%)
```

Der Parameter -v teilt ein gegebenes Netzwerk in Subnetze unterschiedlicher (oder auch gleicher) Länge. Möchte man das Netzwerk 192.168.0.0/24 in 3 Subnetze teilen wobei ein Subnetz mindestens 14, eines mindestens 60 und eines mindestens 4 haben soll gibt man die Anzahl der Hosts mit Comma getrennt und ohne Leerzeichen als Parameter an. **Achtung**, derzeit müssen die Zahlen in absteigender Reihenfolge, beginnend bei der größten, angegeben werden.

```
sc -v 192.168.0.0 24 60,14,4

Netzwerk: 1
        Netzwerkadresse: 192.168.0.0/26
        Erste Host-Adresse: 192.168.0.1
        Letzte Host-Adresse: 192.168.0.62
        Broadcast-Adresse: 192.168.0.63
        Verfuegbare Hosts: 62
        Subnetzmaske: 255.255.255.192

Netzwerk: 2
        Netzwerkadresse: 192.168.0.64/28
        Erste Host-Adresse: 192.168.0.65
        Letzte Host-Adresse: 192.168.0.78
        Broadcast-Adresse: 192.168.0.79
        Verfuegbare Hosts: 14
        Subnetzmaske: 255.255.255.240

Netzwerk: 3
        Netzwerkadresse: 192.168.0.80/29
        Erste Host-Adresse: 192.168.0.81
        Letzte Host-Adresse: 192.168.0.86
        Broadcast-Adresse: 192.168.0.87
        Verfuegbare Hosts: 6
        Subnetzmaske: 255.255.255.248

Host Adressen: 82/254 (32%)
```

Der Parameter -h gibt eine Tabelle aus mit der Sie jede Aufgabe in Sekunden meistern! Eine **Erklärung dazu kommt bald**.

```
sc -h

3. Oktett                                                    |  4. Oktett
255     128     192     224     240     248     252     254     255     128     192     224     240     248     252     254     255
65536   32768   16384   8192    4096    2048    1024    512     256     128     64      32      16      8       4       2       1
/16     /17     /18     /19     /20     /21     /22     /23     /24     /25     /26     /27     /28     /29     /30     /31     /32
```
