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

 

📷 Screenshot Placeholder: 

AD Groups.png

 

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

 

📷 Screenshot Placeholder: 

[INSERT SCREENSHOT – AD Users and Groups Here] 

 

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

 

📷 Screenshot Placeholder: 

[INSERT SCREENSHOT – NTFS Permissions Configuration Here] 

 

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

 

📷 Screenshot Placeholder: 

[INSERT SCREENSHOT – GPO Settings Here] 

 

--- 

 

## ☁️ Microsoft 365 Administration 

 

### 5️⃣ Tenant & Identity Configuration 

 

- Created Microsoft 365 trial tenant 

- Verified custom domain 

- Configured DNS records (MX, SPF) 

- Created 20 cloud users 

- Assigned licenses based on department roles 

 

📷 Screenshot Placeholder: 

[INSERT SCREENSHOT – M365 Users & Licenses Here] 

 

--- 

 

### 6️⃣ Exchange Online Administration 

 

Configured: 

 

- Shared mailboxes (info@, finance@) 

- Send As permissions 

- Send on Behalf permissions 

- Mail forwarding for management 

- Mail flow rule to block external auto-forwarding 

 

Security Best Practice: 

Blocked automatic external forwarding to prevent data leakage. 

 

📷 Screenshot Placeholder: 

[INSERT SCREENSHOT – Mail Flow Rule Configuration Here] 

 

--- 

 

### 7️⃣ Multi-Factor Authentication (MFA) 

 

- Enabled MFA for all users 

- Created break-glass Global Admin account 

- Excluded emergency account from Conditional Access 

- Tested user MFA registration process 

 

📷 Screenshot Placeholder: 

[INSERT SCREENSHOT – MFA Settings Here] 

 

--- 

 

### 8️⃣ Conditional Access Policy 

 

Implemented security policy: 

 

Policy Name: Require MFA Outside Trusted Locations 

 

Configuration: 

- Applied to all users 

- Excluded break-glass admin 

- Required MFA when logging in outside trusted IP range 

 

This simulates enterprise-level identity protection. 

 

📷 Screenshot Placeholder: 

[INSERT SCREENSHOT – Conditional Access Policy Here] 

 

--- 

 

## 📂 SharePoint Online Configuration 

 

- Created department SharePoint sites 

- Configured permission inheritance 

- Assigned department-specific access 

- Restricted external sharing for sensitive departments 

- Enabled version history 

 

📷 Screenshot Placeholder: 

[INSERT SCREENSHOT – SharePoint Site Permissions Here] 

 

--- 

 

## 💬 Microsoft Teams Administration 

 

- Created department Teams 

- Configured team membership via M365 groups 

- Managed messaging policies 

- Controlled guest access 

- Applied governance settings 

 

📷 Screenshot Placeholder: 

[INSERT SCREENSHOT – Teams Admin Center Here] 

 

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
