---
title:  End of availability for classic Teams client
ms.author: heidip
author: MicrosoftHeidi
manager: jtremper
ms.topic: article
ms.date: 02/22/2023
ms.service: msteams
audience: admin
ms.collection: 
- M365-collaboration
- m365initiative-deployteams
ms.reviewer: 
search.appverid: MET150
f1.keywords:
- NOCSH
description: Learn about the end date for classic Teams client for various groups of Teams users.
appliesto: 
- Microsoft Teams
ms.localizationpriority: high
---

# End of availability for classic Teams client

## Overview

After March 31 2024, a new Teams client will be rolled out, in stages, for users who are still on classic Teams. The roll out means installing the new Teams client for users who still have the classic Teams client, and uninstalling the classic Teams client 14 days after the installation of new Teams.

After this process is complete, classic Teams will be unavailable for different users as outlined in this table:

|Availability area                                | Date         |Link |
|-------------------------------------------------|--------------|-----|
|Windows                                          |March 31 2024 |     |
|Mac                                              |March 31 2024 |     |
|EDU                                              |March 31 2024 |     |
|Web                                              |March 31 2024 |     |
|Government Cloud (GCC, GCC High)                 |May 31 2024   |     |
|Government Cloud (DOD)                           |June 30 2024  |     |
|Microsoft 365 operated by 21Vianet in China      |June 30 2024  |     |
|VDI                                              |June 30 2024  | [Upgrade to new Teams for Virtualized Desktop Infrastructure (VDI)](new-teams-vdi-requirements-deploy.md) |
|Unsupported OS users (including Win 10 LTSC)     |June 30 2024  |[Prerequisites](new-teams-deploy-using-policies.md#prerequisites) |
|Policy and prerequisite blocked users            |June 30 2024  |[Troubleshooting installation issues in the new Teams client](new-teams-troubleshooting-installation.md) |

## Timeline updates

This rollout is going to differ based on your Teams Admin Center policy controls.

- Microsoft-managed rollout: If you left the policy controls at their defaults, we'll continue rolling out new Teams as per the schedule outlined above, with one update: We won't proceed with the uninstallation of the classic Teams client for 14 days.
- Admin-managed rollout: Admins can choose to control the new Teams rollout as outlined in [Upgrade to the new Teams using policies](new-teams-deploy-using-policies.md). These policies will no longer work at the start of April, apart from your VDI users, and the following changes will happen:
  - New Teams will become the default client. The toggle to return to classic Teams will still be available if needed.
  - In mid-May, new Teams will be installed, and the toggle to return to classic Teams will no longer be available. We will attempt to uninstall classic Teams, currently after a period of 14 days.

> [!IMPORTANT]
> We're aware of the concerns around our timeline. Classic Teams users who have encountered issues moving to new Teams or who don't meet the prerequisites to upgrade will still have access to the classic Teams client until July 01 2024 at the earliest. This will give admins more time to address any issues encountered during this process.

## User experience

### What users will see until April 01 2024

Starting in March 2024, any classic Teams users who haven’t updated to new Teams will begin seeing an informational banner to remind them about the timeline for the Microsoft AutoUpdate. This banner will appear in the main Teams client window at the top of the page (underneath the main bar).

:::image type="content" source="media/teams-client-eol-switch-banner.png" alt-text="Shows the banner in Teams client that reads 'Classic Teams won't be available. You'll be switched to the new Teams after availability ends. Switch now.' Switch now is a selectable link.":::

> [!NOTE]
> You can dismiss this banner in every client session until the end of February 2024, but it will reappear with each client launch.

Classic Teams will remain available to use until March 31 2024. However, we highly encourage admins to update their users to new Teams, as new features are only being added to the new Teams client. Learn more in the [Upgrade to the new Teams using policies](new-teams-deploy-using-policies.md) article.

If users are on an unsupported OS (including Win 10 LTSC), you’ll see a slightly different banner messaging:

:::image type="content" source="media/teams-client-eol-requirements-banner.png" alt-text="Shows the banner in Teams client that reads 'Classic Teams won't be available for use after the end of the availability period. To use the new Teams, update your OS to meet requirements or contact your IT Admin.' Requirements is a selectable link.":::

> [!NOTE]
> Users on a June 30th timeline will see this banner from April 1 2024.

Here's a list of the banner messages you may experience after January 31 2024:

|Condition for triggering the banner |Banner message |Further information |
|------------------------------------|---------------|--------------------|
|Classic Teams is being used or new Teams is installed |Classic Teams won't be available for use after March 31, 2024. You’ll be switched to the new Teams after this date. Switch now |         |
|Classic Teams is being used, new Teams is not installed |Classic Teams won't be available for use after March 31, 2024. Get the new Teams |         |
|Microsoft can't update because of policy restrictions (Commercial) |Classic Teams won’t be available for use after March 31, 2024, and we can't update to the new Teams due to org policy. For more info, contact your IT admin. Learn more |[Troubleshooting installation issues in the new Teams client](new-teams-troubleshooting-installation.md) |
|If your Teams update policy is set to **Not enabled** |Classic Teams won’t be available for use after March 31, 2024. Contact your IT admin to switch to the new Teams. Learn more |[Classic Teams users to be updated to new Teams after March 31, 2024](new-teams-deploy-using-policies.md) |

### What users will experience after March 31 2024

After March 31 2024, if you’re already running on new Teams, there will be no change in behavior. Your Teams will continue working as expected.

If you are still on classic Teams, the following applies:

- Microsoft-managed rollout: If you left the policy controls at their defaults, we'll continue rolling out new Teams as per the schedule outlined above, with one update: We won't proceed with the uninstallation of the classic Teams client for 14 days.
- Admin-managed rollout: Admins can choose to control the new Teams rollout as outlined in [Upgrade to the new Teams using policies](new-teams-deploy-using-policies.md). These policies will no longer work at the start of April, apart from your VDI users, and the following changes will happen:
  - New Teams will become the default client. The toggle to return to classic Teams will still be available if needed.
  - In mid-May, new Teams will be installed, and the toggle to return to classic Teams will no longer be available. We will attempt to uninstall classic Teams, currently after a period of 14 days.

If you're on the June timeline, here's a list of the banner messages you may experience after March 31 2024:

|Condition for triggering the banner |Banner message |Further information |
|------------------------------------|---------------|--------------------|
|Unsupported Windows operating system |Classic Teams will soon be unavailable for use. To use the new Teams, update your OS to meet requirements or contact your IT admin. Learn more. |[Prerequisites](new-teams-deploy-using-policies.md#prerequisites) |
|Unsupported Mac operating system |Classic Teams will soon be unavailable for use. To use the new Teams, update your OS to meet requirements or contact your IT admin. Learn more. |[Prerequisites](new-teams-deploy-using-policies.md#prerequisites) |
|Unsupported operating system (EDU) |Classic Teams will soon be unavailable for use. To use the new Teams, update your OS to meet requirements or contact your IT admin. Learn more. |[Prerequisites](new-teams-deploy-using-policies.md#prerequisites) |
|Unsupported operating system (Gov) |Classic Teams will soon be unavailable for use. To use the new Teams, update your OS to meet requirements or contact your IT admin. Learn more. |[Prerequisites](new-teams-deploy-using-policies.md#prerequisites) |
|Unsupported operating system (DOD)|Classic Teams will soon be unavailable for use. To use the new Teams, update your OS to meet requirements or contact your IT admin. Learn more. |[Prerequisites](new-teams-deploy-using-policies.md#prerequisites)|
|Microsoft 365 operated by 21Vianet in China |Classic Teams will soon be unavailable for use. To use the new Teams, update your OS to meet requirements or contact your IT admin. Learn more. |[Prerequisites](new-teams-deploy-using-policies.md#prerequisites)|
|Unsupported OS (VDI) |Classic Teams will soon be unavailable for use. Contact your IT admin to switch to the new Teams. Learn more. |[Prerequisites](new-teams-deploy-using-policies.md#prerequisites) |
|Microsoft cannot update because of policy restrictions (EDU) |Classic Teams will soon be unavailable for use, and we can't update to the new Teams due to org policy. For more info, contact your IT admin. Learn more |         |

### What happens if we can’t update users to new Teams

Once classic Teams is no longer available for you, you're going to see a dialog similar to this one, and classic Teams won't work for you anymore.

:::image type="content" source="media/teams-client-eol-notification-box.png" alt-text="Teams dialog box that appears after classic Teams no longer works, if you're unable to be updated to the new Teams client. The notification box has a link to requirements and a button that takes you to Teams on the web.":::

To use Teams after this point, install the new Teams client or use Teams on the web.

If you fall under the June 30 2024 list items and you aren’t able to be updated at the end of March, your classic Teams client will continue to run until June 30 2024. There will continue to be a warning banner at the top of your client. We do ask that users update their OS and address any other issues to continue using the Teams client after this time, as new features are only being added to the new Teams client.

## Admin experience

### What admins will see until the end of March 31 2024

Admins have full control over their tenant’s transition to new Teams via the [Upgrade to the new Teams using policies](new-teams-deploy-using-policies.md) article.

A bulk installer, including offline capability, is provided for admins who want to deploy new Teams using their own tools and process and use Teams policies to move their users to the desired experience: [Bulk upgrade to the new Microsoft Teams client](new-teams-bulk-install-client.md).

Microsoft highly recommends that admins who want more control or a more gradual rollout of new Teams take advantage of these tools and functionality to begin slowly transitioning their users to new Teams now. Policies can be targeted to individual users, groups of users, or your entire tenant to give you flexibility to release to users group by group while monitoring progress and feedback.

### What admins will experience starting April 01 2024

In the Teams admin center:

- Microsoft-managed rollout: If you left the policy controls at their defaults, we'll continue rolling out new Teams as per the schedule outlined above, with one update: We won't proceed with the uninstallation of the classic Teams client for 14 days.
- Admin-managed rollout: Admins can choose to control the new Teams rollout as outlined in [Upgrade to the new Teams using policies](new-teams-deploy-using-policies.md). These policies will no longer work at the start of April, apart from your VDI users, and the following changes will happen:
  - New Teams will become the default client. The toggle to return to classic Teams will still be available if needed.
  - In mid-May, new Teams will be installed, and the toggle to return to classic Teams will no longer be available. We will attempt to uninstall classic Teams, currently after a period of 14 days.

## Frequently Asked Questions

> [!NOTE]
> The unavailability of classic Teams and dates mentioned in this article don't currently apply to Windows 10 users signed into Teams for Life or users signed into both Teams for Life and Teams for Work.

### Users

- **If a user has both clients installed:** Only new Teams will work after the end of availability, and we'll attempt to uninstall the classic Teams client.
- **If only the new Teams client is installed:** There won’t be any difference.
- **If a user can’t install the new Teams client due to a reason outlined in the table above, such as unsupported OS (including Win 10 LTSC):** These users will be allowed to use classic Teams until June 30, 2024 (as per above schedule) to allow for updating operating system to modifying permissions etc. After June 30 2024, classic Teams won't work.

### Admins

- **The system requirements for the new Teams client:** [Prerequisites](new-teams-deploy-using-policies.md#prerequisites)
- **When will admins see the new Teams Only policy in their tenant:** [Upgrade to the new Teams using policies](new-teams-deploy-using-policies.md)
- **What will happen with the update policies:** The update policies may still appear, but they won’t be functional after the end of availability.
- **When will classic Teams client stop being installed with M365 apps:** This will stop happening at the end of the availaibility period.
- **Can I stop the classic Teams client from being uninstalled and what happens if a policy is set to prevent app uninstallation:** Yes, you can stop the classic Teams client from being uninstalled. If your configuration prevents uninstall, Microsoft won't attempt the uninstall again. You'll need to uninstall classic Teams after that point.
- **Do I need to remove the old client:** Microsoft recommends that you remove the classic Teams client once a user has fully transitioned to new Teams. It's security best practice to not leave software that is no longer operational installed on a machine. Microsoft will attempt to remove the classic Teams client on your behalf, but if this is blocked or prevented by your configuration or policies it is your responsibility to conduct this removal yourself.
- **What can I do if users still need classic Teams:** You won’t be able to use classic Teams once availability ends, or June 30 2024 if you meet the conditions in the table at the start of the article. Until that date you'll still have a banner announcing the end of classic Teams at the top of your client. Please reference this page for more information: [Features that are changing in the new Microsoft Teams](new-teams-whats-changing.md)
- **Are there any scripts available if the admin needs to bulk uninstall classic Teams:** Check out our [uninstallation](msi-deployment.md#uninstallation) documentation.

### Client

- **Will classic Teams be removed automatically:** Microsoft will attempt to uninstall classic Teams after the availability period ends. If this fails, admins must uninstall classic Teams for their users. You can find more information on [uninstallation](msi-deployment.md#uninstallation) in this article.
- **When or how will it be removed, and what triggers the uninstall:** This will happen after the availability period ends. As each user receives the automatic update and switches to new Teams, an attempt will be made to uninstall classic Teams.
- **Will classic Teams be removed for all users on the device:** Yes.
- **Will both Windows and Mac support uninstallation:** Yes.
- **What if I need to use classic Teams after the availability period:** You won’t be able to use classic Teams after the availability period ends, or June 30 2024 if you meet the conditions in the table at the start of the article. Until that date you'll still have a banner announcing the end of classic Teams at the top of your client. Please reference this page for more information: [Features that are changing in the new Microsoft Teams](new-teams-whats-changing.md)
- **Will I be able to download classic Teams after the availability period ends:** Yes, but it won't be functional unless you meet one of the conditions to extend classic Teams functionality until June 30 2024.

### VDI

- **Will the earlier date apply to users on VDI devices:** No, the June 30 2024 date applies to users on VDI devices.
