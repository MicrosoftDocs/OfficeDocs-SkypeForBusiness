---
title: "Set up holidays in Microsoft Teams"
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.reviewer: oscarr
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection:  
- Teams_ITAdmin_Help
- M365-collaboration
- M365-voice
audience: Admin
appliesto:
- Microsoft Teams
localization_priority: Normal
f1keywords: None
description: "Learn how to set up holidays in Microsoft Teams and connect them to your auto attendant."
---

# Set up holidays in Microsoft Teams

You can use the Microsoft Teams Holidays feature to schedule specific dates and times when people in your organization will be taking time off from work and won’t be available during regular business hours. 

You can link the holidays to auto attendants that you create within your organization. Auto attendants let callers navigate a menu system to get to the right department or get to information that they need. When you configure holiday call settings for an auto attendant, you can select the holiday from a list, add a greeting, and specify what to do with the call when it’s answered by the auto attendant during the holiday.

A good example is creating a holiday for Christmas for when many of your employees aren’t at work. After you create the holiday and set times, then you would add the holiday to your main auto attendant so when people call in, they will hear an audio message you created. Something like, “We are closed for Christmas from December 22nd through December 27th. Please leave us a voice message so we can return your call when we are back in the office.”

For more information about auto attendants, see [What are Cloud auto attendants](what-are-phone-system-auto-attendants.md)?  

## Create a holiday

1. In the Microsoft Teams admin center, go to **Org-wide settings** > **Holidays**.

2. Select **New holiday**.

3. Enter a name for the holiday.

4. Select **Add new date**.

5. Under **Start time**, select the calendar icon and choose the date when you’d like the holiday to begin.

6. Use the drop-down list to select a start time for the holiday.

7. Under **End time**, select the calendar icon and choose the date when you’d like the holiday to end. If the holiday is one day only, this should be the same date as the one you chose under **Start time**.

8. Use the drop-down list to select an end time for the holiday.

9. Select **Save**.

## Change a holiday

1. In the Microsoft Teams admin center, go to **Org-wide settings** > **Holidays**.

2. Select the holiday from the list.

3. Under **Start time**, select the calendar icon and choose the date when you’d like the holiday to begin.

4. Use the drop-down list to select a start time for the holiday.

5. Under **End time**, select the calendar icon and choose the date when you’d like the holiday to end. 

6. Use the drop-down list to select an end time for the holiday.

7. Select **Save**.

## Connect a holiday to an auto attendant

1. In the Microsoft Teams admin center, go to **Voice** > **Auto attendants**.
2. Select a resource account from the list.
3. In the left pane, select **Holiday call settings**.
4. Select **New holiday**.
5. Select the holiday from the drop-down list.
6. You can add an optional greeting:
    - To play a recorded greeting, select **Play an audio file**, and then select **Upload file**. Browse to the location of the audio file, select the file, and then select **Open**.
    - To create a greeting, select **Type a greeting message**, and then type your message. Callers will hear this message if you haven’t provided an audio file.
7. To end the call after the greeting, under **Actions**, select **Disconnect**. 

    To redirect the call, select **Redirect call**, and then select the person who will receive the redirected call from the drop-down list or search for the person by display name.
8. Select **Save**.

## Related topics

[What are Cloud auto attendants](what-are-phone-system-auto-attendants.md)?