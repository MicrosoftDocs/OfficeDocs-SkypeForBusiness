---
title: "Phone numbers for Audio Conferencing"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 11/21/2017
ms.audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
ms.collection: Adm_Skype4B_Online
ms.custom:
- Adm_O365_FullSet
- LIL_Placement
- Strat_SB_PSTN
ms.assetid: 95a08f84-04e5-4f72-88a8-d6472a7c89d7

description: "Learn what countries and regions have dial-in conferencing numbers, and how they are automatically assigned."
---

# Phone numbers for Audio Conferencing

When you are setting up ** Audio Conferencing** for Skype for Business and Microsoft Teams, dial-in phone numbers are automatically assigned to your organization. You can see the phone numbers that are assigned to your audio conferencing bridge by going to the **Skype for Business admin center** > **Audio conferencing** > **Microsoft bridge**. See [See a list of Audio Conferencing numbers](see-a-list-of-audio-conferencing-numbers.md).
  
> [!NOTE]
> There isn't a resource that contains a listing of all of the dial-in numbers for Audio Conferencing. If you are looking to see if there are dial-in phone numbers available in your area or country/region, use the **Skype for Business admin center** > **Voice** > **Phone Numbers**, click **Add** then **New Service Numbers**. Use the lists for **Country/Region**, **State/Region** and **City** to filter your search.> Also, if you are looking for toll free service numbers, select **Toll-Free** from the **State/Region** list.
  
## Audio Conferencing coverage and pricing

For a complete list of all the countries/regions and cities where Audio Conferencing is available, see [Is PSTN Conferencing with phone numbers available in my country or region?](http://technet.microsoft.com/library/1096d81e-7e14-488c-95d8-b8322e39c059%28Office.14%29.aspx).
  
[Pricing for Audio Conferencing](https://products.office.com/en-us/skype-for-business/audio-conferencing#Requirements)
  
## Dial-in phone numbers in a meeting invite

When a Skype for Business Online or Microsoft Teams user schedules a meeting in Outlook or Outlook Web App, the default audio conferencing number that is set for the user is included in the meeting invite. If you want to select a different default number for one or more users, you can change that by going to the **Skype for Business admin center** > **Audio conferencing** > **Users**. See [Set the Audio Conferencing phone numbers for meeting organizers that are included on invites](set-the-audio-conferencing-phone-numbers-for-meeting-organizers-that-are-include.md).
  
Other dial-in numbers can be seen by clicking on **Find a local number** link in the meeting invite.
  
## Dial-in phone numbers set on an audio conferencing bridge

There are two types of audio conferencing phone numbers that can be assigned to your conferencing bridge: **Shared** and **Dedicated**. Both types of these numbers can be used by any caller to join audio meetings that are being held in your organization.
  
 **Dedicated phone numbers** are those phone numbers that are only available to users within your organization. You can change the languages that are used when someone calls in to one of these numbers.
  
 **Shared phone numbers** are those phone numbers that can be shared with other Office 365 organizations. You can't change the languages that are used when someone calls in to one of these numbers.
  
While the default audio conferencing number that is assigned to an organizer is only included in the meeting invite, a caller can use any of the phone numbers that are assigned to your conferencing bridge to join a meeting. The list of phone numbers that can be used to join a meeting is available using the **Find a local number** link that is included on every meeting invite.
  
## Automatically assigned audio conferencing phone numbers

Shared audio conferencing phone numbers are automatically assigned to organizations when they're enabled for audio conferencing. When the phone numbers are assigned, a phone number is assigned as the default phone number of the conferencing bridge. The phone number assigned as the default number of the bridge will be one from the country/region of the organization.
  
> [!NOTE]
> The country or region location of your organization can be found by signing in to the **Office 365 admin center** and looking under **Organization Profile**. 
  
> [!CAUTION]
> Due to limited availability of toll phone numbers in Venezuela, Indonesia, and United Arab Emirates (UAE), organizations from these countries/regions won't have an Audio Conferencing toll number automatically assigned to them. Toll-free numbers from these locations are available depending on available inventory. 
  
Dedicated audio conferencing phone numbers are service numbers that you can get and then assign to your organization. Service numbers can be found by using the **Skype for Business admin center**. For details, see [Getting service phone numbers for Skype for Business and Microsoft Teams](../what-is-phone-system-in-office-365/getting-service-phone-numbers-for-skype-for-business-and-microsoft-teams.md).
  
To see a list of those countries/regions that have phone numbers automatically assigned to organizations, see [Countries and region availability for Audio Conferencing and Calling Plans](http://technet.microsoft.com/library/6ba72f37-d303-4795-aa8f-7e1845078ed7%28Office.14%29.aspx).
  
## What else should you know?

- To see the list of supported languages for audio conferencing, see [Audio Conferencing supported languages](audio-conferencing-supported-languages.md).
    
- You can use the [Get-CsOnlineDialInConferencingServiceNumber](https://go.microsoft.com/fwlink/?LinkId=617691) cmdlet to see the dedicated phone numbers for audio conferencing for you organization.
    
- You can use the [Get-CsOnlineDialInConferencingLanguagesSupported](https://go.microsoft.com/fwlink/?LinkId=617684) cmdlet to see the languages that can be set on a dedicated dial-in phone number.
    
- You can set up to 4 languages for each audio conferencing phone number - one primary and three secondary. And you can also set languages on a dedicated audio conferencing phone number.
    
- To set the dial-in phone number for a user, see [Set the Audio Conferencing phone numbers for meeting organizers that are included on invites](set-the-audio-conferencing-phone-numbers-for-meeting-organizers-that-are-include.md).
    
||
|:-----|
|![The short icon for LinkedIn Learning.](../images/7e5cb7c8-dc66-4c9a-a16d-a30f10a970bd.png) **New to Office 365?**         Discover free video courses for **Office 365 admins and IT pros**, brought to you by LinkedIn Learning. |
   
## See also

#### Other Resources

[Dial-in conferencing in Office 365](http://technet.microsoft.com/library/90d51188-0ba9-4dc4-bd6c-ae11dd1f8551%28Office.14%29.aspx)

