# 🖥️ AWS Active Directory Lab (Windows EC2)

This lab demonstrates provisioning **Active Directory Domain Services (AD DS)** on an AWS Windows Server EC2 instance, promoting it to a **Domain Controller**, and creating basic user accounts.

---

## Prerequisites
- AWS Account
- macOS device (lab done from Mac)
- Microsoft Remote Desktop installed
- RDP access allowed in AWS Security Group (my IP only)

---

## 1️⃣ Launch Windows Server EC2
- Chose **Windows Server 2019** AMI.
- Kept **default storage** for simplicity (enough for lab use).
- Kept **default VPC network** settings.
- Created a **new key pair** for RDP access.

**Reasoning:**  
Defaults speed up deployment, reduce configuration complexity, and avoid misconfiguring networking for a single-server lab.

**📸 Screenshot:**  
![EC2 Running](<img width="1851" height="1172" alt="Image" src="https://github.com/user-attachments/assets/d00e8934-d07a-4fcd-bc3c-e3076d4b7314" />)

---

## 2️⃣ Connect via RDP
- Downloaded the RDP file from AWS Console.
- Used key pair to decrypt Windows password in AWS Console.
- Connected via **Microsoft Remote Desktop** from Mac.

**📸 Screenshot:**  
![RDP Desktop](<img width="1819" height="1072" alt="Image" src="https://github.com/user-attachments/assets/edc7bb6e-76ab-48e4-8c68-16c8b7ca1475" />)

---

## 3️⃣ Install Active Directory Domain Services
- In **Server Manager → Add Roles and Features**:
  - Chose **Active Directory Domain Services**.
  - Accepted required features.

**📸 Screenshot:**  
![AD DS Role Selected](<img width="1280" height="720" alt="Image" src="https://github.com/user-attachments/assets/45822fea-e631-4d18-944c-ac48ecf03248" />)

---

## 4️⃣ Promote to Domain Controller (New Forest)
- Clicked the **yellow triangle** in Server Manager → **Promote this server to a domain controller**.
- Chose **Add a new forest** → Domain: `mylab.local`.
- Left functional levels default, kept DNS/GC checked.
- Set DSRM password.

---

## 5️⃣ Verify Domain
- After reboot, logged in with `mylab\Administrator`.
- Confirmed domain in **Server Manager → Local Server**.

**📸 Screenshot:**  
![Domain Confirmed](<img width="1280" height="720" alt="Image" src="https://github.com/user-attachments/assets/c69d8f98-e9ab-4952-b861-f75e06e5eaa3" />)

---

## 6️⃣ Create OUs and Users
- Opened **Active Directory Users and Computers (ADUC)**.
- Created OU:
  - `Users`
- Added 2 test users: `jdoe`, `jsmith`.

**📸 Screenshot:**   
![ADUC Users](<img width="2560" height="1440" alt="Image" src="https://github.com/user-attachments/assets/878dd790-660e-4d95-a18b-c6d943f1efb0" />)

---

## 7️⃣ Proof This PC is in the Domain
- Verified in **System → About** that the machine is part of `mylab.local`.

**📸 Screenshot:**  
![System About](<img width="400" height="473" alt="Image" src="https://github.com/user-attachments/assets/e2cc1f26-adee-42b2-afcb-eee5cbaedc1f" />)  
![Local Server Domain](<img width="2560" height="1440" alt="Image" src="https://github.com/user-attachments/assets/a4a58859-3aa7-417d-953b-258a2ca7644c" />)

---

## ✅ Lab Outcomes
- Installed AD DS on Windows Server EC2.
- Created a new forest and promoted the server to Domain Controller.
- Added an OU and test users.
- Verified the server is in the created domain.

---

## 🔐 Security Considerations
- RDP allowed **only** from my IP.
- Domain services not exposed to public internet.
- Default DNS and paths kept for lab simplicity.
