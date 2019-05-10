---
title: "Client Version Rule"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.lscp.ClientCVPolicyRuleEdit
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 6e7e94c2-1475-4334-b8da-716b24a4c255
ROBOTS: NOINDEX, NOFOLLOW
description: "A client version policy is made up of a set of client version rules. These rules define the actions that should be taken when users attempt to log on with specific clients and client versions."
---

# Client Version Rule

A client version policy is made up of a set of client version rules. These rules define the actions that should be taken when users attempt to log on with specific clients and client versions.

## Tasks you can perform

You can perform the following tasks on the **New Client Version Configuration** or **Edit Client Version Configuration** page:

- Add new rules to a client version policy.

- Modify the rules that make up an existing client version policy

## UI Reference

The following lists describe the menus, command, fields, and properties on the page.

- **User agent** You can select a client type from the list. The following table defines user agent codes. This list includes legacy client types, some of which are no longer supported.

|**Client Name**|**User Agent**|
|:-----|:-----|
|Lync 2013, Lync 2010, Office Communicator  <br/> |OC  <br/> |
|Lync Web App, Communicator Web Access  <br/> |CWA  <br/> |
|Lync Phone Edition, Office Communicator Phone  <br/> |OCPhone  <br/> |
|Communicator Phone Edition Platform  <br/> |CPE  <br/> |
|Unified Communications Platform  <br/> |UCCP  <br/> |
|Lync 2010 Attendee  <br/> |AOC  <br/> |
|Live Meeting Add-In  <br/> |LiveMeetingAddins  <br/> |
|Office Live Meeting  <br/> |LMC  <br/> |
|Windows Messenger  <br/> |WM  <br/> |
|Real-time Communications Client  <br/> |RTC  <br/> |
|Lync 2010 for iPad  <br/> |iPadLync  <br/> |
|Lync 2010 for iPhone  <br/> |iPhoneLync  <br/> |
|Lync 2010 for Windows Phone  <br/> |WPLync  <br/> |
|Lync 2010 for Nokia  <br/> |NokiaLync  <br/> |
|Lync 2010 for Android  <br/> |AndroidLync  <br/> |
|Mobility service  <br/> |McxService  <br/> |

- **Version number** You can specify the version numbers for the following fields, or use wildcards to indicate the client version number.

  - **Major version** Specifies the number that corresponds to the major release of the client.

  - **Minor version** Specifies the number that corresponds to the minor release of the client.

  - **Build** Specifies the build number that corresponds to the major and minor release of the client.

  - **Update** Specifies the number that corresponds to the updated release of the client.

- **Comparison operation** You can specify the matching operation for the client version you specified in the preceding steps. The following operations are available:

  - **Same as**

  - **Is not**

  - **Newer than**

  - **Newer than or same as**

  - **Older than**

  - **Older than or same as**

- **Action** You can specify the action to perform when the criteria in the preceding steps are met. The following actions are available:

  - **Allow** Allows the client to log on.

  - **Allow and Upgrade** Allows the client to log on and receive updates from Windows Server Update Service or Microsoft Update. This action is available only when user agent **OC** is selected.

    > [!NOTE]
    > Selecting this action causes a notification to appear the next time users sign in to Skype for Business. The notification states that an update is available, even if updates have not yet been released to Windows Server Update Service or Microsoft Update. To avoid confusion, you should choose this action only after updates become available.

  - **Allow with URL** Allows the client to log on and displays a message about where to download another client version. You specify the URL in the **URL** field.

  - **Block** Prevents the client from logging on.

  - **Block and Upgrade** Prevents the client from logging on and allows the client to receive updates from Windows Server Update Service or Microsoft Update. This action is available only when user agent **OC** is selected.

  - **Block with URL** prevents the client from logging on and displays a message about where to download another client version. You specify the URL in the **URL** field.

For details about interoperability among clients and client versions, see [Client Interoperability](https://technet.microsoft.com/library/0f126571-91a2-45d5-855c-1e4ddb45fc04.aspx) in the Planning documentation. For details about working with client version configurations, see [Modify the Default Action for Clients Not Explicitly Supported or Restricted](https://technet.microsoft.com/library/548dd0f5-62fe-4c3f-8952-2b9fd4c5fff3.aspx) in the Operations documentation.

