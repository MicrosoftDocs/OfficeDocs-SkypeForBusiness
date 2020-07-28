---
title: "Authentication in Microsoft Teams Rooms"
ms.author: v-lanac
author: lanachin
ms.reviewer: sohailta
manager: serdars
audience: ITPro
ms.topic: conceptual
ms.service: msteams
f1.keywords:
- NOCSH
localization_priority: Normal
ms.assetid:
ms.collection: 
  - M365-collaboration
description: "Learn how configure modern authentication for Microsoft Teams Rooms"
---

# Authentication in Microsoft Teams Rooms

Account management for Microsoft Teams Rooms devices is handled at the application level. The application connects to Microsoft Teams, Skype for Business, and Exchange to get resources for the room account to enable calling and meeting experiences. The device is kept account agnostic to allow for always-on capabilities, calling scenarios (for devices configured with a Calling Plan), and custom lockdown mechanisms implemented on these devices. This means that authentication for these devices happen in a different way than for end-user devices.  

Modern authentication is recommended for all customers using Microsoft Teams Rooms devices with Microsoft 365 or Office 365. If you have an on-premises deployment of Exchange server or Skype for Business server, configure [hybrid modern authentication](https://docs.microsoft.com/office365/enterprise/hybrid-modern-auth-overview) with Azure Active Directory (Azure AD) to enable using modern authentication.

Modern authentication is supported on Microsoft Teams Rooms version 4.4.25.0 and later.

## Modern authentication

When you use modern authentication with the Microsoft Teams Rooms application, Active Directory Authentication Library (ADAL) is used to connect to Microsoft Teams, Exchange, and Skype for Business. A Microsoft Teams Rooms device is a shared device and performs a nightly reboot to ensure smooth functioning and to get critical operating system, driver, firmware, or application updates. The modern authentication mechanism uses the [resource owner password credentials](https://tools.ietf.org/html/rfc6749#section-1.3.3) authorization grant type in OAuth 2.0, which doesn't require any user intervention. This is one of the key differences between how modern authentication works for user accounts versus resource accounts that are used by the Microsoft Teams Rooms application. Because of this, Microsoft Teams Rooms resource accounts shouldn't be configured to use multi-factor authentication (MFA), smart card authentication, or client certificate-based authentication (which are all available for end users).

The other key difference between how modern authentication works on Microsoft Teams Rooms devices and end-user devices is that you can't use a resource account to apply device-level conditional access policies such as "Require device to be marked as compliant", or "Require Hybrid Azure AD joined device", and so on. This is because device-level concepts don't apply to modern authentication when used at the application level. Instead, you can enroll a device in Microsoft Intune and apply compliance policies by using the guidance provided in [Managing Teams Meeting Rooms with Intune](https://techcommunity.microsoft.com/t5/intune-customer-success/managing-teams-meeting-rooms-with-intune/ba-p/1069230).

## Enable modern authentication on a Microsoft Teams Rooms device

For Microsoft Teams Rooms to use modern authentication with Skype for Business and Exchange, enable the client-side setting for modern authentication on the Microsoft Teams Rooms device. You can do this in the device settings or in the XML config file.

> [!NOTE]
> Before you enable the client-side setting for modern authentication, make sure that your environment is set up correctly to use modern authentication.

### Using device settings

1. On the Microsoft Team Rooms device, go to **More** (**...**).
    
2. Select **Settings**, and then enter the device administrator username and password.
3. Go to the **Account** tab, turn on **Modern Authentication**, and then select **Save and exit**.

### Using the XML config file

In your SkypeSettings.xml file, set the modern authentication XML element to **True**, as follows.

```
<ModernAuthEnabled>True</ModernAuthEnabled>
```

To apply the setting, see [Manage a Microsoft Teams Rooms console settings remotely with an XML configuration file](xml-config-file.md).

## Prepare your environment for modern authentication

Before you begin, make sure you understand the identity models to use with Office 365 and Azure AD. You can find more information at [Office 365 identity models and Azure Active Directory](https://docs.microsoft.com/Office365/Enterprise/about-office-365-identity) and at [Hybrid identity and directory synchronization for Microsoft 365 or Office 365](https://docs.microsoft.com/Office365/Enterprise/plan-for-directory-synchronization).

### Enable modern authentication in Microsoft 365 or Office 365

To turn on modern authentication for Exchange Online, see [Enable modern authentication in Exchange Online](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/enable-or-disable-modern-authentication-in-exchange-online). If you use Skype for Business Online, you should also make sure that modern authentication is turned on for Skype for Business Online. To learn more, see [Skype for Business Online: Enable your tenant for modern authentication](https://aka.ms/SkypeModernAuth).

We recommended that you do not remove basic authentication policies for Exchange Online or disable basic authentication for your tenant before you have validated that Microsoft Teams Rooms devices can sign in to Exchange Online and Teams or Skype for Business Online successfully when the modern authentication setting is on and that there are no devices that are still configured to use basic authentication.

For more information about disabling basic authentication in Exchange Online, see [Disable Basic authentication in Exchange Online](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/disable-basic-authentication-in-exchange-online).

## Hybrid modern authentication

To ensure successful authentication to your on-premises Exchange server and/or Skype for Business server, you must make sure the resource account that's used with Microsoft Teams Rooms is configured to get authorization from Azure AD. To learn more about hybrid identity and methods that work for your organization, read the following topics: 

- [What is password hash sync?](https://docs.microsoft.com/azure/active-directory/hybrid/whatis-phs)
- [What is passthrough authentication?](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-pta)
- [What is federation?](https://docs.microsoft.com/azure/active-directory/hybrid/whatis-fed)

### Prerequisites specific to Microsoft Teams Rooms

The prerequisites to enable modern authentication in your hybrid topology are covered in [Hybrid modern authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers](https://docs.microsoft.com/office365/enterprise/hybrid-modern-auth-overview). All the prerequisites discussed in the article apply.

However, because Microsoft Teams Rooms uses [resource owner password credentials](https://tools.ietf.org/html/rfc6749#section-1.3.3) authorization and the underlying REST APIs for modern authentication, the following are important differences to be aware of that are specific to Microsoft Teams Rooms.

- You must have Exchange Server 2016 CU8 or later, or Exchange Server 2019 CU1 or later.
- You must have Skype for Business Server 2015 CU5 or later, or Skype for Business Server 2019 or later.
- MFA isn't supported regardless of the topology you have.
- If you use a third-party authentication provider that's supported by Azure AD, it must support OAuth and use  resource owner password credentials authorization.
- Do not use device-level conditional access policies for a resource account configured with the application. Doing so will result in sign-in failures. Instead, enroll a device in Microsoft Intune and apply compliance policies by using the guidance published in [Managing Teams Meeting Rooms with Intune](https://techcommunity.microsoft.com/t5/intune-customer-success/managing-teams-meeting-rooms-with-intune/ba-p/1069230).

### Configure Exchange Server

To enable hybrid modern authentication in Exchange Server, see [How to configure Exchange Server on-premises to use hybrid modern authentication](https://docs.microsoft.com/Office365/Enterprise/configure-exchange-server-for-hybrid-modern-authentication).

### Configure Skype for Business Server

To enable hybrid modern authentication with Skype for Business Server, see [How to configure Skype for Business on-premises to use hybrid modern authentication](https://docs.microsoft.com/Office365/Enterprise/configure-exchange-server-for-hybrid-modern-authentication).

### Remove or disable Skype for Business and Exchange

If your setup doesn't allow for hybrid modern authentication or you need to remove or disable hybrid modern authentication for Exchange or Skype for Business, see [Removing or disabling hybrid modern authentication from Skype for Business and Exchange](https://docs.microsoft.com/Office365/Enterprise/remove-or-disable-hybrid-modern-authentication-from-skype-for-business-and-excha).

### Azure AD conditional access

You can configure a resource account used with Microsoft Teams Rooms for IP/location-based access. To learn more, see [Conditional Access: Block access by location](https://docs.microsoft.com/azure/active-directory/conditional-access/howto-conditional-access-policy-location).

No other conditional access policies are supported. For more information about device compliance, see [Managing Teams Meeting Rooms with Intune](https://techcommunity.microsoft.com/t5/intune-customer-success/managing-teams-meeting-rooms-with-intune/ba-p/1069230).  
