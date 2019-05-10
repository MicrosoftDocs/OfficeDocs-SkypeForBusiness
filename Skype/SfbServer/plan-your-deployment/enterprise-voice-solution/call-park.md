---
title: "Plan for Call Park in Skype for Business"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- IT_Skype16
- Strat_SB_Admin
ms.custom:
ms.assetid: 985dc326-0aef-4308-b98b-c1d0069311e7
description: "Planning for call park in Skype for Business Server Enterprise Voice, which enables putting calls on hold and transferring calls to departments. Includes capacity planning, supported calls, and supported clients."
---

# Plan for Call Park in Skype for Business
 
Planning for call park in Skype for Business Server Enterprise Voice, which enables putting calls on hold and transferring calls to departments. Includes capacity planning, supported calls, and supported clients.
  
The Call Park application enables Enterprise Voice users to do the following:
  
- Put a call on hold and then retrieve the call from the same phone or another phone.
    
- Put a call on hold to transfer it to a department or general area (for example, to a sales department or a warehouse where there is a common area phone).
    
- Put a call on hold and keep the original answering phone free for other calls.
    
When a user parks a call, Skype for Business Server transfers the call to a temporary number, called an orbit, where the call is held until it is retrieved or it times out. Skype for Business Server sends the orbit to the user who parked the call. To retrieve the parked call, the user can dial the orbit number or click the orbit link or button in the Conversation window. 
  
The user who parked a call can notify someone to retrieve the call by using an external mechanism, such as instant messaging (IM) or a paging system, to communicate the orbit number to someone else. The user who parked the call can leave the Conversation window open to receive notification when the call is retrieved.
  
Because orbit ranges are globally unique, it is possible to retrieve calls from any Skype for Business Server site or PBX phone if routing is configured appropriately. If no one retrieves the call within a configurable amount of time, the call rings back to the person who parked it. If that person does not answer the ringback, the call is transferred to a fallback destination, such as to an operator, if so configured. You can configure the number of times the call rings back before being transferred from one to ten times. If no one answers a transferred call, the call is disconnected. The orbit is freed when the call is retrieved or disconnected.
  
When you deploy Call Park, you need to reserve ranges of extension numbers for parking calls. These extensions need to be virtual extensions: extensions that have no user or phone assigned to them. You then configure the call park orbit table with the ranges of extension numbers and specify which Application service hosts the Call Park application that handles each range. Each Front End pool has a Call Park table on the corresponding Back End Server that is used to manage calls that are parked on the pool. The list of orbit ranges is stored in Central Management store and is used to route orbits to the destination pool. Each Skype for Business Server pool where the Call Park application is deployed and configured can have one or more orbit ranges. Orbit ranges must be globally unique across the Skype for Business Server deployment. 
  
You also configure other Call Park settings, such as where calls are redirected if they time out and whether the person on the phone hears music while parked. You can also specify the music file to play while the call is on hold.
  
> [!NOTE]
> Customized music-on-hold files for Call Park are not backed up as part of the Skype for Business Server disaster recovery process and will be lost if the files uploaded to the pool are damaged, corrupted, or erased. Always keep a separate backup copy of the customized music-on-hold files that you have uploaded for Call Park. 
  
The Call Park application is a component of Enterprise Voice. When you deploy Enterprise Voice, the Call Park application is installed and activated automatically. Before you can use Call Park, however, the Enterprise Voice administrator must configure it and enable it for users through voice policy.
  
## Deployment and requirements

The Call Park application is automatically installed when you deploy Enterprise Voice. You enable Call Park by configuring voice policy.
  
### Software requirements

All Front End Servers and Standard Edition servers where Call Park is deployed must have the Windows Media Format Runtime installed for servers running Windows Server 2008 R2, or Microsoft Media Foundation for servers running Windows Server 2012 or Windows Server 2012 R2. For Windows Server 2008 R2, Windows Media Format Runtime is installed as part of Windows Desktop Experience. Windows Media Format Runtime or Microsoft Media Foundation is required for Windows Media Audio (.wma) files that Call Park plays for music on hold.
  
### Port requirements

The Call Park application uses **Port 5075**  for SIP listening requests.
    
> [!NOTE]
> This port is a default setting that you can change by using the **Set-CsApplicationServer** cmdlet. For details about this cmdlet, see the Lync Server Management Shell documentation.
  
### Audio File requirements

The Call Park application supports only Windows Media Audio (.wma) files for music on hold. You can use the Microsoft Expression Encoder 4 to customize files for music on hold. To download Expression Encoder 4, see   ["Expression Encoder 4"](https://go.microsoft.com/fwlink/p/?linkId=202843). Use the tool to convert the file to a .wma format. The recommended format for Call Park music-on-hold files is Media Audio 9, 44 kHz, 16 bits, Mono, CBR, 32 kbps.
  
> [!NOTE]
> The converted file plays over the phone only at 16 kHz, even if it was recorded at 44 kHz. 
  
## Supported clients and calls

The following clients and types of calls are supported for Call Park
  
### Clients Supported for Parking Calls

Calls from any IP, private branch exchange (PBX), public switched telephone network (PSTN), or mobile phone can be parked.
  
> [!NOTE]
> Only audio calls can be parked. Instant messages and conferences cannot be parked. 
  
The following clients can use Call Park to park calls:
  
- Skype for Business
    
- Lync 2013
    
- Lync 2010
    
- Lync 2010 Attendant
    
- Lync Phone Edition
    
> [!NOTE]
> Mobile phones cannot use Call Park to park calls. 
  
### Clients Supported for Retrieving Calls

Orbit ranges are configured as blocks of virtual extensions (extensions without an assigned user or phone). When you configure orbits as virtual extensions, mobile phones and PSTN phones cannot retrieve parked calls.
  
Federated users cannot retrieve parked calls.
  
The following clients can retrieve calls that are parked on Call Park:
  
- Skype for Business
    
- Lync 2013
    
- Lync 2010
    
- Lync 2010 Attendant
    
- Lync Phone Edition
    
- IP common area phones
    
- Non-IP phones that are connected to the Skype for Business Server infrastructure, including common area phones and private branch exchange (PBX) phones
    
## Call Park capacity planning

The following table describes the Call Park user model that you can use as the basis for capacity planning requirements.
  
> [!IMPORTANT]
> Keep in mind that, for disaster recovery capacity planning, each pool of a paired pool should be able to handle the workloads for Call Park services in both pools. 
  
**Call Park User Model**

|**Metric**|**Per Front End pool  <br/>  (with 8 Front End Servers)**|**Per Standard Edition server**|
|:-----|:-----|:-----|
|Park rate  <br/> |8 per minute  <br/> |1 per minute  <br/> |
|Retrieve parked call rate  <br/> |8 per minute  <br/> |1 per minute  <br/> |
|Average park duration  <br/> |60 seconds  <br/> |60 seconds  <br/> |
   

