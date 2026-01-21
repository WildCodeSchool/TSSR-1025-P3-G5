## Creation d'Oraganizational Units (OU) et de groupes

### OU à créer par départements

| Département                          | Nom OU            |
|--------------------------------------|--------------------|
| Communication et Relations publiques | LabUsers-com_rp    |
| Département Juridique                | LabUsers-judic     |
| Développement logiciel               | LabUsers-dev       |
| Direction                            | LabUsers-dir       |
| DSI                                  | LabUsers-dsi       |
| Finance et Comptabilité              | LabUsers-fin_compt |
| QHSE                                 | LabUsers-qhse      |
| Service Commercial                   | LabUsers-business  |

* Possible en graphique ou avec la commandes powershell suivante (exemple avec le premier département) :

`New-ADOrganizationalUnit -Name 'LabUsers-com_rp' -Path "DC=tssr,DC=lan" -Description 'Communication et Relations publiques`

### Groupes à créer par départements

| Département                         | Noms OU            |
|--------------------------------------|--------------------|
| Communication et Relations publiques | GrpUsers-com_rp    |
| Département Juridique                | GrpUsers-judic     |
| Développement logiciel               | GrpUsers-dev       |
| Direction                            | GrpUsers-dir       |
| DSI                                  | GrpUsers-dsi       |
| Finance et Comptabilité              | GrpUsers-fin_compt |
| QHSE                                 | GrpUsers-qhse      |
| Service Commercial                   | GrpUsers-business  |

* Possible en graphique ou avec la commandes powershell suivante (exemple avec le premier département) :

`New-ADGroup -Name 'GrpUsers-com_rp' -GroupScope Global -GroupCategory Security -Path 'OU=LabUsers-com_rp,DC=tssr,DC=lan' -Description 'Groupe communication et rp'`

Le groupe est alors créé dans l'OU correspondante

### Ajout des utilisateurs aux groupes  

* Possible en graphique ou avec la commandes powershell suivante (exemple avec le premier département) :  

Add-ADGroupMember -Members "pjb" -Identity "Direction"
