---
title: Microsoft Teams Rooms Portal
author: donnah007
ms.author: v-donnahill
manager: serdars
ms.reviewer: dstrome 
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
description: Adding MSA role in the service portal.
f1keywords: 
---


# Access control: Adding Managed Service Administator roles in the service portal 


1. Log in with your tenant user account to ervice portal. 
1. Navigate to the Settings panel.
1. Click "Managed Service Administrator" text takes you to the following experience.   


![Figure 13](media/rooms-portal-guide.013.jpg) 



5. Select  "Add Member"  to add the email address of the users you want to add to this role. You must do this one user at a time.  

<!--[Figure 14](media/rooms-portal-guide.014.jpg)  -->


### Access control for the portal: Set Policy 
Important: Please review this section and make sure that access to the portal is limited based on your business needs. 

1. Navigate to Azure portal and select Azure Active Directory. 

![Figure 15](media/rooms-portal-guide.015.jpg) 



1. Select Enterprise Applications.

![Figure 16](media/rooms-portal-guide.016.jpg)  



1. Select FastTrack Rooms in the Application List.



![Figure 17](media/rooms-portal-guide.017.jpg) 



![Figure 18](media/rooms-portal-guide.018.jpg) 

1. Within FastTrack Rooms, select the **Properties** tab, and check **User Assignment Required**. 



1. Navigate to “Users and Groups” to control access to the application. Currently, role assignment is not relevant to the program and does NOT have any effect on user privileges. 

<!--![Figure 19](media/rooms-portal-guide.019.jpg) -->