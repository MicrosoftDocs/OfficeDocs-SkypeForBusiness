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

XXX DATE FORMAT CHANGE

# End of availability for Classic Teams client

## Overview

On 31 March 2024, a new Teams client will be rolled out for users who are still on classic Teams, installing the new Teams client for them and uninstalling the classic Teams client. After this time, classic Teams will be unavailable for different users depending on the schedule below.

|31 March 2024       |30 June 2024            |
|--------------------|------------------------|
|Windows             |VDI [Upgrade to new Teams for Virtualized Desktop Infrastructure (VDI)](new-teams-vdi-requirements-deploy.md) |
|Mac                 |Unsupported OS users    |
|EDU                 |Unsupported browsers    |
|Web                 |GPO blocked users (EDU) |
|Gov Cloud           |                        |
|GPO users (non-EDU) |                        |

https://learn.microsoft.com/microsoftteams/new-teams-vdi-requirements-deploy
GPO blocked users (EDU) Troubleshooting the new Teams installation - Microsoft Teams | Microsoft Learn
GPO blocked users (non-EDU) <Add link Troubleshooting the new Teams installation - Microsoft Teams | Microsoft Learn

## User experience

### What users will see until 31 March 2024

Starting on 1 February 2024, any classic Teams users who haven’t updated to new Teams will begin seeing an informational banner to remind them about the timeline for the auto update. This banner will appear in the main Teams client window at the top of the page (underneath the main bar).

[XXX SCREENSHOT WITH ALT TEXT]

Classic Teams will remain available to use until 31 March 2024. However, we highly encourage admins to update their users to new Teams, as new features are only being added to the new Teams client. Learn more in the [Upgrade to the new Teams using policies](new-teams-deploy-using-policies.md) article.

If users are on unsupported operating system, you’ll see a slightly different banner messaging:

XXX SCREENSHOT WITH ALT TEXT

### What users will experience after 31 March 2024

After 31 March 2024, if you’re already running on new Teams, there will be no change in behavior. Your Teams will continue working as expected.

Users on classic Teams will be automatically updated to the new Teams client. Users won’t be able to switch back to classic Teams after this date, because classic Teams won’t be functional. Microsoft will attempt to uninstall classic Teams at this time.

### What happens if we can’t update users to new Teams

If you’re in the first column of the table above, and you can’t be upgraded to new Teams (due to policies or configuration), classic Teams will stop working after 31 March 2024. You will see an error message indicating the same.

[XXX SCREENSHOT OF ERROR WITH ALT TEXT]

To use Teams after this point, install the new Teams client or use Teams on the web.

If you fall under the list in the XXX COPY LIST CONTENTS DOWN right-hand column of the table above and you aren’t able to be updated at the end of March, your classic Teams client will continue to run until 30 June 2024, with the warning banner at the top of your client. We do ask that users update their OS and address any issues to continue using the Teams client after this time, as new features are only being added to the new Teams client.

[XXX POTENTIAL MULTIPLE SCREENS HERE, SPLIT INTO SCENARIOS?]

## Admin experience

### Until 31 March, 2024

Admins have full control over their tenant’s transition to new Teams via policies in Teams Admin Center or PowerShell: Upgrade to the new Teams client using policies - Microsoft Teams | Microsoft Learn

A bulk installer, including offline capability, has been provided for admins who want to deploy new Teams using their own tools and process and use Teams policies to move their users to the desired experience: Bulk deploy the new Microsoft Teams desktop client - Microsoft Teams | Microsoft Learn

Microsoft highly recommends that admins who want more control or a more gradual rollout of new Teams take advantage of these tools and functionality to begin slowly transitioning their users to new Teams now. Policies can be targeted to individual users, groups of users, or your entire tenant to give you flexibility to release to users group by group while monitoring progress and feedback.

### Starting 31 March 2024

Beginning 31 March 2024, all policy options within Teams Admin Center to control the transition to new Teams will be made unavailable or will no longer function for all users.

After these options are removed, Microsoft will begin moving all users except VDI users back to the **Microsoft controlled** policy setting. After 31 March 2024 the **Microsoft controlled** policy setting will equate to the user being assigned the **New Teams Only** policy which will transition the user to new Teams and then uninstall the classic Teams client.

## Frequently Asked Questions

### Users

- **If a user has both clients installed:** Only new Teams will work after 31 March 2024, and the classic Teams client will be uninstalled if possible.
- **If only the new Teams client is installed:** There won’t be any difference.
- **If a user can’t install the new Teams client due to:**
  - MSIX restrictions:
  - an unsupported OS version:
  - a lack of admin rights (on a Mac):
  - device or security restrictions:

These users will be allowed to use classic Teams till June 30, 2024 (as per above schedule) to allow for updating operating system to modifying permissions etc.  Post June 30, classic Teams will not be available for use.

### Admins

- **The system requirements for the new Teams client:** [Prerequisites](new-teams-deploy-using-policies.md#prerequisites)
- **When will admins see the new Teams Only policy in their tenant:** [Upgrade to the new Teams using policies](new-teams-deploy-using-policies.md)
- **What will happen with the update policies:** The update policies may still appear, but they won’t be functional after 31 March 2024.
- **When will classic Teams client stop being installed with M365 apps:** This will stop happening on 31 March 2024.
- **Can I block the installation of new Teams using the M365 apps:** Yes, until March 31 2024. XXX
- **Can I stop the classic Teams client from being uninstalled and what happens if a policy is set to prevent app uninstallation:** Yes, you can stop the classic Teams client from being uninstalled.
- **Do I need to remove the old client:** Microsoft recommends that you remove the classic Teams client once a user has fully transitioned to new Teams. It is security best practice to not leave software that is no longer operational installed on a machine. Microsoft will attempt to remove the classic Teams client on your behalf, but if this is blocked or prevented by your configuration or policies it is your responsibility to conduct this removal yourself.
- **What can I do if users still need classic Teams:** As of 31 March 2024, there are no remaining scenarios where classic Teams is still needed by users. Please reference this page: What is changing in the new Microsoft Teams - Microsoft Teams | Microsoft Learn
- **Are there any scripts available if the admin needs to bulk uninstall classic Teams:** Check out our [uninstallation](msi-deployment.md#uninstallation) documentation.

### Client

- **Will classic Teams be removed automatically:** Microsoft will attempt to uninstall classic Teams after 31 March 2024. If this fails, admins must uninstall classic Teams for their users. You can find more information on [uninstallation](msi-deployment.md#uninstallation) in this article.
- **When or how will it be removed, and what triggers the uninstall:** This will happen after 31 March 2024. As each user receives the automatic update and switches to new Teams, an attempt will be made to uninstall classic Teams.
- **Will it be removed for all users on the device:** Yes.
- **Will the uninstall clean up the Teams cache:** This is not applicable as the cache for classic Teams and new Teams are different files stored in different locations. Please reference this page: Clear Teams cache - Microsoft Teams | Microsoft Learn
- **Will both Windows and Mac support uninstallation:** Yes.
- **What permissions are required for it to be uninstalled on Windows and Mac:** XXX
- **Will the machine-wide installer be removed:** XXX
- **Will this be different if classic Teams was installed by Office:** No.
- **What if I need to use classic Teams after 31 March 2024:** You won’t be able to use classic Teams after 31 March 2024, unless you meet one of the conditions XXX in the second column at the start of this article. Then you’ll have until 30 June 2024. Until that date you will still have a banner announcing the end of classic Teams at the top of your client.
- **Will I be able to download classic Teams after 31 March 2024:** Yes, but it won't be functional unless you meet one of the conditions in the second column at the start of this article.

### VDI

- **Will the 31 March 2024 date apply to users on VDI devices:** No, the 30 June 2024 date applies to users on VDI devices.
- **How will the new Teams Only policy impact VDI users:** XXX They won’t be affected until 30 June 2024.
