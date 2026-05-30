# Azure AD Connect

## Overview

In this home lab, I demonstrate how to configure **Azure AD Connect** to synchronize an on-premises Active Directory environment with Microsoft Entra ID (Azure AD). This setup creates a hybrid identity environment, allowing users to access both on-prem and cloud resources with the same credentials. It reflects a real-world enterprise scenario where organizations integrate their local infrastructure with cloud services like Microsoft 365.

---

## **Objectives**

- Configure an alternative UPN suffix in Active Directory
- Prepare on-prem accounts for cloud synchronization
- Connect on-prem Active Directory to Microsoft Entra ID
- Synchronize users and groups to the cloud
- Validate successful hybrid identity integration

---

## **Documentation (Step-by-Step with Purpose)**

### **Azure AD Connect 1**

I added an **alternative UPN suffix** in Active Directory to match my Microsoft 365 domain.

Adding a UPN suffix that matches the Microsoft 365 tenant allows users to have a valid login identity for cloud services.

![image alt](https://github.com/Hamedadams01/Axure-Active-Directory-Connection/blob/c3b672cfb5a5ffb6b23e828dd85e76d83037263e/Screenshot_2026-04-17_064943.webp)
![image alt](https://github.com/Hamedadams01/Axure-Active-Directory-Connection/blob/c3b672cfb5a5ffb6b23e828dd85e76d83037263e/Screenshot_2026-04-17_064957.webp)

The Microsoft 365 tenant domain houtech272.onmicrosoft.com is being added so that on-premises user accounts can be assigned this suffix. This makes their usernames match the cloud domain, which is required for proper synchronization and SSO to work.

![image alt](https://github.com/Hamedadams01/Axure-Active-Directory-Connection/blob/c3b672cfb5a5ffb6b23e828dd85e76d83037263e/Screenshot_2026-04-17_065053.webp)

After adding the new UPN suffix, each user account (starting with the Admin account) needs to be updated to use the new cloud-routable domain suffix. This ensures the account will sync correctly to Microsoft Entra ID and the user can sign in using their Microsoft 365 credentials.

![image alt](https://github.com/Hamedadams01/Axure-Active-Directory-Connection/blob/c3b672cfb5a5ffb6b23e828dd85e76d83037263e/Screenshot_2026-04-17_065229.webp)

Azure AD Connect needs to authenticate with your Microsoft 365 tenant in the cloud. You must provide Global Administrator credentials so the tool has permission to create the sync connection and write user objects to Entra ID
![image alt](https://github.com/Hamedadams01/Axure-Active-Directory-Connection/blob/c3b672cfb5a5ffb6b23e828dd85e76d83037263e/Screenshot_2026-04-15_140141.webp)
![image alt](https://github.com/Hamedadams01/Axure-Active-Directory-Connection/blob/c3b672cfb5a5ffb6b23e828dd85e76d83037263e/Screenshot_2026-04-15_140644.webp)
![image alt](https://github.com/Hamedadams01/Axure-Active-Directory-Connection/blob/c3b672cfb5a5ffb6b23e828dd85e76d83037263e/Screenshot_2026-04-15_141419.webp)

This confirms that the sync worked and on-premises AD accounts have been created in the cloud.

![image alt](https://github.com/Hamedadams01/Axure-Active-Directory-Connection/blob/c3b672cfb5a5ffb6b23e828dd85e76d83037263e/Screenshot_2026-04-16_074603.webp)

This confirms that not just user accounts, but also AD security groups have been successfully synced to the cloud. 

![image alt](https://github.com/Hamedadams01/Axure-Active-Directory-Connection/blob/c3b672cfb5a5ffb6b23e828dd85e76d83037263e/Group_Entra_ID.webp)
