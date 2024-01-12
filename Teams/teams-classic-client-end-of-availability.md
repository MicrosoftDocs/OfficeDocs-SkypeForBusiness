---
title:  End of availability for classic Teams client
ms.author: heidip
author: MicrosoftHeidi
manager: jtremper
ms.topic: article
ms.date: 01/11/2023
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

On March 31 2024, a new Teams client will be rolled out for users who are still on classic Teams, installing the new Teams client for them and uninstalling the classic Teams client. After this time, classic Teams will be unavailable for different users as outlined in this table:

|Availability area                                | Date         |Link |
|-------------------------------------------------|--------------|-----|
|Windows                                          |March 31 2024 |     |
|Mac                                              |March 31 2024 |     |
|EDU                                              |March 31 2024 |     |
|Web                                              |March 31 2024 |     |
|Government Cloud (GCC, GCC High, DOD)            |March 31 2024 |     |
|Policy and prerequisite blocked users (non-EDU) |March 31 2024 |[Troubleshooting installation issues in the new Teams client](new-teams-troubleshooting-installation.md) |
|VDI                                              |June 30 2024  | [Upgrade to new Teams for Virtualized Desktop Infrastructure (VDI)](new-teams-vdi-requirements-deploy.md) |
|Unsupported OS users (including Win 10 LTSC)     |June 30 2024  |[Prerequisites](new-teams-deploy-using-policies.md#prerequisites) |
|Policy and prerequisite blocked users (EDU)     |June 30 2024  |[Troubleshooting installation issues in the new Teams client](new-teams-troubleshooting-installation.md)       |

## User experience

### What users will see until March 31 2024

Starting on February 1 2024, any classic Teams users who haven’t updated to new Teams will begin seeing an informational banner to remind them about the timeline for the auto update. This banner will appear in the main Teams client window at the top of the page (underneath the main bar).

:::image type="content" source="media/teams-client-eol-switch-banner.png" alt-text="Shows the banner in Teams client that reads 'Classic Teams won't be available after March 31, 2024. You'll be switched to the new Teams after this date. Switch now.' Switch now is a selectable link.":::

> [!NOTE]
> You can dismiss this banner in every client session until the end of February 2024, but it will reappear with each client launch.

Classic Teams will remain available to use until March 31 2024. However, we highly encourage admins to update their users to new Teams, as new features are only being added to the new Teams client. Learn more in the [Upgrade to the new Teams using policies](new-teams-deploy-using-policies.md) article.

If users are on an unsupported OS (including Win 10 LTSC), you’ll see a slightly different banner messaging:

:::image type="content" source="media/teams-client-eol-requirements-banner.png" alt-text="Shows the banner in Teams client that reads 'Classic Teams won't be available for use after June 30, 2024. To use the new Teams, update your OS to meet requirements or contact your IT Admin.' Requirements is a selectable link.":::

> [!NOTE]
> Users on a June 30th timeline will see this banner from April 1 2024.

### What users will experience after March 31 2024

After March 31 2024, if you’re already running on new Teams, there will be no change in behavior. Your Teams will continue working as expected.

Users on classic Teams will be automatically updated to the new Teams client. Users won’t be able to switch back to classic Teams after this date, because classic Teams won’t be functional. Microsoft will attempt to uninstall classic Teams.

### What happens if we can’t update users to new Teams

If you meet the conditions for one of the March 31 entries in the table at the start of this article, and you can’t be updated to new Teams (due to policies or configuration), the classic Teams client will stop working after March 31 2024. You'll see a notification box indicating this as well.

:::image type="content" source="media/teams-client-eol-notification-box.png" alt-text="Teams notification box that appears after classic Teams no longer works, if you're unable to be updated to the new Teams client. The notification box has a link to requirements and a button that takes you to Teams on the web.":::

To use Teams after this point, install the new Teams client or use Teams on the web.

If you fall under the June 30 2024 list items and you aren’t able to be updated at the end of March, your classic Teams client will continue to run until June 30 2024. There will continue to be a warning banner at the top of your client. We do ask that users update their OS and address any other issues to continue using the Teams client after this time, as new features are only being added to the new Teams client.

## Admin experience

### What admins will see until March 31 2024

Admins have full control over their tenant’s transition to new Teams via the [Upgrade to the new Teams using policies](new-teams-deploy-using-policies.md) article.

A bulk installer, including offline capability, is provided for admins who want to deploy new Teams using their own tools and process and use Teams policies to move their users to the desired experience: [Bulk upgrade to the new Microsoft Teams client](new-teams-bulk-install-client.md).

Microsoft highly recommends that admins who want more control or a more gradual rollout of new Teams take advantage of these tools and functionality to begin slowly transitioning their users to new Teams now. Policies can be targeted to individual users, groups of users, or your entire tenant to give you flexibility to release to users group by group while monitoring progress and feedback.

### What admins will experience starting March 31 2024

Beginning March 31 2024, all policy options within Teams Admin Center to control the transition to new Teams will be made unavailable or will no longer function for all users.

After these options are removed, Microsoft will begin moving all users except VDI users back to the **Microsoft controlled** policy setting. After March 31 2024 the **Microsoft controlled** policy setting will equate to the user being assigned the **New Teams Only** policy (this policy option will be released soon). This will allow them to transition the user to new Teams and then uninstall the classic Teams client. Learn more in the [Upgrade to the new Teams using policies](new-teams-deploy-using-policies.md) article.

## Frequently Asked Questions

### Users

- **If a user has both clients installed:** Only new Teams will work after March 31 2024, and we'll attempt to uninstall the classic Teams client.
- **If only the new Teams client is installed:** There won’t be any difference.
- **If a user can’t install the new Teams client due to a reason outlined in the table above, such as unsupported OS (including Win 10 LTSC):** These users will be allowed to use classic Teams until June 30, 2024 (as per above schedule) to allow for updating operating system to modifying permissions etc. After June 30 2024, classic Teams won't work.

### Admins

- **The system requirements for the new Teams client:** [Prerequisites](new-teams-deploy-using-policies.md#prerequisites)
- **When will admins see the new Teams Only policy in their tenant:** [Upgrade to the new Teams using policies](new-teams-deploy-using-policies.md)
- **What will happen with the update policies:** The update policies may still appear, but they won’t be functional after March 31 2024.
- **When will classic Teams client stop being installed with M365 apps:** This will stop happening on March 31 2024.
- **Can I stop the classic Teams client from being uninstalled and what happens if a policy is set to prevent app uninstallation:** Yes, you can stop the classic Teams client from being uninstalled. If your configuration prevents uninstall, Microsoft won't attempt the uninstall again. You'll need to uninstall classic Teams after that point.
- **Do I need to remove the old client:** Microsoft recommends that you remove the classic Teams client once a user has fully transitioned to new Teams. It's security best practice to not leave software that is no longer operational installed on a machine. Microsoft will attempt to remove the classic Teams client on your behalf, but if this is blocked or prevented by your configuration or policies it is your responsibility to conduct this removal yourself.
- **What can I do if users still need classic Teams:** You won’t be able to use classic Teams after March 31 2024, or June 30 2024 if you meet the conditions in the table at the start of the article. Until that date you'll still have a banner announcing the end of classic Teams at the top of your client. Please reference this page for more information: [Features that are changing in the new Microsoft Teams](new-teams-whats-changing.md)
- **Are there any scripts available if the admin needs to bulk uninstall classic Teams:** Check out our [uninstallation](msi-deployment.md#uninstallation) documentation.

### Client

- **Will classic Teams be removed automatically:** Microsoft will attempt to uninstall classic Teams after March 31 2024. If this fails, admins must uninstall classic Teams for their users. You can find more information on [uninstallation](msi-deployment.md#uninstallation) in this article.
- **When or how will it be removed, and what triggers the uninstall:** This will happen after March 31 2024. As each user receives the automatic update and switches to new Teams, an attempt will be made to uninstall classic Teams.
- **Will classic Teams be removed for all users on the device:** Yes.
- **Will both Windows and Mac support uninstallation:** Yes.
- **What if I need to use classic Teams after March 31 2024:** You won’t be able to use classic Teams after March 31 2024, or June 30 2024 if you meet the conditions in the table at the start of the article. Until that date you'll still have a banner announcing the end of classic Teams at the top of your client. Please reference this page for more information: [Features that are changing in the new Microsoft Teams](new-teams-whats-changing.md)
- **Will I be able to download classic Teams after March 31 2024:** Yes, but it won't be functional unless you meet one of the conditions to extend classic Teams functionality until June 30 2024.

### VDI

- **Will the March 31 2024 date apply to users on VDI devices:** No, the June 30 2024 date applies to users on VDI devices.
