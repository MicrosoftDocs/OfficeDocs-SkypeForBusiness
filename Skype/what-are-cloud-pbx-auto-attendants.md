---
title: What are Cloud PBX auto attendants?
ms.assetid: ab9f05a2-22cb-4692-a585-27f82d1b37c7
---


# What are Cloud PBX auto attendants?

Skype for Business Cloud PBX auto attendants can be used to create a menu system for your organization that lets external and internal callers move through menu system to locate and place or transfer calls to company users or departments in your organization.
  
    
    

When people call, they are presented with a series of voice prompts that help them place a call to a user or locate someone in your organization and then place a call to that user. An auto attendant is a series of voice prompts or and audio file that callers hear instead of a human operator when they call into an organization. An auto attendant lets callers move through the menu system, place calls, or locate users by using a phone keypad (DTMF) or voice inputs using speech recognition. To set up an auto attendant for Cloud PBX, go  [Set up a Cloud PBX auto attendant](set-up-a-cloud-pbx-auto-attendant.md).
A Cloud PBX auto attendant has the following features:
  
    
    


- It can provide corporate or informational greetings.
    
  
- It can provide custom corporate menus. You can customize these menus to have more than one level.
    
  
- It provides directory search that enables people that call in to search the organization's directory for a name.
    
  
- It enables someone that calls in to reach or leave a message for a person in your organization.
    
  
To set up a Cloud PBX auto attendant, go  [Set up a Cloud PBX auto attendant](set-up-a-cloud-pbx-auto-attendant.md).
## Getting started

To get started using auto attendants, it's important to remember that:
  
    
    

- Your organization must have (at a minimum) an Enterprise E3 plus Skype for Business Cloud PBX license or an Enterprise E5 license. The number of Skype for Business Cloud PBX user licenses that are assigned impacts the number of service numbers that are available to be used for auto attendants. The numbers of auto attendants you can have is dependent on the number Skype for Business Cloud PBX and PSTN Conferencing licenses that are assigned in your organization. To learn more about licensing, go  [Skype for Business add-on licensing](skype-for-business-add-on-licensing.md).
    
    > [!TIP]
      > To redirect calls to an operator or a menu option that is an Online user with a Skype for Business Cloud PBX license, you will need to enable them for Enterprise Voice or assign a PSTN Calling plan to them. See  [Assign Skype for Business licenses](assign-skype-for-business-licenses.md). You can also use Windows PowerShell. For example run:  `Set-CsUser -identity "Amos Marble" -EnterpriseVoiceEnabled $true`
- To get and use toll-free service numbers for your auto attendants, you need to set up PSTN Consumption Billing. To do this see  [What is PSTN Consumption billing?](what-is-pstn-consumption-billing.md) and [Set up PSTN Consumption billing](set-up-pstn-consumption-billing.md).
    
    > [!IMPORTANT]
      > User (subscriber) phone numbers can't be assigned to auto attendants - only service toll or toll-free phone numbers can be used. 

## Feature overview


### Dial by Name

Dial by Name is a feature of an auto attendant that is known as directory search. It enables the people who call in to your auto attendant to use voice (speech recognition) or their phone keypad (DTMF) to enter a full or partial name to search company's directory, locate the person and then have the call transferred to them. If you have Skype for Business Online users, **they aren't required to have a phone number or have PSTN calling plan assigned to them but they must have a Skype for Business Cloud PBX license** for them to be reachable when they search using Dial by Name. Dial by Name will even be able to find and transfer calls to Skype for Business Online users that are hosted in different countries or regions for multi-national organizations.
  
    
    

> [!CAUTION]
> On-premises deployments of Skype for Business 2015 or Lync Server 2013 and 2010 users wont' be listed in the directory when someone searches for them. 
  
    
    


### Maximum directory size

There is no limit on the Active Directory size that Dial by Name is supported when using the phone keypad to search for entering partial or full names (FirstName + LastName, and also LastName + FirstName). However, the maximum size of a name list a single auto attendant can support using name recognition with speech is 50,000 users.
  
    
    

||||
|:-----|:-----|:-----|
|**Input type** <br/> |**Search format** <br/> |**Maximum number of users in an organization** <br/> |
|DTMF (keypad entry)  <br/> |Partial  <br/> FirstName + LastName  <br/> LastName + FirstName  <br/> |No hard limit  <br/> |
|Speech (voice input)  <br/> |FirstName  <br/> LastName  <br/> FirstName + LastName  <br/> LastName + FirstName  <br/> |50,000 users  <br/> |
   

> [!NOTE]
> If you are using Dial by Name with speech recognition, but your organization's Active Directory is bigger than 50,000 users, Dial by Name will still work for your callers using a phone keypad and voice inputs will be available for all other scenarios. You can use the Dial Scope feature to narrow down the names that are reachable by changing the scope of Dial by Name for a particular auto attendant. 
  
    
    


### Dial by Name - Keypad (DTMF) entry

People calling in can use Dial by Name to reach users by specifying either full or partial name of the person they are trying to reach. The good thing is that there are various formats that can be used when the name is put in.
  
    
    
When searching your organization's directory, people can use the '0' (zero) key to indicate a space between the first name and last or last name and first. When they are entering the name, they will be asked to terminate their keypad entry with the # (pound) key. For example, "After you enter the name of the person you are trying to reach, press #." If there are multiple names that are found, the person calling will be given a list of names to select from.
  
    
    
People can search for names in your organization using the following search formats on their phone keypad:
  
    
    

|||||
|:-----|:-----|:-----|:-----|
|**Name format** <br/> |**Search type** <br/> |**Example** <br/> |**Search result** <br/> |
|FirstName + LastName  <br/> |Full  <br/> |Amos0Marble#  <br/> |Amos Marble  <br/> |
|LastName + FirstName  <br/> |Full  <br/> |Marble0Amos#  <br/> |Amos Marble  <br/> |
|FirstName  <br/> |Full  <br/> |Amos#  <br/> |Press 1 for Amos Marble  <br/> Press 2 for Amos Marcus  <br/> |
|LastName  <br/> |Full  <br/> |Marble#  <br/> |Press 1 for Amos Marble  <br/> Press 2 for Mary Marble  <br/> |
|FirstName or LastName  <br/> |Partial  <br/> |Mar#  <br/> |Press 1 for Mary Marble  <br/> Press 2 for Mary Jones  <br/> Press 3 for Amos Marcus  <br/> |
|FirsName + LastName  <br/> |Partial  <br/> |Mar0Amos#  <br/> |Press 1 for Amos Marble  <br/> Press 2 for Amos Marcus  <br/> |
|LastName + FirstName  <br/> |Partial  <br/> |Mar0Am#  <br/> |Press 1 for Amos Marble  <br/> Press 2 for Amos Marcus  <br/> |
   
There are several special characters that are used when searching for people using a phone keypad. For example, the person will be asked to use the pound key (#), while key zero (0) is used for a space between names. Pressing the star key (*) will repeat the list of matching names to the person.
  
    
    

|||
|:-----|:-----|
|**Special phone keypad character** <br/> |**What it means** <br/> |
|# (pound key)  <br/> |End character when entering a name.  <br/> |
|0 (zero)  <br/> |Space between names.  <br/> |
|* (star key)  <br/> |Repeat the list of matching names.  <br/> |
   

### Dial by Name - Name recognition with speech

People can search for people in your organization using their voice (speech recognition). They are able to reach anybody in the company's Active Directory by saying the name of the person they are trying to locate. Using voice inputs can recognize names in various formats, including FirstName, LastName, FirstName + LastName, or LastName + FirstName of the person they are trying to reach.
  
    
    
When you enable speech recognition for an auto attendant phone keypad entry (DTMF) wont' be disabled, so both types of input can be used. Phone keypad entry can't be disabled, and can be used at any time, even if speech recognition is enabled on the auto attendant.
  
    
    
As with phone keypad entry, if multiple names are found, the person calling will be presented with a list of names to select from.
  
    
    
People calling in can say names in the following formats:
  
    
    

|||||
|:-----|:-----|:-----|:-----|
|**Name with Speech** <br/> |**Search type** <br/> |**Example** <br/> |**Search result** <br/> |
|FirstName + LastName  <br/> |Full  <br/> |Amos Marble  <br/> |Amos Marble  <br/> |
|LastName + FirstName  <br/> |Full  <br/> |Marble Amos  <br/> |Amos Marble  <br/> |
|FirstName  <br/> |Full  <br/> |Amos  <br/> |Press or say 1 for Amos Marble  <br/> Press or say 2 for Amos Jones  <br/> |
|LastName  <br/> |Full  <br/> |Marble  <br/> |Press or say 1 for Amos Marble  <br/> Press or say 2 for Ben Marble  <br/> |
   

> [!NOTE]
> It might take up to 36 hours for a new user to have their name to be listed in the directory when someone uses Dial by Name with speech recognition. 
  
    
    


### Language support

The following languages are available for text-to-speech:
  
    
    

||||
|:-----|:-----|:-----|
|Arabic (EG)  <br/> |English (NZ)  <br/> |Korean (KO)  <br/> |
|Chinese (HK)  <br/> |English (UK)  <br/> |Norwegian (NO)  <br/> |
|Chinese (TW)  <br/> |English (US)  <br/> |Polish (PL)  <br/> |
|Chinese (ZH)  <br/> |Finnish (FI)  <br/> |Portuguese (BR)  <br/> |
|Danish (DA)  <br/> |French (CA)  <br/> |Portuguese (PT)  <br/> |
|Dutch (NL)  <br/> |French (FR)  <br/> |Russian (RU)  <br/> |
|English (AU)  <br/> |German (DE)  <br/> |Spanish (ES)  <br/> |
|English (CA)  <br/> |Italian (IT)  <br/> |Spanish (MX)  <br/> |
|English (IN)  <br/> |Japanese (JP)  <br/> |Swedish (SV)  <br/> |
   
Speech recognition for auto attendants is available in the following languages:
  
    
    

|||
|:-----|:-----|
|Chinese (ZH)  <br/> |French (FR)  <br/> |
|English (AU)  <br/> |German (DE)  <br/> |
|English (CA)  <br/> |Italian (IT)  <br/> |
|English (IN)  <br/> |Japanese (JP)  <br/> |
|English (UK)  <br/> |Portuguese (BR)  <br/> |
|English (US)  <br/> |Spanish (ES)  <br/> |
|French (CA)  <br/> |Spanish (MX)  <br/> |
   
The following voice commands are available in the fourteen (14﻿) languages supported for speech recognition:
  
    
    

|||
|:-----|:-----|
|**Voice command** <br/> |**Meaning** <br/> |
|Yes  <br/> |Yes - corresponds to pressing 1 for Yes.  <br/> |
|No  <br/> |No - corresponds to pressing 2 for No.  <br/> |
|Repeat  <br/> |Repeats the list of options - corresponds to pressing * to repeat the list of options.  <br/> |
|Operator  <br/> |Breakout to operator - corresponds to pressing 0 for "Operator".  <br/> |
|Main Menu  <br/> |Brings the caller to the main menu of the auto attendant.  <br/> |
|Zero  <br/> |Corresponds to pressing 0 (by default, same as "Operator").  <br/> |
|One  <br/> |Corresponds to pressing 1.  <br/> |
|Two  <br/> |Corresponds to pressing 2.  <br/> |
|Three  <br/> |Corresponds to pressing 3.  <br/> |
|Four  <br/> |Corresponds to pressing 4.  <br/> |
|Five  <br/> |Corresponds to pressing 5.  <br/> |
|Six  <br/> |Corresponds to pressing 6.  <br/> |
|Seven  <br/> |Corresponds to pressing 7.  <br/> |
|Eight  <br/> |Corresponds to pressing 8.  <br/> |
|Nine  <br/> |Corresponds to pressing 9.  <br/> |
   

### Using the operator option

Using the operator for an auto attendant is an optional setting that provides the person calling with an option to speak to a live person.
  
    
    
Key 0 and the voice command "Operator" (in all the languages supported for speech recognition) are assigned to operator by default.
  
    
    

> [!NOTE]
> You can set the button that is pushed for the **Operator** to a different key in using **Menu Options**. 
  
    
    

You can set the following as the operator:
  
    
    

- A Skype for Business Online user that has a Skype for Business Cloud PBX license that is Enterprise Voice-enabled or has a PSTN Calling plan assigned to them. You can set it up so the person calling in can be sent to voicemail. To do this, select a **Person in your company** and set this person's calls to be automatically forwarded directly to voicemail.
    
    > [!NOTE]
      > Users hosted on-premises using Skype for Business Server 2015 or Lync Server 2013 and 2010 can't be used as an Operator. 
- Another auto attendant that's set up for your organization.
    
  
- Any existing call queue that's set up in your organization. To see more about Call Queues, see  [Create a Cloud PBX call queue](create-a-cloud-pbx-call-queue.md).
    
  

### Business hours and call handling

Business hours are set on each auto attendant. If business hours aren't set, all days and all hours in the day are considered business hours because a 24/7 schedule is set by default. Business hours can be set with breaks in time during the day and all of the hours that are not set as business hours are considered after hours. You can set different incoming call handling options and different greetings (which are optional). and Both can be set for business hours and after hours.
  
    
    
Each auto attendant has call handling options that can be set:
  
    
    

- You can have the call just disconnect after greeting.
    
  
- You can also:
    
  - Redirect the call to a Skype for Business Online user that has a Skype for Business Cloud PBX license that is Enterprise Voice-enabled or has a PSTN Calling plan assigned to them. You can set it up so the person calling in can be sent to voicemail. To do this, select a **Person in your company** and set this person's calls to be automatically forwarded directly to voicemail.
    
    > [!NOTE]
      > Users hosted on-premises using Skype for Business Server 2015, Lync Server 2013 and 2010 aren't supported. 
  - Redirect the call to a Call Queue. To see more about Call Queues, see  [Create a Cloud PBX call queue](create-a-cloud-pbx-call-queue.md).
    
  
  - Redirect the call to another auto attendant that you have one set up.
    
  
- Create menu options and play a menu prompt for the person calling. For example: "Press 1 for Sales, Press 2 for Services. To speak to the operator, press 0 at any time."
    
  

### Menu Options

Cloud PBX auto attendants allow you to create menu prompts ("Press 1 for Sales, Press 2 for Services") and set up menu options to route calls based on what the user selects. Setting up menu options for an auto attendant enables an organization to provide interactive guidance to get the person to their destination faster, without relying on a human operator to handle the incoming calls. Menu prompts can be created using text-to-speech (system generated prompts) or by uploading an audio file that has been recorded. Speech recognition uses voice commands for hands-free navigation, but people calling in can also use the phone keypad to navigate menus.
  
    
    
Keys 0 to 9 can be assigned to **Menu Options** in an auto attendant using the Skype for Business admin center. Different sets of menu options can be created for business hours and after hours, and you can enable or disable Dial by Name in the **Menu Options**. Keys can be mapped to transfer the calls to:
  
    
    

- An operator, which is mapped to key 0 by default. However, it can be re-assigned to any other key, or remove the operator from the menu.
    
  
- A Call Queue.
    
  
- Another auto attendant. Multi-level menus can be set up by pointing a **Menu Option** in one auto attendant to another auto attendant with it's own set of Menu Options , which is called a 'nested' auto attendant.
    
  
- A Skype for Business Online user that has a Skype for Business Cloud PBX license that is Enterprise Voice-enabled or has a PSTN Calling plan assigned to them.. You can set it up so the person calling in can be sent to voicemail. To do this, select a **Person in your company** and set this person's calls automatically forwarded directly to voicemail.
    
    > [!NOTE]
      > Users hosted on-premises using Skype for Business Server 2015, Lync Server 2013 and 2010 can't be used in **Menu Options**. 
The name of every menu option becomes a speech recognition keyword, if speech recognition has been enabled. For example, callers can say "One" to select the menu option mapped to key 1, or they can simply say "Sales" to select the same menu option named "Sales".
  
    
    
To set up an auto attendant and the menu options, go  [Set up a Cloud PBX auto attendant](set-up-a-cloud-pbx-auto-attendant.md).
  
    
    

### Getting service numbers for an auto attendant

Before you can create and set up your auto attendants, you will need to get or transfer your existing toll or toll-free service numbers. Once you get the toll or toll-free service phone numbers, they will show up in the ** Skype for Business admin center** > **Voice** > **Phone numbers** tab and the **Number type** listed will be listed as **Service - Toll-Free**. To get your service numbers, see  [Getting Skype for Business service phone numbers](getting-skype-for-business-service-phone-numbers.md) or if you want to transfer and existing service number, see [Transfer phone numbers to Skype for Business Online](transfer-phone-numbers-to-skype-for-business-online.md).
  
    
    

> [!NOTE]
> If you are outside the U.S., you can't use the Skype for Business admin center to get service numbers. Go  [Get phone numbers for Skype for Business Online](get-phone-numbers-for-skype-for-business-online.md) instead to see how to do it from the outside of the U.S.
  
    
    


## Related Topics

 [Here's what you get with Cloud PBX](here-s-what-you-get-with-cloud-pbx.md)
  
    
    
 [Set up PSTN Calling for Skype for Business](set-up-pstn-calling-for-skype-for-business.md)
  
    
    

