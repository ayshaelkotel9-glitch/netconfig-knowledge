CHECKLIST SÉCURITÉ CISCO IOS

ACCÈS ADMIN
- enable secret (jamais enable password)
- service password-encryption
- SSH v2 uniquement : ip ssh version 2, transport input ssh sur les lignes vty
- Pas de Telnet
- exec-timeout 5 0 sur console et vty
- login local + utilisateur avec secret

SWITCH
- Ports inutilisés : shutdown + VLAN poubelle (ex. 999)
- Port-security sur les ports d'accès
- Désactiver DTP : switchport nonegotiate
- Trunk : VLAN natif différent de 1, VLANs autorisés explicites
- BPDU Guard + PortFast sur les ports d'accès
- Pas d'administration depuis le VLAN 1

ROUTEUR
- Bannière légale : banner motd
- no ip http server
- ACL standard/étendues sur les interfaces exposées
- OSPF : authentification MD5, passive-interface par défaut
- NAT : limiter aux réseaux internes via ACL

SUPERVISION
- logging buffered + NTP
- Désactiver CDP sur les interfaces externes
