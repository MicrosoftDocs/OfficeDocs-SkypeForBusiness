---
title: Identity models and authentication
author: MSFTTracyP
ms.author: tracyp
manager: dansimp
ms.date: 09/22/2020
ms.topic: reference
ms.service: msteams
ms.reviewer: anwara
audience: admin
localization_priority: Normal
search.appverid: MET150
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
description: Learn about the different identity models for Microsoft Teams such as cloud-only and hybrid. Also learn about multi-factor authentication.
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-mar2020
---

# Identity models and authentication in Microsoft Teams

Microsoft Teams supports all the identity models that are available with Microsoft 365 and Office 365. Supported identity models include:

-   **Cloud-only**: In this model, a user is created and managed in Microsoft 365 or Office 365 and stored in Azure Active Directory (Azure AD), and the credentials of the user sign-in (account name and password) are verified by Azure AD.

-   **Hybrid identity**: In this model, the user account credentials is managed in an on-premises Active Directory Domain Services (AD DS) domain controller, and the accounts and hashes of the AD DS-hashed passwords are synchronized to Azure AD. The user enters the same password on-premises as they do in the cloud, and at sign-in the password is verified by Azure AD. This model uses Azure AD Connect.

-   **Federated Identity**: This model requires a synchronized identity with the user password is verified by the on-premises identity provider. With this model, the password hash does not need to be synchronized to Azure AD, and Active Directory Federation Services (ADFS) or a third-party identity provider is used to authenticate users against the on-premises Active Directory.

## Configurations

Depending on your organization's decisions of which identity model to implement and use, the implementation requirements may vary. Refer to the requirements table below to ensure that your deployment meets these prerequisites. If you have already deployed Microsoft 365 or Office 365 and have already implemented the identity and authentication method, you may skip these steps.


|Identity Model |Deployment Checklist  |Additional Information  |
|---------|---------|---------|
|All     |<ol type="1"><li>Compare Microsoft 365 and Office 365 Plan Options and obtain a subscription</li><li>Create a Microsoft 365 or Office 365 organization</li><li>Assign Microsoft 365 or Office 365 licenses to the tenant</li><li>Configure Domains and admin users</li><li>Continue with Identity Model specific instructions</li></ol>          |<ul style="list-style-type:none"><li>[Microsoft 365 and Office 365 Plan Options](https://technet.microsoft.com/library/office-365-plan-options.aspx)</li><li>[Compare Microsoft 365 Apps for business Plans](https://go.microsoft.com/fwlink/?linkid=854617)</li><li>[Manage subscription licenses](https://support.office.com/article/Buy-licenses-for-your-Office-365-for-business-subscription-36081d8d-b3fa-4948-8c34-e217bba825e1)</li><li>[Add licenses to a subscription](https://support.office.com/article/Add-licenses-to-a-subscription-paid-for-using-a-product-key-4fb4bd7e-3920-4ce0-98fb-0c06e3fedf53)</li><li>[Set up Microsoft 365 for business](https://support.office.com/Article/set-up-Office-365-for-business-6a3a29a0-e616-4713-99d1-15eda62d04fa)</li><li>[Add users and domain with the setup wizard](https://support.office.com/article/Add-users-and-domain-with-the-setup-wizard-6383f56d-3d09-4dcb-9b41-b5f5a5efd611)</li><li>Note: If you need assistance, [the Microsoft FastTrack](https://go.microsoft.com/fwlink/?linkid=854618) is available to assist.</li></ul>          |
|Cloud Identity     |<ol type="1"><li>Create users using Microsoft 365 admin center</li></ol>           |<ul style="list-style-type:none"><li>[Add users individually or in bulk](https://support.office.com/article/Add-users-individually-or-in-bulk-to-Office-365-Admin-Help-1970f7d6-03b5-442f-b385-5880b9c256ec)</li></ul>         |
|Synchronized Identity     |<ol type="1"><li>Install Azure AD Connect</li><li>Configure Directory Synchronization</li><li>Create users using on-premises Active Directory management tools</li></ol>         |<ul style="list-style-type:none"><li>[Set up directory synchronization](https://support.office.com/article/Set-up-directory-synchronization-for-Office-365-1b3b5318-6977-42ed-b5c7-96fa74b08846)</li><li>Note: Password hashes must be synchronized for Microsoft 365 and Office 365 to perform authentication.</li></ul>         |
|Federated Identity    |<ol type="1"><li>Install Azure AD Connect</li><li>Configure Directory Synchronization</li><li>Install and configure a Federated Identity Provider (ADFS recommended)</li><li>Create users using on-premises Active Directory management tools</li></ol>           |<ul style="list-style-type:none"><li>[Set up directory synchronization](https://support.office.com/article/Set-up-directory-synchronization-for-Office-365-1b3b5318-6977-42ed-b5c7-96fa74b08846)</li><li>[Plan your AD FS deployment](https://go.microsoft.com/fwlink/?linkid=854619)</li><li>[Checklist: Deploy your federation server farm](https://go.microsoft.com/fwlink/?linkid=854620)</li><li>[Configure extranet access for AD FS](https://go.microsoft.com/fwlink/?linkid=854621)</li><li>[Set up a trust between AD FS and Azure AD](https://go.microsoft.com/fwlink/?linkid=854622)</li><li>[Verify and manage single sign-on with ADFS](https://go.microsoft.com/fwlink/?linkid=854624)</li><li>[Azure AD federation compatibility list](https://go.microsoft.com/fwlink/?linkid=854625)</li><li>Note: Password hashes do not need to be synchronized to Azure AD.</li></ul>         |

See [Understanding identity models and Azure AD](https://docs.microsoft.com/microsoft-365/enterprise/about-microsoft-365-identity) for more information.

## Multi-Factor Authentication

Microsoft 365 and Office 365 plans support multi-factor authentication (MFA) that increases the security of user logins to services. With MFA, users are required to acknowledge a phone call, text message, or an app notification on their smartphone after correctly entering their password. Only after this second authentication factor has been satisfied, can a user sign in.

Multi Factor authentication is supported with any Microsoft 365 or Office 365 plan that includes Microsoft Teams. The subscription plans that include Microsoft Teams are discussed later in the Licensing section below.

Once the users are enrolled for MFA, the next time a user signs in, they will see a message that asks them to set up their second authentication factor. Supported authentication methods are:

| Identity model  |Available MFA Second Factor options  |
|---------|---------|
|**Cloud Only**     |MFA for Microsoft 365 or Office 365 <ul><li>Phone Call</li><li>Text Message</li><li>Mobile App Notification</li><li>Mobile App Verification Code</li></ul>        |
|**Hybrid setup (Synchronized or Federated Identity model)**     |<ul><li>MFA for Microsoft 365 or Office 365</li><li>Azure MFA module (ADFS integrated)</li><li>Physical or virtual smart card (ADFS integrated)</li></ul>   Note: Additional MFA solutions are available with [Azure AD Identity Provider Compatibility Docs](https://www.microsoft.com/download/details.aspx?id=56843)       |
