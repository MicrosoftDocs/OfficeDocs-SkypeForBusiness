---
title: "Outbound calling restriction policies for Audio Conferencing and Calling Plans"
ms.author: tonysmit
author: tonysmit
ms.date: 11/8/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 1f737548-8f82-41a7-bec1-28e59050007b
description: "Outbound call restriction policies are available for the following scenarios:"
---

# Outbound calling restriction policies for Audio Conferencing and Calling Plans

Outbound call restriction policies are available for the following scenarios:
  
Audio Conferencing calls
  
End User calls
  
Both settings are controlled by a single policy called OnlineDialOut Policy which has a restriction attribute for each. The restriction settings possible within the policy are:
  
|||
|:-----|:-----|
|Setting  <br/> |Values  <br/> |
|Audio Conferencing Calls  <br/> |International and Domestic  <br/> Domestic  <br/> None  <br/> |
|End User Calls  <br/> |International and Domestic  <br/> Domestic  <br/> None  <br/> |
   
The policy cannot be customized, rather (what is the name we are calling Skype for Business/Teams Online Service???) has pre-defined policy instances for each combination of the settings. 
  
## Set calling restrictions for Audio Conferencing

These policies also be set via the Skype for Business Admin Center by doing the following steps:
  
Select "dial-in conferencing"
  
Select "dial-in users"
  
Select a user and click "edit"
  
Select the desired dial-out restriction on the "Restrictions to dial-outs from meetings of this user" option.
  
(Need to get updated screen shots to show both drop downs)
  
## Want to know more about setting these policies using Windows Powershell?

These policies can be viewed by the Get-CSOnlineDialOutPolicy commandlet and assigned to users by the Grant-CSOnlineDialOutPolicy commandlet. (Is there commandlet help for this policy yet? If so we should link it)
  
The following table gives an overview of each policy:
  
|||
|:-----|:-----|
|Identity='tag:DialoutCPCandPSTNInternational'  <br/> |User in the conference can dial out to international and domestic numbers, and this user can also make outbound calls to international and domestic numbers  <br/> |
|Identity='tag:DialoutCPCDomesticPSTNInternational'  <br/> |User in the conference can only dial out to domestic numbers, and this user can make outbound calls to international and domestic numbers  <br/> |
|Identity='tag:DialoutCPCDisabledPSTNInternational'  <br/> |User in the conference cannot make any dial out. This user can make outbound calls to international and domestic numbers  <br/> |
|Identity='tag:DialoutCPCInternationalPSTNDomestic'  <br/> |User in the conference can dial out to international and domestic numbers, and this user can only make outbound calls to domestic PSTN number  <br/> |
|Identity='tag:DialoutCPCInternationalPSTNDisabled'  <br/> |User in the conference can dial out to international and domestic numbers, and this user cannot make any outbound calls to PSTN number besides emergency numbers  <br/> |
|Identity='tag:DialoutCPCandPSTNDomestic'  <br/> |User in the conference can only dial out to domestic numbers, and this user can only make outbound call to domestic PSTN numbers  <br/> |
|Identity='tag:DialoutCPCDomesticPSTNDisabled'  <br/> |User in the conference can only dial out to domestic numbers, and this user cannot make any outbound calls to PSTN number besides emergency numbers  <br/> |
|Identity='tag:DialoutCPCDisabledPSTNDomestic'  <br/> |User in the conference cannot make any dial out, and this user can only make outbound call to domestic PSTN numbers  <br/> |
|Identity='tag:DialoutCPCandPSTNDisabled'  <br/> |User in the conference cannot make any dial out, and this user cannot make any outbound calls to PSTN number besides emergency numbers  <br/> |
   

