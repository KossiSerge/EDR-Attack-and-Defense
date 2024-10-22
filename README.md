# EDR Attack and Defense

#Project:
This home lab aim is to simulating differents attacks on an endpoints and implementing some detection and response tools. I primarly used the Eric Capuano's article, "so you want to be a soc analyst " and the PSRansom ransomware simulation along with LimaCharlie [EDR] and Sliver [C&amp;C].
Eric Capuano's blog post: https://blog.ecapuano.com/p/so-you-want-to-be-a-soc-analyst-intro
# Setup

## Setting up the Victim VM (Windows 11)
We are disabling security features on our Windows VM.
![disabling microsoftdefender](https://github.com/user-attachments/assets/a9e7f033-a086-435b-aac8-e054cd57081b)
![disable services via registry](https://github.com/user-attachments/assets/912095f4-7ffe-428c-b255-f177fcf78b35)

## Setting up the Attack VM (Linux)
Installation of Sliver, which is a C&C (Command and Control) framework.
![installing Silver ans mingw](https://github.com/user-attachments/assets/3bfff611-8679-4c02-b1c5-60e7006d68f5)
We will now develop our malicious executable (implant).
![launch of silver and implants config](https://github.com/user-attachments/assets/86c0ba37-31f6-4f70-b6e3-04076ecc10ad)

Execution of the implant on the victim's machine, making it active on the victim's system. This allows us to collect information about the victim, such as the defense mechanisms that are in place.
![processes2](https://github.com/user-attachments/assets/ebce1eed-af2a-4474-b22c-3e66b7eaf28b)
![implant running](https://github.com/user-attachments/assets/8ea67977-b842-46b1-971e-63e6d3e0966b)

# Implementation of Various Attacks
## lsass.exe Attack

An attack targeting the lsass.exe process, which is captured in the telemetry data. The lsass.exe process stores sensitive information, including user credentials, especially those of administrators.

![detection rule in action](https://github.com/user-attachments/assets/4cd28af7-e10f-4a32-a59b-9b0abb5d6a4c)

![source and target detect by the rule](https://github.com/user-attachments/assets/7778d9c7-81b0-4004-9084-60e64d11b6b6)


We can clearly see the malicious file executed on the victim's machine in LimaCharlie.

![process active on the network](https://github.com/user-attachments/assets/441cba4b-cfac-4fcf-877a-e880b7792a7a)

The detection of the lsass attack allows us to identify the process responsible for the attack. However, investigating the process using VirusTotal does not provide us with additional information. This is because we created the malicious file from scratch, and it is therefore not listed in OSINT databases

![virustotal](https://github.com/user-attachments/assets/76986c4a-c823-4f0a-a78c-943ca6beff81)

## vssac Credentials Dump Attack

![vssadmin suppression](https://github.com/user-attachments/assets/54d88213-ba9e-495b-b794-ea4ebba74898)
![details suppression de vssadmin](https://github.com/user-attachments/assets/cc47a5d5-eb51-4b94-9a4d-5b25afb2bc9a)

## Ransomware attack
I simulated a ransomware attack using PSRansom.
![C2Server installation](https://github.com/user-attachments/assets/3b54a9b3-ddd2-4da5-9c7b-b84d91fe3aad)

![connection et exfiltration de donnnees](https://github.com/user-attachments/assets/c2f3c12f-daaa-4501-8211-a021e95c11ab)


After executing the PowerShell script, the target folder is encrypted and exfiltrated to the Command and Control server


![Note de chiffrement](https://github.com/user-attachments/assets/6ef92b24-f63f-434f-b4e3-fe7e0e60cd04)


![Execution powershell](https://github.com/user-attachments/assets/67b7bdee-0ba0-4fc5-bbba-5563e32e89b9)

![Restauration des fichiers](https://github.com/user-attachments/assets/8d43b5ae-d40d-4241-b19b-010cc43a91d5)
![dossier a chiffrer](https://github.com/user-attachments/assets/5fbf21a7-e57b-434a-869d-449edb6b6863)

# Rule Creation
## Writing Detection Rules in LimaCharlie
### Rule to Mitigate the lsass Attack
![Rule Lsass Created](https://github.com/user-attachments/assets/05990230-b421-498e-b539-eaf451a4e649)
### Rule to Mitigate the vssas Attack"
![rule for vssadmin delection](https://github.com/user-attachments/assets/096b7a91-9b36-43f1-96d4-065123c725fc)

