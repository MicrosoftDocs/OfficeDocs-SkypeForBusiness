---
title: "Dial-in conferencing in Office 365"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 5/26/2016
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Adm_Skype4B_Online
ms.assetid: 90d51188-0ba9-4dc4-bd6c-ae11dd1f8551
description: "Learn the steps to set up dial-in or Public Switched Telephone Network conferencing for Skype for Business, including buynig and assigning licenses, getting a conferencing provider, and setting up meeting invitations, as well as frequently asked questions.  "
---

# Dial-in conferencing in Office 365

Sometimes people in your organization will need to use a phone to call into a meeting. Skype for Business includes the dial-in conferencing feature for just this situation! People can call into Skype for Business meetings using a phone, instead of using the Skype for Business app on a mobile device or PC. 
  
It's important to remember, when people call into a meeting using a phone, they will only get audio, no video. If they want to get instant messages (IM)s during the meeting, see shared desktops, or get files that are being shared in the meeting, they will need to join the meeting using a mobile device or PC that has the Skype for Business app installed on it. [Install Skype for Business](http://technet.microsoft.com/library/8a0d4da8-9d58-44f9-9759-5c8f340cb3fb%28Office.14%29.aspx).
  
## How to set up dial-in conferencing

As the **[Assign admin roles in Office 365 for business](http://technet.microsoft.com/library/eac4d046-1afd-4f1a-85fc-8219c79e1504%28Office.14%29.aspx)** for your organization, you only need to set up dial-in conferencing for people who plan to schedule or lead meetings.
  
Unless the meeting organizer has locked the meeting, anyone who has the dial-in number and conference ID can join the meeting. You don't need to do anything to set up meeting attendees. 
  
Follow these steps to set up dial-in conferencing for your organization. 
  
### Step 1: Buy and assign licenses

1. Find out if dial-in conferencing available in your country. [Is PSTN Conferencing with phone numbers available in my country or region?](http://technet.microsoft.com/library/1096d81e-7e14-488c-95d8-b8322e39c059%28Office.14%29.aspx)
    
2. To learn which licenses you need to buy for dial-in conferencing, and how much they will cost, see [Skype for Business and Microsoft Teams add-on licensing](../skype-for-business-and-microsoft-teams-add-on-licensing/skype-for-business-and-microsoft-teams-add-on-licensing.md). 
    
3. [Assign or remove licenses for Office 365 for business](http://technet.microsoft.com/library/997596b5-4173-4627-b915-36abac6786dc%28Office.14%29.aspx) you purchased to the people in your organization who are going to schedule or lead meetings.
    
4. If you purchased a [Assign a dial-in or PSTN conferencing license](http://technet.microsoft.com/library/a88b3302-6842-44dd-bc0a-ce50122bf826%28Office.14%29.aspx). 
    
### Step 2: Choose your dial-in conferencing provider

A dial-in conferencing provider does the following:
  
- Provides a  *dial-in conferencing bridge*  . The conferencing bridge will set dial-in phone numbers, PINs and conference IDs for meetings.
    
- Gives toll, toll-free and international phone numbers that people will dial into. The phone numbers are then included in the meeting invite.
    
- Sets the language that people will hear when they dial into a meeting.
    
- Creates meeting conference IDs that are used when people join a meeting.
    
- Gives you organizer PINs to start meetings over the phone.
    
 **Compare dial-in conferencing providers**
  
If you want the easiest solution for dial-in conferencing, choose Microsoft as your dial-in conferencing provider. 
  
If you are in a country where Office 365 dial-in conferencing isn't available, the service quality isn't great because of it's location, or you have an existing contract with a third-party audio conferencing provider (ACP), you should continue to use a third-party dial-in conferencing provider. 
  
Use the following table to compare Microsoft to other dial-in conferencing providers:
  
||**Microsoft (Office 365)**|**Third-party ACP**|
|:-----|:-----|:-----|
|Provider set up  <br/> |Easy to setup. Most settings are automatic.  <br/> |Hard to set up. Requires manual steps.  <br/> |
|Licensing  <br/> |Additional license. See, [Assign a dial-in or PSTN conferencing license](http://technet.microsoft.com/library/a88b3302-6842-44dd-bc0a-ce50122bf826%28Office.14%29.aspx).  <br/> |No license but you still pay per user.  <br/> |
|Management  <br/> |Integrated into the Office 365 admin center.  <br/> |Manual management with third-party.  <br/> |
|User set up  <br/> |Easy  <br/> |Hard.  <br/> |
|Billing  <br/> |Through Office 365.  <br/> | Additional through the third-party ACP. <br/> |
|Dial-in conferencing bridge assignment  <br/> |Automatic  <br/> |Requires a manual entry of conference bridge for each user.  <br/> |
|Conference ID management  <br/> |Automatic  <br/> |Manual  <br/> |
|Reset meeting conference ID  <br/> |Yes. See [Reset a conference ID for a user](../audio-conferencing-in-office-365/reset-a-conference-id-for-a-user.md).  <br/> |Yes but you have to input it manually.  <br/> |
|Toll free telephone numbers  <br/> |Available in a future release.  <br/> |Yes  <br/> |
|Toll domestic telephone numbers  <br/> |Yes  <br/> |Yes  <br/> |
|International toll telephone numbers  <br/> |Yes  <br/> |Yes  <br/> |
|International toll-free telephone numbers  <br/> |Available in a future release.  <br/> |Yes  <br/> |
|Transfer existing phone numbers  <br/> |Yes  <br/> |No  <br/> |
|Dial-out / Call-me - Domestic  <br/> |Yes  <br/> |Yes  <br/> |
|Dial-out / Call-me - International  <br/> |Yes, but only available in some countries/regions. See [Dialing out from a meeting so other people can join it](../audio-conferencing-in-office-365/dialing-out-from-a-meeting-so-other-people-can-join-it.md) for a list of supported countries/regions. <br/> |Yes  <br/> |
|Meeting organizer can authenticate via a PIN  <br/> |Yes  <br/> |No  <br/> |
|Any user in the organization can authentication via a PIN  <br/> |No  <br/> |No  <br/> |
|Meeting invitation page with default dial-in phone numbers.  <br/> |Yes  <br/> |Yes  <br/> |
|Additional dial-in page with complete list of supported dial-in phone numbers  <br/> |Yes  <br/> |Yes  <br/> |
|Option for starting a third-party meeting without a PIN  <br/> |Yes  <br/> |No  <br/> |
|Multiple language support  <br/> |Yes. See [Audio Conferencing supported languages](../audio-conferencing-in-office-365/audio-conferencing-supported-languages.md).  <br/> |Yes  <br/> |
|Manage languages for meeting auto attendant.  <br/> |Yes  <br/> |Yes  <br/> |
|Multiple country support  <br/> |Yes. See [Phone numbers for Audio Conferencing](../audio-conferencing-in-office-365/phone-numbers-for-audio-conferencing.md).  <br/> |Yes  <br/> |
|Users listen to music on hold if meeting hasn't started or if the meeting has been locked  <br/> |Yes  <br/> |No  <br/> |
|Set international dial-in number as default dial-in number (that shows in the meeting invite) for a user  <br/> |Yes  <br/> |No  <br/> |
|Integrated experience for Skype for Business Online user to reset meeting conference ID and PIN  <br/> |Available in a future release.  <br/> |No  <br/> |
|Support for private meetings with dynamic meeting conference IDs  <br/> |Available in a future release.  <br/> |No  <br/> |
   
> [!NOTE]
> In your organization, you can have people that are using Microsoft and a third-party ACP both as the dial-in conferencing providers. But this will make it harder for you to setup and manage dial-in conferencing. 
  
> [!NOTE]
>  Some of the meeting participant settings in Outlook and the Skype for Business client **can't be used with Microsoft dial-in conferencing**. Meetings can only be locked when the **These people don't have to wait in the lobby** option is set to:> **Only me, the meeting organizer** option is selected in the Outlook meeting invite.> **The meeting organizer** option is selected in the Skype for Business client meeting.
  
### Step 3: Set up dial-in conferencing for people who lead or schedule meetings

 **Use Microsoft as your dial-in conferencing provider**
  
1. [Assign Microsoft as the audio conferencing provider](../audio-conferencing-in-office-365/assign-microsoft-as-the-audio-conferencing-provider.md) .
    
2. Use the **Skype for Business admin center** > **Dial-in conferencing** > **Dial-in users** to view the user or users that were enabled to verify that they appear in the list of users and are using Microsoft as the dial-in conferencing provider.
    
3. [Customize meeting invitations](../set-up-skype-for-business-online/customize-meeting-invitations.md) if you want. The dial-in numbers that are set for the user will be automatically added to the meeting invitations that are sent to attendees.
    
4. [Set the Audio Conferencing phone numbers for meeting organizers that are included on invites](../audio-conferencing-in-office-365/set-the-audio-conferencing-phone-numbers-for-meeting-organizers-that-are-include.md) if you need to. This is phone number that will show up in the meeting that is scheduled by the user.
    
 **Use a third-party as your dial-in conferencing provider**
  
> [!NOTE]
> You can set up multiple users with import and export. You can also set up individual users, or remove dial-in conferencing settings. 
  
1. Contact a third-party audio conferencing provider (ACP) and purchase the service from them.
    
2. In the **Skype for Business admin center**, under **Dial-in conferencing**, use the **Export** wizard to export the users in your organization that will be organizing meetings with dial-in access. See[See a list of users that are enabled for Audio Conferencing](../audio-conferencing-in-office-365/see-a-list-of-users-that-are-enabled-for-audio-conferencing.md).
    
3. Send the file that you export to the third-party audio conferencing provider.
    
4. After you receive the file back, use the **Import** wizard to import the users and the dial-in meetings conference IDs.
    
5. [Customize meeting invitations](../set-up-skype-for-business-online/customize-meeting-invitations.md) if you want. The dial-in numbers that are set for the user will be automatically added to the meeting invitations that are sent to attendees.
    
    You can find out more about using an ACP, see:
    
  - [Assign a third-party as the audio conferencing provider](../audio-conferencing-in-office-365/assign-a-third-party-as-the-audio-conferencing-provider.md)
    
  - [Change the dial-in conferencing provider for users](http://technet.microsoft.com/library/9b74f053-4d23-485f-9232-3d30370a8c6e%28Office.14%29.aspx)
    
## Frequently asked questions

Following are some of the top questions we get from our customers who want to use dial-in conferencing. 
  
### What are the benefits of dial-in conferencing?

Calling in to meetings is very useful when people are on the road, for example, and can't attend a meeting using the Skype for Business client on their laptop or mobile devices. But there are other reasons why using a phone to attend a Skype for Business meeting can be a better option than using the Skype for Business app on a computer:
  
- Internet connectivity is limited.
    
- A meeting is audio only.
    
- The person tried to join a Skype for Business meeting and it failed.
    
- The call quality is better if they dial-in.
    
- People can join a meeting "hands free" using Bluetooth devices.
    
- People find it's easier and more convenient for there situation.
    
### Why did users start receiving emails with their dial-in conferencing information?

A new feature that allows administrators in an organization to send and update their dial-in conferencing information and PIN in email has been added. To learn more about it, including how to disable it, see [Enable or disable sending emails when Audio Conferencing settings change](../audio-conferencing-in-office-365/enable-or-disable-sending-emails-when-audio-conferencing-settings-change.md).
  
### How does the Skype for Business Online dial-in conferencing service compare with a third-party Audio Conferencing Provider (ACP)?

Dial-in conferencing in Office 365 provides direct dial-in access for Skype for Business Online meetings without the requirement of having a third-party audio conferencing provider (ACP). Here are a few of the major advantages to using dial-in conferencing in Office 365:
  
- **Sign up** Sign up for dial-in conferencing using Office 365 allows your organization to set up their dial-in or audio conferencing set up without a separate sign up process that is required when a third-party ACP is used. Dial-in conferencing in Office 365 simply requires you to create a user, purchase the **Skype for Business PSTN Conferencing** license, and then assign the correct license to the user.
    
- **Billing and support** With dial-in conferencing in Office 365, you are given a single bill for all of your Office 365 services and will no longer get another bill if you were using a third-party ACP. Also, if you have a need for contacting support for help in addressing issues or troubleshooting, you contact the same number for Microsoft support.
    
- **Management** All of the management tasks for dial-in conferencing including phone numbers, conferencing IDs and meeting PINs are all done using the Skype for Business admin center. There is no need to use any other tools that were required by an ACP.
    
> [!NOTE]
> You can find a table that shows a complete comparison between dial-in conferencing in Office 365 and using a third-party ACP by seeing [Dial-in conferencing in Office 365](dial-in-conferencing-in-office-365.md). 
  
### Can dial-in conferencing be used by the users who are part of an on-premises deployment of Skype for Business Server 2015?

We're not quite there. We are actively working to enable on-premises users to use dial-in conferencing in Skype for Business Online. However, you can continue to use dial-in conferencing that is available in Skype for Business Server 2015 along with a PSTN gateway for your on-premise users. 
  
### Which countries can use dial-in conferencing in Office 365?

For the current list of countries where dial-in conferencing is offered, see [Is PSTN Conferencing with phone numbers available in my country or region?](http://technet.microsoft.com/library/1096d81e-7e14-488c-95d8-b8322e39c059%28Office.14%29.aspx).
  
### How many local dial-in numbers are currently supported?

There are local dial-in numbers that are assigned to you when you purchase the licenses for dial-in conferencing. The dial-in numbers will be included in the meeting invite. These local numbers will be only available to your organization. The phone assigned to your organization and that number is shared by the users within that organization that are enabled for dial-in conferencing. So, Skype for Business Online meetings scheduled by User A and another User B will both have the same dial-in number.
  
Local dial-in numbers, and also in some cases international dial-in numbers from the country where your organization is located, will be included on the meeting invite. If a meeting attendee uses a different number that is include in the invite, it will be a shared phone number.
  
### How many international dial-in numbers does the Skype for Business dial-in conferencing service support?

For a current list of countries/regions, see [Phone numbers for Audio Conferencing](../audio-conferencing-in-office-365/phone-numbers-for-audio-conferencing.md).
  
### Can I set up local numbers for dial-in conferencing from additional cities in the country?

If phone numbers for dial-in conferencing aren't available in your area or don't meet the needs of your organization, please send us feedback at [SkypeFeedback forums](http://www.skypefeedback.com/forums/299910--preview/category/119971-pstn-conferencing).
  
### Can I add a toll-free number for my dial-in conferencing users?

Currently, toll-free numbers aren't available, only local phone numbers are. It would be great to hear from you if you are interested in us adding tool-free phone numbers for dial-in conferencing. Please give us some feedback at [SkypeFeedback forums](http://www.skypefeedback.com/forums/299910--preview/category/119971-pstn-conferencing).
  
### How many total phone participants can I have in my Skype for Business Online meeting?

Dial-in conferencing allows up to 250 phone attendees.
  
To find out about meeting limits, see [Skype for Business Online Limits](https://technet.microsoft.com/en-us/library/skype-for-business-online-limits.aspx#bkmk_Meeting_LyncOnlineLimits).
  
### What is the maximum length of the dial-in conferencing meetings?

The maximum length of time depends on who is in the meeting and the type of authentication they used to join the meeting.
  
|**Meeting attendees**|**Meeting end time**|
|:-----|:-----|
|There are users that have joined using a Skype for Business client or have dialed-in to the meeting.  <br/> |The meeting ends if there are no changes to the attendee list after 24 hours.  <br/> |
|All of the users are dialed in to the meeting but someone has used a PIN to enter the meeting.  <br/> |The meeting ends after 24 hours.  <br/> |
|All of the users are dialed in to the meeting but there wasn't anyone that used a PIN to enter the meeting.  <br/> |The meeting ends after 4 hours.  <br/> |
   
### Can a user dial out to international phone numbers when they are in a Skype for Business Online meeting?

Yes, attendees can dial-out internationally and invite other callers into a Skype for Business Online meeting. See [Dialing out from a meeting so other people can join it](../audio-conferencing-in-office-365/dialing-out-from-a-meeting-so-other-people-can-join-it.md).
  
### How does a Skype for Business Online user schedule a Skype for Business Online meeting with dial-in meeting details?

When a user is assigned a **Skype for Business PSTN Conferencing** license and the user creates a new Skype for Business meeting in Outlook or Outlook on the web, the dial-in phone numbers and conferencing IDs are added to the meeting invite.
  
### How does a user schedule and start a meeting when all attendees will be using a phone to dial-in?

When a user is assigned a **Skype for Business PSTN Conferencing** license, the user is assigned what is called a reservation-less conference ID. This conference ID can be shared along with the conference access phone numbers with meeting attendees without the user having to schedule a meeting.
  
Here is a table that has the scenarios when the organizer and all of the attendees dial in to a meeting:
  
|**User's setting**|**Organizer steps**|**Attendee steps**|
|:-----|:-----|:-----|
|Don't allow anonymous users to start a meeting  <br/> | Dial the dial-in conferencing phone number. <br/>  Enter the conference ID. <br/>  Enter the PIN for the meeting. <br/> | Dial the dial-in conferencing phone number. <br/>  Enter the conference ID. <br/>  If the meeting organizer hasn't joined the meeting yet, the attendee will listen to music in the lobby until the organizer joins the meeting. <br/> |
|Allow an anonymous user to start a meeting  <br/> | Dial the dial-in conferencing phone number. <br/>  Enter the conference ID. <br/> | Dial the dial-in conferencing phone number. <br/>  Enter the conference ID. <br/>  If the attendee joins the meeting before the organizer, each attendee can start the meeting. <br/> |
   
### What is a dial-in conferencing PIN?

A PIN is a numeric password that is similar to an ATM PIN, that is assigned to each user who is enabled for dial-in conferencing. The PIN is used to authenticate the meeting organizer so they can start a meeting when all attendees are dialing in. If the meeting isn't started by a user that has entered the PIN, any attendees who dial in to that conference call will listen to music in a virtual lobby.
  
### How does a user access or change their conference ID?

A Skype for Business Online user can find the conference ID that is assigned to them by scheduling a meeting in Outlook and Outlook on the web. Also, users can find the conference ID in the email that will be sent to them after they are enabled for dial-in conferencing.
  
> [!NOTE]
> Users won't be able to reset their conference ID. The conference ID can only be reset by an administrator for the organization. 
  
We are working on a solution that will let the user will be able access and reset a conference ID without help from an organization's admin.
  
### How does a user access or change his/her PIN?

The Skype for Business Online user can find the PIN in an email that will be sent to them once they are enabled for dial-in conferencing.
  
> [!NOTE]
> A Skype for Business Online user won't be able to reset their PIN. The PIN can only be reset by an organization's administrator. When a PIN is reset an email is sent to the user. 
  
We are working on a solution that will let the user will be able to access and reset a PIN without help from a organization's administrator.
  
### Can a user get a personal conference ID?

Users will be randomly assigned conferencing IDs and can't reserve or set a static conference ID that only they can use. 
  
### What in-meeting dial-pad commands are supported?

- *6 (Mute/unmute themselves)
    
- *1 (Plays the descriptions of dial-pad commands that are available.) 
    
### Can I use dial-in conferencing with Skype Meeting Broadcast?

There isn't support currently for users enabled for dial-in conferencing to join a Skype Meeting Broadcast.
  
### Can a user get operator assistance during a meeting?

No, a user can't get any operator assistance or support by pressing *0 during the meeting. If there are issues with dial-in conferencing, an administrator for an organization can contact Microsoft support in Office 365.
  
## See also

#### Other Resources

[Audio Conferencing troubleshooting and known issues](../audio-conferencing-in-office-365/audio-conferencing-troubleshooting-and-known-issues.md)
  
[Set up Skype for Business Online](../set-up-skype-for-business-online/set-up-skype-for-business-online.md)

