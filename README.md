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

![notif suppression de vssadmin](https://github.com/user-attachments/assets/066ad76f-9ce4-4029-b8fb-0c12cb68326f)


![source and target detect by the rule](https://github.com/user-attachments/assets/7778d9c7-81b0-4004-9084-60e64d11b6b6)


On peut effectivement voir dans Limacharlie le fichier malvaillant qui s'execute au niveau de la victime.

![process active on the network](https://github.com/user-attachments/assets/441cba4b-cfac-4fcf-877a-e880b7792a7a)



#### Ransomware
J'ai fait la simulation d'un ransmeware en utilisant PSRansom.

Telechargement et installation du Server C&C
![C2Server installation](https://github.com/user-attachments/assets/3b54a9b3-ddd2-4da5-9c7b-b84d91fe3aad)
![download PSRansom21](https://github.com/user-attachments/assets/834873df-ff59-40ab-b16a-ae9018f249c6)

Ecoute sur les tout les ports en attente de connection depuis le post de la victime
![listening on all ports](https://github.com/user-attachments/assets/b18acb47-adb6-43dc-bc30-71fdd2fdbab0)

Apres execution du script powershell, on chiffre les donnees et on les exfiltre:
![dossier a chiffrer](https://github.com/user-attachments/assets/8cc378d9-1a88-4931-91fb-f9ffe54483b7)
![dossier apres chiffrement](https://github.com/user-attachments/assets/8a71482f-10cc-4933-b354-9d2f755f5600)
![connection et exfiltration de donnnees](https://github.com/user-attachments/assets/c2f3c12f-daaa-4501-8211-a021e95c11ab)
![chiffrement et exifiltration des donnees](https://github.com/user-attachments/assets/b2a977e1-7678-411e-b79b-522937a10a11)
A l aide d'une note laisser dans le dossier chiffrer, on peut dechiffrer le dossier avec la cle de dechiffrement.
Note de chiffrement:
![Note de chiffrement](https://github.com/user-attachments/assets/6ef92b24-f63f-434f-b4e3-fe7e0e60cd04)
![Restauration des fichiers](https://github.com/user-attachments/assets/8d43b5ae-d40d-4241-b19b-010cc43a91d5)


# Detection

La detection de l attaque du lsass permet d'identifier le process a l origine de l attaque, mais une investigation du process en utilisant Virustotal ne nous permet pas d'avoir plus d'information sur ce dernier. Ceci s'expliaue par le fait que nous avon creer de toute piece le fichier malveillant et n est donc pas repertorier dans les base de donnees des OSINT
![virustotal inspection](https://github.com/user-attachments/assets/4541b518-96b0-424d-8957-19de5b19eb34)
![virustotal](https://github.com/user-attachments/assets/76986c4a-c823-4f0a-a78c-943ca6beff81)


## Telemetries Visualization
![overview of limacharlie](https://github.com/user-attachments/assets/044669be-6068-4826-bce5-8740015fac6d)
![malicious process](https://github.com/user-attachments/assets/ca3e7fd6-b779-40c9-bcd6-560206e71721)
![sensor ](https://github.com/user-attachments/assets/13baeb9f-503d-4269-bed6-baa4353d36e0)


## Blocking and Preventing Attacks

### Writing Detection Rules in LimaCharlie

![Rule Lsass Created](https://github.com/user-attachments/assets/05990230-b421-498e-b539-eaf451a4e649)

![rule for vssadmin delection](https://github.com/user-attachments/assets/096b7a91-9b36-43f1-96d4-065123c725fc)


### Application of detection rules
Pour detecter ces attaques nous avons ecrity et tester mise en place des regles.
![Detection rule applied](https://github.com/user-attachments/assets/b606aeda-bac3-42b7-b96e-c198ff3d46f3)
![detection rule in action](https://github.com/user-attachments/assets/4cd28af7-e10f-4a32-a59b-9b0abb5d6a4c)
![test rule](https://github.com/user-attachments/assets/563cf7c6-3523-44d2-ad05-5cce469f01c2)
