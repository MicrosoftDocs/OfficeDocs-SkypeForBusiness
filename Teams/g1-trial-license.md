---
title: Manage the free Office 365 G1 Trial for US government
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: article
audience: Admin
ms.reviewer: aarimm
ms.service: msteams
search.appverid: MET150
ms.localizationpriority: high
description: "For US government, if you don't have Microsoft Teams and need it in a hurry, roll out the Office 365 G1 Trial for your users who need to work remotely or from home (WFH) in response to the COVID-19 (coronavirus) outbreak."
ms.collection: 
  - M365-collaboration
  - Teams_ITAdmin_RemoteWorkers
appliesto: 
  - Microsoft Teams
---

# Manage the Office 365 G1 Trial for US government 

As of July 1, 2020, the Office 365 E1 Trial license is no longer available. If you need to license users for Microsoft Teams, read the [Microsoft Teams service description](/office365/servicedescriptions/teams-service-description) for a list of paid subscriptions that include Teams. 

Use the guidance in this article to manage your existing Office 365 G1 Trial licenses, including [upgrading to a paid subscription](#upgrade-users-from-the-office-365-g1-trial-license). To learn more, read [Microsoft 365 Government Plans](https://www.microsoft.com/microsoft-365/government/compare-office-365-government-plans) and the [Microsoft Teams capabilities available in the GCC Cloud](plan-for-government-gcc.md).

Don't miss all of our guidance for [supporting remote workers with Teams](support-remote-work-with-teams.md).

## Manage the G1 Trial

Once you've activated the Office 365 G1 Trial, turn on the license for any uses who need it. To learn how, read [Manage user access to Teams](user-access.md).

Once you've turned on the G1 Trial for the users who need it, you'll manage these users just like you manage users who have a paid license. For more information, see [Manage Teams settings for your organization](enable-features-office-365.md).

### Upgrade users from the Office 365 G1 Trial license

To upgrade G1 Trial users to a paid subscription:

1.  Purchase a subscription that includes Teams.

2.  Remove the Office 365 G1 Trial subscription from the user.

3.  Assign the newly purchased license.

For more information, see [Teams for Government](expand-teams-across-your-org/teams-for-government-landing-page.md).

> [!NOTE]
> If the G1 Trial license ends and a user is not immediately upgraded to a subscription that includes Teams, the user data is not removed. The user still exists in Azure Active Directory and all data within Teams still remains. Once a new license is assigned to the user to enable Teams functionality again, all content will still exist.
> 
### Remove an Office 365 G1 Trial license

  - If you would like to remove this license by using PowerShell, see: [Remove licenses from user accounts with Office 365 PowerShell](/office365/enterprise/powershell/remove-licenses-from-user-accounts-with-office-365-powershell)

  - If you would like to remove this license through the admin portal, see: [Delete a user from your organization](/microsoft-365/admin/add-users/delete-a-user)

## Related topics

[Manage user access to Teams](user-access.md)

[Manage Teams settings for your organization](enable-features-office-365.md)
