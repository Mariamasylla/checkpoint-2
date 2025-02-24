**Q.3.1 Quel est le matériel réseau A ? Quel est son rôle sur ce schéma vis-à-vis des ordinateurs ?**
Matériel A : Un switch (commutateur).
 Il connecte les ordinateurs PC1 à PC5, permettant leur communication au sein du même réseau local (LAN).

**Q.3.2 Quel est le matériel réseau B ? Quel est son rôle pour le réseau 10.10.0.0/16?**
Matériel B : Un routeur
 Il assure la communication entre le réseau 10.10.0.0/16 et d'autres réseaux, comme 10.12.2.0/24 et 172.16.5.0/24. 

**Q.3.3 Que signifie f0/0 et g1/0 sur l’élément B ?**
Ce sont les interfaces réseau du routeur B :

f0/0 : Interface Fast Ethernet 0/0  Connectée au switch A.
g1/0 : Interface Gigabit Ethernet 1/0 (1 Gbps). Connectée au routeur R2.

**Q.3.4 Pour l'ordinateur PC2, que représente /16 dans son adresse IP ?**
/16 est le masque de sous-réseau : 255.255.0.0.
Cela signifie que les 16 premiers bits de l’adresse IP identifient le réseau (10.11.0.0/16), et les 16 derniers bits sont réservés pour les hôtes.
PC2 appartient donc au réseau 10.11.0.0/16.

**Q.3.5 Pour ce même ordinateur, que représente l'adresse 10.10.255.254 ?**
10.10.255.254 est la passerelle par défaut pour PC2.
C'est l'interface du routeur B (f0/0) qui permet aux ordinateurs de sortir de leur réseau local et de communiquer avec d'autres sous-réseaux.

**Q.3.6 Adresses de réseau, première, dernière adresse et diffusion**
Ordinateur	Adresse IP	Masque	Adresse réseau	Première adresse	Dernière adresse	Adresse de diffusion
PC1	10.10.4.1	/16 (255.255.0.0)	10.10.0.0	10.10.0.1	10.10.255.254	10.10.255.255
PC2	10.11.80.2	/16 (255.255.0.0)	10.11.0.0	10.11.0.1	10.11.255.254	10.11.255.255
PC5	10.10.4.7	/15 (255.254.0.0)	10.10.0.0	10.10.0.1	10.11.255.254	10.11.255.255

**Q.3.7 Quels ordinateurs peuvent communiquer entre eux ?**
PC1, PC3, PC4 et PC5 sont dans le même réseau 10.10.0.0/15 → ils peuvent communiquer directement.
PC2 est dans 10.11.0.0/16, il ne peut pas communiquer directement avec PC1, PC3, PC4, ou PC5, sauf en passant par le routeur B.
Tout le monde peut communiquer via le routeur B si une configuration de routage est en place.

**Q.3.8 Quels ordinateurs peuvent atteindre le réseau 172.16.5.0/24 ?**
Tous les PC peuvent atteindre 172.16.5.0/24 à condition que le routage soit bien configuré sur les routeurs B et R2.
Chaque PC enverra les paquets à sa passerelle (10.10.255.254), qui les redirigera vers 10.12.2.253 puis 172.16.5.254.

**Q.3.9 Que se passe-t-il si on intervertit PC2 et PC3 sur le switch A ?**
PC2 aurait une IP 10.11.80.2/16, mais il serait connecté dans le réseau 10.10.0.0/16.
PC3 aurait une IP 10.10.80.3/16, mais serait dans le réseau 10.11.0.0/16.
Ils ne pourraient plus communiquer correctement, car ils auraient des adresses IP qui ne correspondent plus au sous-réseau du switch.

**Q.3.10 Comment mettre la configuration IP en dynamique ?**
Utiliser un serveur DHCP pour attribuer automatiquement des adresses IP aux PC.
Le routeur B ou un autre serveur peut jouer ce rôle.

