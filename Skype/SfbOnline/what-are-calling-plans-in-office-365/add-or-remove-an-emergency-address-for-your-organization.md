---
title: "Add, change, or remove an emergency address for your organization"
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.reviewer: mikedav, roykuntz, jastark
ms.topic: article
ms.assetid: f954c67c-b73c-4473-b6cd-a0fbcd0fd4c9
ms.tgt.pltfrm: cloud
ms.service: skype-for-business-online
search.appverid: MET150
ms.collection: 
- Adm_Skype4B_Online
- Strat_SB_PSTN
audience: Admin
appliesto:
- Skype for Business 
- Microsoft Teams
localization_priority: Normal
f1keywords: None
ms.custom:
- Calling Plans
description: "Learn how to add an emergency address to your Skype for Business account. "
---

# Add, change, or remove an emergency address for your organization

An emergency address must be associated with a phone number, but when this happens can vary between country/regions. For example, in the United States, you need to associate an emergency address when you assign the phone number to the user. In the United Kingdom, you need to associate an emergency address to the phone number when you are getting the phone numbers from Office 365 or transferring phone numbers from your current service provider.
  
No matter which country/region you are in, it's possible to add a location or locations to an emergency address or remove an emergency address. Depending on the number of physical locations in your organization, you can create them for buildings, floors, and offices. See [What are emergency locations, addresses, and call routing?](/microsoftteams/what-are-emergency-locations-addresses-and-call-routing) for some details.
  
To learn how to get a Calling Plan and how much it costs, see [Skype for Business and Microsoft Teams add-on licensing](../skype-for-business-and-microsoft-teams-add-on-licensing/skype-for-business-and-microsoft-teams-add-on-licensing.md).
  
## Add an emergency address

1. Sign in to Office 365 with your work or school account.
    
2. Go to the **Microsoft Teams admin center** > **Legacy portal**.
    
3. In the left navigation, go to **Voice** > **Emergency locations**, and then click the **Add new address** button.
    
    > [!Important]
    > For you to see the **Voice** option in the left navigation in the Skype for Business admin center, you must first buy at least one **Enterprise E5 license**, one **Phone System** add-on license, or one **Audio Conferencing** add-on license.
    
4. In the Action pane, under **New Address**, enter the required information in the boxes.
    
5. After you enter all of the information for the address, click **Validate**.
    
    > [!IMPORTANT]
    > Validating a street or civic address involves making sure that it is legitimate and correctly formatted. It is possible that a partially correct emergency address, such as if you mistyped the name of the city, may still pass validation. Even though it's misspelled and passed validation, the combination of the misspelled name of city along with the other correct parts of the address are enough information to route the call to the appropriate emergency dispatch center. 
    
    > NOTE: In Belgium, France, Germany, Ireland, Netherlands, and Spain it is important to understand that in order to successfully activate a phone number in Office 365 the address setup in the Emergency Location, which will be used to acquire the number, must match the phone number’s area code.
  
    If the address can't be validated, you can send a manual validation request by clicking **Send a validation request** if you are trying to validate a U.S. address, or click **Open a service request to get help with address validation** if you are outside the United States.
    
6. After the address is validated, click **Save**.
    
## Change an emergency address

1. Sign in to Office 365 with your work or school account.
    
2. Go to the **Microsoft Teams admin center** > **Legacy portal**.
    
3. In the left navigation, go to **Voice** > **Emergency locations**, select the address you want to change, and in the Action pane click **Edit**.
    
    > [!IMPORTANT]
    > For you to see the **Voice** option in the left navigation in the Skype for Business admin center, you must first buy at least one **Enterprise E5 license**, one **Phone System** add-on license, or one **Audio Conferencing** add-on license.

4. Make your changes, and then click **Validate**.

5. Click **Save**.

## Remove an emergency address

1. Sign in to Office 365 with your work or school account.
    
2. Go to the **Microsoft Teams admin center** > **Legacy portal**.
    
3. In the left navigation, go to **Voice** > **Emergency locations**, select the address you want to delete, and in the Action pane click **Delete**.
    
    > [!IMPORTANT]
    > For you to see the **Voice** option in the left navigation in the Skype for Business admin center, you must first buy at least one **Enterprise E5 license**, one **Phone System** add-on license, or one **Audio Conferencing** add-on license.

## Troubleshooting

**Number in “Failed” state.**

After acquiring a number from the Office 365 portal, the status changed from **“Provisioning”** to **“Failed”**.

This issue often occurs when a number is added from the portal, using an emergency address pointing to a location which is not matching the phone’s area code.

To obtain more information about the number(s) which wasn't activated properly, run the following Powershell :
 
> [!SYNTAX]
> Get-CsOnlineTelephoneNumber | Where-Object {$_.ActivationState -cnotcontains “Activated”} | fl *

The result, aside other information like region, id and ActivationState, should also contain the CityCode.

**Example**, for a Madrid number, the CityCode returned will be "EMEA-ES-ALL-M_MA".

If indeed a wrong emergency address has been used, make sure you have created a new emergency address corresponding to the number’s area code and assign it to the number.

1. Sign in to Office 365 with your work or school account.
    
2. Go to the **Microsoft Teams admin center** > **Legacy portal**.
    
3. In the left navigation, go to **Voice** > **Phone Numbers**, and then double-click on the number in **“Failed”** State and from the right hand site menu, select the **new Emergency Address**.


Please note that after changing the emergency address, the number’s status will change to **“Assignment Pending”** and it can take up to 24 hours for successfully activating.

## Related topics
[What are emergency locations, addresses, and call routing?](/microsoftteams/what-are-emergency-locations-addresses-and-call-routing)

[Manage phone numbers for your organization](/microsoftteams/manage-phone-numbers-for-your-organization)

[Emergency calling terms and conditions](/microsoftteams/emergency-calling-terms-and-conditions)

[Skype for Business Online: Emergency Calling disclaimer label](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/emergency-calling/emergency-calling-label-(en-us)-(v.1.0).zip?raw=true)

  
 
