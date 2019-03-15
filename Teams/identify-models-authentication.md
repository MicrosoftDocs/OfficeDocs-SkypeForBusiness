---
title: Identity models and authentication in Microsoft Teams
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.date: 09/25/2017
ms.topic: reference
ms.service: msteams
ms.reviewer: anach
localization_priority: Normal
search.appverid: MET150
MS.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
description: Learn about the different identity models in Microsoft Teams such as Cloud, Synchronized, and Federated. Also learn about multi-factor authentication.
appliesto:
- Microsoft Teams
---

Identity models and authentication in Microsoft Teams
==========================================

Microsoft Teams support all the identity models that are available with Office 365. Supported identity models include:

-   **Cloud Identity**: In this model, a user is created and managed in Office 365 and stored in Azure Active Directory, and the password is verified by Azure Active Directory.

-   **Synchronized Identity**: In this model, the user identity is managed in an on-premises server, and the accounts and password hashes are synchronized to the cloud. The user enters the same password on-premises as they do in the cloud, and at sign-in the password is verified by Azure Active Directory. This model uses the Microsoft Azure Active Directory Connect Tool.

-   **Federated Identity**: This model requires a synchronized identity with the user password is verified by the on-premises identity provider. With this model, the password hash does not need to be synchronized to Azure AD, and Active Directory Federation Services (ADFS) or a third-party identity provider is used to authenticate users against the on-premises Active Directory.

Configurations
--------------

Depending on your organization’s decisions of which identity model to implement and use, the implementation requirements may vary. Refer to the requirements table below to ensure that your deployment meets these prerequisites. If you have already deployed Office 365 and have already implemented the identity and authentication method, you may skip these steps.


|Identity Model |Deployment Checklist  |Additional Information  |
|---------|---------|---------|
|All     |<ol type="1"><li>Compare Office 365 Plan Options and obtain a subscription</li><li>Create an Office 365 tenant</li><li>Assign Office 365 licenses to the tenant</li><li>Configure Domains and admin users</li><li>Continue with Identity Model specific instructions</li></ol>          |<ul style="list-style-type:none"><li>[Office 365 Plan Options](https://technet.microsoft.com/library/office-365-plan-options.aspx)</li><li>[Compare Office 365 Business Plans](https://go.microsoft.com/fwlink/?linkid=854617)</li><li>[Buy licenses for your Office 365 for business subscription](https://support.office.com/article/Buy-licenses-for-your-Office-365-for-business-subscription-36081d8d-b3fa-4948-8c34-e217bba825e1)</li><li>[Add licenses to a subscription](https://support.office.com/article/Add-licenses-to-a-subscription-paid-for-using-a-product-key-4fb4bd7e-3920-4ce0-98fb-0c06e3fedf53)</li><li>[Set up Office 365 for business](https://support.office.com/Article/set-up-Office-365-for-business-6a3a29a0-e616-4713-99d1-15eda62d04fa)</li><li>[Add users and domain with the setup wizard](https://support.office.com/article/Add-users-and-domain-with-the-setup-wizard-6383f56d-3d09-4dcb-9b41-b5f5a5efd611)</li><li>Note: If you need assistance, [the Microsoft FastTrack for Office 365 team](https://go.microsoft.com/fwlink/?linkid=854618) is available to assist.</li></ul>          |
|Cloud Identity     |<ol type="1"><li>Create users using Office 365 Admin Portal</li></ol>           |<ul style="list-style-type:none"><li>[Add users individually or in bulk to Office 365](https://support.office.com/article/Add-users-individually-or-in-bulk-to-Office-365-Admin-Help-1970f7d6-03b5-442f-b385-5880b9c256ec)</li></ul>         |
|Synchronized Identity     |<ol type="1"><li>Install Azure AD Connect</li><li>Configure Directory Synchronization</li><li>Create users using on-premises Active Directory management tools</li></ol>         |<ul style="list-style-type:none"><li>[Set up directory synchronization for Office 365](https://support.office.com/article/Set-up-directory-synchronization-for-Office-365-1b3b5318-6977-42ed-b5c7-96fa74b08846)</li><li>Note: Password hashes must be synchronized for Office 365 to perform authentication.</li></ul>         |
|Federated Identity    |<ol type="1"><li>Install Azure AD Connect</li><li>Configure Directory Synchronization</li><li>Install and configure a Federated Identity Provider (ADFS recommended)</li><li>Create users using on-premises Active Directory management tools</li></ol>           |<ul style="list-style-type:none"><li>[Set up directory synchronization for Office 365](https://support.office.com/article/Set-up-directory-synchronization-for-Office-365-1b3b5318-6977-42ed-b5c7-96fa74b08846)</li><li>[Plan your AD FS deployment](https://go.microsoft.com/fwlink/?linkid=854619)</li><li>[Checklist: Deploy your federation server farm](https://go.microsoft.com/fwlink/?linkid=854620)</li><li>[Configure extranet access for AD FS](https://go.microsoft.com/fwlink/?linkid=854621)</li><li>[Set up a trust between AD FS and Azure AD](https://go.microsoft.com/fwlink/?linkid=854622)</li><li>[Verify and manage single sign-on with ADFS](https://go.microsoft.com/fwlink/?linkid=854624)</li><li>[Azure AD federation compatibility list](https://go.microsoft.com/fwlink/?linkid=854625)</li><li>Note: Password hashes do not need to be synchronized to Azure Active Directory.</li></ul>         |

Refer to [Choosing a sign-in model for Office 365](https://go.microsoft.com/fwlink/?linkid=854626) and [Understanding Office 365 identity and Azure Active Directory](https://support.office.com/article/Understanding-Office-365-identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9) guides for additional details.

Multi-Factor Authentication
----------------------------

Office 365 plans support Multi-Factor Authentication (MFA) that increases the security of user logins to Office 365 services. With MFA for Office 365, users are required to acknowledge a phone call, text message, or an app notification on their smartphone after correctly entering their password. Only after this second authentication factor has been satisfied, can a user sign in.

Multi Factor authentication is supported with any Office 365 plan that includes Microsoft Teams. The Office 365 subscription plans that include Microsoft Teams are discussed later in the Licensing section below.

Once the users are enrolled for MFA, the next time a user signs in, they see a message that asks them to set up their second authentication factor. Supported authentication methods are:


|Tenant Type  |Available MFA Second Factor options  |Notes  |
|---------|---------|---------|
|**Cloud Only**     |MFA for Office 365 <ul><li>Phone Call</li><li>Text Message</li><li>Mobile App Notification</li><li>Mobile App Verification Code</li></ul>        |[Plan for multi-factor authentication for Office 365 Deployments](https://support.office.com/article/Plan-for-multi-factor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)         |
|**Hybrid setup (Synchronized or Federated Identity model)**     |<ul><li>MFA for Office 365</li><li>Azure MFA module (ADFS integrated)</li><li>Physical or virtual smart card (ADFS integrated)</li></ul>         |Note: Additional MFA solutions are available with [Identity providers that are compatible with Azure AD federation](https://go.microsoft.com/fwlink/p/?LinkId=510953)         |
