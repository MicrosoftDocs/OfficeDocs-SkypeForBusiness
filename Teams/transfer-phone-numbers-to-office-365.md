---
title: "Transfer phone numbers to Office 365"
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.reviewer: mikedav, roykuntz, jastark
ms.topic: article
ms.assetid: 47b3af8e-4171-4dec-8333-c956f108664e
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
- Teams_ITAdmin_Help
- M365-voice
audience: Admin
appliesto:
- Skype for Business 
- Microsoft Teams
localization_priority: Normal
f1keywords:
- ms.lync.lac.PortingNumbersOverview
ms.custom:
- Calling Plans
- LIL_Placement
description: "Learn what you need to know and do before porting phone numbers to Skype for Business, and how to create a port order to transfer them."
---

# Transfer phone numbers to Office 365

It's easy to transfer your phone numbers from your current service provider to Skype for Business. After you port your phone numbers to Skype for Business, Microsoft will become your service provider and will bill you for those phone numbers.
  
Before you start transferring phone numbers, we recommend that you review the information in [Transferring phone numbers common questions](transferring-phone-numbers-common-questions.md). If you have service numbers for dial-in conferencing bridges, auto attendants or other service numbers, toll-free phone numbers or have more than 999 user (subscriber) phone numbers that you need to transfer to Skype for Business, see [Manage phone numbers for your organization](manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md) to download the correct forms and send them to us.

  > [!NOTE]
  > We process port orders for transferring phone numbers only on U.S. business days and not on public holidays or weekends. 
  
## How to create a port order and transfer your phone numbers to Skype for Business
<a name="bk_LNPcountries_1"> </a>

  > [!NOTE]
  > If you have service numbers for dial-in conferencing bridges, auto attendants or other service numbers, toll-free phone numbers or have more than 999 user (subscriber) phone numbers that you need to transfer to Skype for Business, see [Manage phone numbers for your organization](manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md) to select the correct country/region and download the correct forms and send them to us.
 
![An icon showing the Skype for Business logo](media/sfb-logo-30x30.png) **Using the Skype for Business admin center**

 
1. Sign in to Office 365 with your work or school account.
    
2. Go to the **Microsoft Teams admin center** > **Legacy portal**.
    
3. In the left navigation go to **Voice** > **Port orders** > click **Add**.
    
4. On the **New Local Number Port Order** page, read the information and then click **Let's get started**.
    
5. On the **Account info** page, enter the following and then click **Next**:
    
   - **Account number** Account number for the service provider or carrier.
    
   - **Billing telephone number** must be in the E.164 format (requires a + sign to prepend the number). For example, for a North America number, use the format +1XXXYYYZZZZ.
    
   - **PIN to unblock number** PIN - if needed by your current service provider or carrier.
    
   - **Company name** This is the name of your company or organization.
    
     > [!NOTE]
     > The **Company name** box will only accept 25 characters that includes spaces. If the company's name is longer than 25 characters, the first 25 characters of the name will be submitted and the port order will still be processed.
  
   - **Authorizing person** Authorized user's name.
    
     > [!NOTE]
     > The **Authorizing person** box will only accept 15 characters that includes spaces. If the authorized person's name is longer than 15 characters, the first 15 characters of the name will be submitted and the port order will still be processed.
  
   - **Service address** Service address for the account. This will be listed on the bill from your service provider or carrier.
    
   - **City**, **State**, **Zip** of the service address.
    
6. On the **Numbers** page, enter the phone numbers that you want to transfer in E.164 format. For example, for a North America number, use the format +1XXXYYYZZZZ. Use a comma to separate multiple phone numbers.
    
    > [!NOTE]
    > If you are doing a full-port, you need to include the service Billing Telephone Number (BTN) in the list. If you are doing a partial-port, leave the service Billing Telephone Number (BTN) out of this list. 
  
    If you are doing a full-port, select **I am transferring all my numbers from my current carrier**. If you are doing a partial-port, select **I'm only transferring some of my numbers**. After you choose the right one, click **Check number portability**.
    
7. Click **Proceed**.
    
8. On the **Transfer date** page, on the **Day** drop-down list, select the date and under the **Start time** drop-down list, select the time (EST) and then click **Next**.
    
9. On the **Letter of authorization** page, check each of the following boxes. Then under the **Signature** box, type the person that is authorized to make changes to the account. This is the same name that is used on the **Account Information** page > **Authorizing person**. Then click **Next**.
    
10. On the **Submit** page under **Other people to notify** enter any other email address of the people you want to and click **Submit port order**. The port order will now be listed on the **Port orders** page. You can view the status of the order under **Status** column. You can view details of the port order such as the **Order ID**, **Submitted**, **Transfer date** and **Status**. You can see more details for the port order in the Action pane, including the name of the carrier.
    
## What happens next?
<a name="bk_LNPcountries_1"> </a>

Once your port order has been submitted and received, you will be sent an email that verifies your port order. 
  
Your port order request will be checked and updated daily and you will be notified of its progress and status in email. If your request is rejected, you will be asked to open a support ticket and in that support ticket we ask that you provide **Port Order ID**. The port order ID can be found in the Skype for Business admin center under **Voice** > **Port orders** > **Order ID** column.
  
## What if I have problems?
<a name="bk_LNPcountries_1"> </a>

 **The service address isn't the same as the billing address. The address information I submitted on the order matches my customer's bill copy, why is it still rejecting?** Most carriers will identify the porting information based on the service address information, not the billing address. Since a bill copy is a billing record, it may not provide the same information as the service address for the telephone number(s) being ported.
  
 **What should I do if my order is taking too long to process?** We want number porting to be very simple and quick process. If your order is taking longer than you think it should and the status still doesn't show as complete in the Skype for Business admin center, please open support ticket and include the port order ID.

   
## Related topics
[Transferring phone numbers common questions](transferring-phone-numbers-common-questions.md)

[Different kinds of phone numbers used for Calling Plans](different-kinds-of-phone-numbers-used-for-calling-plans.md)

[Emergency calling terms and conditions](emergency-calling-terms-and-conditions.md)

[Skype for Business Online: Emergency Calling disclaimer label](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/emergency-calling/emergency-calling-label-(en-us)-(v.1.0).zip?raw=true)

  
 