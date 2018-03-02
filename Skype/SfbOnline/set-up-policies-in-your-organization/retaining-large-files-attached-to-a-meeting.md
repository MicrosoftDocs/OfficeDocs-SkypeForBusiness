---
title: "Retaining large files attached to a Skype for Business meeting"
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.reviewer: brendonb, markjjo
ms.date: 01/22/2018
ms.topic: article
ms.assetid: 12203a1a-4a9f-4838-88c5-3740ea16ed8d
ms.tgt.pltfrm: cloud
ms.service: skype-for-business-online
ms.collection: Adm_Skype4B_Online
ms.audience: Admin
appliesto:
- Skype for Business
localization_priority: Normal
f1keywords: None
ms.custom:
- Setup
description: "You can attach files to a Skype for Business meeting, which participants can then open and download. Files attached to Skype for Business meetings are retained in the mailboxes of any participant whose mailbox is placed on Litigation Hold, has an Office 365 retention policy applied, or is placed on a hold associated with an eDiscovery case in the Office 365 Security &amp; Compliance Center. This content is saved to participants' Recoverable Items folders in their mailboxes."
---

# Retaining large files attached to a Skype for Business meeting

You can attach files to a Skype for Business meeting, which participants can then open and download. Files attached to Skype for Business meetings are retained in the mailboxes of any participant whose mailbox is placed on Litigation Hold, has an Office 365 retention policy applied, or is placed on a hold associated with an eDiscovery case in the Office 365 Security &amp; Compliance Center. This content is saved to participants' **Recoverable Items** folders in their mailboxes.
  
Files that are retained in mailboxes on hold are indexed and can therefore be searched when running a Content Search in the Security &amp; Compliance Center when searching a participant's mailbox. However, attached files that are larger than 39 MB are split into two or more smaller files and saved as compressed (.zip) files. The  *content*  of these smaller files is not indexed for search, and might not be returned in a Content Search. However, the *metadata*  of these files (such as the file name and author) is indexed for search, and might be returned in a Content Search.
  
> [!NOTE]
> If the mailbox is full or the tenant admin has configured MaxSendSize to be smaller than 39 MB, uploaded file data will not be retained at all. The default MaxSendSize is 150 MB, but tenant admins can configure MaxSendSize to be as small as 1 MB. 
  
Mailboxes that are not on hold will not have any meeting data saved. For example, in a three-person meeting in which the mailboxes of two participants are marked for retention, the meeting data is saved to the mailboxes of those two participants, but not to the mailbox of the third participant, whose mailbox is not on hold.
  
## Related topics
[Create custom external access policies](create-custom-external-access-policies.md)

[Block point-to-point file transfers](block-point-to-point-file-transfers.md)

[Set up client policies for your organization](set-up-client-policies-for-your-organization.md)

[Set up conferencing policies in your organization](set-up-conferencing-policies-for-your-organization.md)
  
## Feedback?
To provide product feedback or to let us know how we're doing, see [Skype for Business Feedback](https://www.skypefeedback.com).