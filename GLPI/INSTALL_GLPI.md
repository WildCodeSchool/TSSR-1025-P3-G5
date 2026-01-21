## Installation de GLPI

### Prérequis

Une image ISO de ubuntu-server

Configuration de la VM :

* Nom : GLPO1
* Type : Linux → ubuntu-server (64-bit)
* RAM : 1 à 2 Go
* CPU : 2 cœurs
* Disque : 20

### Installation des composants

Mise à jour des paquets:  
`sudo apt-get update && sudo apt-get upgrade`

Apache2 :  
`sudo apt-get install apache2 -y`
