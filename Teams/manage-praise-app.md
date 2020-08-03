---
title: Manage the Praise app in the Teams admin center
author: CaitlynZawideh
ms.author: t-cazaw
manager: serdars
audience: admin 
ms.topic: article 
ms.service: msteams
localization_priority: Normal 
description: Learn about admin settings in the Praise app in the Microsoft Teams admin center


---

# Manage the Praise app in the Microsoft Teams admin center

The Praise app in Microsoft Teams helps users show appreciation to members of their organization or classroom. With a selection of badge sets to choose from and the option to create your own badges, Praise is designed to help recognize the effort that goes into the wide range of work that Teams users do, from educators to first line workers.

Admins can control what badges are available to their organization from the Teams admin center. In the left navigation, select **Teams apps > Manage apps**. Open Praise in the [tenant app catalog](https://docs.microsoft.com/microsoftteams/manage-apps#view-apps-in-your-tenant-app-catalog), and go to **Settings**.

## Use built-in badge sets

Built-in sets are collections of badges designed by Microsoft for the Praise app. These sets are not editable by admins. The default badge set is already enabled and available in the Praise app. To change the availability of the default set or of any badges sets, switch the corresponding toggle to On or Off. 

<a name="default-badges"></br></a>

### Default badges

The default badge set is designed to help Teams users recognize their peers for going above and beyond with their work.

![Preview of default badge set](media/default-set-praise.png)

<a name="sel-edu-badges"></br></a>

### Social and emotional learning badges for education

Educators can recognize individual students for social and emotional learning (SEL) achievements and behaviors with badges that illustrate these concepts.

![Preview of the Social and emotional learning badges for  education](media/sel-edu-set-praise.png)

<a name="create-your-own-badges"></br></a>

## Create your own badges

Switch the **Custom badges** toggle to On and select **+ Add a badge**. From there, you can design a custom badge in the side panel.

1. Enter a badge name. This is the name that will appear on the badge when users send praise.
2. Set your badge colors. To set the text and background colors of your badge, you need to enter the colors as hexadecimal (hex) values.

> [!TIP]
> If you’re new to hex values, this article includes a [quick introduction](#hex-colors-intro) to show you how to use them.

3. Upload a badge image. The accepted file type is .PNG. The file must be less than 25kb.
![Badge with background, text, and image fields labeled](media/praise-app-badge-fields.png)
4. Localize your badge name: Under **Locales**, select **Add +**. Select the desired locale from the drop-down list. Then enter the badge name in the designated language.
5. Exclude your badge from specific locales: Under **Exclude these locales**, select **Add +**. Select the locales you want to exclude from the drop-down list.
6. Select **Apply**. Your new badge will now appear in the custom badges table.

> [!NOTE]
> If steps 4 and 5 are skipped, the badge will be in the default language for all locales.
>
> When you’re finished making changes to your badge selection, make sure to select **Submit**. It may take up to a few hours before these changes are available to your organization.

<a name="hex-colors-intro"></br></a>

## Specify colors with hex values

Hex color values are strings of six hexadecimal digits that represent the intensity of red (RR), green (GG), and blue (BB) in a specific color on a scale of 00 to FF. When you put the values of all three colors together, you get a hex value: #RRGGBB

For example, the hex value for the color red is #FF0000 because red is set at the highest possible value, FF, and green and blue are each set at the lowest possible value, 00.

To explore different colors and their hex values, check out [Bing color picker](https://www.bing.com/search?q=color+picker).

Below is a list of example colors to get you started:

|Color  |Hex value|
|-------|---------|
|![hex color #FF6666](media/hexColor1.png)|  #FF6666   |
|![hex color #7FFFD4](media/hexColor2.png)|  #7FFFD4   |
|![hex color #FF75F0](media/hexColor3.png)|  #FF75F0   |
|![hex color #00BFFF](media/hexColor4.png)|  #00BFFF   |
|![hex color #800080](media/hexColor5.png)|  #800080   |
|![hex color #000000](media/hexColor6.png)|  #000000   |

<a name="best-practices"></br></a>

## Best practices for creating custom badges

**Submit all your badges at once.** Because it takes a while for new badges to be processed, it’s best to add all your custom badges to the table before submitting them.

**When choosing colors, keep accessibility in mind.** Some colors go together better than others.  Create contrast between your text and background colors to make the badge name easy to read. For example, if you chose a dark background color, choose a light text color.

**When selecting an image, keep badge dimensions in mind.** For the best quality, we recommend uploading an image file that is 216x216 pixels. Avoid stretching or distorting the image to fit these dimensions.

**If your badge image isn’t rectangular, make the image transparent.** You’ll need to do this before uploading the image file to Praise.

![Left: badge with non-transparent image, right: badge with transparent image](media/praise-app-best-practices.png)

## Badge set assets

Built-in badge sets can't be modified, so when a built-in set is enabled, all badges in the set are added to the Praise app. If you want to add specific badges from a built-in set and leave out others, recreate the badges you want to use as custom badges. You can download the badge image and find the text and background colors of badges from built-in sets in the tables below.

### Default badges assets

</br>

|Badge name     |Image file  |Text color | Background color |
|---------------|------------|---------- |--------|
|Achiever       |<a href="https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/raw/live/Teams/downloads/praise-app/default-set/Achiever.png" download>Achiever.PNG</a>|#D36E70    |#E3F4FC|
|Awesome        |<a href="https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/raw/live/Teams/downloads/praise-app/default-set/Awesome.png" download>Awesome.PNG</a>|#8283B2    |#D1EFF2|
|Coach          |<a href="https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/raw/live/Teams/downloads/praise-app/default-set/Coach.png" download>Coach.PNG</a>|#6AA55A    |#DBF1D6|
|Courage        |<a href="https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/raw/live/Teams/downloads/praise-app/default-set/Courage.png" download>Courage.PNG</a>|#DC5041    |#FCF6C8|
|Creative       |<a href="https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/raw/live/Teams/downloads/praise-app/default-set/Creative.png" download>Creative.PNG</a>|#CF9D50    |#FCF6C8|
|Inclusive      |<a href="https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/raw/live/Teams/downloads/praise-app/default-set/Inclusive.png" download>Inclusive.PNG</a>|#3C77BB    |#E2F4FC|
|Kind Heart     |<a href="https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/raw/live/Teams/downloads/praise-app/default-set/KindHeart.png" download>KindHeart.PNG</a>|#D36D6E    |#F4DEDE|
|Leadership     |<a href="https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/raw/live/Teams/downloads/praise-app/default-set/Leadership.png" download>Leadership.PNG</a>|#419098    |#D2EAEC|
|Optimism       |<a href="https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/raw/live/Teams/downloads/praise-app/default-set/Optimism.png" download>Optimism.PNG</a>|#D8338C    |#F4DDDE|
|Problem Solver |<a href="https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/raw/live/Teams/downloads/praise-app/default-set/ProblemSolver.png" download>ProblemSolver.PNG</a>|#B8916E    |#CBDADF|
|Team Player    |<a href="https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/raw/live/Teams/downloads/praise-app/default-set/TeamPlayer.png" download>TeamPlayer.PNG</a>|#8B8DC0    |#F4EEC0|
|Thank You      |<a href="https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/raw/live/Teams/downloads/praise-app/default-set/ThankYou.png" download>ThankYou.PNG</a>|#469CA4    |#BACCB6|

</br>

### Social and emotional learning badges for education assets

</br>

|Badge name        |Image file  |Text color | Background color |
|------------------|------------|---------- |--------|
|Communication     |<a href="https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/raw/live/Teams/downloads/praise-app/sel-edu-set/Communication.png" download>Communication.PNG</a>|#FFFFFF    |#173B65|
|Critical thinking |<a href="https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/raw/live/Teams/downloads/praise-app/sel-edu-set/CriticalThinking.png" download>CriticalThinking.PNG</a>|#FFFFFF    |#084D26|
|Curiosity         |<a href="https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/raw/live/Teams/downloads/praise-app/sel-edu-set/Curiosity.png" download>Curiosity.PNG</a>|#FFFFFF    |#008078|
|Empathy           |<a href="https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/raw/live/Teams/downloads/praise-app/sel-edu-set/Empathy.png" download>Empathy.PNG</a>|#FFFFFF    |#650B35|
|Goal pursuit      |<a href="https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/raw/live/Teams/downloads/praise-app/sel-edu-set/GoalPursuit.png" download>GoalPursuit.PNG</a>|#FFFFFF    |#006F95|
|Motivation        |<a href="https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/raw/live/Teams/downloads/praise-app/sel-edu-set/Motivation.png" download>Motivation.PNG</a>|#FFFFFF    |#C52127|
|Persistence       |<a href="https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/raw/live/Teams/downloads/praise-app/sel-edu-set/Persistence.png" download>Persistence.PNG</a>|#FFFFFF    |#167D3E|
|Respect           |<a href="https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/raw/live/Teams/downloads/praise-app/sel-edu-set/Respect.png" download>Respect.PNG</a>|#FFFFFF    |#8251A0|
|Responsibility    |<a href="https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/raw/live/Teams/downloads/praise-app/sel-edu-set/Responsibility.png" download>Responsibility.PNG</a>|#FFFFFF    |#B05DA3|
|Self-awareness    |<a href="https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/raw/live/Teams/downloads/praise-app/sel-edu-set/SelfAwareness.png" download>Self-awareness.PNG</a>|#FFFFFF    |#1680E5|
|Self-management   |<a href="https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/raw/live/Teams/downloads/praise-app/sel-edu-set/SelfManagement.png" download>Self-management.PNG</a>|#FFFFFF    |#4C144D|
|Thoughtfulness    |<a href="https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/raw/live/Teams/downloads/praise-app/sel-edu-set/Thoughtfulness.png" download>Thoughtfulness.PNG</a>|#FFFFFF    |#EE4086|
