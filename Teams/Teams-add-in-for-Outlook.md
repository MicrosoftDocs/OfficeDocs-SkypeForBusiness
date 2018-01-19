---
title: Use the Microsoft Teams Meeting add-in in Outlook
author: ChuckEdmonson
ms.author: chucked
manager: lolaj
ms.date: 01/12/2018
ms.topic: article
ms.service: msteams
description: Microsoft Teams installs an add-in into Outlook that lets users schedule a Teams meeting from Outlook.
MS.collection: Strat_MT_TeamsAdmin

---

Use the Teams Meeting add-in in Outlook
=======================================

When Microsoft Teams is installed, the Teams Meeting add-in is added to the Outlook Calendar ribbon. 

![Screenshot of Teams add-in on Outlook ribbon.](media/Teams-add-in-for-Outlook.png)

The Teams Meeting add-in is automatically installed for users who have Microsoft Teams and either Office 2013 or Office 2016 installed on their Windows PC. If you do not want the add-in to appear, you can learn how to [manage Outlook add-ins](https://support.office.com/en-us/article/View-manage-and-install-add-ins-in-Office-programs-16278816-1948-4028-91E5-76DCA5380F8D).

The Teams client will install the correct plug-in by determining if users need the 32-bit or 64-bit version.

Users can use the Teams Meeting add-in in Outlook to schedule online meetings in Microsoft Teams, just like they do with the Skype for Business add-in. 

> [!NOTE]
> The Teams Meeting add-in for Outlook is currently not available for Mac users.​

> [!NOTE]
> Some online meeting features, such as recording, polling, and whiteboarding are not yet available.

### Sign-in requirements

The Teams Meeting add-in requires users to sign in to Teams using Modern Authentication. If users do not use this method to sign in, they’ll still be able to use the Teams client, but will be unable to schedule Teams online meetings using the Outlook add-in. You can rectify this by doing the following:

- If Modern Authentication is not configured for their organization, the admin should configure Modern Authentication.
- If Modern Authentication is configured, but they cancelled out on the dialog box, users should sign in again using multi-factor authentication.

You can learn more about Modern Authentication in Microsoft Teams here.

### LimatatDeployment considerations

NISHANTH: Are there any deployment considerations (e.g., 32-bit vs. 64-bit, C2R vs. MSI) that should be mentioned?

### Other considerations

The Teams Meeting add-in is still building functionality, so be aware of the following:
- Some online meeting features, such as recording, polling, and whiteboarding are not yet available.
- Currently, you can only invite people from within your company, as it is not yet possible for external users to join meetings.
- The add-in is for scheduled meetings with specific participants, not for meetings in a channel. Channel meetings must be scheduled from within Teams. Currently, the Teams Meeting add-in in Outlook is only available for Windows users, but support for Mac is coming.
- The add-in will not work if an Authentication Proxy is in the network path of user's PC and Teams Services.

Learn more about [meetings and calling in Microsoft Teams](https://support.office.com/en-us/article/Meetings-and-calls-d92432d5-dd0f-4d17-8f69-06096b6b48a8?ui=en-US&rs=en-US&ad=US).

