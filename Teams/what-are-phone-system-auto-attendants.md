---
title: "What are Cloud auto attendants?"
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.reviewer: makolomi
ms.date: 4/2/2019
ms.topic: article
ms.assetid: ab9f05a2-22cb-4692-a585-27f82d1b37c7
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
f1.keywords:
- CSH
ms.custom: 
  - ms.teamsadmincenter.autoattendants.overview
  - Phone System
  - seo-marvel-apr2020
ROBOTS: NOINDEX, NOFOLLOW
description: Learn about Cloud auto attendants and how to use them to let callers move through a menu system to locate and place or transfer calls to users or departments.
---

# What are Cloud auto attendants?

Phone System provides auto attendants, which can be used to let external and internal callers move through a menu system to locate and place or transfer calls to users or departments in your organization.
  
An auto attendant is most often a node in a system, giving a caller a series of voice prompts or audio files they hear instead of a human operator. When people call a number associated with an auto attendant, their choices can redirect the call to a user or locate someone in your organization and then connect to that user. They can express their choices and interact with the menu system by using a phone keypad (DTMF) or speech recognition. The choices they make can also redirect the call to another auto attendant, or to a call queue.
  
To set up an auto attendant for Phone System, go to [Set up a Cloud auto attendant](create-a-phone-system-auto-attendant.md).
  
A Cloud auto attendant has the following features:
  
- It can provide corporate or informational greetings.
- It can provide custom corporate menus. You can customize these menus to have more than one level.
- It provides directory search that enables people who call in to search the organization's directory for a name.
- It enables someone who calls in to reach or leave a message for a person in your organization.
- It supports multiple languages for prompts, text-to-speech, and speech recognition.
- It supports specifying holidays and business hours.
- It supports transferring call to  an operator, other users, call queues, and auto attendants.
- It supports shared voicemail for callers to leave a message for an organization.

> [!NOTE]
> This article applies to both Microsoft Teams and Skype for Business Online.

## Getting started

To get started using auto attendants, it's important to remember that:

- An auto attendant is required to have an associated resource account. See [Manage resource accounts in Teams](manage-resource-accounts.md) for details on resource accounts. <!-- You can either use an existing resource account or create a new resource account as you set up your auto attendant. -->
- When you assigning a phone number to an auto attendant, strictly speaking you are assigning it to the resource account associated with that auto attendant. This provides a way to have more than one phone number access an auto attendant. Most often, a resource account will use the cost-free Phone System Virtual User license. This license provides Phone System capabilities to phone numbers at the organizational level, and allows you to create auto attendants and call queues.

> [!NOTE]
> Direct Routing service numbers for auto attendant and call queues are supported for Microsoft Teams users and call agents only.

   > [!TIP]
   > To redirect calls to an operator or a menu option that is an Online user with a **Phone System** license, you will need to enable their account for Enterprise Voice or assign Calling Plans to them. See [Assign Microsoft Teams add-on licenses](teams-add-on-licensing/assign-teams-add-on-licenses.md). You can also use Windows PowerShell. For example run:  `Set-CsUser -identity "Amos Marble" -EnterpriseVoiceEnabled $true`
  
- To get and use toll-free service numbers for your auto attendants, you need to set up Communications Credits. To do this, see [What are Communications Credits?](what-are-communications-credits.md) and [Set up Communications Credits for your organization](set-up-communications-credits-for-your-organization.md).

    > [!IMPORTANT]
    > User (subscriber) phone numbers can't be assigned to auto attendants - only service toll or toll-free phone numbers can be used.

- A complete auto attendant system will usually involve multiple auto attendants.
- It's possible to apply more than one phone number to entry-level auto attendants.
- Non-entry level auto-attendants or call queues in the complete system will only need a phone number if they will be making outbound PSTN calls.
  
## Feature overview

### Searching for users

Dial by Name is a feature of an auto attendant that is also known as directory search. It enables the people who call your auto attendant to use voice (speech recognition) or their phone keypad (DTMF) responses to enter a full or partial name to search company's directory, locate the person, and then have the call transferred to them. Users you wish to have located and reached using Dial by Name **aren't required to have a phone number or have Calling Plans assigned to them, but they must have a Phone System license if they are online users, or Enterprise Voice enabled for Skype for Business Server users**. Dial by Name will even be able to find and transfer calls to Microsoft Teams users who are hosted in different countries or regions for multi-national organizations. Given the prerequisites involved, you explicitly enable Dial by Name in an auto attendant.

Dial by extension is a feature of an auto attendant that is also part of directory search. It enables the people who call your auto attendant to use voice (speech recognition) or their phone keypad (DTMF) responses to enter the phone extension of the user they're trying to reach, and then have the call transferred to them. Users you wish to have located and reached using Dial by extension  **aren't required to have a phone number or have Calling Plans assigned to them, but they must have a Phone System license if they are online users, or Enterprise Voice enabled for Skype for Business Server users**. You will also need to have an appropriately configured dial plan for your users. Dial by extension  will even be able to find and transfer calls to Microsoft Teams users who are hosted in different countries or regions for multi-national organizations. Given the prerequisites involved, you explicitly enable Dial by extension in an auto attendant.

#### Maximum directory size

There is no limit on the number of Active Directory users  Dial by Name and Dial by Extension can support when a caller search for a specific person. A caller can enter partial or full names (FirstName + LastName, and also LastName + FirstName), but needs the full extension number. The maximum name list size that a single auto attendant can support using speech recognition is 80,000 users.
  
|Input type|Search format|Maximum number of users in an organization|
|:-----|:-----|:-----|
|DTMF (keypad entry) |Partial  <br/> FirstName + LastName  <br/> LastName + FirstName |No limit  |
|Speech (voice input) |FirstName  <br/> LastName  <br/> FirstName + LastName  <br/> LastName + FirstName  | 80,000 users |

> [!NOTE]
> If you are using Dial by Name with speech recognition, but your organization's Active Directory is larger than 80,000 users and you haven't limited the scope of Dial by Name using Dial Scope feature, Dial by Name will still work for your callers using a phone keypad, and voice inputs will be available for all other scenarios. You can use the Dial Scope feature to narrow down the names that are reachable by changing the scope of Dial by Name for a particular auto attendant.
  
### Dial by Name - Keypad (DTMF) entry

People calling in can use Dial by Name to reach users by specifying either the full or partial name of the person they are trying to reach. There are various formats that can be used when the name is entered.

When searching your organization's directory, people can use the '0' (zero) key to indicate a space between the first name and last or last name and first. When they are entering the name, they will be asked to terminate their keypad entry with the # key. For example, "After you enter the name of the person you are trying to reach, press #." If there are multiple names that are found, the person calling will be given a list of names to select from.
  
People can search for names in your organization using the following search formats on their phone keypad:
  
|Name format|Search type|Example|Search result|
|:-----|:-----|:-----|:-----|
|FirstName + LastName |Full  |Amos0Marble# |Amos Marble |
|LastName + FirstName |Full |Marble0Amos#  |Amos Marble |
|FirstName  |Full   |Amos#   |Press 1 for Amos Marble  <br/> Press 2 for Amos Marcus |
|LastName |Full |Marble#  |Press 1 for Amos Marble  <br/> Press 2 for Mary Marble |
|FirstName or LastName |Partial |Mar# |Press 1 for Mary Marble  <br/> Press 2 for Mary Jones  <br/> Press 3 for Amos Marcus |
|FirsName + LastName |Partial |Amos0Mar# |Press 1 for Amos Marble  <br/> Press 2 for Amos Marcus |
|LastName + FirstName |Partial |Mar0Am# |Press 1 for Amos Marble  <br/> Press 2 for Amos Marcus |

There are several special characters that are used when searching for people using a phone keypad. For example, the person will be asked to use the pound key (#), while the zero (0) key is used for a space between names. Pressing the star key (*) will repeat the list of matching names to the person.
  
|Special phone keypad character|What it means|
|:-----|:-----|
|#   |End character when entering a name. |
|0   |Space between names. |
|*    |Repeat the list of matching names. |

#### Dial by Name - Name recognition with speech

People can search for others in their organization with their voice (speech recognition). They can also reach anyone in  Active Directory by saying the name of the person they are trying to locate. Using voice inputs can recognize names in various formats, including FirstName, LastName, FirstName + LastName, or LastName + FirstName.
  
You can enable speech recognition for an auto attendant, but phone keypad entry (DTMF) isn't disabled. Phone keypad entry can be used at any time even if speech recognition is enabled on the auto attendant.
  
As with phone keypad entry, if multiple names are found, the person calling hears a list of names to select from.
  
Callers can say names in the following formats:
  
|Name with speech|Search type|Example|Search result|
|:-----|:-----|:-----|:-----|
|FirstName + LastName |Full |Amos Marble |Amos Marble |
|LastName + FirstName |Full  |Marble Amos |Amos Marble |
|FirstName |Full |Amos |Press or say 1 for Amos Marble  <br/> Press or say 2 for Amos Jones |
|LastName |Full |Marble |Press or say 1 for Amos Marble  <br/> Press or say 2 for Ben Marble |

> [!NOTE]
> It might take up to 36 hours for a new user to have their name listed in the directory for Dial by Name with speech recognition due to Active Directory replication lag.
  
### Language support

The following languages are available for text-to-speech used with outgoing prompts:
  
|A-E|E-J|K-Z|
|:-----|:-----|:-----|
|Arabic (EG)  |English (NZ)  |Korean (KO)  |
|Chinese (HK)  |English (UK) |Norwegian (NO)  |
|Chinese (TW) |English (US) |Polish (PL)  |
|Chinese (ZH) |Finnish (FI) |Portuguese (BR) |
|Danish (DA)  |French (CA)  |Portuguese (PT) |
|Dutch (NL)   |French (FR)  |Russian (RU) |
|English (AU)  |German (DE) |Spanish (ES)  |
|English (CA)  |Italian (IT) |Spanish (MX)|
|English (IN)  |Japanese (JP) |Swedish (SV)|

Speech recognition input for auto attendants is available in the following languages:
  
|A-F|F-Z|
|:-----|:-----|
|Chinese (ZH)  |French (FR)  |
|English (AU)  |German (DE)  |
|English (CA)  |Italian (IT)  |
|English (IN)  |Japanese (JP)  |
|English (UK)  |Portuguese (BR)  |
|English (US)  |Spanish (ES)  |
|French (CA)   |Spanish (MX)  |

The following voice commands are available in the 14 languages supported for speech recognition:
  
|Voice command| Corresponds to |
|:-----|:-----|
|Yes | Press 1 for Yes. |
|No | Press 2 for No. |
|Repeat |Repeats the list of options. Press * on the keypad to repeat the list of options. |
|Operator | Press 0 for "Operator" |
|Main Menu  |Brings the caller to the main menu of the auto attendant. |
|Zero | Press 0 (by default, same as "Operator").|
|One | Press 1. |
|Two | Press 2. |
|Three| Press 3.|
|Four | Press 4. |
|Five | Press 5. |
|Six  | Press 6. |
|Seven | Press 7.|
|Eight |Press 8.|
|Nine  |Press 9.|

### The operator option

An auto attendant can optionally be set to give a caller a selection to speak to a human operator.
  
Key 0 and the voice command "Operator"  direct the call to the designated operator by default. This is the case for all languages supported for speech recognition. You can also use **Set menu Options** to set a custom value for the Operator.
  
The operator can be set to:
  
- A Microsoft Teams user or a Skype for Business Server user that is Enterprise Voice-enabled.
- Another auto attendant that's set up for your organization.
- Any existing call queue that's set up in your organization. To see more about call queues, see [Create a Cloud call queue](/SkypeForBusiness/what-is-phone-system-in-office-365/create-a-phone-system-call-queue).

### Business hours and call handling

Business hours can be set on each auto attendant. If business hours aren't set, all days and all hours in the day are considered business hours because a 24/7 schedule is set by default. Business hours can be set with breaks in time during the day, and all of the hours that are not set as business hours are considered after-hours. You can set different incoming call-handling options and different greetings (which are optional) for business hours and after-hours.
  
Each auto attendant has several possible call-handling options:
  
- The call can disconnect after a greeting plays.
- You can also:
  - Redirect the call to a Microsoft Teams user who has a **Phone System** license that is Enterprise Voice-enabled or has Calling Plans assigned to them. You can set it up so the person calling in can be sent to voicemail. To do this, select a **Person in your company** and set this person's calls to be automatically forwarded directly to voicemail.

  - Redirect the call to a call queue. To see more about call queues, see [Create a Cloud call queue](/SkypeForBusiness/what-is-phone-system-in-office-365/create-a-phone-system-call-queue).

  - Redirect the call to another auto attendant.

These options are expressed to the caller by the auto attendant when it plays  menu prompts. For example: "Press 1 for Sales, Press 2 for Services. To speak to the operator, press 0 at any time."

### Set menu Options

Cloud auto attendants allow you to create menu prompts ("Press 1 for Sales, Press 2 for Services") and set up menu options to route calls based on  user selections. Menu options for an auto attendant let an organization provide a series of choices that guide callers to their destination faster, without relying on a human operator to handle incoming calls. Menu prompts can either be created by using text-to-speech (system-generated prompts) or by uploading a recorded audio file. Speech recognition accepts voice commands for hands-free navigation, but people calling in can also use the phone keypad to navigate menus.
  
Keys 0 through 9 can be assigned to dial keys in an auto attendant using the Skype for Business admin center. Different sets of menu options can be created for business hours and after hours, and you can enable or disable Dial by Name in the **Menu Options**. Keys can be mapped to transfer the calls to:
  
- An operator, which is mapped to key 0 by default. However, it can be reassigned to any other key, or removed from the menu.
- A call queue.
- Another auto attendant. Multi-level menus can be set up by pointing a **Menu Option** in one auto attendant to another auto attendant with its own set of Menu Options, which is called a "nested" auto attendant.
- A Microsoft Teams user who has a **Phone System** license that is Enterprise Voice-enabled or has Calling Plans assigned to them. You can set it up so the person calling in can be sent to voicemail. To do this, select a **Person in your company** and set this person's calls to be automatically forwarded directly to voicemail.
  
The name of every menu option becomes a speech-recognition keyword if speech recognition has been enabled. For example, callers can say "One" to select the menu option mapped to key 1, or they can say "Sales" to select the same menu option named "Sales."
  
To set up an auto attendant and the menu options, go [Set up a Cloud auto attendant](create-a-phone-system-auto-attendant.md).
  
### Assigning phone numbers for an auto attendant

You can assign a Microsoft service number, a direct routing number, or a hybrid number to your auto attendant's linked resource account (or to several resource accounts if more than one phone number is desired). See [Plan Direct Routing](direct-routing-plan.md) for additional details.

To assign a service number, you will need to get or port your existing toll or toll-free service numbers. Once you get the toll or toll-free service phone numbers, they show up in **Skype for Business admin center** > **Voice** > **Phone numbers**. **Number type** is listed as **Service - Toll-Free**. To get your service numbers, see [Getting service phone numbers for Skype for Business and Microsoft Teams](./getting-service-phone-numbers.md) or, if you want to transfer and existing service number, see [Transfer phone numbers to Teams](phone-number-calling-plans/transfer-phone-numbers-to-teams.md).
  
> [!NOTE]
> If you are outside the United States, you can't use the Microsoft Teams admin center to get service numbers. Go [Manage phone numbers for your organization](manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md) instead to see how to do it.
  
## Related topics

[Here's what you get with Phone System](here-s-what-you-get-with-phone-system.md)

[Getting service phone numbers for Skype for Business and Microsoft Teams](./getting-service-phone-numbers.md)

[Country and region availability for Audio Conferencing and Calling Plans](country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md)