# Serveur DHCP

Nom d'hôte | SRV-QuestWin  
:---:|:---:



---------
# Après l'installation du DHCP

## 1. Virtuals Machines ([serveur](https://github.com/Fairskip/DHCPWindows/blob/main/R%C3%A9seau%20Interne.jpg)  & [Host](https://github.com/Fairskip/DHCPWindows/blob/main/Reseau%20interne%20windy.jpg))

Configuration > Réseau > Mode d'accès réseau => Réseau Interne.

<br>

## 2. [Renommer le PC du Serveur](https://github.com/Fairskip/DHCPWindows/blob/main/PC%20renamed.jpg)
Accueil > Ce PC > Clic droit > Propriétés  

Paramètres de ce nom d'ordinateur => Modifier les paramètres.  

Propriétés système > Nom de l'ordinateur => Modifier  

Nom de l'ordinateur => SRV-QuestWin  

Ok, Ok, Fermer, Redémarrer  

<br>

## 3. Donner une adresse [IP Statique au serveur](https://github.com/Fairskip/DHCPWindows/blob/main/IP%20statiques.jpg)
Barre de recherche > **ncpa.cpl**  

Ethernet => double clic  

Etat de Ethernet > propriétés  

Propriétés de Ethernet > clic sur Internet Protocol Version 4 > propriété  

Propriétés de Protocole Internet version 4 :  

=> Clic Utiliser l'adresse IP suivante   

* Adresse IP : 172.20.0.254 (! L'IP statique du serveur doit toujours être dans la même rangé que l'etendu de plage qu'on va créer)
* Masque de sous-réseau : 255.255.0.0
* Serveur DNS préféré : 172.20.0.254
  
Ok, fermer, fermer.

<br>

## 4. Créer une [nouvelle étendue](https://github.com/Fairskip/DHCPWindows/blob/main/Etendue.jpg)

DHCP > Clique droit sur le nom du serveur : srv-questwin  

Gestionnaire dhcp](https://github.com/Fairskip/DHCPWindows/blob/main/Gestionnaire%20DHCP.jpg) : dhcp > SRV-QuestWin > IPv4 => Clique droit IPv4 : Nouvelle etendue  

Suivant  

* Nom de l'étendue => Quest_Win1
* Plage d'adresse IP :
  * Adresse IP de début : 172.20.0.100
  * Adresse IP de fin : 172.20.0.200, suivant
  * Longueur : défaut
  * Masque de sous-réseau : 255.255.0.0
    
Suivant (defaut) pour tout puis terminer.

<br>

## 5. Host Windy (windows) : IP & Mac
Sur le Terminal => ipconfig /all
IPv4 | Mac
:---: | :---:
169.254.155.224 /16 | 08-00-27-0c-e3-27 

<br>

# 6. [Réservation d'une adresse IP](https://github.com/Fairskip/DHCPWindows/blob/main/Reservation.jpg)
Réservation > clic droit => [nouvelle réservation](https://github.com/Fairskip/DHCPWindows/blob/main/Reservation_1.jpg)
* Nom de réservation : Windy
* Adresse Ip réservé : 172.20.0.10
* Adresse mac : 08-00-27-0c-e3-27 
* types pris en charge : Les deux
  
Ajouter

# 7. Requête IP : Ordi Host Windy
* IPconfig
![Predhcp](https://github.com/Fairskip/DHCPWindows/blob/main/Windy%20Pre%20dhcp.png)
* IPconfig /release
  ![ipconfig /release](https://github.com/Fairskip/DHCPWindows/blob/main/Host%20IP%20release.jpg)
* IPconfig /renew
  ![ipconfig /renew](https://github.com/Fairskip/DHCPWindows/blob/main/Host%20IP%20renew.jpg)

* Redemande d'IP à nouveau pour obtenir le même Ip réservé
![again](https://github.com/Fairskip/DHCPWindows/blob/main/Windy%20Release%20et%20renew%20again.png)


# 7. Requête IP : Host Fairskip Virtual Box
* sudo dhclient -r enp0s3
* sudo dhclient enp0s3

![Ip requete](https://github.com/Fairskip/DHCPWindows/blob/main/Fairskip%20VB%20Ip%20requete.jpg)
![requete IP](https://github.com/Fairskip/DHCPWindows/blob/main/Fairskip%20VB%20new%20ip.png)

# 8. Baux d'adresses
  ![adresses pris](https://github.com/Fairskip/DHCPWindows/blob/main/IP%20Distribution.jpg)
