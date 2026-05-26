# SW_A1H1_1 

Kommutaator **SW_A1H1_1** asub **Asukoht 1 Hoone 1-s** ehk tootmis- ja kontorihoones.

See on selle hoone keskne switch, mille kaudu ühenduvad:

- ruuter **R2_A1H1**
- tootmise ja kontori switch **SW_A1H1_2**
- tööpinkide, printeri, kaamera ja AP switch **SW_A1H1_3**

---

# Kasutatud pordid

| Port | Ühendatud seade | VLAN | Selgitus |
|---|---|---|---|
| G0/1 | R2_A1H1 | trunk | Ühendus Hoone 1 ruuteriga |
| Fa0/2 | SW_A1H1_2 | trunk | Ühendus tootmise, kontori ja projekteerijate switchiga |
| Fa0/3 | SW_A1H1_3 | trunk | Ühendus tööpinkide, printeri, kaamera ja AP switchiga |

---

#  konfiguratsioon

```cisco
enable
configure terminal

hostname SW_A1H1_1

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

interface g0/1
 description TRUNK_TO_R2_A1H1
 switchport mode trunk

interface fa0/2
 description TRUNK_TO_SW_A1H1_2
 switchport mode trunk

interface fa0/3
 description TRUNK_TO_SW_A1H1_3
 switchport mode trunk

end
write memory
