---
title: "Set up Calling Plans"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 11/15/2017
ms.audience: Admin
ms.topic: get-started-article
ms.service: skype-for-business-online
localization_priority: Normal
ms.collection: Adm_Skype4B_Online
ms.custom:
- Adm_O365_FullSet
- DianeF_Adm_Simplified
- LIL_Placement
- Strat_SB_PSTN
ms.assetid: 57893158-1acd-44ac-acaf-19f58264a9e0

description: "Learn how in Office 365 Calling Plan (PSTN Calling plan) to buy and set up licenses, get phone numbers, add and assign emergency locations and phone numbers to users, and tell your users about their new phone numbers. "
---

# Set up Calling Plans

Calls to other Skype for Business users are free, but if you want your users to be able to call phones outside of your business, get a Domestic Calling Plan or an International Calling Plan in Office 365. It's easy to set this up for your business. 
  
## Step 1: Buy and assign licenses

1. If the Phone System in Office 365 feature isn't included in your plan, you may need to purchase **Phone System** add-on licenses. After you have **Phone System** licenses, purchase [Calling Plans for Office 365](../skype-for-business-and-microsoft-teams-add-on-licensing/calling-plans-for-office-365.md). See [Skype for Business and Microsoft Teams add-on licensing](../skype-for-business-and-microsoft-teams-add-on-licensing/skype-for-business-and-microsoft-teams-add-on-licensing.md), and buy the licenses and plan. 
    
    > [!TIP]
    > **Phone System** licenses and Calling Plans in Office 365 go together, so to see the option to purchase Calling Plans, you must first have the **Phone System** licenses.
  
2. First assign the licenses, and then assign a Calling Plan to the people in your organization. See [Assign Skype for Business and Microsoft Teams licenses](../skype-for-business-and-microsoft-teams-add-on-licensing/assign-skype-for-business-and-microsoft-teams-licenses.md).
    
## Step 2: Get phone numbers

If you're outside of the United States, the order of steps changes slightly. This is because in some countries/regions, you get an emergency address with the phone number that you get from Office 365 or the phone number you transfer. So, if you are outside of the United States, first do [Step 3: Add emergency addresses and locations for your organization](set-up-calling-plans.md#bkmk_add_addresses), and then do **Step 2: Get phone numbers**.
  
1. If you are using phone numbers from Office 365, follow these steps. **If you need to transfer existing phone numbers from another service provider, follow the steps in [Transfer phone numbers to Office 365](transfer-phone-numbers-to-office-365.md)**.
    
2. Sign in to Office 365 with your work or school account.
    
3. Go to the **Office 365 admin center** > **Admin centers** > **Skype for Business >** **Voice**.

    > [!IMPORTANT] > For you to see the **Voice** option in the left navigation in the Skype for Business admin center, you must first buy at least one **Enterprise E5 license**, one **Phone System** add-on license, or one **Audio Conferencing** add-on license.
   
4. Choose **Phone numbers**. You'll see how many **Phone System** licenses you have, to give you an idea how many phone numbers to request.
    
    > [!TIP]
    > You can acquire more phone numbers than you have licenses for. To determine how many phone numbers you can acquire, take your number of licenses, add 10 percent of the number of licenses, and then add 10. For example, if you have purchased 100 licenses, you can acquire 120 phone numbers. See [How many numbers can I get?](how-many-phone-numbers-can-you-get.md) 
  
5. Choose **Add new number** > **New user numbers**, and on the **Add new user numbers** page, choose the country/region, state/region, and city that you want to select numbers from.
    
6.  Under **Quantity**, enter the number of phone numbers that you want for your organization from this area, and click **Add** to create a reservation.
    
    > [!CAUTION]
    > You have 10 minutes to select your phone numbers. After 10 minutes, the phone numbers are returned to the pool of phone numbers at Office 365. 
  
    In the following picture you can see that phone numbers have been added for two different cities, with 9 minutes left to acquire them. 
    
     ![At the Add user numbers page, specify the area where you want to get the numbers for.](../images/f6dc1ef3-0bf2-4b4f-b32c-ca27e69c5553.png)
  
7. You can choose **Show numbers** to see the full list of phone numbers. This is helpful if you don't want a specific phone number in the list.
    
8. Select the phone numbers you want, and then choose **Acquire numbers**.
    
9. You'll return to the **Voice** page, where you'll see all the numbers you acquired.
    
    ![At the Voice dashboard, you'll see all the phone numbers you acquired.](../images/4a9c681c-13f9-4cdc-a25b-93eb00d06b6c.png)
  
## Step 3: Add emergency addresses and locations for your organization
<a name="bkmk_add_addresses"> </a>

1. On the **Voice** page, choose **Emergency locations** > **Add new address**.
    
2. In the **New address** pane, enter a name for your address, and then complete the remaining boxes.
    
     ![When you enter a new emergency address, the formatting of the street name might cause an error.](../images/dc1c5ef3-0554-4fb7-9ab1-5ea3ac9e5eb5.png)
  
    > [!TIP]
    > For English customers, if the street name is a number, be sure to include "st" or "th" at the end, as shown in the above picture. 
  
3. Choose **Validate**.
    
    If needed, you'll be prompted to make corrections to the address. 
    
    > [!CAUTION]
    > Validating a street or civic address involves making sure that it is legitimate and correctly formatted. It is possible that a partially correct emergency address, such as if you mistyped the name of the city, may still pass validation. Even though it's misspelled and passed validation, the combination of the misspelled name of city along with the other correct parts of the address are enough information to route the call to the appropriate emergency dispatch center. 
  
    > [!TIP]
    > If the address needs to be corrected for emergency response, a green banner will appear notifying you that the address was updated. 
  
4. After the address is validated, choose **Save**.
    
## Step 4: Assign phone numbers and emergency addresses to users
<a name="bkmk_add_addresses"> </a>

> [!TIP]
> If you add more people to your business right before doing this step, it may take **several hours** for them to appear on the **Voice users** page. There's a latency.
  
1. On the **Voice users** page, select the people who you want to assign a phone number and emergency address to.
    
2. In the Action pane, click **Assign number**.
    
3. On the **Assign number** page, in the **Select number to assign** list, select the phone number for the user.
    
4. To select an emergency address, enter name of the city in the box and choose **Search**.
    
    > [!IMPORTANT]
    > If you are outside the United States, your numbers already have an emergency address, but you can change it now. See [Assign or change an emergency address for a user](assign-or-change-an-emergency-address-for-a-user.md). 
  
5. After you assign both the phone number and emergency address, choose **Save**.
    
## Step 5: Tell your users about their new phone numbers
<a name="bkmk_add_addresses"> </a>

We recommend sending mail or using your business's preferred communication method to tell the people about their new phone numbers. 

Here's how they can see that phone number in their **Skype for Business** app:
  
1. Sign in to Skype for Business on your desktop.
    
2. Choose **Settings** > **Tools** > **Options**. 
    
     ![To view your phone number, go to Settings > Tools > Options.](../images/20637117-91d7-4a7e-9f06-7abc634a9211.png)
  
3. Then choose **Phones**. 
    
    ![A user can see their assign number in the Skype for Business app by choosing Settings > Tools > Options > Phone.](../images/0128d667-2bf8-4165-b703-e9b78a15b63c.png)
 
In **Microsoft Teams**, users can see their phone number by clicking **Calls** in the left navigation. The phone number is shown above the dial pad.

![A user can see their number in Microsof Teams by clicking Calls in the let navigation.](../images/MicrosoftTeamsUserPhoneNumber.png)

## What else do you need to know?
<a name="bkmk_add_addresses"> </a>

- An emergency address is often referred to as a civic address, street address, or a physical address. It is the street or civic address of a place of business for your organization.
    
- Emergency locations aren't validated, only emergency addresses are.
    
- If you want to know more about emergency addresses, see [What are emergency locations, addresses and call routing?](what-are-emergency-locations-addresses-and-call-routing.md)
    
## Do you want to automate assigning phone numbers?
<a name="bkmk_add_addresses"> </a>

If you know Windows PowerShell, you can use the following cmdlets to automate assigning phone numbers to your users. 
  
- [Get-CsOnlineTelephoneNumber](https://technet.microsoft.com/en-us/library/mt243818.aspx): Retrieves the telephone numbers from the Business Voice Directory.
    
- [Set-CsOnlineVoiceUser](https://technet.microsoft.com/en-us/library/mt243817.aspx): Sets the telephone numbers.
    
To learn more, see [Quick reference: Using Windows PowerShell to do common Skype for Business Online management tasks](https://technet.microsoft.com/en-us/library/dn362776%28v=ocs.15%29.aspx).
  
[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## See also
<a name="BKMK_comment"> </a>

[Skype for Business Online: Emergency Calling disclaimer label](https://go.microsoft.com/fwlink/?LinkID=692099)
  
[Emergency calling terms and conditions](emergency-calling-terms-and-conditions.md)
