---
title: Walkie Talkie usage and performance report
author: lana-chin
ms.author: v-chinlana
manager: jtremper
audience: admin
ms.topic: conceptual
ms.service: microsoft-365-frontline
ms.reviewer: yinchang
ms.date: 10/13/2023
f1.keywords:
- NOCSH
ms.localizationpriority: high
search.appverid: MET150
ms.collection: 
  - M365-collaboration
  - m365-frontline
  - highpri
  - teams-1p-app-admin
description: Learn how to use the Walkie Talkie usage and performance report in the Microsoft Teams admin center to get an overview of Walkie Talkie usage activity in your organization.
appliesto: 
  - Microsoft Teams
  - Microsoft 365 for frontline workers
---
# Walkie Talkie usage and performance report

The Walkie Talkie usage and performance report in the Microsoft Teams admin center gives you an overview of [Walkie Talkie](../walkie-talkie.md) activity in your organization. The report provides information such as the number of push-to-talk (PTT) transmissions made and received, channel activity, transmission duration, and device and participant details.

Use this report to gain insight into Walkie Talkie usage trends and performance in your organization. To access the report, you must be a Teams Administrator, Global Reader, Report Reader, or Global Administrator.

> [!IMPORTANT]
> Microsoft recommends that you use roles with the fewest permissions. This helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use a less-privileged role.

## Download and view the report

1. In the left navigation of the Microsoft Teams admin center, choose **Analytics & reports** > **Usage reports**. On the **View reports** tab, under **Report**, select **Walkie Talkie usage**.
1. Under **Date range**, select a date range of 7 days or 30 days. Then, choose **Run report**.
1. Select **Generate report**.
1. On the **Downloads** tab, under **Status**, choose **Download** to download the report in CSV format.

## Interpret the report

The report gives you a breakdown of each transmission made during the date range that you selected. Here's the information included in the report.

|Column name |Description |
|---------|---------|
|TenantId|Tenant ID.|
|UserId|User ID.|
|DeviceId|Device ID.|
|ChannelId|The Walkie Talkie channel in which communication happens.|
|ConversationId|ID of each PTT transmission.|
|TeamId|ID of the team that corresponds to the Walkie Talkie channel in which the user connects to.|
|UnreachableParticipantsCount|Number of participants flagged as unreachable and hidden from the roster because they weren't able to receive any of the last five transmissions.|
|TransmissionDuration|Duration of time (in milliseconds) between when the service receives the notification that one participant is about to start a transmission to when the service delivers the last package of that transmission.|
|TotalParticipantsCount|Total number of participants connected to the Walkie Talkie channel.|
|PacketCount|Number of packets used to send the audio transmission.|
|NotifiedParticipants|The participants to which a push notification is sent when a transmission starts. In scenarios where the connection between the device and service is lost, a notification is sent to the device to re-establish the connection as soon as possible because a transmission is coming.|
|AudioDurationMilliseconds|Duration of the transmission in milliseconds.|
|ConnectionId|ID of each connection to a Walkie Talkie channel established by the device.|
|TransmissionStartTime |Date and time, in Coordinated Universal Time (UTC), when the first audio packet is received by the service. The format is YYYY-MM-DDTHH:MM:SS. For example, 2024-10-08T20:49:03.|
|TransmissionEndTime|Date and time, in Coordinated Universal Time (UTC), when the last audio packet is received by the service. The format is YYYY-MM-DDTHH:MM:SS. For example, 2024-10-08T20:49:05.|
|ParticipantList|A semi-colon delimited list of IDs of the devices connected to the channel at the time the transmission ends.|
|CallTimedOut|Whether the transmission exceeded the duration limit. This is a Boolean value.|
|Platform|Device operating system.|
|ParticipantType|Whether the participant was the transmitter or a receiver of the transmission.|
|WebSocketState|Whether the status of the connection between the device and the service was already established when the transmission started.|
|AppVersion|Version of the Teams app installed on the device.|
|ClientCallStatus |Indicates if the device was able to receive the transmission without any issue.|

## Related articles

- [Manage the Walkie Talkie app in Teams](../walkie-talkie.md)
- [Get started with Walkie Talkie](https://support.microsoft.com/office/get-started-with-teams-walkie-talkie-25bdc3d5-bbb2-41b7-89bf-650fae0c8e0c)
