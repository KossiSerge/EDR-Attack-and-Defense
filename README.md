# EDR-Detection-Engineering
SOC Analyst lab using LimaCharlie [EDR], Sliver [C&amp;C], and VMs to simulate adversary behavior, create detection rules, block attacks, fine-tune alerts, and integrate YARA for threat detection.

# Set Up

## Setting Victim VM
We are disabling our windows VM safeguard
On desactive le parefeu et microsoft defender 
![disabling microsoftdefender](https://github.com/user-attachments/assets/a9e7f033-a086-435b-aac8-e054cd57081b)
![disable services via registry](https://github.com/user-attachments/assets/912095f4-7ffe-428c-b255-f177fcf78b35)

## Setting Attack VM
Installation of Sliver qui un C&C
![installing Silver ans mingw](https://github.com/user-attachments/assets/3bfff611-8679-4c02-b1c5-60e7006d68f5)
On va maintenant develloper notre executable malicieux(implant)
![launch of silver and implants config](https://github.com/user-attachments/assets/86c0ba37-31f6-4f70-b6e3-04076ecc10ad)

Execution sur la machine victim, ce qui fait qu elle est active sur la machine victime et on peut collecter des information sur la victime, comme les moyens de defense qui sont mise en place.
![processes2](https://github.com/user-attachments/assets/ebce1eed-af2a-4474-b22c-3e66b7eaf28b)
![implant running](https://github.com/user-attachments/assets/8ea67977-b842-46b1-971e-63e6d3e0966b)

### Implementation de quelques attaques

#### Attaque du lsass.exe

Attaque du lsass.exe, qui est enregistre dans la telemetrie. Le lsass.exe qui contient des mots de passe des utilisatuers surtout ceux des administrateurs


![detection rule in action](https://github.com/user-attachments/assets/4cd28af7-e10f-4a32-a59b-9b0abb5d6a4c)

![source and target detect by the rule](https://github.com/user-attachments/assets/7778d9c7-81b0-4004-9084-60e64d11b6b6)


On peut effectivement voir dans Limacharlie le fichier malvaillant qui s'execute au niveau de la victime.

![process active on the network](https://github.com/user-attachments/assets/441cba4b-cfac-4fcf-877a-e880b7792a7a)

La detection de l attaque du lsass permet d'identifier le process a l origine de l attaque, mais une investigation du process en utilisant Virustotal ne nous permet pas d'avoir plus d'information sur ce dernier. Ceci s'expliaue par le fait que nous avon creer de toute piece le fichier malveillant et n est donc pas repertorier dans les base de donnees des OSINT

![virustotal](https://github.com/user-attachments/assets/76986c4a-c823-4f0a-a78c-943ca6beff81)

Attaque credentials dump vssac

![vssadmin suppression](https://github.com/user-attachments/assets/54d88213-ba9e-495b-b794-ea4ebba74898)
![details suppression de vssadmin](https://github.com/user-attachments/assets/cc47a5d5-eb51-4b94-9a4d-5b25afb2bc9a)
#### Ransomware
J'ai fait la simulation d'un ransmeware en utilisant PSRansom.
Telechargement et installation du Server C&C
![C2Server installation](https://github.com/user-attachments/assets/3b54a9b3-ddd2-4da5-9c7b-b84d91fe3aad)


Apres execution du script powershell, on chiffre les donnees et on les exfiltre:



![connection et exfiltration de donnnees](https://github.com/user-attachments/assets/c2f3c12f-daaa-4501-8211-a021e95c11ab)

Detectioon dans limacharlie de l execution du powshell
![dossier a chiffrer](https://github.com/user-attachments/assets/8cc378d9-1a88-4931-91fb-f9ffe54483b7)
![Execution powershell](https://github.com/user-attachments/assets/67b7bdee-0ba0-4fc5-bbba-5563e32e89b9)


A l aide d'une note laisser dans le dossier chiffrer, on peut dechiffrer le dossier avec la cle de dechiffrement.
Note de chiffrement:
![Note de chiffrement](https://github.com/user-attachments/assets/6ef92b24-f63f-434f-b4e3-fe7e0e60cd04)
![Restauration des fichiers](https://github.com/user-attachments/assets/8d43b5ae-d40d-4241-b19b-010cc43a91d5)


## Creation de regles 

### Writing Detection Rules in LimaCharlie
Regle pour parer a l attaque sur le lsass
![Rule Lsass Created](https://github.com/user-attachments/assets/05990230-b421-498e-b539-eaf451a4e649)
Regle pour parer a l attaque sur le vssas
![rule for vssadmin delection](https://github.com/user-attachments/assets/096b7a91-9b36-43f1-96d4-065123c725fc)

