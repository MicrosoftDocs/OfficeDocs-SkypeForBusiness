---
title: Meeting recording expiration feature
author: cichur
ms.author: v-cichur
ms.reviewer: 
manager: serdars
ms.topic: article
audience: admin
ms.service: msteams
searchScope:
  - Microsoft Teams
search.appverid: MET150
description: Learn about the meeting recording expiration feature in Microsoft Teams.
localization_priority: Normal
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---

# Meeting recording expiration feature - Frequently asked questions

**What is the change?**

We are introducing a default 60-day expiration setting for *all* newly created Teams meeting recordings (TMRs). This is on by default for all tenants and you must turn it off if you do not want this feature. The ODSP system will monitor the expiration date set on all TMRs and will automatically move TMRs to the recycle bin on their expiration date.

**Why are we introducing this change?**

We've answered your requests for the meeting recording expiration feature. This is a lightweight housekeeping mechanism to reduce storage clutter created from cold Teams meeting recordings (TMR). On average, 99% of TMRs are never re-watched after 60 days.

**Why is this being turned on by default?**

We believe nearly all customers will benefit from the reduced storage load on their tenant by removing recordings that will likely never be re-watched after 60 days. It's our goal to provide as clean an experience as possible for all customers by default.

**How is the expiration date calculated?**

The expiration date is calculated as the day it's created plus the default number of days set in the Teams policy by the admin.

**How can an Admin change the expiration date be changed?**

Admins can edit the default expiration setting in their Teams policy console. That change will impact only newly created TMRs from that point forward. It won't impact any recordings before that date.

Admins can't change the expiration date on existing TMRs. This is done to protect the decision of the user that owns the TMR.

    3.  &lt;insert pic of the Teams policy setting&gt;

**What is the scope of control for the admin policy?**

    1.  &lt;add information about the granularity of policy application&gt;

**How can end users modify the expiration date?**

 Anyone who has edit and delete permissions on a TMR can modify the expiration date in the file’s details pane in Microsoft OneDrive and SharePoint.

    2.  The user can defer the expiration 14, 30, or 60 days, or they can choose a specific date in the future, or they can select that the file never be expired.

**Who does this impact?**

    1.  Anyone storing TMRs in OneDrive or SharePoint.

**Why should I use this feature?**

    1.  This feature is being turned on by default. To “disable” it, change the default expiration setting for all TMRs in the Teams policy console to “no expiration.”

    2.  You should use this to limit the ODSP storage consumption driven by Teams meeting records (note: TMRs typically consume around 300MB per hour of recording).

**Should I rely on this feature for strict security and compliance adherence?**

    1.  No, you should not rely on this for legal protection since end users can modify the expiration date of any recordings they control.

**Will a retention and/or deletion policy I have set in the security & compliance center override the TMR expiration setting?**

    1.  Yes, any policies you have set in the S+C compliance center will take full precedence. For example:

        1.  If you have a policy that says all files in a site must be retained for 100 days, and the expiration setting for a TMR is 30 days, then the TMR will be retained for the full 100 days.

        2.  If you have a deletion policy that says all TMRs will be deleted after 5 days and you have an expiration setting on a TMR of 30 days, then the TMR will be deleted after 5 days.

**What happens when a TMR expires?**

    1.  On the expiration date, the TMR is moved into the recycle bin and the expiration date field is cleared. If you recover the TMR from the recycle bin, it will not be deleted by this feature again since the expiration date has been cleared.

**How will I be notified about a file’s expiration?**

    1.  Everyone will see a notification about the expiration date in the recording chiclet in the Teams chat window.

    2.  Everyone with view access will see a red icon next to the file in your OneDrive or SharePoint folder 14 days before the file expires.

    3.  The file owner will receive an email notification when the TMR expires and will be directed to the recycle bin to recover the TMR if they desire to do so.

**What SKUs are required for this feature?**

    1.  All SKUs will have this feature by default.

    2.  A1 users will be defaulted to a 30-day expiration period and will not be able to modify the expiration date.

**Is the file expiration an audited event and will I be able to see it in my audit logs?**

    1.  Yes, these will show up as system deletion events in the audit log.

**What if I want the admin to have full control over the lifecycle of TMRs and do not want to give end users the ability to override the expiration date?**

    1.  We recommend using the S+C retain and/ordelete policies available as part of the E5 compliance SKU. That offering is targeted to solve complex policy and SLA-driven administrative legal concerns.

    2.  This feature is solely meant as a lightweight housekeeping mechanism to reduce storage clutter created from cold TMRs.

**When will the file be deleted?**

    1.  The file will be deleted within 5 days of the expiration date, though this is not a strict guarantee.
