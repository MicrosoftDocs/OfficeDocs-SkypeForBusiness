---
title: Skypes-to-phone access numbers
ms.prod: OFFICE365
ms.assetid: 0646580c-3f05-48a1-8f1f-b1e1d0740922
---


# Skypes-to-phone access numbers

 Skype-to-phone is a feature set that enables syndicated partners to provide voice mail and auto attendant features for organizations that use Skype for Business Online.
  
    
    

There are two types of access numbers that can be configured in Skype-to-phone: Outlook Voice Access and auto attendant access numbers. Outlook Voice Access lets users who are enabled for voice messaging in Skype-to-phone to access their mailboxes using a phone and for external callers to be able to call into your organization, you need to configure your auto attendants with the correct access numbers.
## Outlook Voice Access access numbers

With Skype-to-phone, a user can call in to a telephone number that's configured on a UM dial plan to access their mailbox and use the Outlook Voice Access. Using these menus, users can read email, listen to voice messages, interact with their calendar, access their personal contacts, and perform tasks such as configuring their Outlook Voice Access PIN and recording their voice mail greetings.
  
    
    
Here are some examples of how Outlook Voice Access can be used:
  
    
    
 **Access their email**
  
    
    
An Outlook Voice Access user wants to access their email from a telephone and makes a call to an Outlook Voice Access number.
  
    
    

|||
|:-----|:-----|
|Voice prompt  <br/> | *"Welcome. You're connected to Contoso. To access your mailbox, please enter your extension. To contact someone, press the pound key."*  <br/> |
|User  <br/> |Enters an extension number.  <br/> |
|Voice prompt  <br/> | *"Please enter your PIN and press the pound key."*  <br/> |
|User  <br/> |Enters a PIN.  <br/> |
|Voice prompt  <br/> | *"You have two new voice mails, 10 new email messages, and your next meeting is at 10:00 A.M. Please say voice mail, email, calendar, personal contacts, directory, or personal options."*  <br/> |
|User  <br/> | *"Email."*  <br/> The voice mail system reads the message header and then the name, subject, time, and priority for the messages.  <br/> |
   
 **Access their calendar**
  
    
    
An Outlook Voice Access user wants to access their calendar from a telephone and makes a call to an Outlook Voice Access number.
  
    
    

|||
|:-----|:-----|
|Voice prompt  <br/> | *"Welcome. You're connected to Contoso. To access your mailbox, please enter your extension. To contact someone, press the pound key."*  <br/> |
|User  <br/> |Enters an extension number.  <br/> |
|Voice prompt  <br/> | *"Please enter your PIN and press the pound key."*  <br/> |
|User  <br/> |Enters a PIN.  <br/> |
|Voice prompt  <br/> | *"You have two new voice mails, 10 new email messages, and your next meeting is at 10:00 A.M. Please say voice mail, email, calendar, personal contacts, directory, or personal options."*  <br/> |
|User  <br/> | * "Calendar."*  <br/> |
|Voice prompt  <br/> | *"Sure, and which day should I open?"*  <br/> |
|User  <br/> | *"Today."*  <br/> |
|Voice prompt  <br/> | *"Opening today's calendar."*  <br/> |
||The voice mail system reads the message header and then the name, subject, time, and priority for the messages  <br/> |
   
 **Access their voice mail**
  
    
    
An Outlook Voice Access user wants to access their voice mail from a telephone and makes a call to an Outlook Voice Access number.
  
    
    

|||
|:-----|:-----|
|Voice prompt  <br/> | *"Welcome. You're connected to Contoso. To access your mailbox, please enter your extension. To contact someone, press the pound key."*  <br/> |
|User  <br/> |Enters an extension number.  <br/> |
|Voice prompt  <br/> | *"Please enter your PIN and press the pound key."*  <br/> |
|User  <br/> |Enters a PIN.  <br/> |
|Voice prompt  <br/> | *"You have two new voice mails, 10 new email messages, and your next meeting is at 10:00 A.M. Please say voice mail, email, calendar, personal contacts, directory, or personal options."*  <br/> |
|User  <br/> | *"Voice mail."*  <br/> The voice mail system reads the message header and then the name, subject, time, and priority for their voice mail messages.  <br/> |
   

> [!TIP]
> As an administrator, to let users use Outlook Voice Access you must enter an access number that matches the Outlook Voice Access numbers that are configured on a SIP dial plan. To do this, see  [Configure an Outlook Voice Access number](https://go.microsoft.com/fwlink/?LinkId=524981)
  
    
    


## Auto attendant access numbers

In Skype-to-phone in Skype for Business Online to be able to allow callers to call into your organization and have a menu system that greets callers, you must configure an access number for your auto attendants.
  
    
    
In telephony or Unified Messaging environments, an automated attendant or auto attendant menu system transfers callers to the extension of a user or department without the intervention of a receptionist or an operator. In many auto attendant systems, a receptionist or operator can be reached by pressing or saying zero. The automated attendant is a feature in most modern Private Branch eXchanges (PBXs), IP PBXs, and Unified Messaging solutions.
  
    
    
Exchange Unified Messaging in Skype-to-phone enables you to create one or more UM auto attendants depending on the needs of your organization. UM auto attendants can be used to create a voice menu system for an organization that lets external and internal callers move through the UM auto attendant menu system to locate and place or transfer calls to company users or departments in an organization.
  
    
    
When anonymous or unauthenticated users call an external business telephone number, or when internal callers call a defined extension number, they are presented with a series of voice prompts that help them place a call to a user or locate a user in the organization and then place a call to that user. The UM auto attendant is a series of voice prompts or .wav files that callers hear instead of a human operator when they call an organization that has Unified Messaging. The UM auto attendant lets callers move through the menu system, place calls, or locate users by using dual tone multi-frequency (DTMF) or voice inputs. However, for Automatic Speech Recognition (ASR) or voice inputs to be used, you must enable ASR on the UM auto attendant.
  
    
    
A UM auto attendant has the following features:
  
    
    

- It provides corporate or informational greetings.
    
  
- It provides custom corporate menus. You can customize these menus to have more than one level.
    
  
- It provides a directory search function that enables a caller to search the organization's directory for a name.
    
  
- It enables a caller to connect to the telephone of, or leave a message for, members of the organization.
    
  
 See [Set up a UM auto attendant](https://go.microsoft.com/fwlink/?LinkID=519283) if you want to create and set up a single or multiple auto attendants to be used with Skype-to-phone.
  
    
    

