---
title: "Set up Communications Credits for your organization"
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.reviewer: mikedav
ms.topic: article
ms.assetid: bb9f2a8d-f5be-41ed-9d19-25dea5ca9f52
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
- Teams_ITAdmin_Help
- M365-voice
ms.audience: Admin
appliesto:
- Skype for Business 
- Microsoft Teams
localization_priority: Normal
f1keywords: None
ms.custom:
- Licensing
description: "Learn how to set up communication credits (PSTN Consumption) billing licenses for your users and organization. "
---

# Set up Communications Credits for your organization

You will need to set up Communications Credits if you would like to use toll-free numbers with Skype for Business and Microsoft Teams. Also, we recommend that you set up Communications Credits for your Calling Plans (Domestic or International) and Audio Conferencing users who need the ability to dial out to **any destination**. Many countries/regions are included, but some destinations may not be included in your Calling Plan or Audio Conferencing subscriptions. If you don't set up Communications Credits billing and assign a **Communications Credits** license to your users and you run out minutes for your organization (depending on your Calling Plan or Audio Conferencing plan in your country/region), those users won't be able to make calls or dial out from Audio Conferencing meetings. You can get more information, including recommended funding amounts, by reading [What are Communications Credits?](what-are-communications-credits.md)
  
> [!NOTE]
> To find out how much it costs, [see the rates here](https://go.microsoft.com/fwlink/p/?LinkId=799523 ). 
  
## Step 1: Assign an Audio Conferencing and Calling Plan license to your users

When you sign up, you get a certain number of minutes depending on your country/region. You can see the number of minutes you will get search for the country or region [here](country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md). After you use those minutes, calls will be disconnected. To prevent this from happening, you need to set up Communications Credits.
  
To do so, **you need to assign an Audio Conferencing or Phone System license** to your users.
  
- Assign an **Audio Conferencing** license to your users. See [Assign Microsoft Teams licenses](assign-teams-licenses.md).
    
    After you assign this license, you will need to set up audio conferencing. For step-by-step instructions, see [Try or purchase Audio Conferencing in Office 365](try-or-purchase-audio-conferencing-in-office-365-for-teams.md).
    
- Assign **Phone System** and a domestic or domestic and international Calling Plan license to your users. See [Assign Microsoft Teams licenses](assign-teams-licenses.md).
    
    > [!NOTE]
    > Although it's not required for Communications Credits, you still need to also assign a **Domestic Calling Plan** or an **Domestic and International Calling Plan** license.
  
    After you assign these licenses, you will need to get your phone numbers for your organization, and then assign those numbers to the people in your organization. For step-by-step instructions, see [Set up Calling Plans](set-up-calling-plans.md).
    
For more information, see [Microsoft Teams add-on licensing](teams-add-on-licensing/microsoft-teams-add-on-licensing.md)
  
## Step 2: Set up Communications Credits for your organization

1. Sign in to Office 365 with your work or school account.
    
2. In the left navigation of the Office 365 admin center, go to **Billing** > **Subscriptions** > **Add subscriptions**.

3. Expand **Add-on subscriptions**, and then choose **Communications Credits** > **Buy now**.
    
4. On the **Communications Credits** subscription page, fill in your information, and then click **Next**:
    
   - **Add funds** Enter the amount that you want to add to your account. If you don't enable auto-recharge, once these funds are depleted, calling capabilities that are enabled using Communications Credits will be disrupted (such as inbound toll-free service). To avoid having to manually replenish your Communications Credits balance each time your balance reaches 0 (zero), we recommend you enable the auto-recharge feature.
    
   - **Auto-recharge** Enabling auto-recharge will automatically refill your account when the balance falls below the threshold that you set.
    
     It's recommended that you use the **Auto-recharge** setting to avoid any disruption of service should your Communications Credits balance reach 0 (zero). You will be sent an email when recharge transactions succeed, when recharge transactions fail (such as an expired credit card), and when your Communications Credits balance reaches 0 (zero).
    
   - **Recharge amount** Enter the amount in the **Recharge with** box that you want added to your account once it reaches the trigger amount below.
    
   - **Trigger amount** Enter the amount in **When the balance falls below** box that will be used to ' *trigger*  ' the auto-recharge. Once your balance falls below this amount, the recharge amount will be added automatically to your account.

      > [!NOTE]
     > Funds will be applied only to Communications Credits at Microsoft published rates when the services are used. Any funds not used within 12 months of the purchase date will expire and be forfeited. 
     > 
     > Monthly billing for Communication Credits will only be applied if the alloted fund has been used, to learn how to check your monthly usage, read [Skype for Business PSTN usage report](https://docs.microsoft.com/skypeforbusiness/skype-for-business-online-reporting/pstn-usage-report)
    
5. Enter your payment information and click **Place order**.
    >[!IMPORTANT]
    >If you are a volume licensing customer, you may choose your enterprise agreement number for payment. If you have multiple enterprise agreement numbers, you will be able to select which enterprise agreement you would like to use for payment. You will also be given an opportunity to specify a purchase order number to associate with the enterprise agreement number (if applicable).
    
Each organization will have a different usage of Calling Plan volume and rates to consider. You will need to get this type of usage data from your current service provider. Organizations already using Skype for Business Online already as their service provider can get usage data by reviewing it in the **Skype for Business admin center** > **Reports** > **PSTN usage details** report.
  
When you are setting up Communications Credits, you will need to investigate call usage for your organization to determine the amounts that you will need to put in. You can get call usage information by reviewing the **PSTN usage details** report. This report lets you export the call data records to Excel if you want to export the data for storage or create custom reports. To see usage, see [Skype for Business PSTN usage report](https://docs.microsoft.com/skypeforbusiness/skype-for-business-online-reporting/pstn-usage-report)
  
## Step 3: Assign a Communications Credits license to users

1. Sign in to Office 365 with your work or school account.
    
2. In the left navigation of the Office 365 admin center, go to **Users** > **Active users**, and then select a user or users from the list.
    
3. In the Action pane under **Product licenses**, click **Edit**.
    
4. On the **Product licenses** page, toggle **Communications Credits** to **On** to assign this license, and then click **Save**.
    
    > [!NOTE]
    > Even if you have users who are assigned an **Enterprise E5** license, it's still recommended that you do this.
  
## Want to know about plans and pricing?

You can see the plans and pricing by visiting one of the following links:
  
- [Calling Plans](https://go.microsoft.com/fwlink/?LinkId=799761 )
    
- [Audio Conferencing Plans](https://go.microsoft.com/fwlink/?LinkId=799762 )
    
- [Phone System Plans](https://go.microsoft.com/fwlink/?LinkId=799763)
    
You can also see information by [signing in to the Office 365 admin center](https://portal.office.com/adminportal/home?add=sub&amp;adminportal=1#/catalog) and going to **Billing** > **Subscriptions** > **Add subscriptions**.
  
To see a table with the license or licenses you will need for each feature, see [Microsoft Teams add-on licensing](teams-add-on-licensing/microsoft-teams-add-on-licensing.md).
  
## Related topics

- [Set up Skype for Business Online](/SkypeForBusiness/set-up-skype-for-business-online/set-up-skype-for-business-online)
    
- [Set up Cloud Voicemail - Admin help](set-up-phone-system-voicemail.md)
    
- [Set up Calling Plans](set-up-calling-plans.md) and [Calling Plans for Office 365](calling-plans-for-office-365.md)
    
- [Add funds and manage Communications Credits](add-funds-and-manage-communications-credits.md)
    
  
 
