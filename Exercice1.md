**Q.1.1 Pourquoi le ping avec les adresses IP des machines ne fonctionne pas ?**
Modifiez la configuration sur le client pour que cela soit possible.
Le ping peut ne pas fonctionner pour plusieurs raisons. Une des raisons les plus fréquentes est que les machines ne sont pas dans le même réseau ou que les paramètres de réseau sur le client ne sont pas correctement configurés.

**Q.1.2 Le ping avec le nom des machines ne fonctionne pas.**
C:\Windows\System32\drivers\etc\hosts 
on 
172.16.10.10 serveur

**Q.1.3 Configuration du client en DHCP et analyse de l'attribution d'adresse**
**1 : Changer la configuration du client en DHCP  Windows :**

Ouvrir Paramètres → Réseau et Internet → Centre Réseau et partage .
Cliquez sur Modifier les paramètres de la carte .
Faire un clic droit sur l'interface réseau active et choisir Propriétés .
Sélectionnez Protocole Internet version 4 (TCP/IPv4) et cliquez sur Propriétés , Cocher 
Obtenir automatiquement une adresse IP
Obtenir automatiquement les adresses des serveurs DNS
Valider avec OK .

**Sur un client Linux :**

Ouvrir un terminal.
Exécuter la commande 
sudo dhclient -r
sudo dhclient
Cela libère et renouvelle l'adresse IP DHCP.
 **2 : Vérification du serveur DHCP**
Sur le serveur DHCP :

Ouvrez Gestionnaire de serveur → Outils → DHCP .
Naviguer dans IPv4 → Étendue DHCP → Baux actifs .
Vérifiez les adresses IP distribuées et la plage d'adresses configurées.
**3 : Comparaison des adresses IP**
Sur le client, vérifiez l'adresse IP obtenue avec :

ipconfig /all windows

ifconfig         Linux 

**Le client** ne prend pas toujours la première adresse DHCP disponible à cause des baux DHCP actifs, des réservations et du cache DHCP.

**Q.1.4 Attribution spécifique de l'adresse 172.16.10.15 via DHCP**
1 : Vérifier si l'adresse 172.16.10.15 est dans la plage DHCP
Sur le serveur DHCP :

Ouvrez Gestionnaire de serveur → Outils → DHCP .
Naviguer dans IPv4 → Étendue DHCP → Étendue .
Vérifiez la plage d'adresses (ex. 172.16.10.10 - 172.16.10.50).
Si l'adresse 172.16.10.15 est dans la plage, elle peut être attribuée.

2 : Réserver l'adresse pour le client
Récupérer l'adresse MAC du client :
ipconfig /all   # Windows
ifconfig        # Linux
