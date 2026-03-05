## Ajout du rôle Active directory Domain Service

>L'ajout de ce rôle est conseillé avant les autres, notamment le DNS.

* Add Roles and Features
* Selectionner le service
* Suivre les étapes d'installation

![alt text](Ressources/active_directory15.png)

* On configure une nouvelle fôret
* Le nom de domaine spécifié est : **tssr.lan**  

![alt text](Ressources/active_directory13.png)

* Laisser coché DNS server et Global Catalog
* Entrez un mot de passe  

![alt text](Ressources/active_directory12.png)

***Si tout est ok, on clique sur install***
![alt text](Ressources/active_directory11.png)

***À la fin de l'installation, ne pas oublier de promouvoir le serveur en DC***
![alt text](Ressources/active_directory14.png)

## Ajout d'un deuxième serveur

### Installation du serveur windows core en redondance AD-DS | DNS

* Configurer IP, DNS et rejoindre le domaine avec un compte et MDP du DC principal

![alt text](Ressources/active_directory37.png)  

* Installer le rôle AD-DS avec la commande  
 `Install-WindowsFeature AD-Domain-Services -IncludeManagementTools`

* Promouvoir le serveur en DC secondaire  

    `Install-ADDSDomainController
    -DomainName "tssr.lan"
    -InstallDns:$true
    -Credential (Get-Credential)
    -DatabasePath "C:\Windows\NTDS"
    -LogPath "C:\Windows\NTDS"
    -SysvolPath "C:\Windows\SYSVOL"
    -NoRebootOnCompletion:$false
    -Force:$true`  
  
* Get credential : avec un compte du DC principal

![alt text](Ressources/active_directory40.png)  

* La commande `Get-ADDomainController` devrait lister le nouveau DC

![alt text](Ressources/active_directory41.png)

* Ajout du serveur en GUI sur le DC principal

![alt text](Ressources/active_directory39.png)  

### Répartition des rôles FSMO

* Déplacer les rôles vers SRVWIN02
`Move-ADDirectoryServerOperationMasterRole -Identity "SRVWIN02"
-OperationMasterRole SchemaMaster, DomainNamingMaster-Force`

* Vérifier avec `netdom query fsmo`  

![alt text](Ressources/active_directory43.png)
