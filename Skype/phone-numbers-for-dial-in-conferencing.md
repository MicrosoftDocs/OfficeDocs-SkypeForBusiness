---
title: Phone numbers for dial-in conferencing
ms.prod: OFFICE365
ms.assetid: 95a08f84-04e5-4f72-88a8-d6472a7c89d7
---


# Phone numbers for dial-in conferencing

When you are setting up dial-in conferencing in Skype for Business Online, dial-in phone numbers are automatically assigned to your organization. You can see the phone numbers that are assigned to your dial-in conferencing bridge by going to the **Skype for Business admin center** > **Dial-in conferencing** > **Microsoft bridge**. See  [See a list of dial-in conferencing dial-in numbers](see-a-list-of-dial-in-conferencing-dial-in-numbers.md).
  
    
    


## PSTN Conferencing dial-in geographical coverage

For a complete list of all the countries/regions and cities where the PSTN Conferencing is available, see  [Is PSTN Conferencing with phone numbers available in my country or region?](http://technet.microsoft.com/library/1096d81e-7e14-488c-95d8-b8322e39c059%28Office.14%29.aspx).
  
    
    

## Dial-in phone numbers in a meeting invite

When a Skype for Business Online user schedules a meeting in Outlook or Outlook Web App, the default dial-in conferencing number that is set for the user is included in the meeting invite. If you want to select a different default number for one or more users, you can change that by going to the **Skype for Business admin center** > **Dial-in conferencing** > **Dial-in users**. See,  [Set the dial-in phone numbers for meeting organizers that are included on invites](set-the-dial-in-phone-numbers-for-meeting-organizers-that-are-included-on-invite.md).
  
    
    
Other dial-in numbers can be seen by clicking on **Find a local number** link in the meeting invite.
  
    
    

## Dial-in phone numbers set on a dial-in conferencing bridge

There are two types of dial-in conferencing phone numbers that can be assigned to your conferencing bridge: **Shared** and **Dedicated**. Both types of these numbers can be used by any caller to join dial-in meetings that are being held in your organization.
  
    
    
 **Dedicated phone numbers** are those phone numbers that are only available to users within your organization. You can change the languages that are used when someone calls in to one of these numbers.
  
    
    
 **Shared phone numbers** are those phone numbers that can be shared with other Office 365 organizations. You can't change the languages that are used when someone calls in to one of these numbers.
  
    
    
While the default dial-in conferencing number that is assigned to an organizer is only included in the meeting invite, a caller can use any of the phone numbers that are assigned to your conferencing bridge to join a meeting. The list of phone numbers that can be used to join a meeting is available using the **Find a local number** link that is included on every meeting invite.
  
    
    

## Automatically assigned dial-in conferencing phone numbers

Shared dial-in conferencing phone numbers are automatically assigned to organizations when they're enabled for dial-in conferencing. When the phone numbers are assigned, a phone number is assigned as the default phone number of the conferencing bridge. The phone number assigned as the default number of the bridge will be one from the country/region of the organization.
  
    
    

> [!NOTE]
> The country or region location of your organization can be found by signing in to the Office 365 admin center > and looking under **Company Profile**. 
  
    
    


> [!CAUTION]
> Due to limited availability of toll phone numbers in Venezuela, Indonesia and United Arab Emirates (UAE), organizations from these countries/regions won't have a dial-in conferencing toll number automatically assigned to them. Toll-free numbers from these locations are available depending on available inventory. 
  
    
    

Dedicated dial-in conferencing phone numbers are service numbers that you can get and then assign to the your organization. Service numbers can found by using the Skype for Business admin center. For details, see  [Getting Skype for Business service phone numbers](getting-skype-for-business-service-phone-numbers.md).
  
    
    
To see a list of those countries/regions that have phone number automatically assigned to organizations see  [Countries and regions that are supported for Skype for Business Online PSTN Services](countries-and-regions-that-are-supported-for-skype-for-business-online-pstn-serv.md).
  
    
    

## What else should you know?


- To see the list of supported languages for dial-in conferencing, see  [Dial-in conferencing supported languages](dial-in-conferencing-supported-languages.md).
    
  
- You can use the  [Get-CsOnlineDialInConferencingServiceNumber](https://go.microsoft.com/fwlink/?LinkId=617691) cmdlet to see the dedicated phone numbers for dial-in conferencing for you organization.
    
  
- You can use the  [Get-CsOnlineDialInConferencingLanguagesSupported](https://go.microsoft.com/fwlink/?LinkId=617684) cmdlet to see the languages that can be set on a dedicated dial-in phone number.
    
  
- You can set up to 4 languages for each dial-in conferencing phone number - one primary and three secondary. And you can also set languages on a dedicated dial-in conferencing phone number.
    
  
- To set the dial-in phone number for a user, see  [Set the dial-in phone numbers for meeting organizers that are included on invites](set-the-dial-in-phone-numbers-for-meeting-organizers-that-are-included-on-invite.md)
    
  

## See also


#### Other Resources


  
    
    
 [Dial-in conferencing in Office 365](http://technet.microsoft.com/library/90d51188-0ba9-4dc4-bd6c-ae11dd1f8551%28Office.14%29.aspx)
