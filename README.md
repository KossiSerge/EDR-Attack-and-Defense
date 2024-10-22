# EDR-Detection-Engineering
SOC Analyst lab using LimaCharlie [EDR], Sliver [C&amp;C], and VMs to simulate adversary behavior, create detection rules, block attacks, fine-tune alerts, and integrate YARA for threat detection.

# Set Up

## Setting Victim VM
We are disabling our windows VM safeguard
![disable services via registry](https://github.com/user-attachments/assets/912095f4-7ffe-428c-b255-f177fcf78b35)
![disabling microsoftdefender](https://github.com/user-attachments/assets/a9e7f033-a086-435b-aac8-e054cd57081b)

![unrestriced execution policy on Windows 11](https://github.com/user-attachments/assets/6e71de30-85ac-4a2a-863f-311eec69d40a)

## Setting Attack VM
Installation of Sliver
![installing Silver ans mingw](https://github.com/user-attachments/assets/3bfff611-8679-4c02-b1c5-60e7006d68f5)

![implant running](https://github.com/user-attachments/assets/8ea67977-b842-46b1-971e-63e6d3e0966b)

![launch of silver and implants config](https://github.com/user-attachments/assets/86c0ba37-31f6-4f70-b6e3-04076ecc10ad)


### Sliver
![Targetting lsass exe](https://github.com/user-attachments/assets/d736d604-ba38-4695-8ad8-b869da321ce0)
![session check in silver server](https://github.com/user-attachments/assets/a02d2362-f03d-4f74-968b-e0a02ff7b3b4)
![session check2](https://github.com/user-attachments/assets/3065253e-1b1d-4165-bdb4-154f117eedda)
![vssadmin deletion capture](https://github.com/user-attachments/assets/bee32daa-6621-4539-a96c-7f630c11d5e5)

![network connection2](https://github.com/user-attachments/assets/45eb1ee5-cd97-424e-8b43-c644244d89bd)
![network connections](https://github.com/user-attachments/assets/3078f86b-15de-4447-a2ab-ef99234876cc)
![network connections1](https://github.com/user-attachments/assets/06464058-bc6b-44c2-802c-b44ec75540fb)
![Command line showing SLIM_ATOM](https://github.com/user-attachments/assets/90e4395b-4542-496f-ae53-ad9feab247b5)
![details suppression de vssadmin](https://github.com/user-attachments/assets/dbe90658-29df-4b9a-a8e6-ecd2a43cc410)

### PSRansom
Downloading PSRansom
![download PSRansom](https://github.com/user-attachments/assets/be28fcb9-8e40-46b1-9bfa-80665dffef2f)
![download PSRansom21](https://github.com/user-attachments/assets/834873df-ff59-40ab-b16a-ae9018f249c6)
![downloadPSRansom2](https://github.com/user-attachments/assets/39e4e4ad-b5a1-44e8-8ad2-9f5355446f68)
![listening on all ports](https://github.com/user-attachments/assets/b18acb47-adb6-43dc-bc30-71fdd2fdbab0)
![C2Server installation](https://github.com/user-attachments/assets/3b54a9b3-ddd2-4da5-9c7b-b84d91fe3aad)
![Restauration des fichiers](https://github.com/user-attachments/assets/8d43b5ae-d40d-4241-b19b-010cc43a91d5)
![dossier a chiffrer](https://github.com/user-attachments/assets/8cc378d9-1a88-4931-91fb-f9ffe54483b7)
![dossier apres chiffrement](https://github.com/user-attachments/assets/8a71482f-10cc-4933-b354-9d2f755f5600)
![connection et exfiltration de donnnees](https://github.com/user-attachments/assets/c2f3c12f-daaa-4501-8211-a021e95c11ab)

![Note de chiffrement](https://github.com/user-attachments/assets/6ef92b24-f63f-434f-b4e3-fe7e0e60cd04)

# Implementing Attacks
![attacking](https://github.com/user-attachments/assets/33c378b1-4fbc-4327-b2e9-d8a65a29a017)


## Adversary Simulation and Noise Generation

### Attacks Results
![notif suppression de vssadmin](https://github.com/user-attachments/assets/066ad76f-9ce4-4029-b8fb-0c12cb68326f)
![lsass dmp](https://github.com/user-attachments/assets/3d07f264-cba3-45a4-aa02-9de528a2c1df)

# Encryption and Exfiltration of data
![chiffrement et exifiltration des donnees](https://github.com/user-attachments/assets/b2a977e1-7678-411e-b79b-522937a10a11)


# Detection

## Telemetries Visualization
![overview of limacharlie](https://github.com/user-attachments/assets/044669be-6068-4826-bce5-8740015fac6d)
![malicious process](https://github.com/user-attachments/assets/ca3e7fd6-b779-40c9-bcd6-560206e71721)
![process active on the network](https://github.com/user-attachments/assets/91a0e6ec-c696-4b32-a820-b3138be7f874)
![realtime view](https://github.com/user-attachments/assets/4b737f71-c0b5-495e-bbea-0b15a807df2d)
## Blocking and Preventing Attacks

### Writing Detection Rules in LimaCharlie

![Rule Lsass Created](https://github.com/user-attachments/assets/05990230-b421-498e-b539-eaf451a4e649)

![rule for vssadmin delection](https://github.com/user-attachments/assets/096b7a91-9b36-43f1-96d4-065123c725fc)


### Application of detection rules
![Detection rule applied](https://github.com/user-attachments/assets/b606aeda-bac3-42b7-b96e-c198ff3d46f3)
![detection rule in action](https://github.com/user-attachments/assets/4cd28af7-e10f-4a32-a59b-9b0abb5d6a4c)
![test rule](https://github.com/user-attachments/assets/563cf7c6-3523-44d2-ad05-5cce469f01c2)

# Telemetries
![sensor ](https://github.com/user-attachments/assets/13baeb9f-503d-4269-bed6-baa4353d36e0)
![source and target detect by the rule](https://github.com/user-attachments/assets/3d01d8c1-f210-48f8-83ce-a9575b68f87c)

### Virus Total

![virustotal inspection](https://github.com/user-attachments/assets/4541b518-96b0-424d-8957-19de5b19eb34)
![virustotal](https://github.com/user-attachments/assets/76986c4a-c823-4f0a-a78c-943ca6beff81)

### Fine-Tuning Detection Rules



# Key Takeaways

### Lessons Learned:
- **Hands-on Experience**: Working with LimaCharlie provided me with a deeper understanding of detection engineering.
- **Rule Crafting**: Creating accurate and efficient detection rules requires testing and fine-tuning.
- **Real-Time Defense**: Setting up auto-blocking for attacks provides a proactive approach to threat management.
- **YARA Integration**: Using YARA rules adds another layer of detection for file-based threats.
