# SW_A1H1_2 

Kommutaator **SW_A1H1_2** asub **Asukoht 1 Hoone 1-s** ehk tootmis- ja kontorihoones.

Selle switchi külge on ühendatud:

- tootmise näidisarvutid
- kontori näidisarvutid
- projekteerijate näidisarvutid

Switch on ühendatud keskse switchiga **SW_A1H1_1**, mille kaudu liigub VLAN-ide liiklus edasi ruuterisse ja teistesse võrkudesse.

---

# Kasutatud pordid

| Port | Ühendatud seade | VLAN | Selgitus |
|---|---|---|---|
| Fa0/1 | SW_A1H1_1 | trunk | Ühendus keskse switchiga |
| Fa0/2 | PC_Tootmine_A1 | 10 | Tootmise VLAN |
| Fa0/3 | PC_Kontor_A1 | 20 | Kontori VLAN |
| Fa0/4 | PC_Projekt_A1 | 30 | Projekteerijate VLAN |

---

#  konfiguratsioon

```cisco
enable
configure terminal

hostname SW_A1H1_2

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

interface fa0/1
 description TRUNK_TO_SW_A1H1_1
 switchport mode trunk

interface fa0/2
 description PC_TOOTMINE_A1
 switchport mode access
 switchport access vlan 10

interface fa0/3
 description PC_KONTOR_A1
 switchport mode access
 switchport access vlan 20

interface fa0/4
 description PC_PROJEKT_A1
 switchport mode access
 switchport access vlan 30

end
write memory
