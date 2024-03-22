# Liens utiles 

https://gpsearch.azurewebsites.net/

https://learn.microsoft.com/en-us/troubleshoot/windows-server/group-policy/applying-group-policy-troubleshooting-guidance

https://www.antrimohamed.fr/wp-content/uploads/2014/04/Djoin/Offline-domain-Join.pdf

# Group Policy 

## 1.0 SECURITY GPO

You have to configure a GPO that will apply on all company domains.
This GPO is the main policy for account’s security in the company.
This policy must have the following parameters:
- Length : 6 characters
- Age maximum : 90 days
- System must remember the 5 last passwords
- An account must be locked after 5 invalid logons
- The counter of invalid logon must be reinitialized after one hour.
- 
All IT admins have a classic account and an account with administrative permissions.
The previous mustn’t apply on this administrator’s accounts and you must configure a password
policy for these accounts:
- Length : 8 characters
- Age maximum : 30 days
- System must remember the 10 last passwords
- An account must be locked after 3 invalid logons
- The counter of invalid logon must be reinitialized after 4 hour.


## 1.1 GPO FILTERING

Reporters’ computers are heterogeneous. Some reporters have Windows 11 but others have
Windows 7.
You have to apply an outbound firewall rules but outbound rules don’t exist on Windows 7. You
have to be sure the policy that modifies firewall rules only apply on Windows 11 computers.
This rule must allow outbound FTP connection on port 21.
  
In another hand you have a group of Administrative users that use an accounting software. You note that this software write many application logs that take too much space on the accounting
computers. Use a policy that modifies the maximum size of application log and that only applies on users that are member of the accounting group

## 1.2 GPO PARAMETERS

You have security GPO for all employees. You now have to configure the common parameter for
people of Administration.
Your policy must meet the following requirements:
- Apply the wallactus.png wallpaper
- Disable the possibility to change the wallpaper
- Prevent user to change screen saver
- Disable the history of recent opened documents
- Prevent user to adding printers
- Disable access to control panel, command prompt. Also disable the ability to open task manager with Ctrl + Alt + del
- You must prevent users to plug USB devices
- Publish the administration shared folder as network drive
- Configure folder options to show the file extension
- Configure IE settings to force the home page

## 1.3 Advanced Configuration

You have a computer that is used by visitors in the reception room.
You have to secure this computer:
- No access to control panel
- No access to task bar configuration
- No access to desktop icon
- When a user logon a script run internet explorer
You have to be sure that if a company user uses this computer their policies are not applied to this computer


## 1.4 Network Drive

Créer un partage de fichier NTFS sur le serveur Active Directory
Faites en sorte de monter ce partage réseau sur les PC Windows, sur la lettre W.
Utilisez le système intégré aux GPO, puis faites la même chose avec un script (CMD ou Powershell)

## 1.5 Windows Update

Configurer le service de mise à jour afin que les PC Windows se mettent à jour le plusrapidement possible, en dehors des heures de travail

## 1.6 Déploiement Applicatif

Déployer Notepad++ sur les postes de travail
