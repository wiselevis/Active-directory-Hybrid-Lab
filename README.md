# Active Directory & Microsoft 365 Hybrid Administration Lab 

 

## 📌 Project Overview 

 

This project demonstrates the design and implementation of a hybrid IT environment combining on-premises Active Directory with Microsoft 365 (Entra ID). 

 

The lab simulates a 20-user company environment and focuses on identity management, security controls, group policy configuration, and Microsoft 365 administration. 

 

This project was built using a Windows Server virtual machine (VMware) and a Microsoft 365 trial tenant. 

 

--- 

 

## 🏢 Lab Scenario 

 

Company Name: WiseTech Services Ltd   

Users: 20   

Departments: 

- Managers 

- Finance 

- IT 

- Staff

 

Environment: 

- Windows Server (Active Directory Domain Services) 

- Domain: WISE01.local 

- Microsoft 365 Tenant 

- Entra ID (Azure AD) 

- SharePoint Online 

- Microsoft Teams 

- Exchange Online 

 

--- 

 

## 🖥️ Active Directory Configuration 

 

### 1️⃣ OU Structure Design 

 

Created a structured Organizational Unit layout to separate users, computers, and security groups. 

 

OU Structure: 

 

WiseTech 

- Users 

  - Managers 

  - Finance 

  - Staff 

  - IT 

- Computers 

  - Laptops 

  - Desktops 

- Groups 

 <img width="1280" height="680" alt="AD-OU-Structure" src="https://github.com/user-attachments/assets/375b156f-ee33-4c55-8fe0-509590846079" />




--- 

 

### 2️⃣ User & Group Management 

 

- Created 20 domain users 

- Implemented naming convention: firstname.lastname 

- Created security groups: 

  - Managers_GG 

  - Finance_GG 

  - Staff_GG 

  - IT_Admins_GG 

- Applied group-based access control (no direct user permissions) 

 
 <img width="1280" height="680" alt="AD-OU-Users" src="https://github.com/user-attachments/assets/2e016b25-36fb-47ad-b4a7-47c267bc5c47" />



--- 

 

### 3️⃣ NTFS File Server Permissions 

 

Configured shared company folders: 

 

D:\CompanyData 

- Managers 

- Finance 

- Staff 

- Shared 

 

Permissions: 

- Managers folder → Managers_GG only 

- Finance folder → Finance_GG only 

- Staff folder → Staff_GG only 

- Shared folder → All departments (read/write) 

 

Applied proper NTFS permission inheritance and avoided using “Everyone”. 

  
<img width="767" height="520" alt="AD-Permission-Finance" src="https://github.com/user-attachments/assets/5004c87f-44d0-449b-9295-43aa6c4e9521" />

<img width="363" height="450" alt="AD-Permission-for-finance" src="https://github.com/user-attachments/assets/51ab034a-1948-41ed-a993-7a2eea1a4347" />

--- 

 

### 4️⃣ Group Policy Implementation (GPO) 

 

Implemented the following GPO configurations: 

 

Security Policies: 

- Password complexity enabled 

- Account lockout policy configured 

- Screen lock after inactivity 

 

User Restrictions: 

- Disabled Control Panel for Staff 

- Restricted software installation 

- Disabled USB storage (for non-IT users) 

 

Environment Configuration: 

- Mapped network drives automatically 

- Configured company desktop wallpaper 

- Redirected user Documents folder to file server 

 <img width="754" height="530" alt="AD-GPOS" src="https://github.com/user-attachments/assets/18564849-8a29-4fe7-849d-9da42e36d74e" />




--- 

 

## ☁️ Microsoft 365 Administration 

 

### 5️⃣ Tenant & Identity Configuration 

 

- Created Microsoft 365 trial tenant 

- Verified custom domain 

- Configured DNS records (MX, SPF) 

- Created 10 cloud users 

- Assigned licenses based on department roles 

 




<img width="1646" height="1035" alt="AD-Cloud-Licenses" src="https://github.com/user-attachments/assets/b9ce0b20-cfb2-4bb0-ad4f-e1856d7409ce" />

 

--- 
## 🔄 Hybrid Identity – On-Prem AD to Microsoft Entra ID 

 

I configured Azure AD Connect to synchronize on-premises Active Directory with Microsoft Entra ID using Password Hash Synchronization. 

 

### ✅ Verification Performed 

 

• Successful sync cycles confirmed in Synchronization Service   
<img width="794" height="625" alt="AD-Miisclient-Snyc" src="https://github.com/user-attachments/assets/7e3fad7b-14d0-4375-8dbf-6e6ac44af751" />

• PowerShell scheduler verified using: 



<img width="1266" height="673" alt="Image" src="https://github.com/user-attachments/assets/a5fe21ed-a58b-407b-8960-06919747caae" />



### 6️⃣ Exchange Online Administration 

 

Configured: 

 

- Shared mailboxes (info@, helpdesk@) 

- Send As permissions 

- Send on Behalf permissions 

- Mail forwarding for management 

- Mail flow rule to block external auto-forwarding 

 

Security Best Practice: 

Blocked automatic external forwarding to prevent data leakage. 

 <img width="1860" height="1049" alt="Sharemailbox" src="https://github.com/user-attachments/assets/4ff57603-e911-4b13-b842-ba1eaa0403aa" />




 

--- 

 

### 7️⃣ Multi-Factor Authentication (MFA) 

 

- Enabled MFA for all users 

- Created break-glass Global Admin account 

- Excluded emergency account from Conditional Access 

- Tested user MFA registration process 

 



 <img width="1353" height="1072" alt="AD-MFA-USERS" src="https://github.com/user-attachments/assets/13cfb660-e2a3-4e60-abf1-4a2e24dae7e9" />


 

--- 

 

### 8️⃣ Conditional Access Policy 

 

Implemented security policy: 

 

Policy Name: Require MFA Outside Trusted Locations 

 

Configuration: 

- Applied to all users 

- Excluded break-glass admin 

- Required MFA when logging in outside trusted IP range 

 

This simulates enterprise-level identity protection. 

 



 <img width="1664" height="1037" alt="Mfa" src="https://github.com/user-attachments/assets/08dd5a15-0a27-4ba3-b301-3d1bd4afdcd3" />


--- 

 

## 📂 SharePoint Online Configuration 

 

- Created department SharePoint sites 

- Configured permission inheritance 

- Assigned department-specific access 

- Restricted external sharing for sensitive departments 

- Enabled version history 

 



 

--- 

 

## 💬 Microsoft Teams Administration 

 

- Created department Teams 

- Configured team membership via M365 groups 

- Managed messaging policies 

- Controlled guest access 

- Applied governance settings 

 

 <img width="1861" height="1038" alt="AD-Teams-groups" src="https://github.com/user-attachments/assets/0ed6b815-e8b3-44dc-b04e-ad4a4bb1a5b9" />


 

--- 

 

## 🔐 Security & Governance Implementation 

 

Security measures implemented in this lab: 

 

- Group-based access control 

- Least privilege role assignment 

- Break-glass emergency admin account 

- Conditional Access enforcement 

- Mail flow security policy 

- NTFS permission best practices 

 

--- 

 

## 🔄 Joiner, Mover, Leaver Simulation 

 

Tested identity lifecycle management: 

 

New Joiner: 

- Created AD account 

- Assigned group membership 

- Provisioned mailbox 

- Assigned license 

- Enforced MFA 

 

Department Change: 

- Modified group membership 

- Updated SharePoint access 

 

Leaver: 

- Disabled AD account 

- Removed license 

- Secured mailbox data 

- Revoked sessions 

 

--- 

 

## 🛠️ Troubleshooting Scenarios Tested 

 

- User unable to access shared folder 

- MFA registration failure 

- Mail flow rule blocking issue 

- Incorrect DNS configuration 

- Group Policy not applying (gpupdate /force troubleshooting) 

 

--- 

 

## 📚 Key Learning Outcomes 

 

Through this lab I gained hands-on experience in: 

 

- Active Directory structure design 

- NTFS permissions & inheritance 

- Group Policy configuration 

- Microsoft 365 identity administration 

- Exchange Online security configuration 

- Conditional Access implementation 

- SharePoint permission management 

- Teams governance 

- Enterprise security best practices 

 

--- 

 

## ✅ Conclusion 

 

This lab demonstrates practical experience managing a hybrid Active Directory and Microsoft 365 environment. 

 

The focus was on secure identity management, structured access control, and enterprise-level configuration aligned with real-world IT administration practices.
