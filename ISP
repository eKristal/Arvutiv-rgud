## ISP 

Ruuter **ISP** asub ettevõtte võrgust väljaspool ja kujutab Packet Traceris internetiteenuse pakkujat. ISP ruuter on ühendatud peamaja ruuteriga **R1_A1H2**.

Selle ühenduse kaudu liigub lubatud internetiliiklus ettevõtte võrgust välja. ISP ruuter ise ei halda ettevõtte sisemisi VLAN-e, vaid toimib välisvõrgu ehk interneti poole jääva ruuterina.

### Kasutatud pordid

| Port | Ühendatud seade | IP-võrk | Selgitus |
|---|---|---|---|
| G0/0 | R1_A1H2 G0/2 | 203.0.113.0/30 | Ühendus ettevõtte peamise ruuteriga |

###  konfiguratsioon

```cisco
enable
configure terminal

hostname ISP

interface g0/0
 description LINK_TO_R1_A1H2
 ip address 203.0.113.1 255.255.255.252
 no shutdown

end
write memory
