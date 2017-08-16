---
title: How can caller ID be used in your organization
ms.assetid: 5a0bd8ba-3334-46ee-becf-1025597737f6
---


# How can caller ID be used in your organization

Caller ID can be controlled for both inbound and outbound PSTN calls for Skype for Business Online Cloud PBX users by using a policy called CallingLineIdentity.
  
    
    

The Caller ID functionality is available to all Office 365 Cloud PBX users regardless of PSTN connectivity:
- Online PSTN Connectivity
    
  
- On-Premises PSTN Connectivity with Skype for Business Cloud Connector Edition (requires Cloud Connector Edition 1.4.2 and beyond)
    
  
- On-Premises PSTN Connectivity with Skype for Business Server (requires Skype for Business Server 2015 CU5 and beyond)
    
  

> [!NOTE]
> This policy isn't available in Skype for Business 2015 Server. 
  
    
    


## Outbound caller ID

There are three options available for outbound PSTN Caller ID:
  
    
    

- The telephone number assigned to the user - which is the default.
    
  
- A telephone number that is classified as a  *service*  and *toll free*  number in your online PSTN Calling telephone number inventory - usually assigned to an organizational auto attendant or call queue.
    
  
- Set to anonymous.
    
  
However, you can't assign these types of phone numbers for the outbound caller ID:
  
    
    

- Any phone numbers that are classified as a  *user*  in your PSTN Calling telephone number inventory
    
  
- A Skype for Business Server on-premises phone number
    
  
To set the outbound caller ID, see  [Set the Caller ID for a user](set-the-caller-id-for-a-user.md).
  
    
    

### End User Control of Outbound Caller ID

The **EnableUserOverride** attribute enables single or multiple users to change their Caller ID setting to **Anonymous**. This only applies when a **CallingLineIdentity** policy is configured with a **CallingIDSubstitute** parameter of either _LineURI_ or _Substitute_. The default value of **EnableUserOverride** is _False_.
  
    
    
Your end users can set their caller ID to **Anonymous** using the **Call Forward Settings** tab in the Skype for Business desktop client.
  
    
    

||||
|:-----|:-----|:-----|
|**Windows** <br/> |**Version** <br/> |**Supported** <br/> |
|Click-to-Run  <br/> |Current Channel released on December 6, 2016 - version 1611 (Build 7571.2072)  <br/> |Yes  <br/> |
|Click-to-Run  <br/> |First Release for Deferred Channel released on February 22, 2017 - Version 1701 (Build 7766.2060)  <br/> |Yes  <br/> |
|Click-to-Run  <br/> |Deferred Channel released on June 13, 2017 - Version 1701 (Build 7766.2092)  <br/> |Yes  <br/> |
|MSI  <br/> |Skype for Business  <br/> |No  <br/> |
|Mac  <br/> |Skype for Business  <br/> |No  <br/> |
   
Your end users can also set their caller ID setting on the user settings page at:  [https://mysettings.lync.com/pstncalling](https://mysettings.lync.com/pstncalling).
  
    
    

## Inbound Caller ID

The **BlockIncomingCallerID** attribute allows for blocking the caller ID on incoming PSTN calls. You can set this attribute but it isn't available to your end users on the user settings page. And it is currently available only with Online PSTN connectivity.
  
    
    
To set the outbound caller ID, see  [Set the Caller ID for a user](set-the-caller-id-for-a-user.md).
  
    
    

## See also


#### Other Resources


  
    
    
 [Emergency calling terms and conditions](emergency-calling-terms-and-conditions.md)
  
    
    
 [Skype for Business Online PSTN services use terms](skype-for-business-online-pstn-services-use-terms.md)
  
    
    
 [Skype for Business add-on licensing](skype-for-business-add-on-licensing.md)
