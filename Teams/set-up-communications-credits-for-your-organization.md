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
  - M365-voice
  - m365initiative-voice
audience: Admin
appliesto: 
  - Skype for Business
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom: 
  - Licensing
  - seo-marvel-apr2020
description: "Learn how to set up communication credits (PSTN Consumption) billing licenses for your users and organization. "
---

# Set up Communications Credits for your organization

You will need to set up Communications Credits if you would like to use toll-free numbers with Skype for Business and Microsoft Teams. Also, we recommend that you set up Communications Credits for your Calling Plans (Domestic or International) and Audio Conferencing users who need the ability to dial out to **any destination**. Many countries/regions are included, but some destinations may not be included in your Calling Plan or Audio Conferencing subscriptions. If you don't set up Communications Credits billing and assign a **Communications Credits** license to your users and you run out minutes for your organization (depending on your Calling Plan or Audio Conferencing plan in your country/region), those users won't be able to make calls or dial out from Audio Conferencing meetings. You can get more information, including recommended funding amounts, by reading [What are Communications Credits?](what-are-communications-credits.md)
  
> [!NOTE]
> To find out how much it costs, [see the rates here](https://go.microsoft.com/fwlink/p/?LinkId=799523 ). 
  
## Step 1: Assign an Audio Conferencing or Calling Plan license to your users

When you sign up, you get a certain number of minutes depending on your country/region. You can search for your country or region in the [Country or region availability list for Audio Conferencing and Calling Plans](./country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md#select-your-country-or-region-to-see-whats-available-for-your-organization) to see the number of minutes you will get. After you use those minutes, calls will be disconnected. To prevent this from happening, you need to set up Communications Credits.
  
To do so, **you need to assign an Audio Conferencing or a Phone System license** to your users. Communication Credits can be enabled for users that have either of those two licenses assigned or both.
  
- Assign an **Audio Conferencing** license to your users. See [Assign Microsoft Teams add-on licenses](./teams-add-on-licensing/microsoft-teams-add-on-licensing.md).
    
    After you assign this license, you will need to set up audio conferencing. For step-by-step instructions, see [Try or purchase Audio Conferencing in Microsoft 365 or Office 365](try-or-purchase-audio-conferencing-in-office-365-for-teams.md).
    
- Assign **Phone System** and a **Domestic or Domestic and International** Calling Plan license to your users. See [Assign Microsoft Teams add-on licenses](./teams-add-on-licensing/microsoft-teams-add-on-licensing.md).
    
    > [!NOTE]
    > Although it's not required for Communications Credits, you still need to also assign a **Domestic Calling Plan** or a **Domestic and International Calling Plan** license.
  
    After you assign these licenses, you will need to get your phone numbers for your organization, and then assign those numbers to the people in your organization. For step-by-step instructions, see [Set up Calling Plans](set-up-calling-plans.md).
    
For more information, see [Microsoft Teams add-on licensing](./teams-add-on-licensing/microsoft-teams-add-on-licensing.md)
  
## Step 2: Set up Communications Credits for your organization

1. Sign in to the [Microsoft 365 admin center](https://portal.office.com/Adminportal) with your work or school account.
    
2. In the left navigation of the Microsoft 365 admin center, go to **Billing** > **Purchase Services**.

3. Look for **Communication Credits** under the **add-ons** category or search for "Communication Credits" in the **Search all product categories** search box and select **Details**.
    
4. Review the service information and select **Buy**. (Note: A fixed number of Communication Credits licenses are automatically selected in every order.)

5. On the Checkout page, enter your payment information and fill in the required information:
    
   - **Add funds** Enter the amount that you want to add to your account. If you don't enable auto-recharge, once these funds are depleted, calling capabilities that are enabled using Communications Credits will be disrupted (such as inbound toll-free service). To avoid having to manually replenish your Communications Credits balance each time your balance reaches 0 (zero), we recommend you enable the auto-recharge feature.
    
   - **Auto-recharge** Enabling auto-recharge will automatically refill your account when the balance falls below the threshold that you set.
    
     It's recommended that you use the **Auto-recharge** setting to avoid any disruption of service should your Communications Credits balance reach 0 (zero). You will be sent an email when recharge transactions succeed, when recharge transactions fail (such as an expired credit card), and when your Communications Credits balance reaches 0 (zero).
    
   - **Recharge amount** Enter the amount in the **Recharge with** box that you want added to your account once it reaches the trigger amount below.
    
   - **Trigger amount** Enter the amount in **When the balance falls below** box that will be used to ' *trigger*  ' the auto-recharge. Once your balance falls below this amount, the recharge amount will be added automatically to your account.

      > [!NOTE]
     > Funds will be applied only to Communications Credits at Microsoft published rates when the services are used. Any funds not used within 12 months of the purchase date will expire and be forfeited. 
     > 
     > When using the auto-recharge function, invoicing for Communication Credits is generated when the trigger amount is reached and a recharge transaction is processed. Communication credit amounts are used in a first in first out manner. To learn how to check your monthly usage, read [Microsoft Teams PSTN usage report](/microsoftteams/teams-analytics-and-reports/pstn-usage-report).
    
6. Select **Place order**.
    >[!IMPORTANT]
    >If you are a volume licensing customer, you may wish to use your enterprise agreement for payment. If you want to do this, open a Premier Support case to ahve this enabled. If you have multiple enterprise agreement numbers, you will be able to select which enterprise agreement you would like to use for payment. You will also be given an opportunity to specify a purchase order number to associate with the enterprise agreement number (if applicable) once Support enables this.
    
Each organization will have a different usage of Calling Plan volume and rates to consider. You will need to get this type of usage data from your current service provider. Organizations already using Skype for Business Online or Microsoft Teams as their service provider can get usage data by reviewing it in the **Microsoft Teams admin center** > **Analytics & reports** > **Usage reports** > **PSTN and SMS (preview) usage** report.
  
When you are setting up Communications Credits, you will need to investigate call usage for your organization to determine the amounts you need. You can get call usage information by reviewing the **PSTN and SMS (preview) usage** report. This report lets you export the call data records to Excel if you need to store the data or create custom reports. To learn how to see usage, read [Microsoft Teams PSTN usage report](/microsoftteams/teams-analytics-and-reports/pstn-usage-report).
  
## Step 3: Assign a Communications Credits license to users

1. Sign in to the [Microsoft 365 admin center](https://portal.office.com/Adminportal) with your work or school account.
    
2. In the left navigation of the Microsoft 365 admin center, go to **Users** > **Active users**, and then select a user from the list.
    
3. Choose **Licenses and Apps**.
    
4. Toggle **Communications Credits** to **On** to assign this license, and then select **Save**.
    
    > [!NOTE]
    > Even if you have users who are assigned an **Enterprise E5** license, it's still recommended that you do this.

    > [!TIP]
    > You can use [Powershell](/powershell/module/skype/?view=skype-ps&preserve-view=true) to assign licenses and apps to multiple users with one command.
  
## Want to know about plans and pricing?

You can see the plans and pricing by visiting one of the following links:
  
- [Calling Plans](https://go.microsoft.com/fwlink/?LinkId=799761 )
    
- [Audio Conferencing Plans](https://go.microsoft.com/fwlink/?LinkId=799762 )
    
- [Phone System Plans](https://go.microsoft.com/fwlink/?LinkId=799763)
    
You can also see information by [signing in to the Microsoft 365 admin center](https://portal.office.com/adminportal/home?add=sub&amp;adminportal=1#/catalog) and going to **Billing** > **Subscriptions** > **Add subscriptions**.
  
To see a table with the license or licenses you will need for each feature, see [Microsoft Teams add-on licensing](./teams-add-on-licensing/microsoft-teams-add-on-licensing.md).
  
## Related topics

- [Set up Skype for Business Online](/SkypeForBusiness/set-up-skype-for-business-online/set-up-skype-for-business-online)
    
- [Set up Cloud Voicemail - Admin help](set-up-phone-system-voicemail.md)
    
- [Set up Calling Plans](set-up-calling-plans.md) and [Calling Plans for Microsoft 365 or Office 365](calling-plans-for-office-365.md)
    
- [Add funds and manage Communications Credits](add-funds-and-manage-communications-credits.md)
    
  
