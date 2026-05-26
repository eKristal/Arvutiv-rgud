# SW_A1H1_3 

Kommutaator **SW_A1H1_3** asub **Asukoht 1 Hoone 1-s** ehk tootmis- ja kontorihoones.

Selle switchi külge on ühendatud:

- tööpink
- printer
- IP-kaamera
- WiFi pääsupunkt

Switch on ühendatud keskse switchiga **SW_A1H1_1**, mille kaudu liigub VLAN-ide liiklus edasi ruuterisse ja teistesse võrkudesse.

---

# Kasutatud pordid

| Port | Ühendatud seade | VLAN | Selgitus |
|---|---|---|---|
| Fa0/5 | SW_A1H1_1 | trunk | Ühendus keskse switchiga |
| Fa0/1 | PC_Toopink_A1 | 40 | Tööpinkide VLAN |
| Fa0/2 | PRN_A1H1 | 90 | Printerite VLAN |
| Fa0/3 | CAM_A1H1 | 100 | IP-kaamerate VLAN |
| Fa0/4 | AP_A1H1 | 150 | Haldusvõrk / WiFi AP haldus |

---

#  konfiguratsioon

```cisco
enable
configure terminal

hostname SW_A1H1_3

vlan 10
 name TOOTMINE_A1H1

vlan 20
 name KONTOR_A1H1

vlan 30
 name PROJEKTEERIJAD_A1H1

vlan 40
 name TOOPINGID_A1H1

vlan 90
 name PRINTERID_A1

vlan 100
 name KAAMERAD_A1

vlan 150
 name HALDUS_A1

interface fa0/5
 description TRUNK_TO_SW_A1H1_1
 switchport mode trunk

interface fa0/1
 description PC_TOOPINK_A1
 switchport mode access
 switchport access vlan 40

interface fa0/2
 description PRN_A1H1
 switchport mode access
 switchport access vlan 90

interface fa0/3
 description CAM_A1H1
 switchport mode access
 switchport access vlan 100

interface fa0/4
 description AP_A1H1
 switchport mode access
 switchport access vlan 150

end
write memory
