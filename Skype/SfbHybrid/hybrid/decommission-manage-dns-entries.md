---
title: Manage DNS entries when decommissioning your on-premises environment
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.reviewer: bjwhalen
audience: ITPro
f1.keywords:
- NOCSH
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- Hybrid 
- M365-voice
- M365-collaboration
- Teams_ITAdmin_Help
- Adm_Skype4B_Online
description: "Instructions for how to manage DNS entries when decommissioning your on-premises Skype for Business environment."

---

# Update DNS entries to enable your organization to be all Teams Only

Organizations that previously had on-premises deployments of Skype for Business Server or Lync Server may still have DNS entries that point to an on-premises Skype for Business deployment. These records are required if your organization includes on-premises Skype for Business users. However, once your organization no longer has any on-premises Skype for Business or Lync Server users, these records are no longer required. And in fact, as part of completing the migration from on-premises to Teams, these records must be updated to point to Microsoft 365 or removed. Microsoft cannot take this step for you.

When attempting to grant TeamsOnly to the entire tenant, Teams will check DNS to determine if any of these DNS records exist for your organization. If any records are found, and if they point to something other than Microsoft 365, the attempt to change the tenant coexistence mode to TeamsOnly will fail by design. This design is to prevent hybrid organizations with on-premises users from mistakenly applying TeamsOnly mode to the tenant--because doing so would break federation for any on-premises Skype for Business users (whether using Teams or Skype for Business).

Furthermore, these records must be updated so that you can grant TeamsOnly to the entire tenant.


## How to identify stale DNS records

To identify any DNS records that prevent your organization from becoming all Teams Only, you can use the Teams admin center  to change the coexistence mode to TeamsOnly. Go to
**Org-wide setting** -> **Teams Upgrade**. Any DNS records that prevent the organization from becoming Teams Only will be included in the error message.  In the event no DNS records are found, the coexistence mode for your organization will be changed to TeamsOnly. 

## How to remove stale DNS records

If your organization no longer has any on-premises Skype for Business Server or Lync Server users, you must do the following:

- Update Skype for Business DNS records to point to Microsoft 365 (instead of the on-premises deployment).

- Remove Skype for Business DNS records if the SIP domain is no longer used. 

In each domain where you find any of the following records, update them as follows:

| Record type | Name | TTL | Priority | Weight | Port | Value |
| :-----| :-----| :---- | :-----| :-----| :-----| :-----|
| SRV | _sipfederationtls.tcp |	3600 |	100 | 1	| 5061	| sipfed.online.lync.com |
| SRV | _sip.tls | 3600	 | 100 |	1	| 443	| sipdir.online.lync.com |
| CNAME	| lyncdiscover |	3600 |	N/A |	N/A | 	N/A |	webdir.online.lync.com |
| CNAME |	sip	| 3600 |	N/A |	N/A	 | N/A | 	sipdir.online.lync.com |
|||||||


