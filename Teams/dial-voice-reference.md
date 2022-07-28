---
title: Auto attendant and call queue dialing and voice recognition reference
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.reviewer: colongma
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
audience: Admin
appliesto: 
  - Skype for Business
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom: 
  - ms.teamsadmincenter.autoattendants.overview
  - Phone System
  - seo-marvel-apr2020
description: Learn about the Auto attendant and call queue dialing and voice recognition options in Teams.
---
# Auto attendant and call queue dialing and voice recognition reference

Dial by Name or Extension is an auto attendant feature that enables callers to reach Teams users in your organization. Using their voice or phone keypad callers can say or enter the full or partial name, or extension of the person they would like to reach. The auto attendant will search the company directory, locate the person, and then transfer the caller to them.  Dial by Name or Dial by Extension are options you set up when you [configure the call flow settings in an auto attendant](create-a-phone-system-auto-attendant.md?tabs=call-flow).

## Searching for users

Teams users who can be reached by using Dial by Name **aren't required to have a phone number or have Calling Plans assigned to them, but they must be Enterprise Voice enabled for Skype for Business Server users**. For multi-national organizations, Dial by Name will find and transfer callers to Microsoft Teams users who are in different countries or regions.

Teams users who can be reached by using Dial by Extension **aren't required to have a phone number or have Calling Plans assigned to them, but they must be Enterprise Voice enabled for Skype for Business Server users**. You will also need to have an appropriately configured dial plan for your users. For multi-national organizations, Dial by Extension will find and transfer callers to Microsoft Teams users who are in different countries or regions.

Given the prerequisites involved, Dial by Name or Extension must be explicitly enabled when configuring an auto attendant.

### Maximum directory size

There is no limit on the number of Active Directory users Dial by Name and Dial by Extension can support when a caller searches for a specific person. A caller can enter partial or full names (FirstName + LastName, and also LastName + FirstName), but needs the full extension number. The maximum name list size that a single auto attendant can support using speech recognition is 80,000 users.
  
|Input type|Search format|Maximum number of users in an organization|
|:-----|:-----|:-----|
|DTMF (keypad entry) |Partial  <br/> FirstName + LastName  <br/> LastName + FirstName |No limit  |
|Speech (voice input) |FirstName  <br/> LastName  <br/> FirstName + LastName  <br/> LastName + FirstName  | 80,000 users |

> [!NOTE]
> If you are using Dial by Name with speech recognition, but your organization's Active Directory is larger than 80,000 users and you haven't limited the scope of Dial by Name using [Dial Scope](create-a-phone-system-auto-attendant.md?tabs=dial-scope) feature, Dial by Name will still work for your callers using a phone keypad, and voice inputs will be available for all other scenarios. You can use the Dial Scope feature to narrow down the names that are reachable by changing the scope of Dial by Name for a particular auto attendant.

### Search Considerations

Dial by Name searches the entire organization's directory first before applying any Dial Scope Include or Exclude lists that have been configured. If the initial search against the entire directory returns more than 100 users, the Dial Scope lists will not be applied, the search will fail, and the caller will be told that too many names were found.

## Dial by Name - Keypad (DTMF) entry

People calling in can use Dial by Name to reach users by specifying either the full or partial name of the person they are trying to reach. There are various formats that can be used when the name is entered.

When searching your organization's directory, people can use the '0' (zero) key to indicate a space between the first name and last or last name and first. When they are entering the name, they will be asked to terminate their keypad entry with the # key. For example, "After you enter the name of the person you are trying to reach, press #." If there are multiple names that are found, the person calling will be given a list of names to select from.

> [!NOTE]
> If more than 5 names remain after any Dial Scope Include or Exclude lists have been applied, the search will fail and the caller will be told that too many names were found.
  
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

### Dial by Name - Name recognition with speech

People can search for others in their organization with their voice (speech recognition). They can also reach anyone in Active Directory by saying the full or partial name of the person they are trying to locate. Using voice inputs can recognize names in various formats, including FirstName, LastName, FirstName + LastName, or LastName + FirstName.
  
You can enable speech recognition for an auto attendant, but phone keypad entry (DTMF) isn't disabled. Phone keypad entry can be used at any time even if speech recognition is enabled on the auto attendant.
  
As with phone keypad entry, if multiple names are found, the person calling hears a list of names to select from.

> [!NOTE]
> If more than 5 names remain after any Dial Scope Include or Exclude lists have been applied, the search will fail and the caller will be told that too many names were found.
  
Callers can say names in the following formats:
  
|Name with speech|Search type|Example|Search result|
|:-----|:-----|:-----|:-----|
|FirstName + LastName |Full |Amos Marble |Amos Marble |
|LastName + FirstName |Full  |Marble Amos |Amos Marble |
|FirstName |Full |Amos |Press or say 1 for Amos Marble  <br/> Press or say 2 for Amos Jones |
|LastName |Full |Marble |Press or say 1 for Amos Marble  <br/> Press or say 2 for Ben Marble |
|FirstName or LastName |Partial |Mar |Press or say 1 for Mary Marble  <br/> Press or say 2 for Mary Jones  <br/> Press or say 3 for Amos Marcus |
|FirsName + LastName |Partial |Amos Mar |Press or say 1 for Amos Marble  <br/> Press or say 2 for Amos Marcus |

> [!NOTE]
> It might take up to 36 hours for a new user to have their name listed in the directory for Dial by Name with speech recognition due to Active Directory replication lag.

### Dial by Extension

Users you want to make available for **Dial By Extension** need to have an extension specified as part of one of the following phone attributes defined in Active Directory (and synchronized via Azure AD Connect) or Azure Active Directory. (See [Add users individually or in bulk](/microsoft-365/admin/add-users/add-users) for more information.)

- TelephoneNumber (AD and Azure AD)
- HomePhone (AD)
- Mobile (AD and Azure AD)
- OtherTelephone (AD)

The required format to enter the extension in the user phone number field can be one of the following formats:

- *+\<phone number>;ext=\<extension>*
- *+\<phone number>x\<extension>*
- *x\<extension>*

- Example 1: Set-MsolUser -UserPrincipalName usern@domain.com -Phonenumber "+15555555678;ext=5678"
- Example 2: Set-MsolUser -UserPrincipalName usern@domain.com -Phonenumber "+15555555678x5678"
- Example 3: Set-MsolUser -UserPrincipalName usern@domain.com -Phonenumber "x5678"

You can set the extension in the [Microsoft 365 admin center](https://admin.microsoft.com/) or the [Azure Active Directory admin center](https://aad.portal.azure.com). It can take up to 12 hours before changes are available to auto attendants and call queues.

> [!NOTE]
>  If using the TelephoneNumber field to define the extension it's recommended that the format of *+\<phone number>;ext=\<extension>* is used and if the user is also assigned a Teams Phone Number, that both numbers are defined the same way.


## Language support

Language support for text-to-speech and speech recognition is available in these [supported languages](create-a-phone-system-auto-attendant-languages.md).

The following voice commands are available for speech recognition:
  
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

## Related topics

[Getting service phone numbers for Skype for Business and Microsoft Teams](./getting-service-phone-numbers.md)

[Country and region availability for Audio Conferencing and Calling Plans](country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md)
