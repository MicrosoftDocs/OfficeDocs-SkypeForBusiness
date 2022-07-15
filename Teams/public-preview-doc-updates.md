---
title:  Public preview in Microsoft Teams
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
- Teams_ITAdmin_GuestAccess
- M365-collaboration
- m365initiative-deployteams
ms.reviewer: dansteve
search.appverid: MET150
f1.keywords:
- NOCSH
description: Learn about the public preview in Microsoft Teams. Try out new features and provide feedback.
appliesto: 
- Microsoft Teams
ms.localizationpriority: high
---

# Microsoft Teams Public Preview

> [!NOTE] 
> Features included in preview might not be complete and could undergo changes before becoming available in the public release. They're provided for evaluation and exploration purposes only. The preview features aren't supported in Office 365 Government Community Cloud (GCC).

Public Preview for Microsoft Teams provides early access to unreleased features in Teams. Previews allow you to explore and test upcoming features. We also welcome feedback on any feature in public previews. Public preview is enabled per Team user, so you don't need to worry about affecting your entire organization.

For a list of what's available in the Teams public preview, visit [Microsoft Teams Public Preview tech notes](https://techcommunity.microsoft.com/t5/microsoft-teams-public-preview/bd-p/MicrosoftTeamsPublicPreview), [Release Notes for Teams Admin Features](/OfficeUpdates/teams-admin), and [What's new in Teams](https://support.microsoft.com/office/what-s-new-in-microsoft-teams-d7092a6d-c896-424c-b362-a472d5f105de).

## Set the Update policy

Public preview is enabled on a per-user basis, and the option to turn on public preview is controlled in an admin policy. Update policies are used to manage Teams and Office preview users who will see pre-release or preview features in the Teams app. You can use the Global (Org-wide default) policy and customize it, or create one or more custom policies for your users. The policy needs to be assigned to specific users because it doesn't over-write the global policy.

1. Sign in to the [Microsoft Teams admin center](https://admin.teams.microsoft.com/).

2. Select **Teams** > **Teams Update policies**.

1. Select **Add** to create a new policy or select an existing policy to open **Update policy**.

2. Name the update policy, add a description, and select the setting for **Show preview features**.

   -   **Follow Office Preview** (default)
       - This new default option will automatically enable Teams Public Preview features for any user enrolled in Office Current Channel (Preview). 
       - There are no more actions required by the end user.
   -   **Enabled**
       - This option enables Teams Public Preview regardless of whether a user is enrolled in Office Current Channel (Preview). 
       - The end user must also opt in to Teams public preview in their Teams app.

   > [!NOTE]  
   > For existing users in Teams Public Preview who are NOT in the **Current Channel (Preview)**, IT admins need to switch from default, **Follow Office Preview** to **Enabled**.
 
   - **Not enabled** 
     - Teams Public Preview features will not be available to end users.

    ![shows the preview settings dialog.](media/public-preview-policy.png)  

You can also set the policy using the PowerShell `Set-CsTeamsUpdateManagementPolicy` cmdlet with the `-AllowPublicPreview` parameter.

## Enable public preview

To enable public preview on a desktop or web client, you need to complete the following tasks:

1. Select the three dots to the left of your profile to display the Teams menu.
2. Select **About** > **Public preview**.
3. Select **Switch to Public preview**.

> [!NOTE]  
> This option is only available when **Show preview features** is set to **Enabled**.

### Public preview for Microsoft Teams Rooms on Windows

Public preview is off by default. When public preview is on, end-users have access to features that are in public preview on enabled Teams Rooms. To turn on public preview, add ```<EnablePublicPreview>True</EnablePublicPreview>``` to your XML configuration file.

We recommend enrolling 5-10 devices to public preview. 

All public preview features are announced at [Microsoft Teams Public Preview - Microsoft Tech Community](https://techcommunity.microsoft.com/t5/microsoft-teams-public-preview/bd-p/MicrosoftTeamsPublicPreview)

## Teams now follows Office Preview users

The new global policy default of **Follow Office Preview** will allow users to automatically be in the Public Preview channel of Teams if they are in Current Channel (Preview) for the Office 365 Client on Windows and Mac.

Microsoft Office will continue to receive updates from Current Channel (Preview) and Teams client will receive updates via Public Preview channel. This policy will NOT switch Office channels based on Teams channels. 

**How to retain your existing Teams preview users who are NOT using Office Current Channel (Preview)?**

For existing users who you have allowed to opt-in or opt-out of Teams Public Preview and want to maintain that setting in its current form, you will need to switch from the new default, **Follow Office Preview** to **Enabled** (Refer to [Set the Update policy](#set-the-update-policy))

**How to opt-out of this setting?**

You can disable the setting from Teams Admin Center from **Follow Office Preview** to **Not Enabled** (Refer to [Set the Update policy](#set-the-update-policy))

## Related topics

[Public developer preview](/microsoftteams/platform/resources/dev-preview/developer-preview-intro)
