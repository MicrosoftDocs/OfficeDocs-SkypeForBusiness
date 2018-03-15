---
title: "Configuring default picture options in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: End User
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: b1c986f0-6400-447a-9e36-78c1c3a4f793
description: "By default, users' pictures are automatically displayed. If users want to hide their pictures, they can select the Hide my picture option in the Lync client. However, this setting is ignored by some other Office applications."
---

# Configuring default picture options in Lync Server 2013
[]
By default, users' pictures are automatically displayed. If users want to hide their pictures, they can select the **Hide my picture** option in the Lync client. However, this setting is ignored by some other Office applications. 
  
If the possibility of displaying pictures even when turned off by the user is a concern, you can change Lync picture display settings globally or for a site or service so that users' pictures are not shown by default. Use the following Lync Server Management Shell cmdlet so that user's pictures will not be shown unless they explicitly select the **Show my picture** option in the client: 
  
```
Set-CsPrivacyConfiguration -DisplayPublishedPhotoDefault $False
```

For more information about this cmdlet, see the [Set-CsPrivacyConfiguration](set-csprivacyconfiguration.md) in the Lync Server Management Shell documentation. 
  

