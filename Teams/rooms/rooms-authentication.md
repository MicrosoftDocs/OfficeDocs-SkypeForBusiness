---
title: "Authentication in Microsoft Teams Rooms on Windows"
ms.author: dstrome
author: dstrome
ms.reviewer: sohailta
manager: serdars
audience: ITPro
ms.topic: conceptual
ms.service: msteams
f1.keywords: 
  - NOCSH
ms.localizationpriority: medium
ms.assetid: 
ms.collection: 
  - M365-collaboration
  - Teams_ITAdmin_Rooms
description: Learn how to configure modern authentication for Microsoft Teams Rooms on Windows
---

# Authentication in Microsoft Teams Rooms on Windows

Account management for Microsoft Teams Rooms is handled at the application level. The application connects to Microsoft Teams, Skype for Business, and Exchange to get resources for the resource account to enable calling and meeting experiences. Teams Rooms uses a dedicated resource account to allow for always-on capabilities, calling scenarios (for devices configured with a calling plan), and custom lockdown mechanisms. This means that authentication for Teams Rooms happens in a different way than for end-user devices.  

Modern authentication is recommended for all customers using Microsoft Teams Rooms with Microsoft 365 or Office 365. If you have an on-premises deployment of Exchange server or Skype for Business server, configure [hybrid modern authentication](/office365/enterprise/hybrid-modern-auth-overview) with Azure Active Directory (Azure AD) to enable using modern authentication.

Modern authentication is supported on Microsoft Teams Rooms version 4.4.25.0 and later.

## Modern authentication

When you use modern authentication with the Microsoft Teams Rooms application, Active Directory Authentication Library (ADAL) is used to connect to Microsoft Teams, Exchange, and Skype for Business. The modern authentication mechanism uses the [resource owner password credentials](/azure/active-directory/develop/v2-oauth-ropc) authorization grant type in OAuth 2.0, which doesn't require any user intervention. This is one of the key differences between how modern authentication works for user accounts versus resource accounts that are used by Microsoft Teams Rooms. Because of this, Microsoft Teams Rooms resource accounts shouldn't be configured to use multi-factor authentication (MFA), smart card authentication, or client certificate-based authentication (which are all available for end users).

The other key difference between how modern authentication works on Microsoft Teams Rooms and end-user devices is that you can't use a resource account to apply device-level conditional access policies in Azure Active Directory and Endpoint Manager as device info is not passed when using this grant type. Instead, you can enroll a device in Microsoft Endpoint Manager and apply compliance policies. See [Conditional Access and Intune compliance for Microsoft Teams Rooms](conditional-access-and-compliance-for-devices.md) for more information.

## Enable modern authentication on Microsoft Teams Rooms

For Microsoft Teams Rooms to use modern authentication with Skype for Business and Exchange, enable the client-side setting for modern authentication on Microsoft Teams Rooms. You can do this in the device settings or in the XML config file.

> [!NOTE]
> Before you enable the client-side setting for modern authentication, make sure that your environment is set up correctly to use modern authentication.

### Using device settings

1. On Microsoft Teams Rooms, go to **More** (**...**).
    
2. Select **Settings**, and then enter the device administrator username and password.
3. Go to the **Account** tab, turn on **Modern Authentication**, and then select **Save and exit**.

### Using the XML config file

In your SkypeSettings.xml file, set the modern authentication XML element to **True**, as follows.

```XML
<ModernAuthEnabled>True</ModernAuthEnabled>
```

To apply the setting, see [Manage a Microsoft Teams Rooms console settings remotely with an XML configuration file](xml-config-file.md).

## Prepare your environment for modern authentication

Before you begin, make sure you understand the identity models to use with Office 365 and Azure AD. You can find more information at [Office 365 identity models and Azure Active Directory](/Office365/Enterprise/about-office-365-identity) and at [Hybrid identity and directory synchronization for Microsoft 365 or Office 365](/Office365/Enterprise/plan-for-directory-synchronization).

### Enable modern authentication in Microsoft 365 or Office 365

To turn on modern authentication for Exchange Online, see [Enable modern authentication in Exchange Online](/exchange/clients-and-mobile-in-exchange-online/enable-or-disable-modern-authentication-in-exchange-online).

We recommended that you do not remove basic authentication policies for Exchange Online or disable basic authentication for your tenant until you have validated that Microsoft Teams Rooms devices can successfully sign in with Exchange Online and Teams.

For more information about disabling basic authentication in Exchange Online, see [Disable Basic authentication in Exchange Online](/exchange/clients-and-mobile-in-exchange-online/disable-basic-authentication-in-exchange-online).

## Hybrid modern authentication

To ensure successful authentication to your on-premises Exchange server and/or Skype for Business server, you must make sure the resource account that's used with Microsoft Teams Rooms is configured to get authorization from Azure AD.

Teams Rooms authentication flows vary depending on your authentication configuration. For customers using a managed domain, Teams Rooms uses [OAuth 2.0 Resource Owner Password Credentials](/azure/active-directory/develop/v2-oauth-ropc) with Azure Active Directory. However, for customers using a federated domain, [OAuth 2.0 SAML Bearer Assertion Flow](/azure/active-directory/develop/v2-saml-bearer-assertion) is used.

> [!NOTE]
> Your identity provider may need specific configurations or settings for integration with Azure Active Directory or Office 365. Contact your identity provider if you need help with configuring authentication with Teams Rooms.


### Prerequisites specific to Microsoft Teams Rooms

The prerequisites to enable modern authentication in your hybrid topology are covered in [Hybrid modern authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers](/office365/enterprise/hybrid-modern-auth-overview). All the prerequisites discussed in the article apply.

However, because Microsoft Teams Rooms uses [resource owner password credentials](https://tools.ietf.org/html/rfc6749#section-1.3.3) authorization and the underlying REST APIs for modern authentication, the following are important differences to be aware of that are specific to Microsoft Teams Rooms.

- You must have Exchange Server 2016 CU8 or later, or Exchange Server 2019 CU1 or later.
- You must have Skype for Business Server 2015 CU5 or later, or Skype for Business Server 2019 or later.
- MFA isn't supported regardless of the topology you have.
- Microsoft Teams Rooms does not support SIP and UPN mismatch. You must create a Microsoft Teams Rooms account with the same UPN and SIP for it to work.
- If you use a third-party authentication provider that's supported by Azure AD, it must support an active authentication flow through WS-Trust.
- Do not use device-level conditional access policies for a resource account configured with the application. Doing so will result in sign-in failures. Instead, enroll a device in Microsoft Intune and apply compliance policies. See [Conditional Access and Intune compliance for Microsoft Teams Rooms](conditional-access-and-compliance-for-devices.md) for more information.

### Configure Exchange Server

To enable hybrid modern authentication in Exchange Server, see [How to configure Exchange Server on-premises to use hybrid modern authentication](/Office365/Enterprise/configure-exchange-server-for-hybrid-modern-authentication).

### Configure Skype for Business Server

To enable hybrid modern authentication with Skype for Business Server, see [How to configure Skype for Business on-premises to use hybrid modern authentication](/Office365/Enterprise/configure-exchange-server-for-hybrid-modern-authentication).

### Remove or disable Skype for Business and Exchange

If your setup doesn't allow for hybrid modern authentication or you need to remove or disable hybrid modern authentication for Exchange or Skype for Business, see [Removing or disabling hybrid modern authentication from Skype for Business and Exchange](/Office365/Enterprise/remove-or-disable-hybrid-modern-authentication-from-skype-for-business-and-excha).

### Azure AD conditional access

You can configure a resource account used with Microsoft Teams Rooms for IP/location-based access. To learn more, see [Conditional Access: Block access by location](/azure/active-directory/conditional-access/howto-conditional-access-policy-location).

For more information about device compliance, see [Supported Conditional Access and Intune compliance policies for Microsoft Teams Rooms](supported-ca-and-compliance-policies.md).
