Peamaja keskne kommutaator SW_A1H2_1 ühendab R1 ruuteri, serverid ning teised peamaja kommutaatorid. Ruuteri ja teiste kommutaatorite suunalised pordid seadistati trunk-portidena, 
sest nende kaudu liigub mitme VLAN-i liiklus. 
Serverite pordid seadistati access-portidena vastavalt serverivõrkude VLAN-idele.


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

