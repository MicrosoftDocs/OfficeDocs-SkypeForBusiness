---
title: "Configure the personal contacts store on Lync 2010 client computers"
ms.reviewer: 
ms.author: jambirk
author: jambirk
manager: serdars
ms.date: 1/29/2019
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: ec69a6cb-07f2-4057-9544-55035f83eeae
description: "Summary: Configure the personal contact store used by legacy clients."
---

# Configure the personal contacts store on Lync 2010 client computers
  
If you are integrating Skype for Business Server 2015 and Exchange Server 2016 or Exchange Server 2013, then you should configure the personal contact store used by the clients. In particular, you should configure Skype for Business to use Exchange as the personal contact store, and, at the same time, ensure that users are not able to override that decision. This can be done by creating and configuring a Registry value on each client computer.
  
> [!NOTE]
> The following procedure is only necessary for clients using the Lync 2010 client or earlier. The Lync 2013 client and all Skype for Business clients will not have the option of overriding the contact store settings.
  
To configure this value on a single computer, complete the following procedure:
  
1. On the client computer, click **Start** and then click **Run**.
2. In the **Run** dialog box, type regedit and then press ENTER.
3. In Registry Editor, expand **HKEY_LOCAL_MACHINE**, expand **Software**, expand **Policies**, expand **Microsoft**, and then expand **Communicator**.
4. Right-click **Communicator**, point to **New**, and then click **DWORD (32-bit) Value**.
5. After the new value is created, type PersonalContactStoreOverride and then press ENTER to rename the value.
6. Verify that the value of PersonalContactStoreOverride is set to 0 and then close Registry Editor.

If you need to make this same change on multiple computers you can do so by creating a custom Group Policy object. For details on doing this in Windows 10, see the [Create a Group Policy Object](https://docs.microsoft.com/windows/security/threat-protection/windows-firewall/create-a-group-policy-object) article.
  
