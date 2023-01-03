---
title: Configure external meetings and chat with Skype for Business Server hybrid
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.reviewer: alsolom
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - Teams_ITAdmin_GuestAccess
  - M365-collaboration
  - m365initiative-externalcollab
search.appverid: MET150
f1.keywords:
- CSH
ms.custom: 
- ms.teamsadmincenter.externalaccess.overview
- chat-teams-channels-revamp
appliesto: 
  - Microsoft Teams
ms.localizationpriority: normal
description: 
---

# Configure external meetings and chat with Skype for Business Server hybrid

You can configure external meetings and chat in Teams using the *external access* feature. External access is a way for Teams users from outside your organization to find, call, chat, and set up meetings with you in Teams. You can also use external access to communicate with people from other organizations who are still using Skype for Business (online and on-premises) and Skype.

If you want people from other organizations to have access to your teams and channels, use guest access instead. For more information about the differences between external access and guest access, see [Compare external and guest access](communicate-with-users-from-other-organizations.md#compare-external-and-guest-access). 


To enable users in your organization to communicate with users in another organization, both organizations must enable federation. The steps to enable federation for a given organization depend on whether the organization is purely online, hybrid, or purely on-premises.

| If your organization is | Enable federation as follows |
|:---------|:-----------------------|
|Online with no Skype for Business on-premises. This includes organizations that have TeamsOnly users and/or Skype for Business Online users.| If using Teams Admin Center: <br>- Make sure the domains that you want to communicate with are allowed for external access.<br><br>If using PowerShell:<br>- Ensure the tenant is enabled for federation: `Get-CsTenantFederationConfiguration` must show `AllowFederatedUsers=true`. <br>- Ensure the user's effective value of `CsExternalAccessPolicy` has `EnableFederationAccess=true`.<br>- If you are not using open federation, ensure the target domain is listed in `AllowedDomains` of `CsTenantFederationConfiguration`. |
|On-premises only| In on-premises tools: <br>- Ensure federation is enabled in `CsAccessEdgeConfiguration`.<br>- Ensure federation for the user is enabled through `ExternalAccessPolicy` (either through the global policy, site policy, or user assigned policy). <br> - If you are not using open federation, ensure the target domain is listed in `AllowedDomains`.|
|Hybrid with some users online (in either Skype for Business or Teams) and some users on-premises. | Follow above steps for both online and on-premises organizations. |


## Federation Diagnostic Tool

If you're an administrator, you can use the following diagnostic tool to validate a Teams user can communicate with a federated Teams user:

1. Select **Run Tests** below, which will populate the diagnostic in the Microsoft 365 Admin Center. 

   > [!div class="nextstepaction"]
   > [Run Tests: Teams Federation](https://aka.ms/TeamsFederationDiag)

2. In the Run diagnostic pane, enter the **Session Initiation Protocol (SIP) Address** and the **Federated tenant's domain name**, and then select **Run Tests**.

3. The tests will return the best next steps to address any tenant or policy configurations that are preventing communication with the federated user.


## Related topics

