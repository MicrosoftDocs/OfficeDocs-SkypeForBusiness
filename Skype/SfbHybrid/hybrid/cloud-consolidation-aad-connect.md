---
ms.date: 11/09/2018
title: "Update Azure AD Connect to include more than one forest"
ms.author: serdars
author: MicrosoftHeidi
manager: serdars
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
description: "This appendix includes detailed steps for updating Azure AD Connect to include more than one forest as part of cloud consolidation for Teams and Skype for Business."
---

# Update Azure AD Connect to include more than one forest

[!INCLUDE [sfbo-retirement](../../Hub/includes/sfbo-retirement.md)]

Azure AD Connect supports [syncing from multiple forests](/azure/active-directory/connect/active-directory-aadconnect-topologies). It supports only one instance of Azure AD Connect syncing to Azure AD. In cases where Azure AD is already installed in one forest, the existing instance of Azure AD Connect must be updated to sync from the other forest.

 - If all identities are represented only once across both forests (that is, you haven’t made any mail-enabled contacts), then you can simply re-run the Azure AD Connect wizard, choose “Customize synchronization options,” and then on the **Connect Your Directories** page, enter the name of the other forest and credentials.<br><br>
 ![The Connect your directories page.](../media/cloud-consolidation-connect-your-directories.png)
 - If users can exist in more than one directory, and you’ll be merging the data, you'll need to uninstall Azure AD Connect and re-install it. You need to take this action because the cross-forest join rules condition can only be configured during the first install. This is done on the following page:<br><br>
 ![The Uniquely identifying your users page.](../media/cloud-consolidation-uniquely-identifying-your-users.png)


## See also

[Cloud Consolidation for Teams and Skype for Business](cloud-consolidation.md)
