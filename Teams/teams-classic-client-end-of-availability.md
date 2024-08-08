---
title:  End of availability for classic Teams client
ms.author: heidip
author: MicrosoftHeidi
manager: jtremper
ms.topic: article
ms.date: 05/15/2024
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

A new Teams client is in the process of rolling out, in stages, for users who are still on classic Teams client. This rollout involves installing the new Teams client for users who still have the classic Teams client, with Microsoft attempting to uninstall the classic Teams client after the installation of new Teams. This article has the timelines and details of **end of support** and **end of availability** for classic Teams client.

### Timeline updates

This rollout is going to differ based on your Teams Admin Center policy controls.

> [!NOTE]
> These timelines don't apply to GCC, GCCH, and DoD. We cover this in a later section.

> [!IMPORTANT]
> Admins should know that they can always move forward in the steps to new Teams Only from any other point in the rollout schedule, but they can't move backwards in the steps from where they currently are. Some examples:
>
> - If a customer is currently in classic Teams default mode, they can go to new Teams default mode, or new Teams Only, by assigning those policy states. However, they can't move back to the AdminDisabled state.
> - If a customer is currently in new Teams default mode, they can move forward to new Teams Only by assigning that policy state. In this case, they couldn't move back to classic Teams default or AdminDisabled.

**Native clients excluding VDI**:

The end of support for the classic Teams client starts July 1, 2024. The end of availability for the classic Teams client starts July 1, 2025.

:::image type="content" source="media/teams-client-eoa-timeline.png" alt-text="A chart showing the timelines for classic Teams to new Teams.":::

**VDI timeline**:

The end of support for the classic Teams client in VDI starts October 1, 2024. The end of availability for the classic Teams client in VDI starts July 1, 2025.

:::image type="content" source="media/new-teams-vdi-timeline.png" alt-text="A chart showing the timelines for classic Teams to new Teams for VDI.":::

The timeline for VDI in regard to GCCH and DOD tenants. The end of support for VDI for these tenants starts October 1, 2024, and the end of availability starts July 1, 2025. For Microsoft-controlled tenants, the Update policy won't be effective from September 1, 2024, and users will be migrated gradually to new Teams starting at this time.

:::image type="content" source="media/new-teams-vdi-timeline-gcch-dod.png" alt-text="A chart showing the timelines for classic Teams to new Teams for VDI, specific to GCCH and DoD tenants.":::

For more information regarding VDI, see [Upgrade to new Teams for Virtualized Desktop Infrastructure (VDI)](new-teams-vdi-requirements-deploy.md).

- **Microsoft-managed rollout**: If Teams policy was set to be Microsoft-controlled, new Teams is being rolled out according to the outlined schedule. We'll attempt to uninstall classic Teams after a period of time.
- **Admin-managed rollout**: Until the start of April, admins could choose to control the new Teams rollout as outlined in [Upgrade to the new Teams client using policies](new-teams-deploy-using-policies.md). Apart from your VDI users, this period has ended, and admins will now see the following behaviors:
  - New Teams is installed and becomes the default client. The toggle to return to classic Teams is still available if needed.
  - In mid-May, any users remaining on classic Teams will be switched to new Teams, and the toggle to return to classic Teams won't be available. We'll attempt to uninstall classic Teams after a period of time.

These are the important timeline concepts to keep in mind going forward:

- **End of support**: The end of our supporting classic Teams client. We'll no longer provide updates or new features for the client, nor will we help resolve support issues with the classic Teams client.
- **End of availability**: The end of functionality for the classic Teams client. After this deadline, the client will stop working and users will no longer be able to do work in the classic Teams client.

:::image type="content" source="media/teams-client-eoa-timeline-complete.png" alt-text="A chart showing the timelines for the end of support for classic Teams and the end of availability of classic Teams.":::

### Timeline for GCC, GCCH, DoD

This rollout is going to differ based on your Teams Admin Center policy controls, as outlined in the following table:

> [!NOTE]
> If you left the policy controls at their defaults state of Microsoft-controlled, we'll continue rolling out new Teams according to the schedule outlined in this article, but we won't proceed with the uninstallation of the classic Teams client for some time after the upgrade.

|Government cloud and scenario      |Admin opt-in |New Teams toggle shown |New Teams default client | New Teams only|
|-----------------------------------|-------------|-----------------------|-------------------------|---------------|
|GCC/GCCH Microsoft-managed rollout |Currently, the new Teams update will only be available when administrators enable it for their users. Instructions for configuring policy for the new Teams client can be found in our [Upgrade to the new Teams client using policies](new-teams-deploy-using-policies.md) article. When the policy is enabled for a user, they can select the **New Teams** toggle switch in their Teams client to start the update. |Starting in late February, we enabled the new Teams toggle for Microsoft-controlled users. If they're still using the classic Teams client, they will not be updated unless they toggle the switch. |Beginning in late March, the new Teams client became the default client for Teams users. Customers will receive the new Teams update, unless disallowed by policy. Users may still toggle back to the classic Teams client. |Beginning in early May all remaining classic Teams users are being updated to the new Teams client and the toggle switch will be removed. After this process completes, Microsoft will attempt to remove the classic Teams client. |
|GCC/GCCH admin-managed rollout     |NA           |NA                     |Beginning in late May, the new Teams client will become the default client for all active Teams users. Customers will receive the new Teams update. Users may still toggle back to the classic Teams client. |Beginning mid-June all remaining classic Teams users will be updated to the new Teams client and the toggle switch will be removed. After this process completes, Microsoft will attempt to remove the classic Teams client. |
|DOD Microsoft-managed rollout      |Currently, the new Teams update only becomes available when administrators enable it for their users. Instructions for configuring policy for the new Teams client can be found in our [Upgrade to the new Teams client using policies](new-teams-deploy-using-policies.md) article. When the policy is enabled for a user, they can select the **New Teams** toggle switch in their Teams client to start the update. |Starting in late February, we enabled the new Teams toggle for Microsoft-controlled users. If they're still using the classic Teams client, they won't be updated unless they toggle the switch. |Beginning in early May, the new Teams client became the default client for Teams users. Customers will receive the new Teams update, unless disallowed by policy. Users may still toggle back to the classic Teams client. |NA |
|DOD admin-managed rollout          |NA           |NA                     |Beginning in mid-July, the new Teams client will become the default client for all active Teams users. Customers will receive the new Teams update. Users may still toggle back to the classic Teams client. |Beginning mid-August all remaining classic Teams users will be updated to the new Teams client and the toggle switch will be removed. After this process completes, Microsoft will attempt to uninstall the classic Teams client after a period of time. |

## User experience

**Classic Teams will reach the end of support starting July 1, 2024.**

### What users will experience after March 31, 2024

Starting in March 2024, any classic Teams users who hadn’t updated to new Teams began seeing an informational banner to remind them about the classic Teams end of support timeline. This banner appeared in the main Teams client window at the top of the page (underneath the main bar).

:::image type="content" source="media/teams-client-eol-switch-banner-prior.png" alt-text="Shows the banner at the top of the Teams client that reads 'Classic Teams will be unsupported starting July 1, 2024. You'll be switched to the new Teams at that time. Learn more.' Learn more is a selectable link.":::

If we're unable to move you to new Teams, here's a list of the banner messages you may experience:

|Condition for triggering the banner |Banner message |Further information |
|------------------------------------|---------------|--------------------|
|Unsupported Windows operating system |Classic Teams will soon be unavailable for use. To use the new Teams, update your OS to meet requirements or contact your IT admin. Learn more. |[Prerequisites](new-teams-deploy-using-policies.md#prerequisites) |
|Unsupported Mac operating system |Classic Teams will soon be unavailable for use. To use the new Teams, update your OS to meet requirements or contact your IT admin. Learn more. |[Prerequisites](new-teams-mac-install-prerequisites.md#prerequisites) |
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

- Starting October 23, 2024, classic Teams won't be available on Windows 7, 8, and 8.1; and macOS Sierra (10.12), High Sierra (10.13) and Mojave (10.14). If you use classic Teams on these systems, you'll see warning messages starting in August. On October 23, 2024, you won't be able to use the classic Teams app anymore. If you can't update your Windows to a [supported browser](new-teams-web.md#prerequisites), you can use the new Teams web app in a supported browser instead.
- Starting July 1, 2025, classic Teams will stop working on Windows 10, macOS older than Big Sur (11), LTSC, or for users with configuration issues. You'll see the in-app messages about classic Teams going away and you won't be able to use the classic Teams app after that date.

Users who can't upgrade to the new Teams client on their device can use the new Teams web app on [supported browsers](new-teams-web.md#prerequisites) instead.

> [!NOTE]
> You can dismiss this banner when it starts to appear, but the banner will reappear with each client launch.

Here's a list of the messages you may experience:

|Scenario |End of support warning |End of support |End of availability warning |End of availability |
|---------|-----------------------|---------------|----------------------------|--------------------|
|Unsupported operating system |Classic Teams will soon be unsupported, and your OS needs to be updated to run the new Teams. Starting July 1, 2024, we'll no longer be supporting classic Teams. Update your OS or contact your IT department. View minimum requirements |Classic Teams is no longer supported and your OS needs to be updated to run the new Teams. As of July 1, we're no longer supporting classic Teams. Update your OS or contact your IT department. View minimum requirements |Classic Teams will soon be unavailable, and your OS needs to be updated to run the new Teams. Starting July 1, 2025, classic Teams will no longer be available for use. Update your OS or talk to your IT department. View minimum requirements |Classic Teams is no longer available, and your OS needs to be updated to run the new Teams. As of July 1, 2025, classic Teams is no longer available for use. Update your OS or talk to your IT department. To experience the new Teams, you can try it out on the web. View minimum requirements |
|Windows GPO policy blocked users |Classic Teams will soon be unsupported, but due to org policy, we couldn't update you to the new Teams. Starting July 1, 2024, we'll no longer be supporting classic Teams. To update to the new Teams, contact your IT department. Learn about installation issues |Classic Teams is no longer supported, but due to org policy we couldn't update you to the new Teams. As of July 1, we're no longer supporting classic Teams. We couldn't update to the new Teams due to org policy. Contact your IT department. Learn more |Classic Teams will soon be unavailable, but due to org policy, we couldn't update you to the new Teams. Starting July 1, 2025, classic Teams will no longer be available for use. To update to the new Teams, contact your IT department. Learn about installation issues |Classic Teams is no longer available, but due to org policy, we couldn't update you to the new Teams. As of July 1, 2025, classic Teams is no longer available for use. Contact your IT department for more info. To experience the new Teams, you can try it out on the web. Learn about installation issues |
|Any install and launch issues |Classic Teams will soon be unsupported, and we couldn't update you to the new Teams. Starting July 1, 2024, we'll no longer be supporting classic Teams. To update to the new Teams, contact your IT department. Learn about installation issues |Classic Teams is no longer supported, and we couldn't update you to the new Teams. As of July 1, we are no longer supporting classic Teams. We couldn't update to the new Teams. Contact your IT department. Learn more |Classic Teams will soon be unavailable, and we couldn't update you to the new Teams. Starting July 1, 2025, classic Teams will no longer be available for use. To update to the new Teams, contact your IT department. Learn about installation issues |Classic Teams is no longer available, and we couldn't update you to the new Teams. As of July 1, 2025, classic Teams is no longer available for use. Contact your IT department for more info. To experience the new Teams, you can try it out on the web. Learn about installation issues |

Classic Teams will remain available to use as defined in the timelines in this article. However, we highly encourage admins to update their users to new Teams, as new features are only being added to the new Teams client. Learn more in the [Upgrade to the new Teams using policies](new-teams-deploy-using-policies.md) article.

If users are on an unsupported OS (including Win 10 LTSC), you’ll see a slightly different banner messaging:

:::image type="content" source="media/teams-client-end-of-service-banner.png" alt-text="Shows the banner in Teams client that reads 'Classic Teams will be unsupported starting July 1, 2024. To use the new Teams, update your OS or contact your IT department. View minimum requirements.' the View minimum requirements link is a selectable link.":::

### What happens if we can’t update users to new Teams

Once classic Teams isn't available for you, you're going to see a dialog similar to this one, and classic Teams won't work for you anymore.

:::image type="content" source="media/teams-client-eol-notification-box.png" alt-text="Teams dialog box that appears after classic Teams no longer works, if you're unable to be updated to the new Teams client. The notification box has a link to requirements and a button that takes you to Teams on the web.":::

Classic Teams users who've had issues moving to new Teams or who don't meet the [prerequisites](new-teams-deploy-using-policies.md#prerequisites) to upgrade will still have access to the classic Teams client until availability ends. After this time, users who can't upgrade on their devices can use the new Teams web app on a [supported browser](new-teams-web.md#prerequisites) instead.

## Admin experience

### What admins saw until the end of March 31, 2024

Admins have full control over their tenant’s transition to new Teams via the [Upgrade to the new Teams using policies](new-teams-deploy-using-policies.md) article.

A bulk installer, including offline capability, is provided for admins who want to deploy new Teams using their own tools and process and use Teams policies to move their users to the desired experience: [Bulk upgrade to the new Microsoft Teams client](new-teams-bulk-install-client.md).

Microsoft highly recommends that admins who want more control or a more gradual rollout of new Teams take advantage of these tools and functionality to begin slowly transitioning their users to new Teams now. Policies can be targeted to individual users, groups of users, or your entire tenant to give you flexibility to release to users group by group while monitoring progress and feedback.

### What admins are experiencing after April 01, 2024

In the Teams admin center:

- **Microsoft-managed rollout**: If Teams policy was set to be Microsoft-controlled, new Teams is being rolled out according to the outlined schedule. We'll attempt to uninstall classic Teams after a period of time.
- **Admin-managed rollout**: Until the start of April, admins could choose to control the new Teams rollout as outlined in [Upgrade to the new Teams client using policies](new-teams-deploy-using-policies.md). Apart from your VDI users, this period has ended, and the following is now true:
  - New Teams is installed and becomes the default client. The toggle to return to classic Teams is still available if needed.
  - In mid-May, any users remaining on classic Teams will be switched to new Teams, and the toggle to return to classic Teams won't be available. We'll attempt to uninstall classic Teams after a period of time.

> [!IMPORTANT]
> A rare issue with the uninstall of classic Teams has been detected and to be cautious Microsoft has paused the automatic uninstallation of classic Teams for customers who haven't already completed this step. This issue could result in the Teams Meeting Addin in Outlook failing to schedule or join Teams meetings. We are actively investigating this issue and will update once it's resolved. If your users are experiencing this issue, a workaround is to use Teams to schedule or join meetings.
>
> For customers who are experiencing this issue or who wish to perform the uninstall of classic Teams themselves and experience this issue, there are troubleshooting steps available here: [Teams meeting add-in missing from Outlook and new Teams](/microsoftteams/troubleshoot/meetings/teams-meeting-add-in-missing).
