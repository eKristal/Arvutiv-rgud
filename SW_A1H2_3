## SW_A1H2_3 seadistamine

Kommutaator **SW_A1H2_3** asub **Asukoht 1 Hoone 2-s** ehk peamajas. Selle switchi külge on ühendatud peamaja printer, IP-kaamera ja WiFi pääsupunkt. Switch on ühendatud keskse switchiga **SW_A1H2_1**, mille kaudu liigub VLAN-ide liiklus edasi ruuterisse ja teistesse võrkudesse.

Selle switchi ülesanne on jagada seadmed õigesse VLAN-i:

- printer läheb printerite VLAN-i;
- IP-kaamera läheb kaamerate VLAN-i;
- WiFi pääsupunkt läheb haldusvõrku;
- ühendus keskse switchiga töötab trunk-pordina.

### Kasutatud pordid

| Port | Ühendatud seade | VLAN | Selgitus |
|---|---|---:|---|
| Fa0/1 | SW_A1H2_1 | trunk | Ühendus keskse switchiga |
| Fa0/2 | PRN_A1H2 | 90 | Printerite VLAN |
| Fa0/3 | CAM_A1H2 | 100 | IP-kaamerate VLAN |
| Fa0/4 | AP_A1H2 | 150 | Haldusvõrk / WiFi AP haldus |

### Cisco konfiguratsioon

```cisco
enable
configure terminal

hostname SW_A1H2_3

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
 description PRN_A1H2
 switchport mode access
 switchport access vlan 90

interface fa0/3
 description CAM_A1H2
 switchport mode access
 switchport access vlan 100

interface fa0/4
 description AP_A1H2
 switchport mode access
 switchport access vlan 150

end
write memory
