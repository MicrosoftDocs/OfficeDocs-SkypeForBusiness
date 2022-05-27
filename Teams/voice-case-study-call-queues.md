---
title: 'Teams voice Contoso case study: Auto attendants and call queues'
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.date: 06/17/2020
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - M365-voice
ms.reviewer: jowrig
search.appverid: MET150
f1.keywords:
- NOCSH
description: 'Teams voice case study for multi-national corporation: Auto attendants and call queues'
appliesto: 
  - Microsoft Teams
---

# Contoso case study: Auto attendants and call queues

Contoso was familiar with auto attendants and call queues from their on-premises Skype for Business deployment. To understand how to set up Cloud auto attendants and call queues, they reviewed [Plan for Teams auto attendants and call queues](plan-auto-attendant-call-queue.md).

## Requirements depending on site type

Depending on the site type, Contoso had the following needs:

- Site Type A: Traditional legacy telephony systems 

  Site Type A needed to keep the same phone number associated with the receptionist as the number for their auto attendants. The key departments for each of these sites would have their own call queues that would route to team members. There was a mixture of sites that used Phone System with Direct Routing and Phone System with Calling Plans.  

- Site Type B: Skype for Business Enterprise Voice 

  Site Type B had existing auto attendants and call queues that needed to migrate to Teams. Contoso needed to keep the phone numbers associated with the auto attendants. Contoso moved the majority of these sites to Phone System with Calling Plans. However, in the few locations where Calling Plans was not available, Contoso moved these sites to a Direct Routing configuration.  

- Site Type C: Skype for Business Enterprise Voice & traditional legacy telephony system 

  Site Type C had existing auto attendants that resided in the traditional legacy telephony system. The decisions and configurations for this site were the same as Site Type A.   

- For all site types, Contoso asked the following questions:

  - Q: Will we use new or existing numbers? 
    A: Contoso decided to use existing phone numbers to be assigned to the service account for the auto attendant. 

  - Q: When will the auto attendant be available to accept incoming calls? 
    A: Contoso decided to set business hours and have calls received after business hours redirected to an "after-hours" auto attendant.  

  - Q: How will the calls be routed to members in a call queue: attendant, serial, or round robin routing? 
    A: Contoso decided to use Attendant routing, 

  - Q: How will we determine when a user should or should not get a call? 
    A: Contoso decided to use call handling options to determine if the agent is available: presence-based routing. 


## Configuration

The steps to set up an auto attendant and a call queue include the following outlined in [Manage resource accounts](manage-resource-accounts.md): 

1. Obtain a service number. 

2. Obtain a free Phone System - Virtual User license or a paid Phone System license to use with the resource account or a Phone System license.

3. Create the resource account. An auto attendant or call queue is required to have an associated resource account. 

4. Assign the Phone System or a Phone System - Virtual user license to the resource account. For more information, see [Microsoft 365 Phone System – Virtual User license](./teams-add-on-licensing/virtual-user.md).

5. Assign a service phone number to the resource account you assigned licenses to. 

6. Create a Phone System call queue or auto attendant 

7. Link the resource account with a call queue or auto attendant. 


### Sites with Phone System with Direct routing 

Contoso had to set up the phone number provided by the local carrier as the service number in Office 365. 

- To set up a phone number available through Direct Routing, Contoso followed the instructions located in [Manage Resource Accounts](manage-resource-accounts.md). Because Office 365 is not aware of the on-premises phone numbers, Contoso used PowerShell to complete the setup.   

- To configure the Cloud auto attendant, Contoso followed the steps outlined in [Set up a Cloud auto attendant](create-a-phone-system-auto-attendant.md). 

- To set up a Cloud call queue, Contoso followed the steps outlined in [Create a Cloud call queue](create-a-phone-system-call-queue.md).  


### Sites with Phone System with Calling plan

Contoso had to port the phone number that was used for Skype for Business Enterprise Voice auto attendants to Office 365 Phone System. This allowed the same number to be assigned as a service number for use as an auto attendant. 

- To port the phone number, Contoso followed the instructions in [Transfer phone numbers to Teams](./phone-number-calling-plans/transfer-phone-numbers-to-teams.md) and obtained additional guidance at [Manage phone numbers for your organization](./manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md).

- To configure a Cloud auto attendant, Contoso followed the steps outlined in [Set up a Cloud auto attendant](create-a-phone-system-auto-attendant.md).

-  To set up a Cloud call queue, Contoso followed the steps outlined in [Create a Cloud call queue](create-a-phone-system-call-queue.md).  

