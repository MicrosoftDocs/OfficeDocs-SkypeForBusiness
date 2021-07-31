---
title: Manage the join experience for Teams meetings in mobile browsers
author: lanachin
ms.author: v-lanachin
manager: samanro
audience: ITPro
ms.topic: article 
ms.service: msteams 
search.appverid: 
searchScope:
  - Microsoft Teams
  - Microsoft Cloud for Healthcare
f1.keywords:
- NOCSH
localization_priority: Normal
ms.collection: 
  - microsoftcloud-healthcare
  - m365solution-healthcare
  - m365solution-scenario
ms.reviewer: hafarmer
description: 
---

# Manage the join experience for Teams meetings in mobile browsers

Option 1

Microsoft Teams makes it easy for people to join appointments on their mobile devices. For a more seamless experience, attendees can join appointments such as healthcare visits, financial consultations, educator office hours and so on from a mobile browser. They don’t need to download and install Teams on their Android and iOS mobile devices.

When an attendee joins an appointment, they aren't prompted to download Teams to their mobile device. Instead, Teams opens in a mobile browser, where they can select **Join now** to connect to the meeting.

Currently, this *mobile browser join* experience is available for appointments that are scheduled through the following:

- [The Bookings app](../bookings-app-admin.md)
- [The Microsoft Teams Electronic Health Records (EHR) connector](healthcare/ehr-admin.md)


Option 2

Microsoft Teams makes it easy for people to join appointments such as healthcare visits, financial consultations, educator office hours and so on from their mobile devices. For a more seamless experience, attendees can join appointments from a mobile browser. They don't need to download and install Teams on their Android or iOS mobile devices.

When an attendee joins an appointment, they aren't prompted to download Teams to their mobile device. Instead, Teams opens in a mobile browser, where they can select **Join now** to connect to the meeting.

Currently, this *mobile browser join* experience is available for appointments that are scheduled through the following:

- [The Bookings app](../bookings-app-admin.md)
- [The Microsoft Teams Electronic Health Records (EHR) connector](healthcare/ehr-admin.md)

## Set up mobile browser join

### Appointments scheduled through the Bookings app

In Bookings, you can turn on this feature for specific appointment types and individual appointments. 

After you turn on the feature, attendees aren't prompted to download and install Teams when they join. The confirmation email or SMS text that’s sent to attendees will contain a meeting join link that opens Teams in a mobile browser. On Android devices, Teams opens in Chrome. On iOS devices, Teams opens in Safari. 

#### Turn on mobile browser join for an appointment type

In Bookings, go to **Settings** > **Appointment types**, select an [appointment type](https://support.microsoft.com/office/create-an-appointment-type-810eac77-6a65-4dc8-964d-c00eadf43887), and then turn on **Allow attendees to join from a mobile browser**.

:::image type="content" source="../media/mobile-browser-join-bookings-appointment-type.png" alt-text="Screenshot of the Allow attendees to join from a mobile browser setting for appointment types in the Bookings app":::

After you do this, mobile browser join is enabled for all appointments of this type.

#### Turn on mobile browser join for an individual appointment

In Bookings, select **New booking**, and then turn on **Allow attendees to join from a mobile browser**.
:::image type="content" source="../media/mobile-browser-join-bookings-form.png" alt-text="Screenshot of the Allow attendees to join from a mobile browser setting on the new booking form in the Bookings app":::

### Appointments scheduled through the Teams EHR connector

No setup needed! You don't need to do anything for patients to join Teams EHR connector appointments on a mobile browser.

The Teams EHR connector supports patients joining virtual visits through MyChart web and mobile. At the time of the appointment, patients can start a virtual visit from MyChart by using the **Begin virtual visit** button. The patient chooses the browser they want, and then Teams opens in that browser.

## Supported mobile browsers

Here are the mobile browsers that are currently supported. We support the latest version plus two previous versions, unless otherwise indicated.

|Platform  |Chrome |Safari |Edge (Chromium)|
|---------|:---:|:---:|:---:|
|Android   |   &#x2714;      |         |         |
|iOS    |         |  &#x2714; &sup1;       |         |
|macOS     |         |  &#x2714; &sup2;    |         |

&sup1; iOS apps on Safari can't select microphone and speaker devices. For example, Bluetooth devices. This is a limitation of the operating system, which controls controls the default device selection.

&sup2; Safari 14+ and macOS 11+ is needed for outgoing video support.

> [!NOTE]
> We're adding more capabilities to the meeting join experience in future releases of Teams, so check back for the most up-to-date information. To stay on top of upcoming Teams features, check out the [Microsoft 365 Roadmap](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=microsoft%2Cteams).

## Related articles

- [Virtual visits with Teams and the Bookings app](../bookings-app-admin.md)
- [Create an Bookings appointment type](https://support.microsoft.com/office/create-an-appointment-type-810eac77-6a65-4dc8-964d-c00eadf43887).
- [Join a Bookings appointment as an attendee](https://support.microsoft.com/office/join-a-bookings-appointment-as-an-attendee-95cea12d-2220-421f-a663-6efb20913c7f)
- [Virtual visits with Teams - Integration into EHR](healthcare/ehr-admin.md)
