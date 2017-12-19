---
title: Add the Microsoft Teams SMTP domain as an accepted domain in Exchange Online | Microsoft Support
author: LolaJacobsen
ms.author: lolaj
manager: lolaj
ms.date: 09/25/2017
ms.topic: article
ms.service: msteams
description: Learn to add the Microsoft Teams SMTP domain as an accepted domain in Exchange Online to send notifications to team members.

---

Add the Microsoft Teams SMTP domain as an accepted domain in Exchange Online 
=============================================================================

Whether you create an Office 365 Group in the admin console or by using Outlook, Exchange Online is used to send notifications of a team member being added to a Group. These messages are generated from your tenant as they represent your default domain SMTP FQDN.

![Screenshot of an example Outlook email message header showing a user has been added to a group.](media/Add_the_Microsoft_Teams_SMTP_domain_as_an_accepted_domain_in_Exchange_Online_image1.jpg)

Teams uses Microsoft Exchange Online as well to send notifications to team members when they’ve been added. The difference being the domain FQDN of the SMTP message is “@email.teams.microsoft.com” and could be caught by spam filtering. As you can see from the image below, Outlook considers this message as an external sender which is subject to standard security features such as blocking images and certain content.

![Screenshot of an example Outlook email message header showing a user has been added to a group.](media/Add_the_Microsoft_Teams_SMTP_domain_as_an_accepted_domain_in_Exchange_Online_image2.jpg)

For best result and seamless operation, consider adding the Microsoft Teams SMTP domain to your “accepted domains” list in your Exchange Online spam configuration:

![Screenshot of the Allow lists section of Exchange Online spam configuration settings.](media/Add_the_Microsoft_Teams_SMTP_domain_as_an_accepted_domain_in_Exchange_Online_image3.png)
