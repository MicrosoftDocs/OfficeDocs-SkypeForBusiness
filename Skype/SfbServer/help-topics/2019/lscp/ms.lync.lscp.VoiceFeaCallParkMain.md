---
title: "Call Park"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
audience: ITPro
ms.topic: article
ms.custom:
- ms.lync.lscp.VoiceFeaCallParkMain
ms.prod: skype-for-business-itpro
f1.keywords:
- CSH
ms.localizationpriority: medium
ms.assetid: b752617d-554d-470e-b17b-387403ac74ed
ROBOTS: NOINDEX, NOFOLLOW
description: "When a call is parked, it is transferred to a temporary number where the call is held until someone retrieves it or it times out. You need to configure a table with the ranges of extension numbers that you are reserving for parked calls. These extensions need to be virtual extensions (that is, extensions that have no user or phone assigned to them). Each pool that runs the Call Park application can have one or more ranges of extensions. These ranges must be globally unique across your deployment."
---

# Call Park

When a call is parked, it is transferred to a temporary number where the call is held until someone retrieves it or it times out. You need to configure a table with the ranges of extension numbers that you are reserving for parked calls. These extensions need to be virtual extensions (that is, extensions that have no user or phone assigned to them). Each pool that runs the Call Park application can have one or more ranges of extensions. These ranges must be globally unique across your deployment.

The **Call Park** page displays a list of all the Call Park number ranges that are defined for your organization.

## Tasks you can perform

You can perform the following tasks from the **Call Park** page:

- Create a new number range

- Change an existing number range

- Delete a number range

## UI Reference

The following list describes the commands on the page.

- **New** Starts a new Call Park number range.

- **Edit** Opens the selected number range for editing, selects all number ranges in the list, or deletes the selected number range.

- **Refresh** Refreshes the list of number ranges.

The following list describes the fields on the page.

- **Name** The unique name that identifies the number range.

- **Start range** The beginning number of the range.

- **End range** The ending number of the range.

- **Destination** The fully qualified domain name (FQDN) or service ID of the Application service that hosts the Call Park application for the number range.

For details about Call Park features and capabilities, see [Plan for Call Park in Skype for Business](../../../plan-your-deployment/enterprise-voice-solution/call-park.md). For details about working with Call Park number ranges, see [Configure Phone Number Extensions for Parking Calls](/previous-versions/office/lync-server-2013/lync-server-2013-configure-phone-number-extensions-for-parking-calls).