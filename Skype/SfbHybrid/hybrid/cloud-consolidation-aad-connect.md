---
ms.date: 11/09/2018
title: "Update Microsoft Entra Connect to include more than one forest"
author: MicrosoftHeidi
ms.author: heidip
manager: jtremper
ms.reviewer: bjwhalen
ms.topic: article
ms.service: skype-for-business-server
search.appverid: MET150
ms.collection: 
- Hybrid 
- M365-voice
- m365initiative-voice
- M365-collaboration
- Teams_ITAdmin_Help
- Adm_Skype4B_Online
audience: ITPro
f1.keywords:
- NOCSH
appliesto:
- Skype for Business 
- Microsoft Teams
ms.localizationpriority: medium
description: "This appendix includes detailed steps for updating Microsoft Entra Connect to include more than one forest as part of cloud consolidation for Teams and Skype for Business."
---

# Update Microsoft Entra Connect to include more than one forest

[!INCLUDE [sfbo-retirement](../../Hub/includes/sfbo-retirement.md)]

Microsoft Entra Connect supports [syncing from multiple forests](/azure/active-directory/connect/active-directory-aadconnect-topologies). It supports only one instance of Microsoft Entra Connect syncing to Microsoft Entra ID. In cases where Microsoft Entra ID is already installed in one forest, the existing instance of Microsoft Entra Connect must be updated to sync from the other forest.

 - If all identities are represented only once across both forests (that is, you haven’t made any mail-enabled contacts), then you can rerun the Microsoft Entra Connect wizard, choose “Customize synchronization options,” and then on the **Connect Your Directories** page, enter the name of the other forest and credentials.<br><br>
 ![The Connect your directories page.](../media/cloud-consolidation-connect-your-directories.png)
 - If users can exist in more than one directory, and you’ll be merging the data, you'll need to uninstall Microsoft Entra Connect and reinstall it. You need to take this action because the cross-forest join rules condition can only be configured during the first install. This is done on the following page:<br><br>
 ![The Uniquely identifying your users page.](../media/cloud-consolidation-uniquely-identifying-your-users.png)


## See also

[Cloud Consolidation for Teams and Skype for Business](cloud-consolidation.md)
