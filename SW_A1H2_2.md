## SW_A1H2_2 seadistamine

Kommutaator **SW_A1H2_2** asub Asukoht 1 Hoone 2-s ehk peamajas. Selle switchi külge on ühendatud juhatuse, müügi-, personali- ja arendusosakonna näidisarvutid. Switch on ühendatud keskse switchiga **SW_A1H2_1**, mille kaudu liigub VLAN-ide liiklus edasi ruuterisse ja teistesse võrkudesse.

### Kasutatud pordid

| Port | Ühendatud seade | VLAN | Selgitus |
|---|---|---:|---|
| Fa0/1 | SW_A1H2_1 | trunk | Ühendus keskse switchiga |
| Fa0/2 | PC_Juhatus | 50 | Juhatuse VLAN |
| Fa0/3 | PC_Myyk | 60 | Müügiosakonna VLAN |
| Fa0/4 | PC_Personal | 70 | Personaliosakonna VLAN |
| Fa0/5 | PC_Arendus | 80 | Arendusosakonna VLAN |

### Cisco konfiguratsioon

```cisco
enable
configure terminal

hostname SW_A1H2_2

vlan 50
 name JUHATUS_A1H2
vlan 60
 name MYYK_A1H2
vlan 70
 name PERSONAL_A1H2
vlan 80
 name ARENDUS_A1H2
vlan 90
 name PRINTERID_A1
vlan 100
 name KAAMERAD_A1
vlan 110
 name SERVERID
vlan 111
 name VALVE_SERVERID
vlan 112
 name DMZ
vlan 120
 name WIFI_TOOTAJAD
vlan 130
 name WIFI_JUHTKOND
vlan 140
 name WIFI_KULALISED
vlan 150
 name HALDUS_A1

interface fa0/1
 description TRUNK_TO_SW_A1H2_1
 switchport mode trunk

interface fa0/2
 description PC_JUHATUS
 switchport mode access
 switchport access vlan 50

interface fa0/3
 description PC_MYYK
 switchport mode access
 switchport access vlan 60

interface fa0/4
 description PC_PERSONAL
 switchport mode access
 switchport access vlan 70

interface fa0/5
 description PC_ARENDUS
 switchport mode access
 switchport access vlan 80

end
write memory
