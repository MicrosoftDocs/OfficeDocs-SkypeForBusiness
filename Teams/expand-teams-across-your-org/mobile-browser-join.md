---
title: Manage the join experience for Teams virtual visits on mobile browsers
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
ms.localizationpriority: medium
ms.collection: 
  - microsoftcloud-healthcare
  - m365solution-healthcare
  - m365solution-scenario
ms.reviewer: hafarmer
description: Learn about the join experience for Teams virtual visits on mobile browsers. 
---

# Manage the join experience for Teams virtual visits on mobile browsers

Microsoft Teams makes it easy for people to join appointments on their mobile devices without having to download Teams. For a more seamless experience, attendees can join appointments such as healthcare visits, financial consultations, educator office hours and so on from a mobile browser. Attendees don't need to install the Teams mobile app on their Android or iOS mobile devices.

With mobile browser join, when an attendee joins an appointment from a mobile device, they aren't prompted to download Teams. Instead, Teams opens in a mobile browser, where the attendee can select **Join now** to join. With this feature, keep in mind that if Teams is already installed on an attendee's mobile device, Teams will open in a mobile browser and not in the app.

Currently, mobile browser join is available for appointments that are scheduled through the following:

- [The Bookings app](https://support.microsoft.com/office/apps-and-services-cc1fba57-9900-4634-8306-2360a40c665b?ui=en-us&rs=en-us&ad=us#PickTab=Bookings)
- [Microsoft Teams Electronic Health Records (EHR) connector](healthcare/ehr-admin.md)

## Set up mobile browser join

### Appointments scheduled through the Bookings app

Schedulers in your organization can turn on this feature for specific appointment types and for individual appointments in the Bookings app.

After this feature is turned on, the confirmation email or SMS text that’s sent to attendees will contain a meeting join link that opens Teams in a mobile browser. On Android mobile devices, Teams opens in Chrome. On iOS mobile devices, Teams opens in Safari.

#### Turn on mobile browser join for an appointment type

In Bookings, go to **Settings** > **Appointment types**, select an [appointment type](https://support.microsoft.com/office/create-an-appointment-type-810eac77-6a65-4dc8-964d-c00eadf43887), and then turn on **Allow attendees to join from a mobile browser**. Doing this enables mobile browser join for all appointments of this type.

:::image type="content" source="../media/mobile-browser-join-bookings-appointment-type.png" alt-text="Screenshot of the Allow attendees to join from a mobile browser setting for appointment types in the Bookings app":::

#### Turn on mobile browser join for an individual appointment

In Bookings, select **New booking**, and then turn on **Allow attendees to join from a mobile browser**.

:::image type="content" source="../media/mobile-browser-join-bookings-form.png" alt-text="Screenshot of the Allow attendees to join from a mobile browser setting on the new booking form in the Bookings app":::

### Appointments scheduled through the Teams EHR connector

No set up is needed by you or your staff!

The Teams EHR connector supports patients joining virtual visits through MyChart web and mobile. At the time of the appointment, patients can start a virtual visit from MyChart by using the **Begin virtual visit** button. The patient chooses the browser they want, and then Teams opens in that browser.

## Supported mobile browsers

Here are the mobile browsers that are currently supported. We support the latest version plus two previous versions, unless otherwise indicated.

|Platform  |Chrome |Safari |Edge (Chromium)|
|---------|:---:|:---:|:---:|
|Android   |   &#x2714;      |         |         |
|iOS    |         |  &#x2714; &sup1;       |         |
|macOS     |         |  &#x2714; &sup2;    |         |

&sup1; iOS apps on Safari can't select microphone and speaker devices. For example, Bluetooth devices. This is a limitation of the operating system, which controls the default device selection.

&sup2; Safari 14+ and macOS 11+ is needed for outgoing video support.

## Things to consider

The staff member who conducts the virtual visit can share their screen from their Teams desktop, mobile, or web client with an attendee who joins from a mobile browser. However, attendees can't share their screen from a mobile browser.

> [!NOTE]
> We're adding more capabilities to the meeting join experience in future releases of Teams, so check back for the most up-to-date information. To stay on top of upcoming Teams features, check out the [Microsoft 365 Roadmap](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=microsoft%2Cteams).

## Related articles

- [Virtual visits with Teams and the Bookings app](bookings-virtual-visits.md)
- [Create an Bookings appointment type](https://support.microsoft.com/office/create-an-appointment-type-810eac77-6a65-4dc8-964d-c00eadf43887)
- [Join a Bookings appointment as an attendee](https://support.microsoft.com/office/join-a-bookings-appointment-as-an-attendee-95cea12d-2220-421f-a663-6efb20913c7f)
- [Virtual visits with Teams - Integration into EHR](healthcare/ehr-admin.md)
