---
title: "Transferring phone numbers common questions"
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.reviewer: mikedav, roykuntz, jastark
ms.topic: article
ms.assetid: 28cbf7d7-97f3-4a99-aa76-897022c14a24
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
- Calling Plans
description: "The following are frequently asked questions about transferring phone numbers to Skype for Business. After reviewing the answers, you should be ready to create a port order and transfer your phone numbers. See Transfer phone numbers to Office 365 for instructions."
---

# Transferring phone numbers common questions

The following are frequently asked questions about transferring phone numbers to Skype for Business. After reviewing the answers, you should be ready to create a port order and transfer your phone numbers. See [Transfer phone numbers to Office 365](transfer-phone-numbers-to-office-365.md) for instructions.
  
## What countries/regions support number porting?

You can port or transfer phone numbers in all of the supported countries or regions but how you submit a port order request depend on the country or region where the phone numbers come from. You can see a listing of the countries/regions that are supported by [Countries and region availability for Audio Conferencing and Calling Plans](country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md). 

When you are doing phone number management tasks such as transferring (porting) numbers or getting phone numbers that are aren't available in the Skype for Business admin center, see [Manage phone numbers for your organization](manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md).
  
## What numbers can be transferred?

 **YOU CAN TRANSFER:**
  
In general, you can transfer any phone number that is from a supported provider, including:
  
- Land line phone numbers.
    
- Mobile device phone numbers such as those used for cell phone and tablets, etc.
    
    > [!NOTE]
    > Transferring mobile numbers is only available in the U.S. and Puerto Rico. 
  
- Toll phone numbers.
    
- Toll-free phone numbers.
    
    > [!NOTE]
    > Universal International Freephone Number (UIFN) can't be transferred to us. 
  
- Service phone numbers such as those used for conference bridges, auto attendants, etc.
    
- Fax phone numbers, but they can't be used for faxing. They will have to be assigned to a user.
    
- VoIP phone numbers from a phone provider such as Vonage or RingCentral.
    
- Skype for Business Hybrid phone numbers. If you want to transfer these numbers, you need send email to us at <ptn@microsoft.com>.
    
  **YOU CANNOT TRANSFER:**
  
> [!NOTE]
> At this time, you can't transfer any phone number or numbers that aren't from a supported country/region, including phone numbers from a VoIP phone provider. To see a list of supported countries/regions, see [Country and region availability for Audio Conferencing and Calling Plans](country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md)
  
- Phone numbers used for data connections like for DSL lines or broadband Internet connections.
    
- Phone numbers dedicated to faxing.
    
    If you have existing dedicated phone numbers that are being used for faxing, you  *can*  transfer these numbers over to Skype for Business but your fax services won't continue to work as expected. Faxing services aren't available to Skype for Business customers, even if you have licenses for **Phone System**, **Domestic Calling Plan** or **International Calling Plan**.
    
    If you port the phone number to Skype for Business, you can assign this phone number to a user in your organization instead of using it for faxing.
    
> [!NOTE]
> At this time in the United Kingdom (U.K.), we currently don't support transferring UK non-geographic numbers including shared cost numbers for area codes 0843, 0844, 0845, 0870, 0871, 0872. 
  
## What information will I need to provide?

You'll need to have all of the account information for your current carrier. The information you will need to put in the port order is mostly found on the most recent bill or invoice from your current service provider. You'll also need to know whose name is on the account and of course what numbers you want to port.
  
## What are full-port and partial-port transfers?

When you are porting phone numbers to Office 365, you have the option to transfer all of your numbers, or some of them.
  
- **Full-port** This is when you transfer all of your numbers from your current service provider to Skype for Business Online. When you are asked for the phone numbers you want to transfer, you *must include* the billing telephone number along with all of the other phone numbers on your account.
    
    For example, let's say your billing telephone number is  *+1 425-555-1234*  and you want to port all of your 25 phone numbers (*+1 425-555-1235 through 1259*). When you follow the instructions below to transfer your numbers, you would enter: **+14255551234 - +14255551259**.
    
- **Partial-port** This is when you are only transferring some of your phone numbers from your current service provider to Skype for Business Online. When you are want to port some of the phone numbers tied to the same billing telephone number, you ** *must not include* ** the billing telephone number along with all of the other phone numbers on your account.
    
    For example, let's say your billing phone number (BTN) is  *+1 425-555-1234*  and you want to port only 5 of your 25 phone numbers (*+1 425-555-1235 through 1259*). When you follow the instructions below to transfer your numbers, you would enter: **+1 425 555 1235 - +1 425 555 1239**.
    
## Can I submit a single number porting request for all of my numbers at one time?
<a name="bkmk_type_1"> </a>

A unique request is needed for each carrier and type of number being ported.
  
For example, you need to submit a unique number porting request for each of the following types of numbers:
  
- Local Toll numbers, also known as subscriber numbers or geographic numbers
    
- Toll Free numbers with area codes such as: 800, 844, 855, 866, 877 and 888
    
- Mobile numbers
    
- Service numbers that can be used for Audio Conferencing in Office 365.
    
Here's more information about submitting number porting requests for each of these types of numbers:
  
- **Telephone numbers** provided by different carriers require a unique porting request for numbers with each carrier.
    
- **Toll Free numbers** with area codes such as: 800, 844, 855, 866, 877 and 888 cannot be included in a number porting request with other types of numbers. To port these Toll Free numbers, you must [Manually submit a custom service request](/SkypeForBusiness/what-are-calling-plans-in-office-365/manually-submit-a-custom-service-request); they cannot be submitted in the Skype for Business admin center. See [Manage phone numbers for your organization](manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md).
    
    It's important to use the correct LOA for the country, and type of phone numbers, you want to port. You can download the LOA that you need [download the Letter of Authorization (LOA) that you need here](manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md).
    
- **Mobile numbers** require a PIN code to authorize the transfer. Therefore, they need separate number porting request.
    
- **Service number** porting requests need to be submitted by themselves. They cannot be submitted with other types of numbers.
    
## How long does it take to port numbers?
<a name="bkmk_type_1"> </a>

After you've completed the port order request, it will take between 7-14 days to be processed. However, depending on your service provider it may take up to 30 days. After the phone numbers are ported over, you will get an email from us telling you that you are good to go.
  
You can check the status of your port order by going to the Skype for Business admin center > **Voice** > **Port orders**. The status will be listed in the window under the **Status** column.
  
## Can user (subscriber) phone numbers be converted to service numbers?
<a name="bkmk_type_1"> </a>

Yes they can. All you need to do is submit a service request that includes your organization's tenant GUID and the phone numbers you want converted. To do this go see [Manage phone numbers for your organization](manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md). 
  
## Common mistakes to watch out for
<a name="bkmk_type_1"> </a>

Number porting is easy to do. Your order can get messed up, however, when there is a problem with the phone service provider, the order is incomplete and missing information, or there are typos.
  
Here are the most common mistakes we see customers make when they port numbers. Save yourself a call to customer support and double-check for these errors.
  
- Make sure the account information you give matches exactly what your phone carrier has on record. Mismatched information is the most common cause of errors and delay your port order. Verify the following is true:
    
  - Authorized name is correct.
    
  - Address is correct.
    
  - Account number is correct.
    
  - Billing Telephone Number (BTN) is correct.
    
- Make sure there are no advanced call control features, for example, Call Hunt, Distinctive Ring, that are enabled on these telephone numbers.
    
- Make sure you haven't placed any new service orders or disconnects with your current service provider.
    
- Make sure all numbers are from the same carrier and the same account.
    
- Make sure your service is active. Freezing the account prevents the change of carriers on the account. The authorized user will need to submit an order to the current carrier to remove the freeze. This process can take 1-3 weeks depending on the carrier.
    
## Can you transfer or port out numbers?
<a name="bkmk_type_1"> </a>

To transfer or  *port out*  phone numbers from Skype for Business Online to another telephone service provider or carrier, you will need to set a PIN. After you set the PIN, you need to include it when you request to port a phone number out. To see how to set up your PIN, see [Set your PIN for transferring numbers to a new service provider](/SkypeForBusiness/what-are-calling-plans-in-office-365/set-your-pin-for-transferring-numbers-to-a-new-service-provider).

> [!NOTE]
> If you need to get more telephone numbers than this, please [contact support for business products - Admin Help](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)

  
## Related topics

[Different kinds of phone numbers used for Calling Plans](different-kinds-of-phone-numbers-used-for-calling-plans.md)

[Emergency calling terms and conditions](emergency-calling-terms-and-conditions.md)

[Skype for Business Online: Emergency Calling disclaimer label](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/emergency-calling/emergency-calling-label-(en-us)-(v.1.0).zip?raw=true)
  
 
