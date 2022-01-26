---
title: Assign Teams Phone with Calling Plan phone numbers to your users
author: dstrome 
ms.author: dstrome
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
f1.keywords:
- NOCSH
ms.localizationpriority: medium
MS.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
- Teams_Business_Voice
search.appverid: MET150
description: Learn how to assign Microsoft 365 Teams Phone with Calling Plan phone numbers to users in your organization.
appliesto: 
- Microsoft Teams
---

# Step 5: Assign Teams Phone with Calling Plan phone numbers to your users

Before users can use Teams to make or receive phone calls to or from regular phone lines, you need to assign phone numbers to them. In Microsoft Teams clients, the phone number that you assign to a user is listed in the dial pad when the user clicks **Calls**. Do the following for each user that needs a phone number.

> [!NOTE]
> If you don't see any phone numbers, please wait. It may take several hours for your new phone numbers to become available in Teams.

1. Open the Microsoft Teams admin center and log in with a user that is a Global admin. This is usually the account you used to sign up for Microsoft 365.
1. In the left navigation pane, go to <a href="https://admin.teams.microsoft.com/phone-numbers" target="_blank">**Voice** > **Phone numbers**</a>.
1. On the **Phone numbers** page, select an unassigned number in the list, and then click **Edit**.  
1. In the **Edit** pane, under **Assigned to**, search for the user by display name or user name, and then click **Assign**.
1. Under **Emergency location**, you can select either the emergency location you added in the [Set up emergency locations](set-up-emergency-locations.md) step, or if you need to create a new location for another office or a home office, click **Add a location**.
1. Decide whether to send a welcome email with phone number information to the user. If you want to:
    - **Bring your existing phone numbers** to Teams Phone with Calling Plan (called phone number porting), *unselect* **Email user with telephone number information**.
    - **Use the new phone numbers** selected by Teams Phone with Calling Plan, *select* **Email user with telephone number information**.
1. Click **Save**.
1. Repeat the above steps for each user to which you want to assign a phone number.

> [!NOTE]
> Because of the latency between Microsoft 365 or Office 365 and Teams, it can take up to 24 hours for users to be enabled. If the phone number isn't assigned correctly after 24 hours, [contact support for business products - Admin Help](/microsoft-365/admin/contact-support-for-business-products). We're here to help!

> [!div class="nextstepaction"]
> [Next step: Set up an auto attendant](set-up-auto-attendant.md?tabs=general-info#steps)
