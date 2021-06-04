---
title: 'Teams voice Contoso case study: Audio Conferencing'
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.date: 06/17/2020
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - M365-voice
ms.reviewer: jowrig
search.appverid: MET150
f1.keywords:
- NOCSH
description: Teams voice case study for multi-national corporation - audio conferencing
appliesto: 
  - Microsoft Teams
---

# Contoso case study: Audio Conferencing

To gain an understanding of audio conferencing&mdash;what it is, what it costs, availability, and how it works&mdash;Contoso reviewed [Audio Conferencing in Office 365](deploy-audio-conferencing-teams-landing-page.md). 

## Overview 

For audio conferencing, Contoso used phone numbers that are well known within the organization as well as externally. Because Contoso wanted to maintain these numbers where possible, they reviewed the information on assigning dedicated and shared phone numbers to the audio conferencing bridge. 

Based on their research, Contoso made the following decisions: 

- Only a segment of the population that regularly host audio conferencing calls would receive Audio Conferencing licenses. 

- Contoso would use dedicated phone numbers and port their existing numbers for use with Audio Conferencing.   

Because Contoso users were using Skype for Business and all users' mailboxes reside online, many users have existing meetings scheduled. Contoso read [Using the Meeting Migration Service (MMS)](/SkypeForBusiness/audio-conferencing-in-office-365/setting-up-the-meeting-migration-service-mms?bc=%2fmicrosoftteams%2fbreadcrumb%2ftoc.json&toc=%2fMicrosoftTeams%2ftoc.json) to learn that existing meetings are updated automatically for Contoso when they change the end user to TeamsOnly mode.  


## Configuration

Phone numbers that are associated with audio conferencing are referred to as service numbers within Phone System. 

- For locations using Calling Plans, to port their existing phone numbers from their phone carrier to Office 365, Contoso followed the steps in [Getting service phone numbers](getting-service-phone-numbers.md).

- To assign the Audio Conferencing license to the end user in the technical pilot, the Contoso administrator followed the steps in [Manage the Audio Conferencing settings for your organization](manage-the-audio-conferencing-settings-for-my-organization-in-teams.md). 

- For the business pilot and migration, Contoso used group-based licensing by following the steps in [Assign licenses to users by group membership in Azure Active Directory](/azure/active-directory/users-groups-roles/licensing-groups-assign).  

 

