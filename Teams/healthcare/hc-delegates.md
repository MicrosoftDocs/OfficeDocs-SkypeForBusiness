---
title: "A user can explicitly set a delegate status and pick/assign another user as the delegate. The person who has been assigned as a delegate is notified that they have been nominated to be a delegate. When a chat conversation or compose mode is initiated with the target user who has a delegate assigned,  banner shows the sender clearly that messages should be sent to the assigned delegate instead. "
author: jambirk
ms.author: jambirk 
manager: serdars
audience: ITPro
ms.topic: article 
ms.service: msteams 
search.appverid: MET150
localization_priority: Normal
MS.collection: Teams_ITAdmin_PracticalGuidance
appliesto:
- Microsoft Teams
ms.reviewer: vanido
description: (may 19) A user can explicitly set a delegate status and pick/assign another user as the delegate. The person who has been assigned as a delegate is notified that they have been nominated to be a delegate. When a chat conversation or compose mode is initiated with the target user who has a delegate assigned,  banner shows the sender clearly that messages should be sent to the assigned delegate instead. 
---

# Set a delegate status

A user can explicitly set a delegate status and pick/assign another user as the delegate. The person who has been assigned as a delegate is notified that they have been nominated to be a delegate. When a chat conversation or compose mode is initiated with the target user who has a delegate assigned,  banner shows the sender clearly that messages should be sent to the assigned delegate instead.

This is a user-initiated process in the client, and Admin involvement is limited to enabling the feature in the O365/Teams tenant. Presumably allowing auto-forward this will be another setting in the Messaging policy screen.

## Delegation overview

*Usage example without setting delegates:*  Dr. Franco Piccio is on-call at the radiology department. He receives an urgent personal call and has to step away for the next couple of hours. He asks one of his peers in the radiology department, Dr. Lena Ehrle, to cover for him while he is gone. He informally hands over his pager to Dr. Ehrle, who is listening for urgent messages and pings on the pager and responds to them on behalf of Dr. Piccio in addition to her current responsibilities. Others on the team may not realize the informal delegation happened, and confusion ensues with a patient's care.

*Usage example with setting delegates:* Dr. Franco Piccio is on-call at the radiology department. He receives an urgent personal call and has to step away for the next couple of hours. He asks one of his peers in the radiology department, Dr. Lena Ehrle to cover for him while he is gone. He changes his status in Teams to do not disturb and sets Dr. Ehrle as a delegate, enabling auto-forward of messages. Others on the team realize the delegation happened as they're attempting to contact Dr. Piccio, and little to no confusion ensues with a patient's care.

## [OPTIONAL] Planning for feature

Some features would require careful pre-planning before deployment can begin. For those features, cover what planning tasks customers should complete.

## Configure feature

How do you configure this feature? Cover these points: 

- Are there any prerequisites?

- Is this feature per org or per user? 

- Use PowerShell or UI?

- Short instructions on how to turn on the feature for the organization or for individual users. 

## Manage feature

- Add subsections with basic management tasks that would be required or that we expect customer to perform. 

### Management task 1

### Management task 2

## Security & Compliance

List any security or compliance impact of this feature here. Cover the following:

- Where is the data associated with this feature stored?

- Include any other data implications such as GDPR compliance.


## Related topics

[Get started with Teams for Healthcare organizations](teams-in-hc.md)
