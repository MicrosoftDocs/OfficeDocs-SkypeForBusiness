---
title: "Configure the personal contacts store on client computers for Skype for Business Server 2015"
ms.author: jambirk
author: jambirk
manager: serdars
ms.date: 12/20/2016
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: ec69a6cb-07f2-4057-9544-55035f83eeae
description: "Summary: Configure the personal contact store used by Exchange Server 2016 or Exchange Server 2013 and Skype for Business Server 2015."
---

# Configure the personal contacts store on client computers for Skype for Business Server 2015
 
**Summary:** Configure the personal contact store used by Exchange Server 2016 or Exchange Server 2013 and Skype for Business Server 2015.
  
If you are integrating Skype for Business Server 2015 and Exchange Server 2016 or Exchange Server 2013, then you should configure the personal contact store on any client computers running Skype for Business. In particular, you should configure Skype for Business to use Exchange as the personal contact store, and, at the same time, ensure that users are not able to override that decision. This can be done by creating and configuring a Registry value on each client computer.
  
Note that this is not required on computers running Skype for Business.
  
To configure this value on a single computer, complete the following procedure:
  
1. On the client computer, click **Start** and then click **Run**.
    
2. In the **Run** dialog box, type regedit and then press ENTER.
    
3. In Registry Editor, expand **HKEY_LOCAL_MACHINE**, expand **Software**, expand **Policies**, expand **Microsoft**, and then expand **Communicator**.
    
4. Right-click **Communicator**, point to **New**, and then click **DWORD (32-bit) Value**.
    
5. After the new value is created, type PersonalContactStoreOverride and then press ENTER to rename the value.
    
6. Verify that the value of PersonalContactStoreOverride is set to 0 and then close Registry Editor.
    
If you need to make this same change on multiple computers you can do so by creating a custom Group Policy object. For details, see the Group Policy documentation at [https://go.microsoft.com/fwlink/p/?LinkId=268543](https://go.microsoft.com/fwlink/p/?LinkId=268543).
  

