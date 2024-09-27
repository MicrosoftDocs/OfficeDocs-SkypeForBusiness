---
title: Manage feedback policies in Microsoft Teams
author: MicrosoftHeidi
ms.author: heidip
manager: jtremper
ms.reviewer: andrewklutz
ms.date: 09/27/2024
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
  - M365-collaboration
f1.keywords:
- NOCSH
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Learn how to use feedback policies to control whether Teams users in your organization can submit feedback about Teams to Microsoft.
---

# Manage feedback policies in Microsoft Teams

Users in your organization can send feedback about Microsoft Teams to let us know how we're doing directly from within the Teams desktop, web clients, and mobile. We're continually improving the Teams experience and we use this feedback to make Teams better.

> [!NOTE]
> Feedback policies aren't available in DOD deployments.
> Mobile feedback policies aren't available in GCC, GCC High, or DOD deployments.

## The **Report a problem** feature

Users can send comments and suggestions about Teams to us by going to the elipsis (**...**) menu > **Feedback** > **Report a problem** in Teams desktop and web. You can access feedback on mobile using **Settings** > **Help & feedback** > **Report a problem**.

> [!NOTE]
> Data sent through **Report a problem** is considered "Support Data" under your Microsoft 365 or Office 365 agreement, including information that would otherwise be considered "customer data" or "personal data".

## Surveys

Users can also rate their experience with Teams and send us details about the rating they give. This pop-up survey is displayed to users from time-to-time in Teams. When a user selects **Provide feedback** in the notification, the survey is displayed for them to complete.

![the survey notification and form in Teams.](media/manage-feedback-policies-in-teams-survey.png)

## Set whether users can send feedback about Teams to Microsoft

As an admin, you can control whether users in your organization can report a problem or with Teams to Microsoft and whether they receive a survey.

These capabilitites are currently controlled by two sets of policies based on user platfrom and feedback feature. This table provides more information on policies for different platforms and feedback features.


|Platform/Feedback feature |Report a problem/Send feedback |Give a compliment |Suggest a feature |Surveys |
|--------------------------|-------------------------------|------------------|------------------|--------|
|Teams desktop and web     |Cloud policy service for Microsoft 365&sup1 |Cloud policy service for Microsoft 365&sup1 |Cloud policy service for Microsoft 365&sup1 |Teams feedback policy&sup2 |
|Teams mobile              |Teams feedback policy&sup3 |Teams feedback policy&sup3 |Teams feedback policy&sup3 |Teams feedback policy&sup3 |

<sup>1</sup> Available only for commercial cloud tenants. GCC and GCC High deployments continue to use Teams feedback policy for Desktop and Web.

<sup>2</sup> Teams Feedback policies aren't available in DOD deployments for Desktop and Web clients.

<sup>3</sup> Teams feedback policies aren't available in GCC, GCC High, or DOD deployments for Mobile clients.

See [Manage Microsoft feedback for your organization](/microsoft-365/admin/manage/manage-feedback-ms-org) for details on managing the Cloud policy service for Microsoft 365.

## Teams feedback policy

By default, all users in your organization are automatically assigned the global (Org-wide default) policy, and the feedback and survey features are enabled in the policy. The exception is Teams for Education, where the features are enabled for teachers and disabled for students.

You can edit the global policy or create and assign a custom policy. After you edit the global policy or assign a custom policy, it can take a few hours for changes to take effect.

Say, for example, you want to allow all users in your organization to send feedback and receive surveys except for new hires in training. In this scenario, you create a custom policy to turn off these features and assign it to new hires. All other users in your organization get the global policy with the feature turned on.

You manage feedback policies by using PowerShell. Use the [**New-CsTeamsFeedbackPolicy** cmdlet](/powershell/module/teams/new-csteamsfeedbackpolicy) to create a custom policy. Use the **Grant-CsTeamsFeedbackPolicy** cmdlet to assign it to one or more users or groups of users, such as a security group or distribution group. Use **Set-CsTeamsFeedbackPolicy** to set specific flags.

To turn off and turn on the features, set the following parameters:

- **Give feedback**: Set the **userInitiatedMode** parameter to **enabled** to allow users who are assigned the policy to give feedback. Setting the parameter to **disabled** turns off the feature and users who are assigned the policy don't have the option to give feedback.
- **Surveys**: Set the **receiveSurveysMode** parameter to **enabled** to allow users who are assigned the policy to receive the survey. To have users receive the survey and allow them to opt out, set the parameter to **enabledUserOverride**. In Teams, users can then go to **Settings** > **Privacy** and choose whether they want to participate in surveys. Setting the parameter to **disabled** turns off the feature and users who are assigned the policy won't receive the survey.

> [!NOTE]
> **receiveSurveysMode** doesn't control call quality feedback by default. If an admin wants to control call quality feedback via **receiveSurveysMode**, they should contact the engineering team.

- **Screenshots**: Use the **AllowScreenshotCollection** flag to add screenshot collection opt-in for users.
- **Email**: Use the **AllowEmailCollection** flag to add an email field.
- **Log collection**: Use the **AllowLogCollection** flag to add log collection opt-in for users. Log collection is currently enabled only on mobile. For more details on what data is shared via logs, [learn more at this link](https://go.microsoft.com/fwlink/?linkid=2168178).
- **Suggest a feature**: Set the **EnableFeatureSuggestions** parameter to **True** to allow users who are assigned the policy to suggest a feature. Setting the parameter to **disabled** turns off the feature and users who are assigned the policy don't have the option to give feedback. The default setting is taken from your Microsoft 365 optional connected experiences policy setting. To learn more about that setting, see [Overview of optional connected experiences in Office](/deployoffice/privacy/optional-connected-experiences).

## Create a custom feedback policy

In this example, we create a feedback policy called New Hire Feedback Policy and we turn off the ability to give feedback through **Give feedback** and the survey.

```PowerShell
New-CsTeamsFeedbackPolicy -identity "New Hire Feedback Policy" -userInitiatedMode disabled -receiveSurveysMode disabled
```

## Assign a custom feedback policy to users

[!INCLUDE [assign-policy](includes/assign-policy.md)]

In this example, we assign a custom policy named New Hire Feedback Policy to a user named user1.

```PowerShell
Grant-CsTeamsFeedbackPolicy -Identity user1@contoso.com -PolicyName "New Hire Feedback Policy"
```

## Related topics

- [Manage Microsoft feedback for your organization](/microsoft-365/admin/manage/manage-feedback-ms-org)
- [Teams PowerShell Overview](teams-powershell-overview.md)
- [Assign policies to your users in Teams](policy-assignment-overview.md)
