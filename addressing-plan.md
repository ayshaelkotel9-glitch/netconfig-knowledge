# PLAN D'ADRESSAGE - CLINIQUE EL JEM (donnees fictives)

## SITE 1 (siege)
- VLAN 10 - Administration : 192.168.10.0/24, passerelle 192.168.10.1
- VLAN 20 - Soins : 192.168.20.0/24, passerelle 192.168.20.1
- VLAN 30 - Invites : 192.168.30.0/24, passerelle 192.168.30.1
- VLAN 99 - VLAN natif du trunk (aucun hote)
- VLAN 999 - VLAN poubelle (ports inutilises, en shutdown)

## SITE 2 (annexe)
- VLAN 40 - Administration : 192.168.40.0/24, passerelle 192.168.40.1
- VLAN 50 - Soins : 192.168.50.0/24, passerelle 192.168.50.1
- VLAN 60 - Invites : 192.168.60.0/24, passerelle 192.168.60.1

## LIEN WAN SITE 1 <-> SITE 2
- Reseau : 10.0.0.0/30
- Routeur Site 1 (R1) : 10.0.0.1
- Routeur Site 2 (R2) : 10.0.0.2

## OSPF
- Process ID : 1
- Aire : 0
- Authentification MD5, cle ID 1
- passive-interface default (sauf le lien WAN)

## NAT
- Pool/IP publique fictive (plage de documentation) : 203.0.113.0/30
- NAT overload sur l'interface de sortie de R1
- ACL NAT : autoriser uniquement 192.168.0.0/16

## EQUIPEMENTS
- Switch L3 Site 1 : SW1
- Routeur Site 1 : R1
- Routeur Site 2 : R2
