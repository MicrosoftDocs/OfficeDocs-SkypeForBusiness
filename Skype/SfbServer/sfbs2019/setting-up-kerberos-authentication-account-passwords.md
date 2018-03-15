---
title: "Setting up Kerberos authentication account passwords in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: b435f88e-4a77-4be7-b7e5-c17484303b74
description: "After you create the computer object for the Kerberos authentication account, you can set up the password for the account. You run the Windows PowerShell cmdlet for setting the Kerberos account password on one server. You can set the password on the object that you created for the Kerberos authentication. The password can be set to a known value, but by default is a random password. The password is available to all Kerberos authentication sources that use the account. You use Windows PowerShell cmdlets to set up and manage Kerberos account passwords."
---

# Setting up Kerberos authentication account passwords in Lync Server 2013
[]
After you create the computer object for the Kerberos authentication account, you can set up the password for the account. You run the Windows PowerShell cmdlet for setting the Kerberos account password on one server. You can set the password on the object that you created for the Kerberos authentication. The password can be set to a known value, but by default is a random password. The password is available to all Kerberos authentication sources that use the account. You use Windows PowerShell cmdlets to set up and manage Kerberos account passwords. 
  
> [!NOTE]
> The Kerberos account object is a computer object, but uses the UserAccount parameter for operations in the Windows PowerShell cmdlets that are referenced. Note that this is not a mistake, but the intended behavior of the cmdlet when used with the Kerberos account creation and maintenance. 
  
## In this section

- [Set a Kerberos authentication account password on a server in Lync Server 2013](set-a-kerberos-authentication-account-password-on-a-server.md)
    
- [Synchronize a Kerberos authentication account password to IIS in Lync Server 2013](synchronize-a-kerberos-authentication-account-password-to-iis.md)
    

