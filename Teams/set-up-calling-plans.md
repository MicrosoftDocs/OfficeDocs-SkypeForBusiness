---
title: "Set up Calling Plans"
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.reviewer: mikedav, roykuntz, jastark
ms.topic: article
ms.assetid: 57893158-1acd-44ac-acaf-19f58264a9e0
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
f1keywords: None
ms.custom: 
  - Calling Plans
  - LIL_Placement
description: "For Office 365 Calling Plan, learn how to buy and set up licenses, get phone numbers, add and assign emergency locations and phone numbers to users, and tell your users about their new phone numbers."
---
# Set up Calling Plans

Calls to other Teams users are free, but if you want your users to be able to call phones outside of your business, get a Domestic Calling Plan or an International Calling Plan in Office 365. It's easy to set this up for your business. 

## Step 1: Find out if Calling Plans are available in your country/region
Go to [Country and region availability for Audio Conferencing and Calling Plans](country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md) and select your country or region to get availability information about Calling Plans, as well as information about Audio Conferencing, Phone System, toll and toll-free numbers, and Communications Credits.
  
## Step 2: Buy and assign licenses
1. If the Phone System in Office 365 feature isn't included in your plan, you may need to purchase **Phone System** add-on licenses. After you have **Phone System** licenses, purchase [Calling Plans for Office 365](calling-plans-for-office-365.md). See [Microsoft Teams add-on licensing](teams-add-on-licensing/microsoft-teams-add-on-licensing.md), and buy the licenses and plan. 
    
    > [!TIP]
    > **Phone System** licenses and Calling Plans in Office 365 go together, so to see the option to purchase Calling Plans, you must first have the **Phone System** licenses.
  
2. First assign the licenses, and then assign a Calling Plan to the people in your organization. See [Assign Microsoft Teams licenses](assign-teams-licenses.md).
    
## Step 3: Get phone numbers
There are three ways to get new user numbers:

- **Use the Teams admin center.** For some countries/regions, you can get numbers for your users by using the Tea,s admin center, see [Getting phone numbers for your users](/microsoftteams/getting-phone-numbers-for-your-users).
    
- **Port your existing numbers.** You can port or transfer existing numbers from your current service provider or phone carrier to Office 365. See [Transfer phone numbers to Teams](phone-number-calling-plans/transfer-phone-numbers-to-teams.md) or [Manage phone numbers for your organization](manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md) for more information to help you do this.  
  
- **Use a request form for new numbers.** Sometimes (depending on your country/region) you won't be able to get your new phone numbers using the Skype for Business admin center, or you will need specific phone numbers or area codes. If so, you will need to download a form and send it back to us. See [Manage phone numbers for your organization](manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md) for more information. 

## Step 4: Add emergency addresses and locations for your organization
<a name="bkmk_add_addresses"> </a>
An emergency address must be associated with a phone number; when this association happens can vary among country and regions. For example, in the United States, you need to associate an emergency address when you assign the phone number to the user. In the United Kingdom, you need to associate an emergency address to the phone number when you are getting the phone numbers from Office 365 or transferring phone numbers from your current service provider. 

1. On the **Voice** page, choose **Emergency locations** > **Add new address**.

2. In the **New Address** pane, enter a name for your address, and then complete the remaining boxes.
    
     ![Screen shot of the New Address pane](media/dc1c5ef3-0554-4fb7-9ab1-5ea3ac9e5eb5.png)
  
    > [!TIP]
    > For English customers, if the street name is a number, be sure to include "st" or "th" at the end, as shown in the above picture.

3. Choose **Validate**.

    If needed, you'll be prompted to make corrections to the address.

    > [!CAUTION]
    > Validating a street or civic address involves making sure that it is legitimate and correctly formatted. It is possible that a partially correct emergency address, such as if you mistyped the name of the city, may still pass validation. Even though it's misspelled and passed validation, the combination of the misspelled name of city along with the other correct parts of the address are enough information to route the call to the appropriate emergency dispatch center.

    > [!TIP]
    > If the address needs to be corrected for emergency response, a green banner will appear notifying you that the address was updated.

4. After the address is validated, choose **Save**.

    
## Step 5: Assign an emergency address and a phone number to a user
<a name="bkmk_add_addresses"> </a>
When you are setting up Calling Plans in Office 365, you must assign a phone number and emergency address to each of your users. The emergency address must be created before you can associate it with a phone number. 

> [!TIP]
> If you add more people to your business right before doing this step, it may take **several hours** for them to appear on the **Voice users** page. There's a latency.

1. On the **Voice users** page, select the people who you want to assign a phone number and emergency address to.

2. In the Action pane, click **Assign number**.

3. On the **Assign number** page, in the **Select number to assign** list, select the phone number for the user.

4. To select an emergency address, enter name of the city in the box and choose **Search**.

    > [!IMPORTANT]
    > If you are outside the United States, your numbers already have an emergency address, but you can change it now. See [Assign or change an emergency address for a user](/skypeforbusiness/what-are-calling-plans-in-office-365/assign-or-change-an-emergency-address-for-a-user). 
  
5. After you assign both the phone number and emergency address, choose **Save**.


## Step 6: Tell your users about their new phone numbers


We recommend sending mail or using your business's preferred communication method to tell the people about their new phone numbers.

Here's how they can see that phone number in their **Skype for Business** app:

1. Sign in to Skype for Business on your desktop.
    
2. Choose **Settings** > **Tools** > **Options**. 
    
     ![Screen shot of Options on the Tools menu](media/20637117-91d7-4a7e-9f06-7abc634a9211.png)
  
3. Then choose **Phones**. 
    
    ![Screen shot of the Skype for Business phone options](media/0128d667-2bf8-4165-b703-e9b78a15b63c.png)
 
In **Microsoft Teams**, users can see their phone number by clicking **Calls** in the left navigation. The phone number is shown above the dial pad.

![Screen shot of the options available after clicking Calls](media/teams-phone-number.png)

**For more detailed information about all of the steps involved in setting up a Calling Plan, see [Set up Calling Plans](set-up-calling-plans.md).**

## What else do you need to know?
<a name="bkmk_add_addresses"> </a>

- An emergency address is often referred to as a civic address, street address, or a physical address. It is the street or civic address of a place of business for your organization.
    
- Emergency locations aren't validated, only emergency addresses are.
    
- If you want to know more about emergency addresses, see [What are emergency locations, addresses and call routing?](what-are-emergency-locations-addresses-and-call-routing.md)
    
## Do you want to automate assigning phone numbers?
<a name="bkmk_add_addresses"> </a>

If you know Windows PowerShell, you can use the following cmdlets to automate assigning phone numbers to your users. 
  
- [Get-CsOnlineTelephoneNumber](https://technet.microsoft.com/library/mt243818.aspx): Retrieves the telephone numbers from the Business Voice Directory.
    
- [Set-CsOnlineVoiceUser](https://technet.microsoft.com/library/mt243817.aspx): Sets the telephone numbers.
    
To learn more, see [Quick reference: Using Windows PowerShell to do common Skype for Business Online management tasks](https://technet.microsoft.com/library/dn362776%28v=ocs.15%29.aspx).
  
   > [!NOTE]
   > If you need to get more telephone numbers than this, please [contact support for business products - Admin Help](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b).


## Related topics
[Transferring phone numbers common questions](transferring-phone-numbers-common-questions.md)

[Different kinds of phone numbers used for Calling Plans](different-kinds-of-phone-numbers-used-for-calling-plans.md)

[Manage phone numbers for your organization](manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md)

[Emergency calling terms and conditions](emergency-calling-terms-and-conditions.md)

[Skype for Business Online: Emergency Calling disclaimer label](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/emergency-calling/emergency-calling-label-(en-us)-(v.1.0).zip?raw=true)

  
 