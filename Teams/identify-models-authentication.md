---
title: Identity models and authentication for Microsoft Teams
author: MSFTTracyP
ms.author: tracyp
manager: dansimp
ms.date: 09/25/2020
ms.topic: reference
ms.service: msteams
ms.reviewer: anwara
audience: admin
ms.localizationpriority: medium
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

# Identity models and authentication for Microsoft Teams

Microsoft Teams supports all the identity models that are available with Microsoft 365 and Office 365, which include:

- **Cloud-only**: User accounts are created and managed in Microsoft 365 or Office 365 and stored in Azure Active Directory (Azure AD). User sign-in credentials (account name and password) are validated by Azure AD.

- **Hybrid**: User accounts are typically managed in an on-premises Active Directory Domain Services (AD DS) forest. Depending on the configuration, credential validation can be done by Azure AD, AD DS, or a federated identity provider. This model uses directory synchronization from AD DS to Azure AD with Azure AD Connect.

For more information, see [Microsoft 365 identity models and Azure AD](/microsoft-365/enterprise/about-microsoft-365-identity).

## Configurations

Depending on your organization's decisions of which identity model and configuration you use, the implementation steps may vary.

If you haven't already deployed Microsoft 365 or Office 365 and an identity model, use this table. 

|Identity Model |Deployment Checklist  |Additional information  |
|---------|---------|---------|
|All     |<ol type="1"><li>Compare Microsoft 365 and Office 365 plan options and obtain a subscription and a tenant.</li><li>Create a Microsoft 365 or Office 365 organization for your tenant.</li><li>Purchase Microsoft 365 or Office 365 licenses for the tenant</li><li>Configure domains and admin user accounts.</li></ol>  |<ul><li>[Office 365 plan options](/office365/servicedescriptions/office-365-platform-service-description/office-365-plan-options)</li><li>[Compare Microsoft 365 for business Plans](https://go.microsoft.com/fwlink/?linkid=854617)</li><li>[Buy or remove subscription licenses](https://support.office.com/article/Buy-licenses-for-your-Office-365-for-business-subscription-36081d8d-b3fa-4948-8c34-e217bba825e1)</li><li>[Add licenses to a subscription](https://support.office.com/article/Add-licenses-to-a-subscription-paid-for-using-a-product-key-4fb4bd7e-3920-4ce0-98fb-0c06e3fedf53)</li><li>[Set up Microsoft 365 for business](https://support.office.com/Article/set-up-Office-365-for-business-6a3a29a0-e616-4713-99d1-15eda62d04fa)</li><li>[Add a domain with the setup wizard](https://support.office.com/article/Add-users-and-domain-with-the-setup-wizard-6383f56d-3d09-4dcb-9b41-b5f5a5efd611)</li></ul><br>[Microsoft FastTrack](https://www.microsoft.com/fasttrack/microsoft-365) is available to assist you.  |
|Cloud identity     |<ul><li>Create user accounts with the Microsoft 365 admin center</li></ul> |<ul><li>[Add users and assign licenses](https://support.office.com/article/Add-users-individually-or-in-bulk-to-Office-365-Admin-Help-1970f7d6-03b5-442f-b385-5880b9c256ec)</li></ul> |
|Hybrid identity     |<ol type="1"><li>Install Azure AD Connect.</li><li>Configure directory synchronization.</li><li>Manage users and groups with AD DS tools.</li></ol> |<ul><li>[Set up directory synchronization](/microsoft-365/enterprise/set-up-directory-synchronization)</li></ul> |
|Hybrid identity with federated authentication    |<ol type="1"><li>Install and configure a federated identity provider such as AD FS.</li><li>Install Azure AD Connect and configure directory synchronization and federated authentication.</li><li>Manage users and groups with AD DS tools.</li></ol> |<ul><li>[Plan your AD FS deployment](/previous-versions/azure/azure-services/dn151324(v=azure.100))</li><li>[Checklist: Deploy your federation server farm](/previous-versions/azure/azure-services/dn528856(v=azure.100))</li><li>[Configure extranet access for AD FS](/previous-versions/azure/azure-services/dn528859(v=azure.100))</li><li>[Set up a trust between AD FS and Azure AD](/previous-versions/azure/azure-services/jj205461(v=azure.100))</li><li>[Verify and manage single sign-on with ADFS](/previous-versions/azure/azure-services/jj151809(v=azure.100))</li><li>[Set up directory synchronization](/microsoft-365/enterprise/set-up-directory-synchronization)</li></ul> |
||||

## Multi-factor authentication

Passwords are the most common method of authentication for signing in to a computer or online service, but they are also the most vulnerable. People can choose easy passwords and use the same passwords for multiple sign-ins to different computers and services. 

To provide an additional level of security for sign-ins, use multi-factor authentication (MFA), which requires both a password and an additional verification method such as:

- A text message sent to a phone that requires the user to type a verification code.
- A phone call.
- The Microsoft Authenticator smart phone app.
- Other methods available with hybrid identity and federated authentication.

MFA is supported with any Microsoft 365 or Office 365 plan that includes Microsoft Teams. It is highly recommended that at a minimum you require MFA for that accounts that are [assigned administrator roles](/microsoft-365/admin/add-users/about-admin-roles), such as Teams service admin.

You should also roll out MFA to your users. Once your users are enrolled for MFA, the next time they sign in, they will see a message that asks them to set up their additional verification method. 

For more information, see [Multi-factor authentication for Microsoft 365](/microsoft-365/admin/security-and-compliance/multi-factor-authentication-microsoft-365).