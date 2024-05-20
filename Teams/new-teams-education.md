---
title:  New Microsoft Teams for Education (EDU)
author: MicrosoftHeidi
ms.author: heidip
manager: jtremper
ms.topic: article
ms.date: 12/01/2023
ms.service: msteams
audience: admin
ms.collection: 
- Teams_ITAdmin_GuestAccess
- M365-collaboration
- m365initiative-deployteams
ms.reviewer: shajohri
search.appverid: MET150
f1.keywords:
- NOCSH
description: Learn about updating to the new Teams for Education (EDU)
appliesto: 
- Microsoft Teams
ms.localizationpriority: high
---
# Update to the new Microsoft Teams for Education

As announced on October 5, 2023 ([New Microsoft Teams for Education is now available for Windows and Mac](https://techcommunity.microsoft.com/t5/education-blog/new-microsoft-teams-for-education-is-now-available-for-windows/ba-p/3945610)), new Teams for Education is ready for users in our Education community.  

Along with our latest innovations in speed, performance, flexibility, and intelligence, this update to new Teams allows us to deliver features and capabilities to our education customers more quickly. All new features and capabilities, including enhancements to existing features, will be available exclusively in the new Teams.

The new Teams update is seamless for our Education users. Updating is quick and easy and users will be able to pick up exactly where they left off after updating to new Teams.  

>[!Note]
>New Teams for Education is available for web for Edge and Chrome. It will be available for other web browsers in early 2024.

> [!TIP]
> As a companion to this article, we recommend using the [Microsoft Teams for Education Setup Guide](https://go.microsoft.com/fwlink/?linkid=2270300) to review best practices without signing in and activating automated setup features. This guide will customize your experience based on your environment.

## Update schedule

**On January 2, 2024, Microsoft will update the classic Teams client to the new Teams client** for all tenants whose IT administrators took no explicit action to update to new Teams via Teams Admin Center policy (meaning, they still are using the default setting *Microsoft Controlled*). IT administrators can still set classic Teams for their users via policy.  

We encourage you to update to new Teams today. You don't need to wait until January to update.

Administrators can choose to update their users to new Teams on a different schedule. However, we highly recommend they complete the update **by the end of February 2024** to avoid disrupting classes, as all remaining users of classic Teams will be automatically updated to new Teams after **March 31, 2024**.

|When|What|
|:-----|:-----|
|January 2, 2024|- Microsoft will update the classic Teams client to the new Teams client for all tenants whose IT administrators took no explicit action to update to new Teams via Teams Admin Center policy (meaning, they still are using the default setting Microsoft Controlled in Teams Admin center policies). IT administrators still have the option to set classic Teams for their users via policy.</br></br>- Tenants who have set other policy values (apart from Microsoft controlled) in Teams Admin center, won't have their policy overridden. These tenants won't be impacted by this change. |
|March 31, 2024|- All remaining users of classic Teams will be automatically updated to new Teams after March 31, 2024.</br>- IT Administrators won't have the option to move back to classic Teams via policy.|

## Set policies for update

It's important that school IT administrators set the policy to update to new Teams for their users. The same policies apply when updating to new Teams for Education for all platforms: Windows, Mac, and Web.

1. Sign in to the [Microsoft Teams admin center](https://admin.teams.microsoft.com/).
2. Select **Teams > Teams Update policies** from the left navigation pane.
3. Select **Add to create a new policy or select an existing policy to open Update policy.
4. Name the update policy, add a description, and select the setting for “Use the new Teams client”.

   :::image type="content" source="media/new-teams-update-options.png" alt-text="user the new teams options ":::

5. Select New Teams as default and apply this policy to users in your organization.  
6. Once the policy is set, users decide when it will update. Select **Switch now** to update immediately, or **Switch when I'm not using Teams** to automatically install the update after they finish with their current session.

   :::image type="content" source="media/new-teams-edu-switch-now.png" alt-text="switch now or later":::

>[!Note]
>There are different policy settings which you can use to update to new Teams, based on the needs within your school. For detailed information about how to update to new Teams via policy and for various other policy settings, learn more at: [Update to the new Teams client using policies](new-teams-deploy-using-policies.md).

## Blocked downloads or installations

IT administrators who have blocked software downloads or installations for users in their tenant, must allow software download or installations of new Teams before setting the policy in the Teams Admin Center to deploy new Teams. To unblock software downloads for their users, learn more at: [Troubleshooting the new Teams installation](/microsoftteams/troubleshoot/teams-administration/fix-new-teams-installation-issues)

## Bulk update to the new Teams

- If IT administrators prefer to bulk update to new Teams using their choice of software management tools, learn more at: [Bulk deploy the new Microsoft Teams desktop client](new-teams-bulk-install-client.md).
- If IT administrators prefer to update to new Teams via other Microsoft 365 apps, learn more at [Upgrade to new Microsoft Teams with Microsoft 365 Apps](new-teams-deploy-with-m365apps.md).

### Known issues and latest updates

Check here for: [Known issues in the new Microsoft Teams](new-teams-known-issues.md)

Check back here for the latest details, as Microsoft continues to provide the most current information on updating to new Teams for Education.  Or, if you have any feedback you’d like to provide, do so on our [Education Support page](https://edusupport.microsoft.com/support).
