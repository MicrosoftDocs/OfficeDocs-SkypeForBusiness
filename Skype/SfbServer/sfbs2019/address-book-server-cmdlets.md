---
title: "Address Book Server cmdlets in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 33da45da-3c57-4d04-9679-f0e5a0cfd37e
description: "Address Book servers are intermediaries between Active Directory Domain Services and Microsoft Lync Server 2013. The Address Book server ensures that the user information stored in Lync Server 2013 is in synch with the user information stored in Active Directory. This is done by periodically synching Address Book files with information stored in the User database. In turn, Lync Server includes a number of cmdlets for managing Address Book servers."
---

# Address Book Server cmdlets in Lync Server 2013
[]
Address Book servers are intermediaries between Active Directory Domain Services and Microsoft Lync Server 2013. The Address Book server ensures that the user information stored in Lync Server 2013 is in synch with the user information stored in Active Directory. This is done by periodically synching Address Book files with information stored in the User database. In turn, Lync Server includes a number of cmdlets for managing Address Book servers.
  
## Address Book Server Cmdlets

You cannot configure the Address Book Server settings in Lync Server Control Panel. Windows PowerShell is the primary tool for managing these settings. The following is a list of cmdlets that relate directly to managing the Address Book Server:
  
 **Address Book Server**
  
> [Get-CsAddressBookConfiguration](get-csaddressbookconfiguration.md)
    
> [New-CsAddressBookConfiguration](new-csaddressbookconfiguration.md)
    
> [Remove-CsAddressBookConfiguration](remove-csaddressbookconfiguration.md)
    
> [Set-CsAddressBookConfiguration](set-csaddressbookconfiguration.md)
    
> [Update-CsAddressBook](update-csaddressbook.md)
    
> [Debug-CsAddressBookReplication](debug-csaddressbookreplication.md)
    
> [Test-CsAddressBookService](test-csaddressbookservice.md)
    
> [Test-CsAddressBookWebQuery](test-csaddressbookwebquery.md)
    
## See also

#### 

[Lync Server PowerShell Blog](https://go.microsoft.com/fwlink/p/?linkId=203150)

