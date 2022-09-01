---
title: Accessibility guide for Microsoft Teams Admins
ms.author: meghan
author: meganrmhan
ms.reviewer: eljones    
manager: serdars
ms.topic: conceptual
ms.service: msteams
audience: admin
search.appverid: MET150
description: Learn how to view your policy assignment activities in the Activity log in the Microsoft Teams admin center.
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.custom: 
ms.collection: 
  - M365-collaboration
---

# Accessibility guide for Microsoft Teams Admins

As the Microsoft Teams administrator for your organization, you can help make your Teams environment as inclusive and accessible as possible for all your users. Follow the guides and resources below to configure Microsoft Teams for optimal accessibility.

> [!NOTE]
> Many of the accessibility options are turned on by default but you can check that they weren’t turned off by following the guides below.

## Turn on captions and transcription for meetings and calls

Create inclusive meetings and calls for users with disabilities so everyone can participate and contribute. 

### Turn on live captions for meetings

Live captions are real-time auto-generated text of what is said in a meeting. They appear a few lines at a time for a user who has turned them on, and aren’t saved.

To turn on live captions for users:

1. In the Microsoft Teams admin center, go to **Meetings**, and then select the dropdown **Meeting policies**.

2. Select the policy you want to modify.
 
3. Go to the **Participants & guests** section.

4. Switch **Live captions** to **Not enabled but the user can override**.

5. Select **Save**.

> [!TIP]
> Share the following link so users can learn how to [turn on live captions during meetings](https://support.microsoft.com/office/use-live-captions-in-a-teams-meeting-4be2d304-f675-4b57-8347-cbd000a21260#ID0EBD=Desktop).

> [!NOTE]
> Live captions are available for meetings held in Commercial, and the U.S. Government Community Cloud (GCC) organizations.

### Turn on transcription for calls

Transcription is auto-generated, recorded text of what was said in a call. When turned on, the transcript is available to users to review after a call has ended.

To turn on transcription for users:

1. In the Microsoft Teams admin center, go to **Voice**, and then select the dropdown **Calling policies**.

2. Select the policy you want to modify.

3. Turn **Transcription** to **On**, then select **Save**.

### Why captions and transcripts are important

Captions and transcripts are text versions of the words someone is speaking. They give people the option to see text in addition to, or instead of, audio alone. Captions also benefit people who are deaf or hard of hearing by giving additional information on top of what some users receive from the sign language interpreter or CART captioner they might work with.

Captions and transcription are helpful in a wide variety of situations, but are especially helpful for:

- People who are deaf or hard of hearing

- People with learning disabilities

For more information, see [Web Content Accessibility Guidelines (WCAG) 1.2.4.: Captions (Live)](https://www.w3.org/WAI/WCAG21/Understanding/captions-live).

## Give meeting access to sign language interpreters and CART captioners

Give sign language interpreters and CART (communication access real-time translation) captioners access to Microsoft Teams meetings so they can work more effectively together with users who are deaf or hard of hearing.

### Admit sign language interpreters and CART captioners to meetings

Sign language interpreters and CART captioners likely don't work for your organization, but you can invite them to Microsoft Teams meetings by [by giving them guest access](/MicrosoftTeams/guest-access).

After guest access has been given, to admit sign language interpreters and CART captioners to meetings:

1. In the Microsoft Teams admin center, go to **Meetings**, and then select the dropdown **Meeting policies**.

2. Select the policy you want to modify.

3. Go to the **Participants & guests** section.

4. Choose the option under **Automatically admit people** that best fits your organization's compliance and security requirements. You can select one of the following options:

   - Everyone (not recommended)

   - People in my organization and guests (recommended)
 
   - People in my organization, trusted organizations, and guests

   - People in my organization

   - Organizer only

   - Invited users only

5. Select **Save**.

> [!NOTE]
> The setting **Automatically admit people** doesn't apply to dial-in users.

### Turn on IP video feed for your users

Give sign language interpreters the ability to share IP video feed during Microsoft Teams meetings so they can communicate with users who are deaf or hard of hearing.

To check if IP video feed is turned on:

1. In the Microsoft Teams admin center, go to **Meetings**, and then select the dropdown **Meeting policies**.

2. Select the policy you want to modify.

3. Go to the **Audio & video** section.

4. Check that **IP video** is turned **On**, then select **Save**.

> [!TIP]
> Share the following links with users so they can adjust how they use Teams to maximize their ability to participate, focus, and collaborate in meetings:
> - [Customize your meeting view](https://support.microsoft.com/office/customize-your-meeting-view-95aaeaf8-0f22-46cf-a6f9-34ca9b04a1b2)
> - [Use CART captions](https://support.microsoft.com/office/use-cart-captions-in-a-microsoft-teams-meeting-human-generated-captions-2dd889e8-32a8-4582-98b8-6c96cf14eb47#:~:text=Use%20CART%20captions%20in%20a%20Microsoft%20Teams%20meeting,out%20of%20your%20captions.%20...%204%20See%20also)

For more information, see [Web Content Accessiblity Guide (WCAG) 1.2.6.: Sign language interpretation](https://www.w3.org/TR/WCAG21/#sign-language-prerecorded).

## Reduce distractions in meetings

Encourage user participation by turning on video filters to reduce distractions in Teams meetings.

### Turn on video filters

Video filters help reduce distractions during meetings.

To turn on video filters:

1. In the Microsoft Teams admin center, go to **Meetings**, and then select the dropdown **Meeting policies**.

2. Select the policy you want to modify.

3. Go to the **Content sharing** section.

4. Choose the option under **Select video filters** that best fits your organization's compliance and security requirements. Select one of the following options:

   - Background blur only
   
   - Backgorund blur and default images

   - All filters

5. Select **Save**.

> [!TIP]
> Share the following links so users can adjust their Teams meeting preferences to reduce distractions:
> - [Change background effects in Teams meetings](https://support.microsoft.com/office/change-your-background-for-a-teams-meeting-f77a2381-443a-499d-825e-509a140f4780#ID0EDD=Desktop)
> - [Reduce background noise in Teams meetings](https://support.microsoft.com/office/reduce-background-noise-in-teams-meetings-1a9c6819-137d-4b3b-a1c8-4ab20b234c0d)

### Why it's helpful to reduce distractions

Some users in your organization might find it difficult to focus during video meetings and calls because of movement, light, and other distractions in participants' backgrounds. Using video filters helps users control distractions and participate fully.

*Background effects* can help people focus on the speaker rather than on the speaker's background. Microsoft Teams has a library of backgrounds, and users can also upload their own.

*Background blur* helps to improve visibility and focus when in meetings or calls because it reduces distractions in the background but keeps users in focus.

Video filters are helpful in a wide variety of situations, but are especially helpful for:

- People who are neurodiverse

- People who are deaf or hard of hearing

For more information, see [Web Content Accessibility Guideline (WCAG) 1.4.8.: Visual Presentation](https://www.w3.org/WAI/WCAG21/Understanding/visual-presentation.html).