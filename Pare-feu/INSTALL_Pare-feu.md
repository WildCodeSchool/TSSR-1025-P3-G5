## Instalation de pfsense

### Prérequis

VirtualBox installé sur la machine hôte.
ISO de pfSense Community Edition (à télécharger depuis <https://pfsense.org/download>)  

**Installer la dernière version stable**

![alt text](Ressources/pfsense_install4.png)

---

### Nouvelle VM pfSense

* Nom : FW01
* Type : BSD → FreeBSD (64-bit)
* RAM : 1 à 2 Go
* CPU : 2 cœurs
Disque : 20G
* **Réseau 5 cartes** :

**Pour créer une 5eme carte (non disponible en GUI) en CLI :**  

`VBoxManage modifyvm "FW01" --nic5 intnet --intnet5 "intnet-vlan30" --nictype5 virtio --cableconnected5 on`
***ici "intnet-vlan30" sur la VM "FW01"***  

| Carte | Attaché à          | Nom réseau      | Rôle pfSense | IP configurée | Commentaire                           |
| ----- | ------------------ | --------------- | ------------ | ---------------------- | ------------------------------------- |
| 1     | **Pont**           | —               | WAN          | DHCP ou 192.168.1.x/24 | Connecté à box FAI                    |
| 2     | **Réseau interne** | `intnet-vlan10` | LAN_10_Serveurs          | 172.16.10.1/24         | Réseau interne                        |
| 3     | **Réseau interne** | `DMZ`           | DMZ          | 10.10.10.1/24          | Zone démilitarisée (serveurs exposés) |
| 4     |        Réseau interne             |      `intnet-vlan20`            |              |                        |                                       |
| 5     |       Réseau interne              |  `intnet-vlan30`               |              |                        |                                       |

***Selection de l'interface WAN***
![alt text](Ressources/pfsense_install7.png)
***Adresse IP du LAN après avoir selectionné l'interface***
![alt text](Ressources/pfsense_install6.png)

* Ne pas choisir d'option DHCP pour les interfaces LAN et DMZ car ce service sera géré par Windows Server (SRWIN01)
  
### Accès Web GUI & Configuration de base

Depuis une VM sur le réseau LAN (172.16.10.0/24) :

On ouvre le navigateur  → <https://172.16.10.1>

Login : admin / pfsense
