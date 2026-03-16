# Tableau de synthèse des éléments du schéma

| Nom du matétiel | OS                           | Fonction                            | Type     | @ IP /CIDR        | Disques (nb, taille, espace libre) | RAM (totale, % utilisation) |
|-----------------|------------------------------|-------------------------------------|----------|-------------------|------------------------------------|-----------------------------|
| FW01            | pfSense - FeeBSD             | Pare-Feu & routeur                  | Pare-feu | 192.168...... /24 | 1 - 20 Go - 10 Go                  | 1024 Mo -                   |
| SRVWIN01        | Windows Server 2022          | AD - DNS - DHCP - Fichiers partagés | Serveur  | 172.16.10.5 /28   | 2 - (2 x 40 go) - (21 Go - 39 Go)  | 3124 Mo - 55 %              |
| GLPI01          | Debian 13 CLI                | GLPI - Support et parc              | Serveur  | 172.16.10.6 /28   | 1 - 25 Go - 20 Go                  | 1536 Mo -                   |
| CLIWIN01        | Windows 10 professional      | Client DSI                          | Client   | 172.16.20.X /24   | 1 - 50 Go - 5 Go                   | 4096 Mo - 60 %              |
| CLIWIN02        | Windows 11                   | Client Lambda                       | Client   | 172.16.30.X /24   | 1 - 50 Go - 5 Go                   | 4096 Mo - 60 %              |
| IPBX01          | FreePBX 17 (Debian 12 based) | VoIP                                | Serveur  | 10.10.10.3 /29    | 1 - 60 Go - 20 Go                  | 3124 Mo -                   |
| SRWIN04         | Windows Server 2022 Core     | Rôle WSUS - FSMO                          | Serveur  | 172.16.10.7 /28   | 1 - 30Go - 15 Go                   | 2048 Mo -                   |
| SRVLX02         | Ubuntu 24.04 CLI             | Site web externe                    | Serveur  | 10.10.10.2 /29    | 1 - 20 Go - 10 Go                  | 2048 Mo -                   |
| SRVWIN02        | Windows Server 2022 Core     | Redondance AD DNS                   | Serveur  | 172.16.10.9 /28   | 1 - 50 Go - 40 Go                  | 2048 Mo -                   |
| SRVLX01         | Ubuntu 24.04 CLI             | iRedMail - Messagerie               | Serveur  | 10.10.10.4 /29    | 1 - 40 Go - 15 Go                  | 2048 Mo -                   |
