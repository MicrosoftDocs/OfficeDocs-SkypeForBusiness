---
title: Manage the Praise app in the Teams admin center
author: LanaChin
ms.author: v-lanachin
manager: samanro
ms.reviewer: jozhuan
audience: admin 
ms.topic: article 
ms.service: msteams
ms.localizationpriority: medium 
description: Learn about admin settings in the Praise app in the Microsoft Teams admin center

---

# Manage the Praise app in the Microsoft Teams admin center

The Praise app in Microsoft Teams helps users show appreciation to members of your organization or classroom. The badges in Praise are designed to help recognize the effort that goes into the wide range of work that Teams users do, from educators to frontline workers. To learn more, check out [Send Praise to people](https://support.microsoft.com/office/send-praise-to-people-50f26b47-565f-40fe-8642-5ca2a5ed261e).

Admins must have a Teams license to access this feature. If you try to access this feature without a Teams license, you'll get an error message.

> [!NOTE]
> The Praise app is available for GCC cloud environment, but not for GCC High or DoD.

## Enable or disable Praise in your organization

Praise is enabled by default for all Teams users in your organization. You can turn off or turn on the app at the org level on the [Manage apps](manage-apps.md) page in the Microsoft Teams admin center.

1. In the left navigation of the Microsoft Teams admin center, go to **Teams apps** > **Manage apps**.
2. In the list of apps, search for the Praise app, select it, and then switch the **Status** toggle to **Blocked** or **Allowed**.

Keep in mind that this setting affects both the Praise app and the Praise feature in the Viva Insights app in Teams.

## Enable or disable Praise for specific users in your organization

To allow or block specific users in your organization from using Praise, make sure Praise is turned on for your organization on the [Manage apps](manage-apps.md) page. Then create a custom app permission policy and assign it to those users. To learn more, see [Manage app permission policies in Teams](teams-app-permission-policies.md).

## Badges

Here's the set of badges in Praise. Teams users in your organization can use these badges to recognize their peers for going above and beyond with their work.

:::image type="content" source="media/default-set-praise.png" alt-text="Image of badges in default badge set.":::

> [!NOTE]
> Starting February 2022, people can only send and receive default badges. Custom badges are no longer available and options for custom badges are being removed from the app's **Settings** page in the Teams admin center soon.

<!-- ## Badge set assets

Built-in badge sets can't be modified, so when a built-in set is enabled, all badges in the set are added to the Praise app. If you want to add specific badges from a built-in set and leave out others, re-create the badges you want to use as custom badges. You can download the badge image and find the text and background colors of badges from built-in sets in the tables below.

### Default badges assets

|Badge name     |Image file  |Text color | Background color |
|---------------|------------|---------- |--------|
|Achiever       |[Achiever PNG](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/raw/live/Teams/downloads/praise-app/default-set/achiever-badge.png)|#D36E70    |#E3F4FC|
|Awesome        |[Awesome PNG](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/raw/live/Teams/downloads/praise-app/default-set/awesome-badge.png)</a>|#8283B2    |#D1EFF2|
|Coach          |[Coach PNG](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/raw/live/Teams/downloads/praise-app/default-set/coach-badge.png)</a>|#6AA55A    |#DBF1D6|
|Courage        |[Courage PNG](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/raw/live/Teams/downloads/praise-app/default-set/courage-badge.png)</a>|#DC5041    |#FCF6C8|
|Creative       |[Creative PNG](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/raw/live/Teams/downloads/praise-app/default-set/creative-badge.png) |#CF9D50    |#FCF6C8|
|Inclusive      |[Inclusive PNG](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/raw/live/Teams/downloads/praise-app/default-set/inclusive-badge.png)</a>|#3C77BB    |#E2F4FC|
|Kind Heart     |[Kind Heart PNG](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/raw/live/Teams/downloads/praise-app/default-set/kind-heart-badge.png)</a>|#D36D6E    |#F4DEDE|
|Leadership     |[Leadership PNG](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/raw/live/Teams/downloads/praise-app/default-set/leadership-badge.png)|#419098    |#D2EAEC|
|Optimism       |[Optimism PNG](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/raw/live/Teams/downloads/praise-app/default-set/optimism-badge.png)</a>|#D8338C    |#F4DDDE|
|Problem solver |[Problem solver PNG](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/raw/live/Teams/downloads/praise-app/default-set/problem-solver-badge.png)|#B8916E    |#CBDADF|
|Team player    |[Team player PNG](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/raw/live/Teams/downloads/praise-app/default-set/team-player-badge.png)|#8B8DC0    |#F4EEC0|
|Thank you      |[Thank you PNG](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/raw/live/Teams/downloads/praise-app/default-set/thank-you-badge.png)|#469CA4    |#BACCB6|

## Upcoming changes

Starting in January 2022, what's currently available for badges will change. Social and emotional learning badges for education, including self-awareness and self-management, will no longer be available.

The **Create a custom badge** option will also no longer be available as of January 2022.

Additionally, the **Status** toggle in the Teams admin center that allows or block Praise will affect both the Praise app and the Praise feature in the Viva Insights app in Teams.-->