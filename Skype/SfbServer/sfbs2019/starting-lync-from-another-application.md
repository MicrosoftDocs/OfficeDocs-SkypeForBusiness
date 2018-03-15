---
title: "Starting Lync from another application"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: End User
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 573b30b1-6590-4b24-8e96-a41be57cb0ef

description: "You can use command-line parameters to quick-start Lync 2013. For example, if a user clicks a phone number in another application, the application can start an instance of Lync 2013 and initiate a call to that number."
---

# Starting Lync from another application
[]
You can use command-line parameters to quick-start Lync 2013. For example, if a user clicks a phone number in another application, the application can start an instance of Lync 2013 and initiate a call to that number.
  
Lync 2013 can also recognize a semicolon-delimited list of contact names for multiparty conferencing.
  
If Lync 2013 is configured to automatically sign in when started, then starting Lync 2013 with command-line parameters will open the Lync main window. If Lync is not configured to automatically sign in when started, the sign-in window opens.
  
The following table shows the available parameters.
  
**Lync 2013 Command-Line Parameters**

|**Extension**|**Format of Data**|**Action**|
|:-----|:-----|:-----|
|tel:  <br/> |tel URI  <br/> |Opens the Conversation window for an audio call but does not dial the specified number.  <br/> |
|callto:  <br/> |tel:, sip:, or typeable tel URI  <br/> |Opens the Conversation window for an audio call but does not dial the specified number.  <br/> |
|sip:  <br/> |SIP URI  <br/> |Opens the Conversation window with the specified SIP Uniform Resource Identifier (URI) in the participant list.  <br/> |
|Sips:  <br/> |SIP URI  <br/> |If Lync 2013 is configured to use the Transport Layer Security (TLS) protocol, functions exactly like sip:. If TLS is not being used, displays a dialog box informing the user that a higher level of security is required.  <br/> |
|conf:  <br/> |SIP URI of conference to join  <br/> |If URI is self, instantiates the focus and brings up roster-only view. Otherwise, brings up roster view but does not send INVITE.  <br/> |
|im:  <br/> |SIP URI  <br/> |Displays an instant messaging (IM)-only Conversation window with the SIP URI. Accepts multiple SIP URIs specified inside angle brackets (\<\>) without any separator.  <br/> ```im:<sip:user1@host><sip:user2@host>```|
   
The following table provides examples of these command-line parameters.
  
**Command-Line Parameter Examples**

|**Instance**|**Results**|
|:-----|:-----|
|Tel:+14255550101  <br/> |Opens a phone-only view with +14255550101.  <br/> |
|Callto:tel:+ 14255550101  <br/> |Opens a phone-only view with +14255550101.  <br/> |
|Callto:sip:kazuto@litwareinc.com  <br/> |Opens a phone-only view with kazuto@litwareinc.com.  <br/> |
|sip:kazuto@litwareinc.com  <br/> |Opens a Conversation window with kazuto@litwareinc.com.  <br/> |
|conf:sip:https://meet.contoso.com/kazuto/7322994  <br/> |Opens a Conversation window and displays meeting audio join options.  <br/> |
   

