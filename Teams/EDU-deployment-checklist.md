---
title: Deployment checklist for EDU - Microsoft Teams
author: LolaJacobsen
ms.author: lolaj
manager: lolaj
ms.date: 11/13/2017
ms.topic: article
ms.service: msteams
description: Checklist for planning a Microsoft Teams deployment for EDU.
Set_Free_Tag: Strat_MT_TeamsAdmin
---

Deployment checklist for EDU: Microsoft Teams
=============================================

This article outlines considerations for IT Admins to explore when deciding how to manage Teams within their school. Not everything listed will require action, it’s just here to give you an understanding of how to manage different parts of the product that aren’t directly controlled by the settings for Teams. 

This is an important distinction to understand: Teams is built on top of other services to provide its hub experience. This means that particular settings must be changed in the core service to control behavior in Teams. 

To get an quick overview of how Teams fits into our Office 365 vision, check out [Microsoft Teams Overview](Teams-overview.md). This is where you'll find all of our Teams IT Admin documentation too.
 
## I want to jump right in and deploy Teams
The Teams Quick Start Guide for EDU walks you through Teams deploymnet using recommended settings. It covers best practices for several key actions:

 - Managing team creation 
 - Team naming conventions


## Groups
Teams uses Office 365 Groups to handle its team construct and permission controls for its members. If you want to learn about all the great work that's happening with Office 365 groups, check out their blog post from the Ignite 2017 conference, [Office 365 Groups at Microsoft Ignite 2017](https://techcommunity.microsoft.com/t5/Office-365-Blog/Office-365-Groups-at-Microsoft-Ignite-2017/ba-p/114795). One particular session of interest is Unleash Office 365 Groups: Deep Dive where they walk through the next two sections with a live demo and give you some tips and tricks along the way.

## Managing team creation
The primary concern many admins have for Teams is around who can create teams (the underlying group). Office 365 Groups does recommend having a self-serve model where all users can create Teams (Groups), it’s probably not a one size first all recommendation, especially for the schools of Kindergarten to Grade 12. 

Check out our guidance on how to [Plan for Office 365 Groups when creating teams in Microsoft Teams](plan-Office-365-groups.md) routinely to stay up to date with our guidance. The [Manage who can create Office 365 Groups](https://support.office.com/en-us/article/Manage-who-can-create-Office-365-Groups-4c46c8cb-17d0-44b5-9776-005fced8e618) article demonstrates how to use PowerShell to control these permissions and what kind of licenses are required to take advantage of these features. 

## Team naming convention 
Office 365 Groups are currently previewing their feature for allowing IT Admins to enforce group naming policies with Prefix, Suffix, and blocked words. A few IT Admin roles do have the permissions to override these rules and name a group as they please or the business requires.   If these are controls you need in your tenant, you can get the implementation details on [Office 365 Groups naming policy](https://support.office.com/en-us/article/Office-365-Groups-Naming-Policy-6ceca4d3-cad1-4532-9f0f-d469dfbbb552). If you are interested in trying out these features, you can reach out to Mike McLean (mmclean@microsoft.com) or Vijay Nelson (vlnelson@microsoft.com) and request to be added to the private preview. 

This is a great way to start the crawl, walk, run approach for self-serve group creation in higher education. Start with a servicing desk that takes in groups. Then, once you have all your naming conventions and blocked works set, slowly enable it for staff, then eventually everyone. 

1. Concerned about groups showing up in the mailing list
1. How to prevent name collisions 
2. AD Security groups that have similar group names to Team created groups


## Guest Access

Guest access is a great way to leverage collaboration for those who are outside of your tenant to participate in your teams such as guest lecturers or speakers. Our article [Set up guest access to Teams](set-up-guests.md) highlights all the controls that are available to you as an IT Admin. Our other [Guest Access](guest-access.md) describe the experience for admins and users when adding\interacting with Guests. 

1. Should we speak about guest lecturer scenario?
2. What does cross university research scenario look like?
3. Group Expiration Policy by User group?
4. Ie. Student groups should expire after 4 month (semester) or 4 years (degree timeframe?)

## SharePoint

Teams uses SharePoint as the default file storage provider. Read more at [How SharePoint Online and OneDrive for Business interact with Microsoft Teams](SharePoint-OneDrive-interact.md). If you want to use a third-party storage provider, read more on Custom cloud storage <need link here!>. 

## Managing storage quota

IT Admins who want to know how their quota is calculated and how best to manage it should head over to [Manage site collection storage limits](https://support.office.com/en-us/article/Manage-site-collection-storage-limits-77389C2C-8E7E-4B16-AB97-1C7103784B08) for more details. If you don’t want to be bothered with managing each site’s collection, they show you how to let the service automatically handle that for you. 

## Security and Compliance

Legal Hold: [Place a Microsoft Teams user or team on legal hold](legal-hold.md)

## Client Updates

## Release Notes

## Getting started with T-Bot

## School Data Sync

Is this something we even want to talk about or recommend. Maybe. Follow up with Michael W Lam on what happens in year 2. 

