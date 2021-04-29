---
title: Set up Microsoft 365 Business Voice emergency locations
author: dstrome 
ms.author: dstrome
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
f1.keywords:
- NOCSH
localization_priority: Normal
MS.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
- Teams_Business_Voice
search.appverid: MET150
description: Learn how to set up emergency locations for Microsoft 365 Business Voice.
appliesto: 
- Microsoft Teams
---

# Step 1: Set up a Business Voice emergency location

An emergency location is used when someone in your organization calls emergency services such as fire, police, or ambulance. When a person calls an emergency service, the address that's configured as your organization's emergency address is sent to the service. This step sets up the primary emergency location for your organization. This location will be associated with your company's main phone number in a later step.

If you have users in multiple locations, such as home offices or offices in other cities, you can configure additional emergency locations. You can even configure specific places within a location. Places can be different buildings, floors, offices, or other places where users may be at a location. Additional locations and places can be added after you complete your initial setup of Business Voice.

## Add an emergency location

1. Open the [Microsoft Teams admin center](https://admin.teams.microsoft.com) and log in with a user that is a Global admin (this is usually the account you used to sign up for Microsoft 365).
1. In the left navigation of the Microsoft Teams admin center, click **Locations** > **Emergency addresses**.
1. Click **Add**.
1. Enter a name and description for the location.
1. Select the country or region, and then enter the address.

   > [!NOTE]
   > In Belgium, France, Germany, Ireland, Netherlands, and Spain, it's important to understand that to successfully activate a phone number in Microsoft 365 or Office 365, the address set up in the emergency location, which is used to acquire the number, must match the phone number's area code.

1. If the address isn't found and you want to manually edit the address, turn on **Edit the address manually**.
1. Click **Save**.

> [!div class="nextstepaction"]
> [Next step: Set up phone numbers](set-up-phone-numbers.md)
