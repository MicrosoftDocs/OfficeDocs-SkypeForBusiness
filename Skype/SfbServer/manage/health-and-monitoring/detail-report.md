---
title: "Conference Detail Report in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 1d61cd81-dcfe-40b4-9a41-a73b038bc216
description: "Summary: Learn about the Conference Detail Report used in Skype for Business Server."
---

# Conference Detail Report in Skype for Business Server

**Summary:** Learn about the Conference Detail Report used in Skype for Business Server.

The Conference Detail Report provides detailed information about all the users who participated in a conference. For example, you can see such information as the date and time that a user joined the conference, the date and time that the user left the conference, and the user agent of the endpoint that was used to connect that user to the conference. You can also see information the user's role in each conference (for example, Presenter or Attendee). Perhaps most important, you get quickly see which users successfully join and complete the conference, and which users were not able to successfully join and complete the conference.

## Accessing the Conference Detail Report

The Conference Detail Report can be accessed from the following reports:

- The [Call Admission Control Report](call-admission-control-report.md) (by clicking the Detail metric for a conference)

- The [Failure List Report](failure-list-report.md) (by clicking the Conference metric)

- The [User Activity Report](call-diagnostic-reports-per-user.md) (by clicking the Conference URI metric)

From the Conference Detail Report you can access the [Diagnostic Repor](diagnostic-report.md) by clicking the Diagnostic Report (Detail) metric.

## Filters

None. You cannot filter on the Conference Detail Report.

## Metrics

The following table lists the information provided in the Conference Information section of the Conference Detail Report.

**Conference Information Metrics**


| **Name**                 | **Description**                                                                                                            |
|:-------------------------|:---------------------------------------------------------------------------------------------------------------------------|
| **Conference URI** <br/> | URI assigned to the conference. For example:  <br/> sip:kmyer@litwareinc.com;gruu;opaque=app:conf:focus:id:drg2y8v4  <br/> |
| **Pool FQDN** <br/>      | Fully-qualified domain name of the Registrar pool or Edge Server involved in a session.  <br/>                             |
| **Start time** <br/>     | Date and time that the conference started.  <br/>                                                                          |
| **Organizer** <br/>      | SIP address of the user who organized the conference.  <br/>                                                               |
| **End time** <br/>       | Date and time that the conference ended.  <br/>                                                                            |

The following table lists the information provided in the Conference Participation Section of the Conference Detail Report.

**Conference Participation Metrics**

|**Name**|**Description**|
|:-----|:-----|
|**User** <br/> |SIP address of the user who participated in the conference.  <br/> |
|**Role** <br/> |Role (for example, Presenter) played by the conference participant.  <br/> |
|**Connectivity** <br/> |Network connectivity (typically From Internal or From External) for the participant.  <br/> |
|**Join time** <br/> |Date and time that the participant joined the conference.  <br/> |
|**Leave time** <br/> |Date and time that the participant left the conference.  <br/> |
|**User agent** <br/> |Identifier for the software used by the participant's endpoint.  <br/> |
|**Diagnostic reports** <br/> |Provides diagnostic and troubleshooting information. Including SIP response codes, diagnostic headers, conference join times, and diagnostic IDs for failed sessions.  <br/> |

The following table lists the information provided in the Conference Modalities section of the Conference Detail Report.

**Conference Modalities Metrics**

|**Name**|**Description**|
|:-----|:-----|
|**User** <br/> |SIP address of the user who participated in the conference.  <br/> |
|**Join time** <br/> |Date and time that the participant joined the conference.  <br/> |
|**Leave time** <br/> |Date and time that a participant left the conference.  <br/> |
|**Conferencing server URI** <br/> |URI for the Conferencing server used in the conference.  <br/> |
|**Diagnostic reports** <br/> |Provides diagnostic and troubleshooting information. Including SIP response codes, diagnostic headers, conference join times, and diagnostic IDs for failed sessions.  <br/> |


