---
title: "Installing Lync for Windows Phone in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: bf502546-ff69-489f-a92e-a78b58803d53
description: "In this articleInstalling Lync for Windows MobileIf You Use a DNS SRV Record to Publish Exchange Web ServicesVerifying Mobile Client Installation"
---

# Installing Lync for Windows Phone in Lync Server 2013
[]
 **In this article**
  
[Installing Lync for Windows Mobile](#sectionSection0)
  
[If You Use a DNS SRV Record to Publish Exchange Web Services](#sectionSection1)
  
[Verifying Mobile Client Installation](#sectionSection2)
  
Lync 2013 for Windows Phone is a user-installable application that is available in the Windows Phone Marketplace. 
  
## Installing Lync for Windows Mobile
<a name="sectionSection0"> </a>

You can instruct your users to install Lync 2013 for Windows Phone on their devices by directing them to the Windows Phone Marketplace at [https://go.microsoft.com/fwlink/p/?linkid=231901](https://go.microsoft.com/fwlink/p/?linkid=231901).
  
## If You Use a DNS SRV Record to Publish Exchange Web Services
<a name="sectionSection1"> </a>

To enable Exchange integration for Lync clients, some organizations publish the Exchange Web Services URL by using a DNS SRV record. The document "Understanding and Troubleshooting Exchange Integration," available in the Microsoft Download Center at [https://go.microsoft.com/fwlink/?LinkID=391095](https://go.microsoft.com/fwlink/?LinkID=391095), describes scenarios in which this might be necessary. However, Exchange integration for Windows Phone users will not work in this scenario, because the Windows Phone platform does not support SRV lookups. You will need to instruct Windows Phone users to specify the Exchange Web Services URL instead of allowing the phone to automatically detect the server.
  
Instruct your users to configure the Lync settings on their Windows Phones as follows:
  
1. In Windows Phone, in the Lync settings, select the **Exchange** screen. 
    
2. Move **Auto-Detect Server** to **Off**.
    
3. Tap the empty field and enter the fully qualified domain name (FQDN) or URL for Exchange Web Services.
    
    > [!NOTE]
    > You can specify either the fully qualified domain name (FQDN) or the full URL of your Exchange Web Services server. If you specify the FQDN, the protocol (https://) and the Exchange Web Services path (/ews/exchange.asmx) are added automatically. If your Exchange Web Services path is different, you can specify the full URL. 
  
4. Close the screen.
    
## Verifying Mobile Client Installation
<a name="sectionSection2"> </a>

After you configure the client and sign in successfully, use the following tests to verify that your installation of Lync 2013 is working correctly on your mobile device.
  
### Search for a contact in the corporate directory

1. In the Contacts list, tap **Search** at the bottom. 
    
2. Search for a contact that exists only in the global address list.
    
3. Verify that the contact name appears in the search results.
    
### Test instant messaging and presence

1. In the Contacts list, tap a contact.
    
2. In the contact card, tap the **IM** icon. 
    
3. Verify that an instant messaging (IM) window appears and that you can type and send an IM.
    
### Test dial-out conferencing

1. In Outlook, schedule a Lync meeting.
    
2. On the mobile device, open the meeting invitation.
    
3. Click the link in the meeting to join.
    
4. Answer the call from the conference service and verify that you are connected to meeting audio.
    
### Test push notifications

1. On user A's mobile device, sign in to Lync with user A's account.
    
2. Open another application on the mobile device.
    
3. On a different client, sign in to Lync with user B's account.
    
4. Send an IM from user B to user A.
    
5. Verify that the IM notification appears on user A's mobile device.
    

