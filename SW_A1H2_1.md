## SW_A1H2_1 seadistamine

Kommutaator **SW_A1H2_1** asub Asukoht 1 Hoone 2-s ehk peamajas. Tegemist on keskse switchiga, mille külge on ühendatud peamaja ruuter **R1_A1H2**, teised peamaja switchid ning serverid. Selle switchi kaudu liigub VLAN-ide liiklus edasi ruuterisse ja teistesse võrkudesse.

### Kasutatud pordid

| Port | Ühendatud seade | VLAN | Selgitus |
|---|---|---:|---|
| G0/1 | R1_A1H2 | trunk | Ühendus peamaja ruuteriga |
| Fa0/2 | SW_A1H2_2 | trunk | Ühendus osakondade switchiga |
| Fa0/3 | SW_A1H2_3 | trunk | Ühendus printerite, kaamera ja AP switchiga |
| Fa0/4 | SRV_AD_DNS | 110 | AD ja DNS server |
| Fa0/5 | SRV_FILE | 110 | Failiserver |
| Fa0/6 | SRV_WEB | 112 | Veebiserver DMZ võrgus |
| Fa0/7 | SRV_VMS_1 | 111 | Videovalve server 1 |
| Fa0/8 | SRV_VMS_2 | 111 | Videovalve server 2 |
| Fa0/9 | SRV_OSAKONNAD | 110 | Osakondade serverid |

### Cisco konfiguratsioon

```cisco
enable
configure terminal

hostname SW_A1H2_1

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

interface g0/1
 description TRUNK_TO_R1_A1H2
 switchport mode trunk

interface fa0/2
 description TRUNK_TO_SW_A1H2_2
 switchport mode trunk

interface fa0/3
 description TRUNK_TO_SW_A1H2_3
 switchport mode trunk

interface fa0/4
 description SRV_AD_DNS
 switchport mode access
 switchport access vlan 110

interface fa0/5
 description SRV_FILE
 switchport mode access
 switchport access vlan 110

interface fa0/6
 description SRV_WEB_DMZ
 switchport mode access
 switchport access vlan 112

interface fa0/7
 description SRV_VMS_1
 switchport mode access
 switchport access vlan 111

interface fa0/8
 description SRV_VMS_2
 switchport mode access
 switchport access vlan 111

interface fa0/9
 description SRV_OSAKONNAD
 switchport mode access
 switchport access vlan 110

end
write memory
