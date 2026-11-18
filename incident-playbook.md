# INCIDENT PLAYBOOK : ERREURS FREQUENTES CISCO IOS

| Symptome | Cause probable | Correction |
|---|---|---|
| Le trunk perd des VLAN apres une modification | "switchport trunk allowed vlan X" ecrase la liste existante | Utiliser "switchport trunk allowed vlan add X" |
| Message CDP native VLAN mismatch | VLAN natif different aux deux extremites du trunk | Aligner "switchport trunk native vlan" des deux cotes |
| Trunk non etabli ou instable | DTP actif (negociation automatique) | "switchport mode trunk" + "switchport nonegotiate" |
| Interface VLAN (SVI) en down/down | Aucun port actif dans ce VLAN ou VLAN absent du trunk | Verifier "show vlan brief" et "show interfaces trunk" |
| Pas de routage inter-VLAN sur switch L3 | "ip routing" absent | Activer "ip routing" |
| Router-on-a-stick sans effet | Interface physique en shutdown ou "encapsulation dot1Q" manquant | "no shutdown" sur l'interface mere, verifier chaque sous-interface |
| Tout le trafic est bloque apres une ACL | Deny implicite en fin d'ACL | Ajouter "permit ip any any" si necessaire, verifier le sens (in/out) |
| ACL sans effet | Mauvaise interface ou mauvais sens | Verifier "show ip interface" et "show access-lists" |
| Port passe en err-disabled | Violation port-security ou BPDU Guard | Corriger la cause puis "shutdown" / "no shutdown" |
| NAT ne traduit pas | "ip nat inside/outside" manquant ou ACL source incorrecte | Marquer les interfaces et verifier "show ip nat translations" |
| Voisin OSPF absent | Area, masque, timers, authentification ou passive-interface incorrects | "show ip ospf neighbor" et "show ip ospf interface" |
| Perte d'acces a distance apres modification | Config appliquee sans acces console de secours | Garder la console, tester avant "write memory" |
| Mot de passe lisible dans la config | "enable password" ou absence de chiffrement | "enable secret" + "service password-encryption" |
| Acces Telnet ouvert | "transport input" non restreint | "transport input ssh" sur les lignes vty |
