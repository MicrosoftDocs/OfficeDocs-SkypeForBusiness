---
title: Set up PSTN Consumption billing
ms.prod: OFFICE365
ms.assetid: bb9f2a8d-f5be-41ed-9d19-25dea5ca9f52
---


# Set up PSTN Consumption billing

You will need to set up PSTN Consumption if you would like to use toll free numbers with Skype for Business. Also, we recommend that you set up PSTN Consumption billing for your PSTN Calling and Conferencing users that need the ability to dial out to **any PSTN destination**. Many countries/regions are included but some PSTN destinations may not be included in your PSTN Calling or PSTN Conferencing subscriptions. If you don't set up PSTN Consumption billing and assign a PSTN Consumption license to your users and you run out minutes for your organization (depending on your PSTN Calling, Conferencing plan in your country/region), those users won't be able to make calls or dial-out from Online PSTN Conferencing meetings. You can find out more information including recommended funding amounts by seeing [What is PSTN Consumption billing?](what-is-pstn-consumption-billing.md).
  
    
    


> [!NOTE]
> If you're wondering how much it is and the rates, see  [PSTN Consumption Rate Table](https://go.microsoft.com/fwlink/p/?LinkId=799523 ). 
  
    
    


## Step 1: Assign PSTN Conferencing and PSTN Calling Licenses to your users

When you sign up, you get certain amount of minutes depending on your country/region. You can see the number of minutes you will get  [Where can my PSTN Calling users call?](http://technet.microsoft.com/library/9fb78723-05f4-4b86-98e4-fa2a1da3ab5c%28Office.14%29.aspx). After you use up those minutes however PSTN calls will be disconnected. To prevent this from happening, you need to set up Skype for Business PSTN Consumption Billing.
  
    
    
To set it up, **you need to either assign a PSTN Conferencing or Cloud PBX license** to your users.
  
    
    

- Assign a dial-in or PSTN conferencing license to your users. See  [Assign Skype for Business licenses](assign-skype-for-business-licenses.md).
    
    After you assign this license, you will need to set up dial-in (PSTN) conferencing. For step-by-step instructions, see  [Set up dial-in or PSTN conferencing for Skype for Business](set-up-dial-in-or-pstn-conferencing-for-skype-for-business.md).
    
  
- Assign Cloud PBX and PSTN Calling plan licenses to your users. See  [Assign Skype for Business licenses](assign-skype-for-business-licenses.md).
    
    > [!NOTE]
      > Although for it's not required for PSTN Consumption Billing, you need to still also assign the PSTN Calling plan license. 

    After you assign these licenses, you will need to get your phone numbers for your organization, and then assign those numbers to the people in your organization. For step-by-step instructions, see  [Set up PSTN Calling for Skype for Business](set-up-pstn-calling-for-skype-for-business.md).
    
  
Looking for more information about  [Skype for Business add-on licensing](skype-for-business-add-on-licensing.md)
  
    
    

## Step 2: Set up PSTN Consumption Billing for your organization


1. Sign in to Office 365 with your work or school account.
    
  
2. In the left navigation of the Office 365 admin center, go to **Billing** > **Subscriptions** > **Add Subscriptions** > **Add-on subscriptions** > **Skype for Business PSTN Consumption** and then click **Buy now**.
    
  
3. On the **Skype for Business PSTN Consumption** subscription page, add or fill in and then click **Next**:
    
  - **Add funds** Put in the amount that you want to add to your account. If you don't enable auto-recharge, once these funds are depleted, calling capabilities that are enabled via PSTN consumption will be disrupted (such as inbound toll free service). To avoid having to manually replenish your PSTN Consumption balance each time your balance reaches 0 (zero), we recommend customers enable the auto-recharge feature.
    
  
  - **Auto-recharge** Enabling auto-recharge will automatically refill your account when the balance falls below the threshold that you set.
    
    It's recommended that you use the **Auto-recharge** ' setting to avoid any disruption of service should your PSTN consumption balance reaches 0 (zero). You will be sent an email when recharge transactions succeed, recharge transactions fail (such as an expired credit card) and when your PSTN consumption balance reaches 0 (zero).
    
  - **Recharge amount** Put the amount in the **Recharge with** box that you want added to your account once it reaches the trigger amount below.
    
  
  - **Trigger amount** Put the amount in **When the balance falls below** box that will be used to ' *trigger*  ' the auto-recharge. Once your balance falls below this amount, the Recharge amount will be added automatically to your account.
    
  
4. On the How do you want to pay put in your payment information and click **Place order**.
    
    > [!NOTE]
      > Funds will be applied only to Skype for Business PSTN Consumption services at Microsoft's published rates when the services are used. Any funds not used within 12 months of the purchase date will expire and be forfeited. 
Each organization will have a different usage of PSTN Calling volume and rates to consider. You will need to get this type of usage data from your current service provider. For those organizations using Skype for Business Online already as their service provider, you can get usage data by reviewing it in the **Skype for Business admin center** > **Reports** > **PSTN usage details** report.
  
    
    
When you are setting up PSTN Consumption billing, you will need to investigate call usage for your organization to determine the amounts that you will need to put in. You can get call usage information by reviewing the **PSTN usage details** report. This report lets you export the call data records to Excel if you want to export the data for storage or to create custom reports. To see usage, see [Skype for Business PSTN usage report](skype-for-business-pstn-usage-report.md)
  
    
    

## Step 3: Assign a Skype for Business PSTN Consumption license to those users


1. Sign in to Office 365 with your work or school account.
    
  
2. In the left navigation of the Office 365 admin center, go to **Users** > **Active users** and then select the user or users from the list.
    
    > [!TIP]
      > If you are assigning licenses to up to 20 users at the same time, you can use the **Select a view** drop-down then choose one of the options or create your own view. Then click **Edit** > **Next** > **Next** then select the license and click **Submit**. 
3. In the Action pane under **Product licenses**, click **Edit**.
    
  
4. On the **Product licenses** page, toggle **Skype for Business PSTN Consumption** to **On** to assign this license and click **Save**.
    
    > [!NOTE]
      > Even if you have users that are assigned an **Enterprise E5** license it's still recommended that you do this.

## Want to know about plans and pricing?

You can see the plans and pricing by seeing one of the following links:
  
    
    

-  [Skype for Business PSTN Calling Plans](https://go.microsoft.com/fwlink/?LinkId=799761 )
    
  
-  [Skype for Business PSTN Conferencing Plans](https://go.microsoft.com/fwlink/?LinkId=799762 )
    
  
-  [Skype for Business Cloud PBX Plans](https://go.microsoft.com/fwlink/?LinkId=799763)
    
  
You can also see information by  [signing into the Office 365 admin center](https://portal.office.com/adminportal/home?add=sub&amp;adminportal=1#/catalog) and going to **Billing** > **Subscriptions** > **Add subscriptions**.
  
    
    
To see a table with the license or licenses you will need for each feature, see  [Skype for Business add-on licensing](skype-for-business-add-on-licensing.md).
  
    
    

