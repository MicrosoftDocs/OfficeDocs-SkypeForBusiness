---
title: Set up dial-in or PSTN conferencing for Skype for Business
ms.assetid: d01954f1-4f37-4cf5-a636-20039e5c59e9
---


# Set up dial-in or PSTN conferencing for Skype for Business

Sometimes people in your organization will need to use a phone to call into a meeting. Skype for Business includes the dial-in conferencing feature for just this situation! People can call into Skype for Business meetings using a phone, instead of using the Skype for Business app on a mobile device or PC. 
  
    
    

You only need to set up dial-in conferencing (also called **PSTN conferencing** ) for people who plan to schedule or lead meetings. Meeting attendees who dial-in don't need any licenses assigned to them or other setup.
## Step 1: Buy and assign licenses
<a name="__top"> </a>

You must be an  [About Office 365 admin roles](http://technet.microsoft.com/library/da585eea-f576-4f55-a1e0-87090b6aaa9d%28Office.14%29.aspx) to perform this step.
  
    
    

1. Find out if dial-in or PSTN conferencing available in your country.  [Countries and regions that are supported for Skype for Business Online PSTN Services](countries-and-regions-that-are-supported-for-skype-for-business-online-pstn-serv.md). 
    
  
2. Learn which licenses you need to buy for dial-in conferencing, and how much they will cost. See  [Skype for Business add-on licensing](skype-for-business-add-on-licensing.md), and buy the licenses. 
    
  
3.  [Assign or remove licenses for Office 365 for business](http://technet.microsoft.com/library/997596b5-4173-4627-b915-36abac6786dc%28Office.14%29.aspx) you purchased to the people in your organization who are going to schedule or lead meetings.
    
  
4. If you purchased dial-in conferencing add-on licenses and PSTN Consumption billing licenses, assign them, too. For instructions, see  [Assign Skype for Business licenses](assign-skype-for-business-licenses.md).
    
  

## Step 2: Decide on your dial-in conferencing provider
<a name="__top"> </a>

A dial-in conferencing provider supplies a  *dial-in conferencing bridge*  . The conferencing bridge sets your dial-in phone numbers, PINs and conference IDs for meetings. Decide whether to use Microsoft or a third-party dial-in provider:
  
    
    

- **Microsoft as your dial-in conferencing provider**: If you want the easiest solution for dial-in conferencing, choose Microsoft as your dial-in conferencing provider.
    
  
- **Third-party as your dial-in conferencing provider**: If you are in a country where Office 365 dial-in conferencing isn't available, the service quality isn't great because of it's location, or you have an existing contract, choose a third-party dial-in conferencing provider. To find a provider, go to ** [Microsoft PinPoint](http://go.microsoft.com/fwlink/?LinkId=797530)**.
    
  

> [!TIP]
> In your organization, you can have some people who use Microsoft as their dial-in conferencing provider, and others who use a third-party provider. But this will be more complicated for you to setup and manage. 
  
    
    

For a detailed comparison between Microsoft as your dial-in provider and a third-party, see  [Compare dial-in conferencing providers](compare-dial-in-conferencing-providers.md). 
  
    
    

## Step 3: Assign the dial-in conferencing provider to people who lead or schedule meetings
<a name="__top"> </a>

Now that you've decided on your dial-in conferencing provider, you need to assign the provider to people in your organization who lead or schedule meetings. Do one of the following: 
  
    
    

-  [Assign Microsoft as the dial-in conferencing provider](assign-microsoft-as-the-dial-in-conferencing-provider.md) .
    
  
- Or  [Assign a third-party as the dial-in conferencing provider](assign-a-third-party-as-the-dial-in-conferencing-provider.md). 
    
  

## Step 4: Set up meeting invitations
<a name="__top"> </a>

The following steps are **optional**, but a lot of admins like to do them:
  
    
    

1.  [Customize meeting invitations](customize-meeting-invitations.md) . The dial-in numbers that are set for the user will be automatically added to the meeting invitations that are sent to attendees. However, you can add your own help and legal links, a text message, and small company graphic.
    
  
2.  [Set the dial-in phone numbers for meeting organizers that are included on invites](set-the-dial-in-phone-numbers-for-meeting-organizers-that-are-included-on-invite.md) . This is the phone number that will show up in the meeting that is scheduled by the user.
    
  
3.  [Set auto attendant languages for a dial-in conferencing](set-auto-attendant-languages-for-a-dial-in-conferencing.md) that the dial-in conferencing auto-attendant uses to greet a caller when they dial into a dial-in conferencing phone number. This step only applies if you're using Microsoft as your dial-in provider.
    
  
4.  [Set the length of the PIN for dial-in meetings](set-the-length-of-the-pin-for-dial-in-meetings.md) .
    
  

## Frequently asked questions
<a name="__top"> </a>

Following are some of the top questions we get from our customers who want to use dial-in conferencing. 
  
    
    

### What are the benefits of dial-in conferencing?

Calling in to meetings is very useful when people are on the road, for example, and can't attend a meeting using the Skype for Business client on their laptop or mobile devices. But there are other reasons why using a phone to attend a Skype for Business meeting can be a better option than using the Skype for Business app on a computer:
  
    
    

- Internet connectivity is limited.
    
  
- A meeting is audio only.
    
  
- The person tried to join a Skype for Business meeting and it failed.
    
  
- The call quality is better if they dial-in.
    
  
- People can join a meeting "hands free" using Bluetooth devices.
    
  
- People find it's easier and more convenient for their situation.
    
  

### Who can attend a dial-in conferencing meeting? And who can I hear?

Anyone who has the dial-in number and conference ID can join a Skype for Business meeting, unless the meeting organizer has locked the meeting.
  
    
    
Whether you're calling in using a phone or your the Skype for Business web app, you'll be able to hear everyone else on the call, and they can hear you. The meeting organizer has the ability to "mute" meeting attendees if they don't want to hear them. 
  
    
    

### Can I add a toll-free number for my dial-in conferencing users?

Yes, toll-free phone numbers (service numbers) are available but only in some countries/regions. To see a list of the numbers that are available, go  [Where can I get toll-free numbers?](http://technet.microsoft.com/library/448bb563-c122-48ce-aab9-a97157a17bd3%28Office.14%29.aspx).
  
    
    

### How many local dial-in numbers are currently supported?

There are local dial-in numbers that are assigned to you when you purchase the licenses for dial-in conferencing. The dial-in numbers will be included in the meeting invite. These local numbers will be only available to your organization. The phone assigned to your organization and that number is shared by the users within that organization that are enabled for dial-in conferencing. So, Skype for Business Online meetings scheduled by User A and another User B will both have the same dial-in number.
  
    
    
Local dial-in numbers, and also in some cases international dial-in numbers from the country where your organization is located, will be included on the meeting invite. If a meeting attendee uses a different number that is include in the invite, it will be a shared phone number.
  
    
    

### How many international dial-in numbers does the Skype for Business dial-in conferencing service support?

For a current list of countries/regions, see  [Phone numbers for dial-in conferencing](phone-numbers-for-dial-in-conferencing.md).
  
    
    

### Can I set up local numbers for dial-in conferencing from additional cities in the country?

If phone numbers for dial-in conferencing aren't available in your area or don't meet the needs of your organization, please send us feedback at  [SkypeFeedback forums](http://www.skypefeedback.com/forums/299910--preview/category/119971-pstn-conferencing).
  
    
    

### What is the maximum length of the dial-in conferencing meetings?

The maximum length of time depends on who is in the meeting and the type of authentication they used to join the meeting.
  
    
    


|**Meeting attendees**|**Meeting end time**|
|:-----|:-----|
|There are users that have joined using a Skype for Business client or have dialed-in to the meeting.  <br/> |The meeting ends if there are no changes to the attendee list after 24 hours.  <br/> |
|All of the users are dialed in to the meeting but someone has used a PIN to enter the meeting.  <br/> |The meeting ends after 24 hours.  <br/> |
|All of the users are dialed in to the meeting but there wasn't anyone that used a PIN to enter the meeting.  <br/> |The meeting ends after 4 hours.  <br/> |
   

### How many total phone participants can I have in my Skype for Business Online meeting?

Dial-in conferencing allows up to 250 phone attendees.
  
    
    
To find out about meeting limits, see  [Skype for Business Online Limits](https://technet.microsoft.com/en-us/library/skype-for-business-online-limits.aspx#bkmk_Meeting_LyncOnlineLimits).
  
    
    

### Why did users start receiving emails with their dial-in conferencing information?

We added a new feature that allows you - the  [Assign admin roles in Office 365 for business](http://technet.microsoft.com/library/eac4d046-1afd-4f1a-85fc-8219c79e1504%28Office.14%29.aspx) - to send and update dial-in conferencing information and PIN in email. To learn more about it, including how to disable it, see [Enable or disable sending emails when dial-in conferencing settings change](enable-or-disable-sending-emails-when-dial-in-conferencing-settings-change.md).
  
    
    

### Can dial-in conferencing be used by the users who are part of an on-premises deployment of Skype for Business Server 2015?

We're not quite there. However, you can continue to use dial-in conferencing that is available in Skype for Business Server 2015 along with a PSTN gateway for your on-premise users. 
  
    
    

### Can a user get a personal conference ID?

Users will be randomly assigned conferencing IDs and can't reserve or set a static conference ID that only they can use. 
  
    
    

### Can I use dial-in conferencing with Skype Meeting Broadcast?

There isn't support currently for users enabled for dial-in conferencing to join a Skype Meeting Broadcast.
  
    
    

### Can a user get operator assistance during a meeting?

No, a user can't get any operator assistance or support by pressing *0 during the meeting. If there are issues with dial-in conferencing, an administrator for an organization can contact  [Contact support for business products - Admin Help](http://technet.microsoft.com/library/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b%28Office.14%29.aspx).
  
    
    

### How does a user access or change their conference ID?

A Skype for Business Online user can find the conference ID that is assigned to them by scheduling a meeting in Outlook and Outlook on the web. Also, users can find the conference ID in the email that will be sent to them after they are set up for dial-in conferencing.
  
    
    

> [!NOTE]
> Users won't be able to reset their conference ID. The conference ID can only be reset by you - the  [Assign admin roles in Office 365 for business](http://technet.microsoft.com/library/eac4d046-1afd-4f1a-85fc-8219c79e1504%28Office.14%29.aspx) - for the organization.
  
    
    

We are working on a solution that will let the user will be able access and reset a conference ID without help from an organization's admin.
  
    
    

### How does a user access or change his/her PIN?

The Skype for Business Online user can find the PIN in an email that will be sent to them once they are set up for dial-in conferencing.
  
    
    

> [!NOTE]
> A Skype for Business Online user won't be able to reset their PIN. The PIN can only be reset by you, the admin. When a PIN is reset an email is sent to the user. 
  
    
    

We are working on a solution that will let the user will be able to access and reset a PIN without help from a organization's administrator.
  
    
    

### What in-meeting dial-pad commands are supported?


- *6 (Mute/unmute themselves)
    
  
- *1 (Plays the descriptions of dial-pad commands that are available.) 
    
  

### Can attendees dial out to international phone numbers when they are in a Skype for Business Online meeting?

Yes, attendees can dial-out internationally and invite other callers into a Skype for Business Online meeting. See  [Dialing out from a meeting so other people can join it](dialing-out-from-a-meeting-so-other-people-can-join-it.md).
  
    
    

### How does a Skype for Business Online user schedule a Skype for Business Online meeting with dial-in meeting details?

When a user is assigned a **Skype for Business PSTN Conferencing** license and the user creates a new Skype for Business meeting in Outlook or Outlook on the web, the dial-in phone numbers and conferencing IDs are added to the meeting invite automatically.
  
    
    

### How does a user schedule and start a meeting when all attendees will be using a phone to dial-in?

When a user is assigned a **Skype for Business PSTN Conferencing** license, the user is assigned what is called a reservation-less conference ID. This conference ID can be shared along with the conference access phone numbers with meeting attendees without the user having to schedule a meeting.
  
    
    
Here is a table that has the scenarios when the organizer and all of the attendees dial in to a meeting:
  
    
    


|**User's setting**|**Organizer steps**|**Attendee steps**|
|:-----|:-----|:-----|
|Don't allow anonymous users to start a meeting  <br/> | Dial the dial-in conferencing phone number. <br/>  Enter the conference ID. <br/>  Enter the PIN for the meeting. <br/> | Dial the dial-in conferencing phone number. <br/>  Enter the conference ID. <br/>  If the meeting organizer hasn't joined the meeting yet, the attendee will listen to music in the lobby until the organizer joins the meeting. <br/> |
|Allow an anonymous user to start a meeting  <br/> | Dial the dial-in conferencing phone number. <br/>  Enter the conference ID. <br/> | Dial the dial-in conferencing phone number. <br/>  Enter the conference ID. <br/>  If the attendee joins the meeting before the organizer, each attendee can start the meeting. <br/> |
   

## 
<a name="__top"> </a>


> [!NOTE]
> This feature is not yet available to customers using Office 365 operated by 21Vianet in China. To learn more, see  [Learn about Office 365 operated by 21Vianet](http://technet.microsoft.com/library/A8AB5061-3346-4DA0-BB7C-5260822B53AE%28Office.14%29.aspx). 
  
    
    


## See also
<a name="__top"> </a>


#### Other Resources


  
    
    
 [Set up Skype for Business Online](set-up-skype-for-business-online.md)
  
    
    
 [Phone numbers for dial-in conferencing](phone-numbers-for-dial-in-conferencing.md)
  
    
    
 [Set options for online meetings and conference calls](http://technet.microsoft.com/library/DCD1CA39-0C1F-466C-9573-F04138FEF5E2%28Office.14%29.aspx)
