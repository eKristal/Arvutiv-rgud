# SW_A2_3 

Kommutaator **SW_A2_3** asub **Asukoht 2** tootmis- ja kontorihoones.

Selle switchi külge on ühendatud:

- tööpink
- printer
- IP-kaamera
- WiFi pääsupunkt

Switch on ühendatud keskse switchiga **SW_A2_1**, mille kaudu liigub VLAN-ide liiklus edasi ruuterisse ja teistesse võrkudesse.

---

# Kasutatud pordid

| Port | Ühendatud seade | VLAN | Selgitus |
|---|---|---|---|
| Fa0/1 | SW_A2_1 | trunk | Ühendus keskse switchiga |
| Fa0/2 | Toopink_A2 | 40 | Tööpinkide VLAN |
| Fa0/3 | PRN_A2 | 90 | Printerite VLAN |
| Fa0/4 | CAM_A2 | 100 | IP-kaamerate VLAN |
| Fa0/5 | AP_A2 | 151 | Asukoht 2 haldusvõrk / WiFi AP haldus |

---

#  konfiguratsioon

```cisco
enable
configure terminal

hostname SW_A2_3

vlan 10
 name TOOTMINE_A2

vlan 20
 name KONTOR_A2

vlan 40
 name TOOPINGID_A2

vlan 90
 name PRINTERID_A2

vlan 100
 name KAAMERAD_A2

vlan 151
 name HALDUS_A2

interface fa0/1
 description TRUNK_TO_SW_A2_1
 switchport mode trunk

interface fa0/2
 description PC_TOOPINK_A2
 switchport mode access
 switchport access vlan 40

interface fa0/3
 description PRN_A2
 switchport mode access
 switchport access vlan 90

interface fa0/4
 description CAM_A2
 switchport mode access
 switchport access vlan 100

interface fa0/5
 description AP_A2
 switchport mode access
 switchport access vlan 151

end
write memory
