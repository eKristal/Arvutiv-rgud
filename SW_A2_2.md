# SW_A2_2 

Kommutaator **SW_A2_2** asub **Asukoht 2** tootmis- ja kontorihoones.

Selle switchi külge on ühendatud:

- Asukoht 2 tootmise näidisarvutid
- Asukoht 2 kontori näidisarvutid

Switch on ühendatud keskse switchiga **SW_A2_1**, mille kaudu liigub VLAN-ide liiklus edasi ruuterisse ja teistesse võrkudesse.

---

# Kasutatud pordid

| Port | Ühendatud seade | VLAN | Selgitus |
|---|---|---|---|
| Fa0/1 | SW_A2_1 | trunk | Ühendus keskse switchiga |
| Fa0/2 | Tootmine_A2 | 10 | Asukoht 2 tootmise VLAN |
| Fa0/3 | Kontor_A2 | 20 | Asukoht 2 kontori VLAN |

---

#  konfiguratsioon

```cisco
enable
configure terminal

hostname SW_A2_2

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
 description PC_TOOTMINE_A2
 switchport mode access
 switchport access vlan 10

interface fa0/3
 description PC_KONTOR_A2
 switchport mode access
 switchport access vlan 20

end
write memory
