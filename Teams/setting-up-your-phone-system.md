---
title: "Setting up Phone System in your organization"
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.reviewer: makolomi
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
audience: Admin
appliesto: 
  - Skype for Business
  - Microsoft Teams
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: 
  - Phone System
description: "Learn how to set up Phone System (Cloud PBX) for your organization. "
---

# Set up Phone System in your organization

The following is a step-by-step guide for setting up Phone System in Office 365. Links to additional, detailed information are available at the end of each step.

## Step 1: Make sure that Phone System is available in your country or region

1.	First go to [Country and region availability for Audio Conferencing and Calling Plans](country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md), and select your country or region from the list at the top of the page. 
2.	Under **Phone System**, review the list of features and details. 
3.	If Phone System is available, go to step 2. 

## Step 2: Buy and assign Phone System and Calling Plan licenses

To assign a Phone System and Calling Plan license to a single user, the steps are the same as assigning an Office 365 license.  You can also assign licenses to multiple users in bulk. For more information, see [Assign Microsoft Teams licenses](assign-teams-licenses.md).

If Calling Plans are not available for your country or region, consider using Direct Routing to connect your on-premises telephony infrastructure to Phone System.  For more information, see [Phone System Direct Routing](direct-routing-landing-page.md).

## Step 3: Get phone numbers for your users

Before you can set up users in your organization to make and receive phone calls, you must get phone numbers for them.

You have three ways of getting numbers for your users:
- Get new numbers using the Teams admin center.
- Get new numbers that aren't available in the Teams admin center.
- Port or transfer your existing numbers from your current service provider or phone carrier to Office 365.

You must use the **Add numbers** page to see, search, acquire, and reserve those numbers. You can search by Country/Region, State, and City, and then enter the number of phone numbers you will need for your users.

### Get new user phone numbers using the Teams admin center

1. Sign in to Microsoft 365 with your work or school account.

2. Go to the **Teams admin center**.
    
3. In the left navigation go to **Voice** > **Phone numbers**, click **Add**, and then follow the prompts.
    
### Get new numbers that aren't available in the Teams admin center
  
Sometimes (depending on your country/region) you won't be able to get your new numbers using the Teams admin center. In this case, you'll need to download a form and send it back to us. To learn how to request new user numbers, see [Manage phone numbers for your organization](manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md).   
  
### Port or transfer phone numbers from your service provider or phone carrier
  
- If you need 999 or fewer phone numbers for your users, you can use the **New Local Number Port Order** wizard in the Teams admin center. Follow the steps found in [Transfer phone numbers to  Teams](phone-number-calling-plans/transfer-phone-numbers-to-teams.md) to transfer your phone numbers.
    
- If you need to port more than 999 phone numbers, see [Manage phone numbers for your organization](manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md) to submit a port order service request or order. 

For detailed information about getting new phone numbers or transferring existing numbers, see [Manage phone numbers for your organization](manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md).

## Step 4: Get service phone numbers (audio conferencing, call queues, auto attendants)

In addition to getting phone numbers for your users from Office 365, you can search and acquire toll or toll-free phone numbers for services such as audio conferencing (for conference bridges), auto attendants, and call queues. Service phone numbers have a higher concurrent calling capacity than user or subscriber phone numbers. For example, a service number can handle hundreds of calls simultaneously, whereas a user's phone number can only handle a few calls simultaneously.

### Get new service numbers using the Teams admin center


1. Sign in to Office 365 with your work or school account.

2. Go to the **Teams admin center**.

3. In the left navigation pane go to **Voice** > **Phone numbers** > **Add new number**, and then click **New service numbers**.

    > [!IMPORTANT]
    > For you to see the **Voice** option in the left navigation pane in the Teams admin center, you must first buy at least one **Enterprise E5 license**, one **Phone System** add-on license, or one **Audio Conferencing** add-on license.

### Get new numbers that aren't available in the Teams admin center
  
Sometimes (depending on your country/region) you won't be able to get your new numbers using the Teams admin center. In this case, you will need to download a form and send it back to us. To learn how to request new numbers, see [Manage phone numbers for your organization](manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md). 

### Port or transfer existing service numbers

If you want to transfer service numbers from your current service provider or carrier, you need to manually submit a port order to Microsoft. You need to submit separate port orders for each type of service number (toll vs. toll-free) that you will be transferring using a Letter of Authorization (LOA). In the Letter of Authorization (LOA), you must select the correct type of service number. When contacting Microsoft support, specify that you are transferring a service number (*and not a user or subscriber number*), or the concurrent calling capacity may not be enough to handle call volumes. If you want to transfer phone numbers or do other things with your phone numbers, see [Manage phone numbers for your organization](manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md).

## Step 5: If you want to set up Calling Plans

If you have been following the steps above, you have already bought and assigned Phone System and licenses and a Calling Plan (step 2) and acquired phone numbers for your users (step 3), so your calling plan is partially set up. To complete the procedures for setting up Calling Plan, see [Set up Calling Plans](set-up-calling-plans.md).


## Step 6: If you want to set up Audio Conferencing

Sometimes people in your organization will need to use a phone to call in to a meeting. Microsoft Teams includes the Audio Conferencing feature for just this situation. People can call in to  Teams meetings using a phone, instead of using the Teams app on a mobile device or PC.
For information about how to set up Audio Conferencing, see [Set up Audio Conferencing for Teams](set-up-audio-conferencing-in-teams.md).

## Step 7: If you want to set up a Cloud call queue

Cloud call queues include greetings that are used when someone calls in to a phone number for your organization, the ability to automatically put the calls on hold, and the ability to search for the next available call agent to handle the call while the people who call are listening to music on hold. You can create single or multiple call queues for your organization.

For more information about call queues, see [Create a Cloud call queue](create-a-phone-system-call-queue.md).

## Step 8: If you want to set up a Cloud auto attendant

Auto attendants let people that call in to your organization and navigate a menu system to get them to the right department, call queue, person, or the operator. You can create an auto attendant for your organization by using the Teams admin center.

For information about setting up a Cloud auto attendendant, see [Set up a Cloud auto attendant](create-a-phone-system-auto-attendant.md).


## Step 9: Assign service phone numbers (audio conferencing, call queues, auto attendants)

Once you have your service numbers from **Step 4 above**, you need to assign them to each type of service that you want. For example, if you want a dedicated service phone number (toll or toll-free), you'll need to assign the number to the conferencing bridge.

- For Audio Conferencing, you can assign a dedicated number to a conferencing bridge by going to **Teams admin center** > **Meetings** > **Conference bridges** and follow the prompts.  For more information, see  [Change the toll or toll-free numbers on your Audio Conferencing bridge](change-the-phone-numbers-on-your-audio-conferencing-bridge.md).

- For Auto Attendants, you can assign a dedicated number to an auto attendant by going to  **Teams admin center** > **Voice** > **Auto attendants** and follow the prompts.  For more information, see [Set up a Cloud auto attendant](create-a-phone-system-auto-attendant.md).

- For Call Queues, you can assign a dedicated number to a call queue by going to **Teams admin center** > **Voice** > **Call queues** and follow the prompts. For more information, see [Create a Cloud call queue](create-a-phone-system-call-queue.md).

For detailed information about getting new service numbers and porting existing service numbers, see [Getting service phone numbers](getting-service-phone-numbers.md).

## Step 10: Set up Communications Credits for your organization

If you would like to use toll-free numbers with Microsoft Teams, You'll need to set up Communications Credits. Microsoft recommends that you set up Communications Credits for your Calling Plans (Domestic or International) and Audio Conferencing users who need the ability to dial out to any destination. Many countries/regions are included, but some destinations may not be included in your Calling Plan or Audio Conferencing subscriptions. 

If you don't set up Communications Credits billing and assign a **Communications Credits** license to your users and you run out minutes for your organization (depending on your Calling Plan or Audio Conferencing plan in your country/region), those users won't be able to make calls or dial out from Audio Conferencing meetings. For more information, including recommended funding amounts, see [What are Communications Credits?](what-are-communications-credits.md) and [Set up Communications Credits for your organization](set-up-communications-credits-for-your-organization.md).
  

## Related topics
[Here's what you get with Phone System in Office 365](here-s-what-you-get-with-phone-system.md)

[Manage phone numbers for your organization](manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md)

[Getting service phone numbers for Skype for Business and Microsoft Teams](getting-service-phone-numbers.md)

[Country and region availability for Audio Conferencing and Calling Plans](country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md)
    
  
 
