---
title: Manage meeting settings in Microsoft Teams
author: lanachin
ms.author: v-lanac
manager: serdars
ms.reviewer: sonua
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.audience: Admin
appliesto: 
- Microsoft Teams
localization_priority: Normal
search.appverid: MET150
MS.collection: Teams_ITAdmin_Help
description: Learn how to manage settings for Teams meetings that users schedule in your organization. 
---

# Manage meeting settings in Microsoft Teams

As an admin, use Teams meetings settings to control whether anonymous users can join Teams meetings, customize meeting invitations and if you want to enable Quality of Service (QoS), set ports for real-time traffic. These settings apply to all Teams meetings that users schedule in your organization. You can easily manage these settings from **Meetings** > **Meeting settings** in the Microsoft Teams & Skype for Business admin center. 

## Allow anonymous users to join meetings

With anonymous join, anyone can join the meeting as an anonymous user by clicking the link in the meeting invite. 

![teams-logo-30x30.png](media/teams-logo-30x30.png) Using the Microsoft Teams & Skype for Business admin center
1. In the left navigation, go to **Meetings** > **Meeting settings**. 
2. Under **Participants**, turn on **Anonymous users can join a meeting**. 

    ![meeting-settings-participants.png](media/meeting-settings-participants.png "Screen shot of the participants settings for Teams meetings in the Microsoft Teams & Skype for Business adin center")

If you don't want anonymous users to join meetings scheduled by users in your organizaiton, turn off this setting. 
## Customize meeting invitations

You can customize Teams meeting invitations to meet your organization's needs. You can add your organization's logo and include helpful information, such as links to your support website and legal disclaimer, and a text-only footer. 

### Tips for creating a logo for meeting invitations  

1. Create an image that's no more than 188 pixels wide by 30 pixels tall (it's quite small). [NEEDS REVIEW]
2. Save the image in JPG format.   
3. Store the image in a central location that everyone in your organization can access, such as a network share. 

### Customize your meeting invitations

![teams-logo-30x30.png](media/teams-logo-30x30.png) Using the Microsoft Teams & Skype for Business admin center

1. In the left navigation, go to **Meetings** > **Meeting settings**.
2. Under **Email invitation**, do the following: 

    ![meeting-settings-invitation.png](media/meeting-settings-invitation.png "Screen shot of the meeting invitation settings that you can customize for Teams meetings") 

    - **Logo URL** Enter the URL where your logo is stored. 
    - **Legal URL** If your organization has a legal website that you want people to go to for any legal concerns, enter the URL here. 
    - **Help URL** If your organization has a support website that you want people to go to if they run into issues, enter the URL here.
    - **Footer** Enter text that you want to include as a footer. 
3. Wait an hour or so for the changes to propagate across all Office 365 services. Then schedule a Teams meeting to see what the meeting invitation looks like.  

    [NEEDS REVIEW: ADD SCREEN SHOT OF CUSTOM MEETING INVITE]

## Set how you want to handle real-time media traffic for Teams meetings (coming soon) 
If you're using QoS to prioritize network traffic, you can enable QoS markers and you can set port ranges for each type of media traffic. 

 ![teams-logo-30x30.png](media/teams-logo-30x30.png) Using the Microsoft Teams & Skype for Business admin center

1. In the left navigation, go to **Meetings** > **Meeting settings**. 
2. Under **Network**, do the following:

    ![meeting-settings-network.png](media/meeting-settings-network.png "Screen shot of the network settings for Teams meetings in the Microsoft Teams & Skype for Business admin center")

    - To enable QoS markers, turn on **Insert Quality of Service (QoS) markers for real-time media traffic**.
    - To specify port ranges, next to **Select a port range for each type of real-time media traffic**, select  **Specify port ranges**, and then enter the starting and ending ports for audio, video, and screen sharing. 
    
        If you select **Automatically use any available ports**, available ports between 1024 and 65535 are used. 

 ### Related topics
- [Quality of Service (QoS) in Teams](qos-in-teams.md)

