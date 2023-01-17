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
ms.localizationpriority: medium
ms.collection:
- Hybrid
- M365-voice
- M365-collaboration
- Teams_ITAdmin_Help
- Adm_Skype4B_Online
description: "Instructions for how to manage DNS entries when decommissioning your on-premises Skype for Business environment."

---

# Update DNS entries to enable your organization to be all Teams Only

[!INCLUDE [sfbo-retirement](../../Hub/includes/sfbo-retirement.md)]

Organizations that previously had on-premises deployments of Skype for Business Server or Lync Server may still have DNS entries that point to an on-premises Skype for Business deployment. These records are required if your organization includes on-premises Skype for Business users. However, once your organization no longer has any on-premises Skype for Business or Lync Server users, these original records are no longer required by the on-premises deployment and **these DNS entries must be updated to point to Microsoft 365 (or in some cases removed)** as part of your migration from on-premises to Teams Only. *Microsoft cannot update these DNS records on your behalf.*

When attempting to grant TeamsOnly to the entire tenant, Teams will check DNS to determine if any of these DNS records listed below exist in each of your Microsoft 365 verified domains in your organization. If any records are found, and if they point to something other than Microsoft 365, the attempt to change the tenant coexistence mode to TeamsOnly will fail by design. This prevents hybrid organizations with on-premises users from mistakenly applying TeamsOnly mode to the tenant--because doing so would break federation for all on-premises Skype for Business users in the organization (whether using Teams or Skype for Business).

## How to identify stale DNS records

To identify any DNS records that prevent your organization from becoming all Teams Only, you can use the Teams admin center to change the coexistence mode to TeamsOnly. Go to
**Teams** > **Teams upgrade settings**. Any DNS records that prevent the organization from becoming Teams Only will be included in the error message.  In the event no DNS records are found, the coexistence mode for your organization will be changed to TeamsOnly.

Alternatively, you can use Teams PowerShell to do the same thing, as shown below:

   ```PowerShell
   Grant-CsTeamsUpgradePolicy -PolicyName UpgradeToTeams -Global
   ```

## DNS records to be updated

If your organization no longer has any users hosted in on-premises Skype for Business Server or Lync Server, you must do the following:

- Update the Skype for Business DNS records list below to point to Microsoft 365 (instead of the on-premises deployment). If you have more than one SIP domain, you must do this for each SIP domain that is a Microsoft 365 verified domain.

- Remove Skype for Business DNS records if the SIP domain is no longer used.

In each domain where you find any of the following records, update them as follows:

|Record type|Name|TTL|Priority|Weight|Port|Value|
|---|---|---|---|---|---|---|
|SRV|_sipfederationtls._tcp|3600|100|1|5061|sipfed.online.lync.com|
|SRV|_sip._tls|3600|100|1|443|sipdir.online.lync.com|
|CNAME|lyncdiscover|3600|N/A|N/A|N/A|webdir.online.lync.com|
|CNAME|sip|3600|N/A|N/A|N/A|sipdir.online.lync.com|

In addition, CNAME records for meet or dialin (if present) can be deleted. Finally, any DNS records for Skype for Business in your internal network should be removed.

> [!NOTE]
> In rare cases, changing DNS from pointing on premises to Microsoft 365 for your organization may cause federation with some other organizations to stop working until that other organization updates their federation configuration:
>
> - Any federated organizations that are using the older Direct Federation model (also known as Allowed Partner Server) will need to update their allowed domain entries for their organization to remove the proxy FQDN. This legacy federation model is not based on DNS SRV records, so such a configuration will become out of date once your organization moves to the cloud.
>
> - Any federated organization that does not have an enabled hosting provider for sipfed.online.lync.<span>com will need to update their configuration to enable that. This situation is only possible if the federated organization is purely on-premises and has never federated with any hybrid or online tenant. In such a case, federation with these organizations will not work until they enable their hosting provider.
>
> If you suspect that any of your federated partners may be using Direct Federation or have not federated with any online or hybrid organization, we suggest you send them a communication about this as you prepare to complete your migration to the cloud.
