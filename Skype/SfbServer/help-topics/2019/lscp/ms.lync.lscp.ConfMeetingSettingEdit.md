---
title: "Meeting Configuration Create New or Edit Existing"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.lscp.ConfMeetingSettingEdit
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: e8fc19fa-6cd7-4f68-b90a-1c7e1b649abd
ROBOTS: NOINDEX, NOFOLLOW
description: "Meeting configuration settings define the user join experience for conferences scheduled by users. These settings only apply to scheduled meetings. They do not apply to ad-hoc meetings created by clicking the Meet Now option in the client."
---

# Meeting Configuration: Create New or Edit Existing

Meeting configuration settings define the user join experience for conferences scheduled by users. These settings only apply to scheduled meetings. They do not apply to ad-hoc meetings created by clicking the **Meet Now** option in the client.

## UI Reference

The following list describes the fields on the page.

- **Scope** Identifies the scope of the meeting configuration that you are creating or modifying: global, site, or pool.

- **Name** Meeting configurations are named by default, and the name cannot be changed.

- **PSTN callers bypass lobby** Select this check box to automatically admit users who are dialing in to the conference over a public switched telephone network (PSTN) phone line. Clear this check box to route PSTN callers to the conference lobby, where they are on hold until a conference presenter grants them access to the conference.

- **Designate as presenter** Select the category of users (besides the meeting organizer) who are automatically designated as presenters when they join a conference. Regardless of this setting, presenters can be explicitly designated as presenters when the conference is scheduled, or they can be explicitly promoted to presenter during the conference. The options are:

  - **None** Select this option if no one other than the organizer is automatically designated as a presenter.

  - **Company** Select this option to automatically designate only members of your organization as presenters.

  - **Everyone** Select this option to automatically designate anyone to be a presenter.

- **Assigned conference type by default** This setting controls whether the Outlook Conferencing Addin always schedules conferences by using the organizer's assigned conference, which means that scheduled conferences always have the same join URL and audio information. Select this check box to have scheduled conferences always use the same join URL. Clear this check box to use a different join URL for each conference.

- **Admit anonymous users by default** Select this check box if anonymous (that is, unauthenticated) users are allowed to attend conferences by default. Clear this check box if anonymous users are not allowed to attend conferences by default.

- **Logo URL** Type the URL that has the image to be used for custom conference invitations.

- **Help URL** Type the URL for a website where users can obtain assistance for joining the conference.

- **Legal text URL** Type the URL for a website that has the legal information and disclaimers for the conference.

- **Custom footer text** Type the text to be used on custom conference invitations.

For details about working with meeting configurations, see [Create a or modify a Collection of Meeting Configuration Settings](https://technet.microsoft.com/library/ce6773c1-a0d5-4405-8e32-33a6f3a46a1a.aspx) in the Operations documentation. For details about setting meeting configurations for large meetings, see [Setting Up Support for Large Meetings](https://technet.microsoft.com/library/8e22d34b-b395-408d-9d48-8f2a3abe9513.aspx) in the Planning documentation.


