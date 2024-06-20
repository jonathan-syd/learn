# Contact

jonathan.marcheix@syd.fr

# LABS 

https://lms.godeploy.it/

# Powershell

[https://github.com/jonathan-syd/learn/pwsh](https://github.com/jonathan-syd/learn/blob/main/pwsh)

# Liens utiles 

https://gpsearch.azurewebsites.net/

https://learn.microsoft.com/en-us/troubleshoot/windows-server/group-policy/applying-group-policy-troubleshooting-guidance

https://support.microsoft.com/fr-fr/topic/ms16-072-mise-%C3%A0-jour-de-s%C3%A9curit%C3%A9-pour-la-strat%C3%A9gie-de-groupe-dat%C3%A9e-du-14-juin-2016-7570425d-d460-3003-b2ac-a464c874725d

https://www.antrimohamed.fr/wp-content/uploads/2014/04/Djoin/Offline-domain-Join.pdf

https://community.spiceworks.com/t/add-a-network-location-via-powershell/722383/3

https://support.mozilla.org/en-US/kb/make-firefox-enterprise-default-browser

https://www.dannymoran.com/wmi-filter-cheat-sheet/

Déploiement script avec SCCM : https://learn.microsoft.com/fr-fr/mem/configmgr/apps/deploy-use/create-deploy-scripts


### Role FSMO : 
`netdom /query:fsmo`

Pour accéder au schéma : `regsvr32 schmmgmt.dll`


# Group Policy 

## 1.0 SECURITY GPO

Vous devez configurer une GPO (stratégie de groupe) qui s’appliquera à tous les domaines de l’entreprise. Cette GPO constitue la principale politique de sécurité des comptes dans l’entreprise. Cette politique doit respecter les paramètres suivants :

- Longueur minimale du mot de passe : 6 caractères
- Durée de validité maximale du mot de passe : 90 jours
- Le système doit se souvenir des 5 derniers mots de passe utilisés
- Un compte doit être verrouillé après 5 tentatives de connexion infructueuses
- Le compteur des tentatives de connexion infructueuses doit être réinitialisé après une heure.

Toutefois, les administrateurs informatiques disposent d’un compte classique et d’un compte avec des permissions administratives. Les règles précédentes ne doivent pas s’appliquer aux comptes des administrateurs. 
Vous devez également configurer une politique de mot de passe spécifique pour ces comptes administratifs :

- Longueur minimale du mot de passe : 8 caractères
- Durée de validité maximale du mot de passe : 30 jours
- Le système doit se souvenir des 10 derniers mots de passe utilisés
- Un compte doit être verrouillé après 3 tentatives de connexion infructueuses
- Le compteur des tentatives de connexion infructueuses doit être réinitialisé après 4 heures


## 1.1 GPO FILTERING

Les ordinateurs des journalistes sont hétérogènes. Certains journalistes utilisent Windows 11, tandis que d’autres utilisent Windows 7.

Vous devez appliquer des règles de pare-feu sortant, mais les règles sortantes n’existent pas sur Windows 7. Vous devez vous assurer que la stratégie qui modifie les règles de pare-feu s’applique uniquement aux ordinateurs Windows 11.

Cette règle doit autoriser les connexions FTP sortantes sur le port 21.

D’autre part, vous avez un groupe d’utilisateurs administratifs qui utilisent un logiciel de comptabilité. Vous constatez que ce logiciel génère de nombreux journaux d’application qui occupent trop d’espace sur les ordinateurs de comptabilité. Utilisez une stratégie qui modifie la taille maximale des journaux d’application et qui s’applique uniquement aux utilisateurs membres du groupe administratifs.

## 1.2 GPO PARAMETERS

Vous avez des stratégies de groupe de sécurité pour tous les employés. Vous devez maintenant configurer le paramètre commun pour les personnes de l’Administration.

Your policy must meet the following requirements:
- Apply the wallactus.png wallpaper
- Disable the possibility to change the wallpaper
- Prevent user to change screen saver
- Disable the history of recent opened documents
- Prevent user to adding printers
- Disable access to control panel, command prompt. Also disable the ability to open task manager with Ctrl + Alt + del
- You must prevent users to plug USB devices
- Configure folder options to show the file extension
- Configure IE settings to force the home page

## 1.3 Advanced Configuration

Vous avez un ordinateur utilisé par les visiteurs dans la salle de réception (sur le sous-réseau 192.168.0.0/24). Vous devez sécuriser cet ordinateur :

Pas d’accès au panneau de configuration

Pas d’accès à la configuration de la barre des tâches

Pas d’accès à l’icône du bureau


Lorsqu’un utilisateur se connecte, un script exécute Internet Explorer. Vous devez vous assurer que si un utilisateur de l’entreprise utilise cet ordinateur, ses politiques ne s’appliquent pas à cet ordinateur


## 1.4 Network Drive

Créer un partage de fichier NTFS sur le serveur Active Directory

Faites en sorte de monter ce partage réseau sur les PC Windows, sur la lettre W.

Utilisez le système intégré aux GPO, puis faites la même chose avec un script (CMD ou Powershell)

## 1.5 Windows Update

Configurer le service de mise à jour afin que les PC Windows se mettent à jour le plusrapidement possible, en dehors des heures de travail

## 1.6 Déploiement Applicatif

Déployer Notepad++ sur les postes de travail

