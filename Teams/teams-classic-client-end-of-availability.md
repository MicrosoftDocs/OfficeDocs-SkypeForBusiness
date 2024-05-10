---
title:  End of availability for classic Teams client
ms.author: heidip
author: MicrosoftHeidi
manager: jtremper
ms.topic: article
ms.date: 04/23/2024
ms.service: msteams
audience: admin
ms.collection: 
- M365-collaboration
- m365initiative-deployteams
ms.reviewer: 
search.appverid: MET150
f1.keywords:
- NOCSH
description: Learn about the end date for support and the end of availability for classic Teams client in regard to various groups of Teams users.
appliesto: 
- Microsoft Teams
ms.localizationpriority: high
---

# End of availability for classic Teams client

## Overview

A new Teams client is in the process of rolling out, in stages, for users who are still on classic Teams client. This rollout involves installing the new Teams client for users who still have the classic Teams client, with Microsoft attempting to uninstall the classic Teams client 14 days after the installation of new Teams. This article will discuss the timelines and details of **end of support** and **end of availability** for classic Teams client.

### Timeline updates

This rollout is going to differ based on your Teams Admin Center policy controls.

> [!IMPORTANT]
> These timelines don't apply to GCC, GCCH, and DoD. We cover this in a later section.

**Native clients excluding VDI**:

The end of support for the classic Teams client starts July 1, 2024. The end of availability for the classic Teams client starts July 1, 2025.

:::image type="content" source="media/teams-client-eoa-timeline.png" alt-text="A chart showing the timelines for classic Teams to new Teams.":::

**VDI timeline**:

> [!IMPORTANT]
> An updated VDI timeline for GCCH/DOD will be published soon.

The end of support for the classic Teams client in VDI starts October 1, 2024. The end of availability for the classic Teams client in VDI starts July 1, 2025.

:::image type="content" source="media/new-teams-vdi-timeline.png" alt-text="A chart showing the timelines for classic Teams to new Teams for VDI.":::

For more information regarding VDI, see [Upgrade to new Teams for Virtualized Desktop Infrastructure (VDI)](new-teams-vdi-requirements-deploy.md).

- Microsoft-managed rollout: If you left the policy controls at their defaults state of Microsoft-controlled, we'll continue rolling out new Teams according to the schedule outlined previously, with one update: We won't proceed with the uninstallation of the classic Teams client for 14 days.
- Admin-managed rollout: Admins can choose to control the new Teams rollout as outlined in [Upgrade to the new Teams client using policies](new-teams-deploy-using-policies.md). These policies will no longer be honored at the start of April, apart from your VDI users, and the following changes will happen:
  - New Teams will be installed and become the default client. The toggle to return to classic Teams will still be available if needed.
  - In mid-May, any users remaining on classic Teams will be switched to new Teams, and the toggle to return to classic Teams will no longer be available. We'll attempt to uninstall classic Teams after 14 days.

We now have additional information regarding the timeline for the end of service and end of availability for classic Teams client.

- End of support: The end of our supporting classic Teams client. We will no longer provide updates or new features for the client, nor will we help resolve support issues with the classic Teams client.
- End of availability: The end of functionality for the classic Teams client. After this deadline, the client will stop working and users will no longer be able to do work in the classic Teams client.

:::image type="content" source="media/teams-client-eoa-timeline-complete.png" alt-text="A chart showing the timelines for the end of support for classic Teams and the end of availability of classic Teams.":::

### Timeline for GCC, GCCH, DoD

This rollout is going to differ based on your Teams Admin Center policy controls.

#### GCC/GCCH

- Microsoft-managed rollout: If you left the policy controls at their default state of Microsoft-controlled, we'll continue rolling out new Teams as follows, keeping in mind that we won't proceed with the uninstallation of the classic Teams client for 14 days.
  - Admin opt-in: Currently, the new Teams update will only be available when administrators enable it for their users. Instructions for configuring policy for the new Teams client can be found in our [Upgrade to the new Teams client using policies](new-teams-deploy-using-policies.md) article. When the policy is enabled for a user, they may then select the **New Teams** toggle switch in their Teams client to initiate the update.
  - New Teams toggle shown: Starting in late February, we will enable the new Teams toggle for Microsoft-controlled users. If they are still using the classic Teams client, they will not be updated unless they toggle the switch.
  - New Teams becomes the default Client: Beginning in late March, the new Teams client will become the default client for Teams users. Customers will receive the new Teams update, unless disallowed by policy. Users may still toggle back to the classic Teams client.
  - New Teams only: Beginning in early May all remaining classic Teams users will be updated to the new Teams client and the toggle switch will be removed. After this process completes, Microsoft will attempt to remove the classic Teams client.
- Admin-managed rollout:
  - New Teams becomes the default client. Beginning in late May, the new Teams client will become the default client for all active Teams users. Customers will receive the new Teams update. Users may still toggle back to the classic Teams client.
  - New Teams Only. Beginning mid-June all remaining classic Teams users will be updated to the new Teams client and the toggle switch will be removed. After this process completes, Microsoft will attempt to remove the classic Teams client.

#### DoD

Starting in mid-July, Teams update policies you've applied in Teams Admin Center will no longer be honored and a Microsoft-controlled rollout will begin according to the following schedule.

- Microsoft-managed rollout: If you left the policy controls at their defaults state of Microsoft-controlled, we'll continue rolling out new Teams as per the schedule outlined previously, with one update: We won't proceed with the uninstallation of the classic Teams client for 14 days.
  - Admin opt-in: Currently, the new Teams update will only be available when administrators enable it for their users. Instructions for configuring policy for the new Teams client can be found here: [Upgrade to the new Teams client using policies](new-teams-deploy-using-policies.md). When the policy is enabled for a user, they may then select the **New Teams** toggle switch in their Teams client to initiate the update.
  - New Teams toggle shown: Starting in late March, we will enable the new Teams toggle for Microsoft-controlled users. If they're still using the classic Teams client, they will not be updated unless they toggle the switch.
  - New Teams becomes the default Client: Beginning in early May, the new Teams client will become the default client for Teams users. Customers will receive the new Teams update, unless disallowed by policy. Users may still toggle back to the classic Teams client.
- Admin-managed rollout:
New Teams only: Beginning in early June all remaining classic Teams users will be updated to the new Teams client and the toggle switch will be removed. After this process completes, Microsoft will attempt to remove the classic Teams client.
Admin-managed tenants. Admins can control their new Teams rollout by setting the Teams updates policy for their users as described in [Upgrade to the new Teams client using policies](new-teams-deploy-using-policies.md). Admins may control the Teams update policy until mid-July.
  - New Teams becomes the default client. Beginning in mid-July, the new Teams client will become the default client for all active Teams users. Customers will receive the new Teams update. Users may still toggle back to the classic Teams client.
  - New Teams Only. Beginning mid-August all remaining classic Teams users will be updated to the new Teams client and the toggle switch will be removed. After this process completes, Microsoft will attempt to remove the classic Teams client after 14 days.

## User experience

**Classic Teams will reach the end of support starting July 1, 2024.**

### What users will experience after March 31, 2024

Starting in March 2024, any classic Teams users who haven’t updated to new Teams will begin seeing an informational banner to remind them about the classic Teams end of support timeline. This banner will appear in the main Teams client window at the top of the page (underneath the main bar).

:::image type="content" source="media/teams-client-eol-switch-banner-prior.png" alt-text="Shows the banner at the top of the Teams client that reads 'Classic Teams will be unsupported starting July 1, 2024. You'll be switched to the new Teams at that time. Learn more.' Learn more is a selectable link.":::

If we're unable to move you to new Teams, here's a list of the banner messages you may experience:

|Condition for triggering the banner |Banner message |Further information |
|------------------------------------|---------------|--------------------|
|Unsupported Windows operating system |Classic Teams will soon be unavailable for use. To use the new Teams, update your OS to meet requirements or contact your IT admin. Learn more. |[Prerequisites](new-teams-deploy-using-policies.md#prerequisites) |
|Unsupported Mac operating system |Classic Teams will soon be unavailable for use. To use the new Teams, update your OS to meet requirements or contact your IT admin. Learn more. |[Prerequisites](new-teams-deploy-using-policies.md#prerequisites) |
|Unsupported operating system (EDU) |Classic Teams will soon be unavailable for use. To use the new Teams, update your OS to meet requirements or contact your IT admin. Learn more. |[Prerequisites](new-teams-deploy-using-policies.md#prerequisites) |
|Unsupported operating system (Gov) |Classic Teams will soon be unavailable for use. To use the new Teams, update your OS to meet requirements or contact your IT admin. Learn more. |[Prerequisites](new-teams-deploy-using-policies.md#prerequisites) |
|Unsupported operating system (DOD)|Classic Teams will soon be unavailable for use. To use the new Teams, update your OS to meet requirements or contact your IT admin. Learn more. |[Prerequisites](new-teams-deploy-using-policies.md#prerequisites)|
|Microsoft 365 operated by 21Vianet in China |Classic Teams will soon be unavailable for use. To use the new Teams, update your OS to meet requirements or contact your IT admin. Learn more. |[Prerequisites](new-teams-deploy-using-policies.md#prerequisites)|
|Unsupported OS (VDI) |Classic Teams will soon be unavailable for use. Contact your IT admin to switch to the new Teams. Learn more. |[Prerequisites](new-teams-deploy-using-policies.md#prerequisites) |
|Microsoft can't update because of policy restrictions (EDU) |Classic Teams will soon be unavailable for use, and we can't update to the new Teams due to org policy. For more info, contact your IT admin. Learn more |         |

**On July 1, 2024, classic Teams becomes unsupported**. Users still running classic Teams due to configuration issues or an unsupported OS will experience in-app dialog messages informing them that the client is no longer supported. These dialogs are dismissible, but will reappear periodically.

:::image type="content" source="media/teams-client-unsupported-cannot-upgrade.png" alt-text="A screenshot of an in-app dialog banner explaining that the Teams classic client has reached the end of supportability, and this device couldn't be upgraded. There's also a link to 'Learn about installation issues' and two buttons. The first button says to 'Continue using classic Teams' and the second says 'Try new Teams on the web'.":::

### Classic Teams End of availability

#### Unsupported OS

- For users on Windows 7, 8, and 8.1, classic Teams will reach the end of availability starting on **October 23, 2024**. Users running classic Teams on these operating systems will see warning dialogs about end of availability starting in August. On October 23, 2024, users will experience the end of availability dialogs and will be blocked from accessing the classic Teams desktop clients.

If users can't upgrade their OS, the new Teams web app will be available on [supported browsers](new-teams-web.md#prerequisites) as an alternative. Users will experience non-dismissible in-app dialogs informing about the end of availability with an option to use new Teams web app.

- For users on Win 10, macOS versions below Big Sur(11), LTSC users, or users with configuration issues, classic Teams will reach the end of availability starting July 1, 2025. Users running classic Teams on these operating systems will experience the end of availability dialogs and will be blocked from accessing the classic Teams desktop clients.

If users can't upgrade to the new Teams client on their device, the new Teams web app will be available on [supported browsers](new-teams-web.md#prerequisites) as an alternative.

> [!NOTE]
> You can dismiss this banner when it starts to appear, but the banner will reappear with each client launch.

Here's a list of the messages you may experience:

|Scenario |End of support warning |End of support |End of availability warning |End of availability |
|---------|-----------------------|---------------|----------------------------|--------------------|
|Unsupported operating system |Classic Teams will soon be unsupported, and your OS needs to be updated to run the new Teams. Starting July 1, 2024, we'll no longer be supporting classic Teams. Update your OS or contact your IT department. View minimum requirements |Classic Teams is no longer supported and your OS needs to be updated to run the new Teams. As of July 1, we're no longer supporting classic Teams. Update your OS or contact your IT department. View minimum requirements |Classic Teams will soon be unavailable, and your OS needs to be updated to run the new Teams. Starting July 1, 2025, classic Teams will no longer be available for use. Update your OS or talk to your IT department. View minimum requirements |Classic Teams is no longer available, and your OS needs to be updated to run the new Teams. As of July 1, 2025, classic Teams is no longer available for use. Update your OS or talk to your IT department. To experience the new Teams, you can try it out on the web. View minimum requirements |
|Windows GPO policy blocked users |Classic Teams will soon be unsupported, but due to org policy, we couldn't update you to the new Teams. Starting July 1, 2024, we'll no longer be supporting classic Teams. To update to the new Teams, contact your IT department. Learn about installation issues |Classic Teams is no longer supported, but due to org policy we couldn't update you to the new Teams. As of July 1, we're no longer supporting classic Teams. We couldn't update to the new Teams due to org policy. Contact your IT department. Learn more |Classic Teams will soon be unavailable, but due to org policy, we couldn't update you to the new Teams. Starting July 1, 2025, classic Teams will no longer be available for use. To update t othe new Teams, contact your IT department. Learn about installation issues |Classic Teams is no longer available, but due to org policy, we couldn't update you to the new Teams. As of July 1, 2025, classic Teams is no longer available for use. Contact your IT department for more info. To experience the new Teams, you can try it out on the web. Learn about installation issues |
|Any install and launch issues |Classic Teams will soon be unsupported, and we couldn't update you to the new Teams. Starting July 1, 2024, we'll no longer be supporting classic Teams. To update to the new Teams, contact your IT department. Learn about installation issues |Classic Teams is no longer supported, and we couldn't update you to the new Teams. As of July 1, we are no longer supporting classic Teams. We couldn't update to the new Teams. Contact your IT department. Learn more |Classic Teams will soon be unavailable, and we couldn't update you to the new Teams. Starting July 1, 2025, classic Teams will no longer be available for use. To update to the new Teams, contact your IT department. Learn about installation issues |Classic Teams is no longer available, and we couldn't update you to the new Teams. As of July 1, 2025, classic Teams is no longer available for use. Contact your IT department for more info. To experience the new Teams, you can try it out on the web. Learn about installation issues |

Classic Teams will remain available to use as defined in the timelines in this article. However, we highly encourage admins to update their users to new Teams, as new features are only being added to the new Teams client. Learn more in the [Upgrade to the new Teams using policies](new-teams-deploy-using-policies.md) article.

If users are on an unsupported OS (including Win 10 LTSC), you’ll see a slightly different banner messaging:

:::image type="content" source="media/teams-client-end-of-service-banner.png" alt-text="Shows the banner in Teams client that reads 'Classic Teams will be unsupported starting July 1, 2024. To use the new Teams, update your OS or contact your IT department. View minimum requirements.' the View minimum requirements link is a selectable link.":::

### What happens if we can’t update users to new Teams

Once classic Teams is no longer available for you, you're going to see a dialog similar to this one, and classic Teams won't work for you anymore.

:::image type="content" source="media/teams-client-eol-notification-box.png" alt-text="Teams dialog box that appears after classic Teams no longer works, if you're unable to be updated to the new Teams client. The notification box has a link to requirements and a button that takes you to Teams on the web.":::

Classic Teams users who have encountered issues moving to new Teams or who don't meet the [prerequisites](new-teams-deploy-using-policies.md#prerequisites) to upgrade will still have access to the classic Teams client until July 01, 2025. This timeframe gives admins more time to address any issues encountered during this process. We do ask that users update their OS and address any other issues to continue using the Teams client after this time, as new features are only being added to the new Teams client.

## Admin experience

### What admins will see until the end of March 31, 2024

Admins have full control over their tenant’s transition to new Teams via the [Upgrade to the new Teams using policies](new-teams-deploy-using-policies.md) article.

A bulk installer, including offline capability, is provided for admins who want to deploy new Teams using their own tools and process and use Teams policies to move their users to the desired experience: [Bulk upgrade to the new Microsoft Teams client](new-teams-bulk-install-client.md).

Microsoft highly recommends that admins who want more control or a more gradual rollout of new Teams take advantage of these tools and functionality to begin slowly transitioning their users to new Teams now. Policies can be targeted to individual users, groups of users, or your entire tenant to give you flexibility to release to users group by group while monitoring progress and feedback.

### What admins will experience after April 01, 2024

In the Teams admin center:

- Microsoft-managed rollout: If you left the policy controls at their defaults, we'll continue rolling out new Teams according to the previously outlined schedule, with one update: We won't proceed with the uninstallation of the classic Teams client for 14 days.
- Admin-managed rollout: Admins can choose to control the new Teams rollout as outlined in [Upgrade to the new Teams using policies](new-teams-deploy-using-policies.md). These policies will no longer work at the start of April, apart from your VDI users, and the following changes will happen:
  - New Teams will become the default client. The toggle to return to classic Teams will still be available if needed.
  - In mid-May, new Teams will be installed, and the toggle to return to classic Teams will no longer be available. We'll attempt to uninstall classic Teams, currently after a period of 14 days.

## Frequently Asked Questions

### Users

- **If a user has both clients installed:** Only new Teams will work after the end of availability, and we'll attempt to uninstall the classic Teams client after 14 days.
- **If only the new Teams client is installed:** There won’t be any difference.
- **If a user can’t install the new Teams client due to a reason outlined in the previous table, such as unsupported OS (including Win 10 LTSC):** These users will be allowed to use classic Teams until June 30, 2025 to allow for updating operating system to modifying permissions etc. After June 30, 2025, classic Teams won't work.

### Admins

- **The system requirements for the new Teams client:** [Prerequisites](new-teams-deploy-using-policies.md#prerequisites).
- **When will admins see the new Teams Only policy in their tenant:** This is available in the Teams admin center now. See [Upgrade to the new Teams using policies](new-teams-deploy-using-policies.md).
- **What will happen with the update policies:** The update policies will apply only to VDI clients after March 31, 2024.
- **When will classic Teams client stop being installed with M365 apps:** The installation of the classic Teams client will stop happening at the end of the availability period.
- **Can I stop the classic Teams client from being uninstalled and what happens if a policy is set to prevent app uninstallation:** Yes, you can stop the classic Teams client from being uninstalled. If your configuration prevents uninstall, Microsoft won't attempt the uninstall again. You'll need to uninstall classic Teams after that point.
- **Do I need to remove the old client:** Microsoft recommends that you remove the classic Teams client once a user is fully transitioned to new Teams. It's security best practice to not leave software that is no longer operational installed on a machine. Microsoft will attempt to remove the classic Teams client on your behalf, but if your configuration or policies are blocking or preventing this uninstall it's your responsibility to do this removal yourself.
- **What can I do if users still need the classic Teams client:** You won’t be able to use classic Teams once availability ends. Until that date you'll still have a banner announcing the end of classic Teams at the top of your client. For more information review: [Features that are changing in the new Microsoft Teams](new-teams-whats-changing.md).
- **Are there any scripts available if the admin needs to bulk uninstall the classic Teams client:** Check out our [uninstallation](msi-deployment.md#uninstallation) documentation.

### Client

- **Will the classic Teams client be removed automatically:** Microsoft will attempt to uninstall classic Teams after the availability period ends. If this fails, admins must uninstall classic Teams for their users. You can find more information on [uninstallation](msi-deployment.md#uninstallation) in this article.
- **When or how will it be removed, and what triggers the uninstall:** This removal will happen after the availability period ends. As each user receives the automatic update and switches to new Teams, an attempt will be made to uninstall classic Teams.
- **Will the classic Teams client be removed for all users on the device:** Yes.
- **Will both Windows and Mac support uninstallation:** Yes.
- **What if I need to use the classic Teams client after the availability period:** You won’t be able to use classic Teams after the availability period ends. Until that date you'll still have a banner announcing the end of classic Teams at the top of your client. For more information, see [Features that are changing in the new Microsoft Teams](new-teams-whats-changing.md).
- **Will I be able to download the classic Teams client after the availability period ends:** Yes, but it won't be functional unless you meet one of the conditions to extend classic Teams functionality until the end of availability date.

### VDI

- **Will the earlier date apply to users on VDI devices:** No, the October 1 2024 date applies to users on VDI devices.
