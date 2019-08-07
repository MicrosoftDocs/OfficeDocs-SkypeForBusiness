---
title: "Skype Room System multiple forest on-premises deployments"
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.reviewer: davgroom
ms.topic: quickstart
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 6793fca0-3970-44e4-8703-1925428c1967
description: "Read this topic to learn how to deploy Skype Room System in a multiple forest on-premises environment."
---

# Skype Room System multiple forest on-premises deployments
 
Read this topic to learn how to deploy Skype Room System in a multiple forest on-premises environment.
  
> [!NOTE]
> In order to deploy in multiple forests, Skype Room System requires Exchange Server 2013 CU6 released on August 26, 2014. Avoid re-using an existing mailbox for Skype Room System. Use a new (delete old mailbox and re-create) resource mailbox for Skype Room System. To restore the meetings lost by deleting the mailbox, see [Connect or restore a deleted mailbox](https://technet.microsoft.com/library/jj863438%28v=exchg.150%29.aspx). 
  
After creating the mailbox, you can use Set-CalendarProcessing to configure the mailbox. Refer to steps 3 through 6 under Single forest on-premises deployments for more details. After creating an Exchange Resource mailbox for Skype Room System, enable the account for Skype for Business by following the steps in Enabling Skype Room System Accounts for Skype for Business under Single forest on-premises deployments.
  
## Option 1: Create a new resource mailbox

To deploy Skype Room System in a multi-forest environment:
  
1. Create a Linked User (LinkedRoomTest) in Active Directory (Authentication Forest).
    
2. Run the following commands in the Exchange Server Management Shell:
    
   ```
   $cred = Get-Credential AuthForest\LinkedRoomTest
   new-mailbox -Alias LinkedRoomTest -LinkedMasterAccount AuthForest\LinkedRoomTest -LinkedDomainController AuthForest-4939.AuthForest.extest.contoso.com -UserPrincipalName LinkedRoomTest@ExchangeForest.contoso.comm -Name LinkedRoomTest -LinkedCredential $cred -LinkedRoom
   ```

## Option 2: Change an existing room mailbox to Skype Room System (linked) resource mailbox

```
$cred=Get-Credential AuthForest\LinkedRoomTest1
Set-mailbox -Alias LinkedRoomTest1 -LinkedMasterAccount AuthForest\LinkedRoomTest1 -LinkedDomainController AuthForest-4939.AuthForest.extest.contoso.com -Name LinkedRoomTest1 -LinkedCredential $cred -Identity LinkedRoomTest1
```


