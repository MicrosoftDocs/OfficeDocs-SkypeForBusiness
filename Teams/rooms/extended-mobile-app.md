---
title: Mobile App extension
author: donnah007 
ms.author: v-donnahill
manager: serdars
ms.date: 04/09/2022
ms.reviewer:dstrome
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Mobile application extension for Teams Rooms
f1keywords: Microsoft Teams Rooms Managed Service mobile app extension
---

This document intends to describe and summarize how Microsoft Teams Rooms – Managed Service will integrate and incorporate a newly formed mobile application into its ecosystem. This document is focused on the high-level overview of the plan for the mobile application and how the project was approached. This also goes over scenarios and use cases for the mobile application.

Scenarios

1. Enable a seamless MTR Managed Services experience via a mobile application
- Receive push notifications for new incidents. Tapping the notification opens the incident details opens the incident details immediately
- List all active and resolved incidents including read and unread status on messages
- View the basic incident details with ticket information – including messages
- Viewing ticket attachments and files
- A basic user panel with the option to sign out (you will not get notifications/messages if signed out)

1. Integrate the ability to act on a ticket within the application
- Acknowledge incident (mark as read)
- Read, post, and reply to messages on a ticket
- Dark Mode (Full accessibility in V2)
- Capability to add an attachment (take and upload pictures) 
- Report on an incident (Creating a ticket)

Use Case

Our mobile application should follow our design principles, be consistent with our portal experience without taking any component away from it and add to the overall MTR Managed Services experience, also it should enable the one stop experience for customers to report and manage incidents in their organization through the application. 

*Loading Screen
![Text, letter Description automatically generated](../media/extended-mobile-app-001.png)  

Sign in
![Graphical user interface, application, TeamsDescription automatically generated](../media/extended-mobile-app-002.png)   

Incidents Page*
![Graphical user interface, text, application, emailDescription automatically generated](../media/extended-mobile-app-003.png)
 

*Incidents Loading
![Table Description automatically generated](../media/extended-mobile-app-004.png)

Ticket Details
![Text, table Description automatically generated with medium confidence](../media/extended-mobile-app-005.png)

Ticket Messages Loading*![A picture containing icon Description automatically generated](../media/extended-mobile-app-006.png)



 
*Ticket Attachments
![Graphical user interface, text, application Description automatically generated](../media/extended-mobile-app-007.png)

Error – General
![Graphical user interface, text, application, email Description automatically generated](../media/extended-mobile-app-008.png)

Error – General (2)*
![A picture containing chart Description automatically generated](../media/extended-mobile-app-009.png)


*Empty State
![Text, application Description automatically generated](../media/extended-mobile-app-010.png)

User
![Text Description automatically generated with medium confidence](../media/extended-mobile-app-011.png)

Report Incident*
![Graphical user interface, application Description automatically generated](../media/extended-mobile-app-012.png)