---
title: "Location Policy Create New or Edit Existing"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.lscp.NcsLocEdit
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: d9b30b3b-570b-49a6-b2b4-46b0cf490153
ROBOTS: NOINDEX, NOFOLLOW
description: "You can configure Location policies to determine whether Enhanced 9-1-1 (E9-1-1) is enabled and how it is used, as well as how location information is used for users and contacts."
---

# Location Policy: Create New or Edit Existing

You can configure Location policies to determine whether Enhanced 9-1-1 (E9-1-1) is enabled and how it is used, as well as how location information is used for users and contacts.

## UI Reference

The following list describes the fields on the page.

- **Scope** Identifies the scope of the location policy that you are creating or modifying: global, site, or user.

- **Name** Each location policy requires a name. Global and site location policies are named by default, and the name cannot be changed. For user location policies, use a descriptive name that identifies the user or group of users.

    > [!NOTE]
    > After you save the location policy, the name cannot be changed.

- **Enable Enhanced 9-1-1 (E9-1-1)** Select this check box to enable E9-1-1 for users who are assigned this location policy.

- **Location** Specify whether users are prompted for location information:

  - **Required** Select this option if users are to be prompted for location information when their client registers at a new location. Users can dismiss the prompt without entering location information.

  - **Not required** Select this option if users are not to be prompted for location information.

  - **Disclaimer** Select this option if users are to be prompted for location information, but will see a disclaimer message if they decline the prompt without entering the information. Users can complete an emergency call but no other calls until they enter the location information.

- **Use location for E9-1-1 only** Select this check box if location information is to be used only for emergency calls.

- **PSTN usage** Select the public switched telephone network (PSTN) usage that will be used to determine which voice route will be used for routing emergency calls from clients that use this profile. The route associated with this usage should point to a SIP trunk dedicated to emergency calls or to an Emergency Location Identification Number (ELIN) gateway that routes emergency calls to the nearest Public Safety Answering Point (PSAP). Options are **Internal**, **Local**, or **Long distance**.

- **E9-1-1 dial number** Specify the number that is dialed to reach emergency services.

- **E9-1-1 dial mask** Specify a number that a user dials, which is then translated into the emergency dial number. For example, enter a value of 212 in this field so that a user can dial 212 to reach emergency services. This allows for alternate emergency numbers to be dialed and still have the call reach emergency services (for example, if someone from a country or region with a different emergency number attempts to dial that country or region's number rather than the number for the country or region they are currently in). You can define multiple emergency dial masks by separating the values with semicolons. For example, 212;414. The maximum length of the string is 100 characters. Each character must be a digit 0 through 9.

    > [!IMPORTANT]
    > Make sure that the dial mask is not the same as a number in a call park number range, because call park routing takes precedence over emergency dial string conversion. To see the Call Park number ranges, click **Voice Features** in the left navigation bar, and then click **Call Park**.

- **Notification URI** Specify one or more SIP URIs to be notified when an emergency call is made. For example, type the company security office's SIP URI to notify security staff with an instant message whenever an emergency call is made. If the caller's location is available, the location is included in the notification. You can specify multiple SIP URIs as a comma-separated list. For example, "sip:security@litwareinc.com","sip:kmyer@litwareinc.com". The string must be from 1 to 256 characters in length and must begin with the prefix "sip:". You can also specify distribution lists.

- **Conference URI** Specify the SIP URI (telephone number, in this case) for a third party to be conferenced in to emergency calls. For example, type the company security office's phone number so that they receive a call when an emergency call is made. The setting for **Conference mode** determines whether the third party can participate or just listen in to the call. The string must be from 1 to 256 characters in length and must begin with the prefix sip:.

- **Conference mode** If you specified a value for **Conference URI**, set this field to one of the following values:

  - **One-way** Specifies that the third party can only listen in to the call between the caller and the PSAP operator.

  - **Two-way** Specifies that the third party can participate in the call between the caller and the PSAP operator.

For details about Enterprise Voice emergency service features and capabilities, see [Overview of E9-1-1](https://technet.microsoft.com/library/c01e6774-bc9f-4c5b-a60b-478b7317b2b7.aspx) in the Planning documentation. For details about working with location policies, see [Configuring Location Policy](https://technet.microsoft.com/library/14e41bcb-ea0a-49c2-99b3-1f61fc34416d.aspx) in the Operations documentation.


