# subnetcalculator

```
Usage:
        prog.exe -c <ip> <netmask> --> show network info
        prog.exe -s <ip> <netmask> <n> --> split network into <n> subnets
        prog.exe -v <ip> <netmask> <subnets/hosts per subnet> --> split network into several subnets, define the hosts like 100,40,10
```

Der Parameter -c gibt all Informationen zu dem Netzwerk aus, in dem sich eine IP Adresse befindet.

```
main -c 192.168.0.30 24

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
main -s 192.168.0.0 24 4

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

Der Parameter -v teilt ein gegebenes Netzwerk in Subnetze unterschiedlicher (oder auch gleicher) Länge. Möchte man das Netzwerk 192.168.0.0/24 in 3 Subnetze teilen wobei ein Subnetz mindestens 14, eines mindestens 60 und eines mindestens 4 haben soll gibt man die Anzahl der Hosts mit Comma getrennt und ohne Leerzeichen als Parameter an.

```
main -v 192.168.0.0 24 14,60,4

Netzwerk: 1
        Netzwerkadresse: 192.168.0.0/28
        Erste Host-Adresse: 192.168.0.1
        Letzte Host-Adresse: 192.168.0.14
        Broadcast-Adresse: 192.168.0.15
        Verfuegbare Hosts: 14
        Subnetzmaske: 255.255.255.240

Netzwerk: 2
        Netzwerkadresse: 192.168.0.0/26
        Erste Host-Adresse: 192.168.0.1
        Letzte Host-Adresse: 192.168.0.62
        Broadcast-Adresse: 192.168.0.63
        Verfuegbare Hosts: 62
        Subnetzmaske: 255.255.255.192

Netzwerk: 3
        Netzwerkadresse: 192.168.0.64/29
        Erste Host-Adresse: 192.168.0.65
        Letzte Host-Adresse: 192.168.0.70
        Broadcast-Adresse: 192.168.0.71
        Verfuegbare Hosts: 6
        Subnetzmaske: 255.255.255.248
        
Host Adressen: 82/254 (32%)
```
