---
title: "Authentication in Microsoft Teams Rooms on Windows"
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: dimehta
ms.date: 03/01/2024
ms.topic: article
audience: Admin
ms.service: msteams
ms.subservice: itpro-rooms
appliesto: 
  - Microsoft Teams
ms.collection: 
  - M365-collaboration
  - teams-rooms-devices
  - Tier1
f1.keywords: 
  - NOCSH
ms.localizationpriority: medium
description: Learn how to configure modern authentication for Microsoft Teams Rooms on Windows
---

# Authentication in Microsoft Teams Rooms on Windows

Microsoft Teams Rooms on Windows shares authentication component with Teams desktop client and uses the same underlying authentication libraries to connect to Teams and other Microsoft 365 services. As such, Teams rooms requirements for authentication are based on Microsoft Teams requirements. Learn more about [Identity models and authentication for Microsoft Teams](/microsoftteams/identify-models-authentication).
  
However, Teams rooms on Windows have some key differences compared to an end user personal computer where Teams desktop runs. These differences may impact authentication configurations for Teams rooms.

The key differences are as below:  

1. Microsoft Teams rooms accounts are centrally managed by IT administrators in an organization. End users don't have ability to sign in/ out of Teams Rooms devices.
1. Microsoft Teams rooms use Microsoft Entra user accounts that are configured with resources mailbox in Microsoft Exchange. Learn more about [Manage resource mailboxes in Exchange Online](/exchange/recipients-in-exchange-online/manage-resource-mailboxes) 
1. Microsoft Teams rooms on Windows application run under least privileged local user that has been further locked down using Windows [Shell Launcher V2](/windows/iot/iot-enterprise/customize/shell-launcher) to remove Windows shell components (Start menu, taskbar, settings etc.), such that only Teams Rooms application is aware of resource account used to sign in to Microsoft Teams. This mechanism also prevents other applications to get account information from Windows Account Manager as Windows has no information about resource account used by Teams rooms application.
1. Authentication in Microsoft Teams Rooms on Windows doesn’t require any user intervention and doesn’t support second-factor authentication. The modern authentication mechanism uses the [resource owner password credentials](/azure/active-directory/develop/v2-oauth-ropc) authorization grant type in OAuth 2.0.

It’s important to note that Microsoft Teams Rooms resource accounts shouldn't be configured to use multifactor authentication (MFA), smart card authentication, or client certificate-based authentication (which are all available for end users).

Teams rooms resource account access to Microsoft 365 service can be set up using Conditional Access policies.  Since Windows has no knowledge of resource account that is used by Teams room application, to apply device-level conditional access policies, you must enroll Teams Rooms on Windows devices with Microsoft Endpoint Manager. Learn more about [Enrolling Microsoft Teams Rooms on Windows devices with Microsoft Endpoint Manager](https://techcommunity.microsoft.com/t5/intune-customer-success/enrolling-microsoft-teams-rooms-on-windows-devices-with/ba-p/3246986). When device is enrolled in Endpoint Manager, Teams Room application uses Windows enrolled account using Web access management (WAM) to send device compliance status for conditional access evaluation. To learn more about Conditional access and End Manager device compliance policies, see [Conditional Access and Intune compliance for Microsoft Teams Rooms](/microsoftteams/rooms/conditional-access-and-compliance-for-devices) and [Supported Conditional Access and Intune device compliance policies for Microsoft Teams Rooms](/microsoftteams/rooms/supported-ca-and-compliance-policies?tabs=mtr-w)

You can configure a resource account used with Microsoft Teams Rooms for IP/location-based access. To learn more, see [Conditional Access: Block access by location](/azure/active-directory/conditional-access/howto-conditional-access-policy-location).

For more information about device compliance, see [Supported Conditional Access and Intune compliance policies for Microsoft Teams Rooms](supported-ca-and-compliance-policies.md).
