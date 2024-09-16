---
title: Microsoft Teams Rooms Pro Management Portal
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: srpall
ms.date: 03/26/2024
ms.topic: article
audience: Admin
ms.service: msteams
ms.subservice: itpro-rooms
appliesto: 
  - Microsoft Teams
ms.collection: 
  - M365-collaboration
  - teams-rooms-devices
  - Tier1
ms.localizationpriority: medium
search.appverid: MET150
description: Provide a view of the health of your meeting rooms.
f1keywords: 
---

# Microsoft Teams Rooms Pro Management Portal

## Overview

The Teams Rooms Pro Management portal provides a view of the health of your meeting rooms and helps to facilitate your existing monitoring tools and practices. This feature is only available in public or commercial cloud. It's not available in GCC, GCC-H, or DoD government clouds.

The scope of the monitoring is:

- View of incidents
  - Top issues affecting your rooms.
  - Actions required to restore rooms to healthy status.
- View of Microsoft Teams Room devices
  - Snapshot of status at Microsoft Teams Rooms device level.
  - Basic history and details for every device.

> [!Important]
> Review [**Assign users to the Pro Manager Administrator role**](enrolling-mtrp-managed-service.md#assign-users-to-the-teams-rooms-pro-manager-role) and make sure that access to the portal is restricted based on your organizational needs.

## Terminology

Here are frequently used terms in the portal.

|Term |Meaning |
| :- | :- |
|**Teams Rooms Pro Monitoring Software** |Monitoring agent that is deployed on each of the Microsoft Teams Room devices.|
|**App** |Microsoft Teams Room system app|
|**Room/Device** |The certified Microsoft Teams Room system device.|
|**Unmonitored** |Teams Rooms Pro management monitoring software deployed as part of management services isn't able to connect to the cloud services. We aren't receiving telemetry about the device.|
|<p>**Healthy /** </p><p>**Unhealthy** </p>|Abnormalities in device or peripheral. |
|**Suppressed** |If a device is known to be in maintenance, and its alerts should be ignored, the device or specific alerts can be suppressed.|
|**Onboarding** |The state of a room device while it's getting setup but isn't ready yet and isn't a supported room to receive alerts.|
|**Incident** |An issue affecting meeting experiences of end users that need attention.|
|**Misconfigured** |Configuration detected isn't correct or commonly used. |

## Incidents view

This view is an overview of the Incidents tab in your Teams Rooms Pro Management portal. 

### Top-level summary 
The top-level summary shows at a glance the issues affecting your rooms and what you need to do.

Incidents are expected to be in one of two states:

- **Need Action**: Action required by you to resolve the incident.
- **System Investigating**: This is set to automatic investigation by the monitoring platform and next steps will be provided if the issue can't be automatically resolved.

### Reviewing incidents

Selecting any of items that have status “**Needs action**” shows additional details about the incident.

## Types of Incidents

Incidents are classified into two broad severity types:

- **Critical & Important**: Incidents that are likely causing problems in meetings and should be prioritized to be fixed.
- **Warning** & **Recommendations** – Incidents that are notifications to plan maintenance actions. If these aren't taken care of, then over time the rooms are more likely to encounter an issue. Warnings are intended to give you time to plan and organize support. Recommendations are best practices and guidance to keep your rooms configured in an optimal state.

A warning may transition to an **Important** status if the issue isn't resolved in a timely manner.

## Health status of device and incidents


Incidents that are classified as either **Critical** or **Important** in severity will affect the health status of a device. If there is at least one incident of **Severity = **Important** associated with a device, it's classified as an ***unhealthy*** device.

Incidents classified as **“Warning”** severity don't affect the health status reported on a device. However, if a device has warning level incidents associated with it, then it would be shown with the health status of the device.

Incidents classified as a **Warning** or **Recommendation** severity don't affect the health status reported on a device. However, if a device has **Warning** level incidents associated with it, then it will be shown as a health status of the device.

The following are some of the types of incidents that you might see and the explanations for each type. For each type, the action associated with the incident will be more specific depending on the issue.

**Table 1: Incidents with "Critical" or “Important” severity**

|Type |Explanation |
| :- | :- |
|**Display** |The display connected to the device doesn't appear to be healthy.|
|**Conference microphone, Conference speaker** |The audio devices (microphone and/or speaker) seem to be misconfigured.|
|**Camera** |The camera connected to the device doesn't appear to be healthy.|
|**HDMI Ingest** |HDMI Ingest isn't healthy.|
|**Sign-In** (Exchange) |Microsoft Teams Rooms app accesses calendar information from Exchange and any issue with sign in success will be reported with a sign-in incident.|
|**Sign-In** (Teams) |Microsoft Teams Rooms app signs into the device and failure to sign in will be reported with this incident (if the customer is using Teams).|
|**Sign-In** (Skype for Business) |Microsoft Teams Rooms app signs into the device, and failure to sign in will be reported with this incident (if the customer is using Skype for Business).|
|**Proximity Sensor** |Microsoft Teams Rooms app invites attendees to join a meeting if they are in proximity. Failures in this feature will be reported under this incident.|

**Table 2: Incidents with “Warning” severity**

|Type |Explanation |
| :- | :- |
|**App version** |The version of the Microsoft Teams Rooms App running on the device isn't current. Stale versions are known causes of problems experienced by users. |
|**OS version** |The version of Windows operating system running in the meeting room is no longer recommended. |

## Responding to Incidents

Incidents fall into two categories.

### “Needs Action” Incidents

Incidents that have status set to **“Needs Action”** are assigned to you to take a corrective action.

Each such incident will have a description field holds information about the incident, typical causes, and resolutions that may be useful to resolve certain issues so that you can act without delay. There's a **Notes** tab with an entry for any action the system may have taken to remediate the issue or an entry with the recommended guidance on what action you can take to remediate the issue. 

### “System Investigating” incidents

For the incidents under System investigation, these are issues that have been detected by the Teams Rooms Pro management service and are being triaged by the AI for remediation next steps.

## Rooms View

Each room resource account assigned to a device is a proxy for a room and its connected peripherals. A healthy device represents a healthy room and an unhealthy device represents a room likely causing problems during meetings. In addition to the Incidents view, the Teams Rooms Pro Management Portal also provides a room health overview, and helps you to troubleshoot device details, and to understand repeated failures with incident history.

**Healthy, Unhealthy, Unmonitored**
The top panel on the Rooms view provides a quick snapshot of how many of your devices are in a good state (“Healthy”), how many are affected by issues (“Unhealthy”), how many aren't providing telemetry (“Unmonitored”), and how many devices are suppressed from alerting (as an override). Rooms are monitored for health using an evolving criteria and heuristics. The goal is to reflect the reality of the user experience in the room as accurately as possible and make it actionable.

**Healthy / Unhealthy rooms**:

Devices and peripherals which don't have any incidents of severity “Important” are meeting current criteria for health are marked as healthy. There's a visual cue of a green heart to represent a healthy state. However, just because a room may be marked as Unhealthy (as indicated by a red broken heart), doesn't necessarily imply that there's a room *outage* for every unhealthy device in the portal. The description and action part of the incident contains more specific details about the issue and potential impact on user experience.

**Unmonitored device:**

For rooms that have the state of **Unmonitored**, it means that the Teams Rooms Pro management monitoring agent deployed is disconnected from Teams Rooms Pro Management cloud services. We aren't receiving telemetry about the room and don't have latest health status. This may happen due to network issues, firewall policy changes or if there are changes made to the device image.

## Room Detail: Status and Changes

**Room Details: Status**

The device *Status* tab provides a consolidated view of the status of a device, all the issues active for the device, the actions that are needed to resolve them, or that are ongoing. The Status tab also contains the breakdown of different components of health for the device under *Incidents tab*. If a device is disconnected, Status details won't be available.

**Show all signals:**
To view all signals contained within a signal category, enable the **Show all signals** toggle button. Expansion arrows will appear next to category headings which can be clicked on to expand the accordion view for the underlying signals that make up that category.

**Suppress/Unsuppress Ticket**
When a room is enrolled, you're indicating that you want to receive notifications for changes in room telemetry. There are occasions when a particular device or peripheral is in a known state where you don't want tickets or notifications generated. Using the Suppress ticket functionality, will silence any notification about that particular signal. When you're ready for the service to monitor and notify you about that signal, unsuppress the individual signal.

**Active Ticket Category Expansion**
Under each ticket category, any active, or latest resolved ticket will be displayed along with the severity and when the ticket was last updated. By selecting on the expansion arrow, all tickets will appear with an active link to the ticket information.

## Active Ticket: Overview

Each incident that is created identifies the issue that has been detected and the corrective action that needs to be taken to restore the room to a healthy state. The ticket generated will convey incident overview with any messages generated by the Teams Rooms Pro Management service. All attachments that have been collected for incident troubleshooting will be listed. The history tab provides the dates that issues have been identified.

**Active Ticket: Notes**
The messages UI is the primary communication tool to interact with your own team and monitor messages from the Teams Rooms Pro Management bot.

**Active Ticket: Attachments**
There are occasions where your team will need additional information to augment their investigation of the issue. The attachment tab provides you with the ability to upload pictures, videos, or logs.

**Active Ticket: History**
Each room signal has only one ticket number that is assigned to it on purpose. A room device or peripheral persists in a room and may have issues over time. By maintaining this information under a specific unique ticket ID, all historic information is maintained and can be analyzed for patterns of behavior. The History UI provides a view of all tickets actions created and resolved for this signal.
