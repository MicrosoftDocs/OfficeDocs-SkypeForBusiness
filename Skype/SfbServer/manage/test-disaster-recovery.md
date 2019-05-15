---
title: "Disaster recovery testing in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "Perform a system recovery for a Skype for Business Server pool server to test your documented disaster recovery process"
---

# Disaster recovery testing in Skype for Business Server

Perform a system recovery for a Skype for Business Server pool server to test your documented disaster recovery process. This test will simulate a complete hardware failure for one server, and will help guarantee that the resources, plans, and data are available for recovery. Try to rotate the focus of the test each month so that your organization tests the failure of a different server or other piece of equipment every time. 

Note that the schedule by which organizations perform Disaster Recovery testing will vary. It is very important that disaster recovery testing is not ignored or neglected. 

Export your Skype for Business Server topology, policies, and configuration settings to a file. Among other things, this file can then be used to restore this information to the Central Management store after an upgrade, a hardware failure, or some other issue has resulted in data loss.

Import your Skype for Business Server topology, policies, and configuration settings to either the Central Management store or to the local computer as shown in the following commands: 

`Import-CsConfiguration -ByteInput <Byte[]> [-Force <SwitchParameter>] [-LocalStore <SwitchParameter>]`

`Import-CsConfiguration -FileName <String> [-Force <SwitchParameter>] [-LocalStore <SwitchParameter>]` 

To back up production data:

- Back up the RTC and LCSLog databases by using the standard SQL Server backup process to dump the database to a file or tape dump device.
- Use third-party backup application to back up the data to file or to tape.
- Use the Export-CsUserData cmdlet to create an XML export of the whole RTC database.
- Use the file system backup or third-party backup to back up meeting content and compliance logs.
- Use the Export-CsConfiguration command-line tool to back up Skype for Business Server settings.

The first step in the failover procedure includes a forced move of users from the production pool to the Disaster Recovery pool. This will be a forced move because the production pool won't be available to accept the user relocation.

The Skype for Business Server move user process is effectively a change to an attribute on the user account object in addition to a record update on the RTC SQL database. This data can be restored from the original backup dump device from the production SQL Server using the standard SQL Server restore process, or using a third-party backup/restore utility.

After this data is restored, users can effectively connect to the Disaster Recovery pool, and operate as usual. To enable users to connect to the Disaster Recovery pool, a DNS record change will be required.

The production Skype for Business pool will be referenced by clients using the auto-configuration and DNS SRV records of:

- SRV: _sip._tls.\<domain> /CNAME: SIP.\<domain>
- CNAME: SIP.\<domain> /cvc-pool-1.\<domain>

To facilitate the failover, this CNAME record must be updated to reference the DROCSPool FQDN:

- CNAME: SIP.<domain> /DROCSPool.\<domain>
- Sip.\<domain>
- AV.\<domain>
- webconf.\<domain>
