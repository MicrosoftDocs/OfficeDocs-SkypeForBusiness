---
title: Set up Microsoft Teams Phone System with Calling Plan emergency locations
author: DaniEASmith
ms.author: danismith
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
f1.keywords: 
  - NOCSH
ms.localizationpriority: medium
search.appverid: MET150
description: Learn how to set up emergency locations for Microsoft Teams Phone System with Calling Plan.
appliesto: 
  - Microsoft Teams
ms.collection: 
  - M365-voice
  - M365initiative-voice
---

# Step 1: Set up a Teams Phone System emergency location

An emergency location is used when someone in your organization calls emergency services such as fire, police, or ambulance. When a person calls an emergency service, the address that's configured as your organization's emergency address is sent to the service. This step sets up the primary emergency location for your organization. This location will be associated with your company's main phone number in a later step.

If you have users in multiple locations, such as home offices or offices in other cities, you can configure additional emergency locations. You can even configure specific places within a location. Places can be different buildings, floors, offices, or other places where users may be at a location. Other locations and places can be added after you complete your initial setup of Teams Phone System with Calling Plan.

## Add an emergency location

1. Open the Microsoft Teams admin center and log in with a user account that is a Global admin. This account is usually the one you used to sign up for Microsoft 365.
2. In the left navigation pane, go to <a href="https://admin.teams.microsoft.com/locations" target="_blank">**Locations** > **Emergency addresses**</a>.
3. Click **Add**.
4. Enter a name and description for the location.
5. Select the country or region, and then enter the address.

   > [!NOTE]
   > In Belgium, France, Germany, Ireland, Netherlands, and Spain, it's important to understand that to successfully activate a phone number in Microsoft 365 or Office 365, the address set up in the emergency location, which is used to acquire the number, must match the phone number's area code.

6. If the address isn't found and you want to manually edit the address, turn on **Edit the address manually**.
7. Click **Save**.

> [!div class="nextstepaction"]
> [Next step: Set up phone numbers](set-up-phone-numbers.md)
