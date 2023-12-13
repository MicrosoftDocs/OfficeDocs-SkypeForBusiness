---
ms.date: 11/28/2017
title: "Skype for Business mobile app security"
ms.reviewer: 
ms.author: serdars
author: pamgreen
manager: serdars
ms.topic: article
ms.assetid: d2be8c74-3ba2-4b2d-9807-634904e1f0e8
ms.tgt.pltfrm: cloud
ms.service: skype-for-business-online
search.appverid: MET150
ms.collection: Adm_Skype4B_Online
audience: Admin
appliesto:
- Skype for Business
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.custom:
- Setup
description: "Learn to set up mobile app security for your users. "
---

# Skype for Business mobile app security

[!INCLUDE [sfbo-retirement](../../Hub/includes/sfbo-retirement.md)]

## Skype for Business Client Security

This article covers data encryption information on Skype for Business Mobile Apps.
  
| |**Username/Password**|**App Data (Conversations,<br/> Contact List, Meetings)**|**Diagnostic logs**|
|:-----|:-----|:-----|:-----|
|**Android** |We store credentials information in Android Accounts. We also encrypt credentials before saving them into Accounts. We use " **AES/CBC/PKCS5Padding** " algorithm for encryption. |We store in an encrypted SQL database using a library called [sqlcipher](https://www.zetetic.net/sqlcipher/design/). We use their default algorithm of 256-bit AES in CBC mode. The data at rest is always encrypted in the database file and is only unencrypted in transit inside of the app's volatile memory and call stacks. We also encrypt voicemail files using the same method as the user's name and password encryption (they[/mem/intune/protect/device-compliance-get-started](/mem/intune/protect/device-compliance-get-started) aren't stored in the DB). Voicemails are temporarily unencrypted on disk to allow playback. |This information isn't encrypted. |
|**iOS** |We DO NOT encrypt the username/password in the keychain. The keychain is encrypted, however, on its own. |We're already using [NSFileProtectionCompleteUntilFirstUserAuthentication](https://developer.apple.com/reference/foundation/fileprotectiontype/1616633-completeuntilfirstuserauthentica) data protection flag on all files in the app storage. This means that files in the app storage would be encrypted until user unlocks the device for the first time after the device reboot. |This information isn't encrypted. |
|**Windows Phone** |Windows Phone uses the DPAPI (Data Protection API) in Windows to secure passwords. I believe the encryption scheme used is AES. Windows doesn't give us an option to configure the key size (or scheme), so it's whatever DPAPI gives. It uses the device TPM to secure keys, which are specific to the user and device. Note that DPAPI keys aren't specific to the app. |WP App Data is protected with [DPAP](/previous-versions/windows/apps/hh487164(v=vs.105))I, like the creds. Depending on how much detail we want, some of the index information for the App Data is protected by (non-DPAPI) AES encryption to avoid salting, so we can look up without decrypting, and that key is in turn protected with DPAPI. Cached data can be read by any process from the same phone, assuming it can reach our data folder. Windows encryption doesn't protect from sandbox breach, only external access attempts. |This information isn't encrypted. |
   
> [!NOTE]
> Refer to [this public documentation](/mem/intune/protect/device-compliance-get-started) for device pin enforcement available on each of the above Mobile platforms.
  
## Related topics
[Set up Skype for Business Online](set-up-skype-for-business-online.md)

[Let Skype for Business users add Skype contacts](let-skype-for-business-users-add-skype-contacts.md)

  

