---
title: "Enable or Disable Offline Instant Messaging (IM) in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: quickstart
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: c0f44352-fb4a-45d3-85b0-a4320d4b8339
description: "Learn to enable or disable Offline Instant Messaging (IM) in Skype for Business Server."
---

# Enable or Disable Offline Instant Messaging (IM) in Skype for Business Server
 
Learn to enable or disable Offline Instant Messaging (IM) in Skype for Business Server.
  
## Enable Offline Instant Messaging (IM) in Skype for Business Server

Offline IM is a client side feature built into Skype for Business client (2016 C2R build 16.0.6701.1000 or higher) that leverages Exchange Web Services (EWS) to send messages from the Skype for Business client to a user's Exchange mailbox. Offline IM uses Exchange Web Services (EWS) to send Offline messages from the Skype for Business client to the mailbox of recipient. EWS must be available to the Skype for Business client for Offline messages to be sent. To learn more about planning for instant messaging and presence, see [Plan for instant messaging and presence in Skype for Business Server](../../plan-your-deployment/instant-messaging-and-presence.md).
  
> [!NOTE]
> If the user's mailbox is hosted in Exchange On-Premises, the Skype for Business client (2016 C2R build 16.0.6920.1000) is required 
  
### To enable or disable Offline IM in Skype for Business Server

1. Open the Skype for Business Server Management Shell.
    
2. Run the following command to enable Offline IM.
    
   ```
   Set-CsImConfiguration -EnableOfflineIM $True
   ```

    > [!NOTE]
    > In Skype for Business Server 2015 CU3, the EnableOfflineIM option is set to $True by default. To disable, set this value to $False. 
  
3. Run the following command to confirm the ability to store Offline IM's is set.
    
   ```
   Get-CsImConfiguration
   ```

## Offline IM Integration with Exchange

Offline IM will not be available to senders if they have a client policy that disables automatic saving of Offline messages to the conversation history folder (EnableIMAutoArchiving = $false). There is no mechanism to check if the recipient is able to receive Offline messages.
  
For Offline messages sent within the same organization they will be received as an email message with message class of IM.Note.MissedConversation and will be included in Outlook **Missed Conversation** folder, as well as conversation history which will be picked up in recent list/conversation history tab in Skype for Business clients.
  
For Offline messages sent from federated organization they will be received as an email message without IM.Note.MisssedConversation and will not be picked up in the missed conversation or conversation history folders. 
  
## Troubleshooting

There is a two minute timer from when an offline message is sent to when it's picked up and processed. If offline messages can't be processed they will appear in the following directory: 
  
  <pre>  %localappdata%\microsoft\office\16.0\lync\SipUserAddress\History Spooler   </pre>

The primary Skype for Business ETL log will contain information about Offline message processing and is your best source for investigation/troubleshooting. 
  
> [!NOTE]
> An issue has been reported where Offline messages failed to send and the 'Drafts' folder was getting filled with messages. This occurred with Exchange On-Premises mailboxes. The issue has been fixed in all C2R channels as of 6/14/2016.  
