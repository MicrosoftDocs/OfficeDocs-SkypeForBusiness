---
title: Cloud Video Interop for Microsoft Teams
author: lolaj
ms.author: lolaj
manager: serdars
ms.topic: article
ms.service: msteams
search.appverid: MET150
ms.reviewer: srividhc
description: Cloud Video Interop for Microsfot Teams enables third-party video teleconferencing devices (VTCs) to be able to join Microsoft Teams meetings. 
localization_priority: Normal
MS.collection: Strat_MT_TeamsAdmin
appliesto: 
- Microsoft Teams
---

# Cloud Video Interop for Microsoft Teams

Cloud Video Interop for Teams enables interoperability with third-party video teleconferencing devices (VTCs) when joining Microsoft Teams meetings. 

Video teleconferencing with content collaboration helps you make the most out of meetings. However, meeting room systems and devices are expensive to upgrade. Cloud Video Interop for Microsoft Teams works with systems and delivers a native meeting experience for all participants – in meeting rooms or inside of Teams clients. 

## Partners certified for Microsoft Teams

The following partners have video interop solutions for Microsoft Teams. Your company may choose to work with any combination of these partners within your enterprise. 

[Do we want to include the dates, as below? We will need to update the BlueJeans link on/near the release date.]
[Also, I can add the logos if you think they're needed.]

|Partner solution|Availability|
|----|---|
|[Polycom RealConnect for Office 365](https://aka.ms/PolycomRealConnect)|Available now|
|[Pexip Infinity for Microsoft Teams](https://aka.ms/PexipInfinity) | October 19, 2018|
|[BlueJeans Gateway for Microsoft Teams](https://aka.ms/BluejeansGateway) | October 31, 2019|


Our partners has developed a gateway solution to connect thrid-party standards-based SIP and H.323 devices to Microsoft Teams meetings. These solutions include: 
 
- Certified for Microsoft Teams
- Co-engineered with Microsoft
- Customer TAP prior to certification
- Gateway design instead of VMR (VTCs are first-class meeting participants with individual roster entry)
- HD video (1080p) and content (VBSS)
- Support for H.323 and SIP meeting room devices
- Native Teams/Exchange scheduling
- Deployed and Managed in Azure
 
The following diagram describes the high-level architecture of a Teams partner solution.

![Teams Cloud Video Interop partner solution](media/teams-cloud-video-interop-partner-solution.png)

The scenario flow is as follows:

![Teams Cloud Video Interop scenario flow](media/teams-cloud-video-interop-scenario-flow.png) 

Use the following chart as a guide to get started with video interop in your organization:

![Getting started with video interop](media/getting-started-with-cloud-video-interop.png)

## Set up Cloud Video Interop for users in your organization
 
This section explains how you can plan and set up Cloud Video Interop.
 
 After you have decided on your partner(s), you will need to get set up with provisioning details, as well as a partner tenant key. 
 
This tenant key will be the dial out to the partner service. In the following example, 813878896@t.plcm.vc is the tenant key. 

![Tenant key example](media/tenant-key-example.png)

You will need to execute the following cmdlets to provision the tenant key, and also enable select users or your whole organization to create meetings with video interop coordinates.
 
- **[Get-CsTeamsVideoInteropServicepolicy](https://docs.microsoft.com/en-us/powershell/module/skype/get-csteamsvideointeropservicepolicy):** 
Microsoft provides pre-constructed policies for each of our supported partners that allow you to designate which partner(s) to use for cloud video interop.

    This cmdlet allows you to identify the pre-constructed policies that you can use in your organization. You can assign this policy to one or more of your users leveraging the Grant-CsTeamsVideoInteropServicePolicy cmdlet.
 
- **[Grant-CsTeamsVideoInteropServicePolicy](https://docs.microsoft.com/en-us/powershell/module/skype/grant-csteamsvideointeropservicepolicy):**
The Grant-CsTeamsVideoInteropServicePolicy cmdlet allows you to assign a pre-constructed policy for use in your organization or assign the policy to specific users.
 
- **[New-CsVideoInteropServiceProvider](https://docs.microsoft.com/en-us/powershell/module/skype/new-csvideointeropserviceprovider):**
Use the New-CsVideoInteropServiceProvider to specify information about a supported CVI partner your organization would like to use.
 
- **[Set-CsVideoInteropServiceProvider](https://docs.microsoft.com/en-us/powershell/module/skype/set-csvideointeropserviceprovider):**
Use the Set-CsVideoInteropServiceProvider to update information about a supported CVI partner your organization uses.
 
- **[Get-CsVideoInteropServiceProvider](https://docs.microsoft.com/en-us/powershell/module/skype/get-csvideointeropserviceprovider):**
Get all of the providers that have been configured for use within the organization.
 
- **[Remove-CsVideoInteropServiceProvider](https://docs.microsoft.com/en-us/powershell/module/skype/remove-csvideointeropserviceprovider):**
Use Remove-CsVideoInteropServiceProvider to remove all provider information about a provider that your organization no longer uses.  
 
You will need to provide permission consent for the VTCs to join your organizations meetings via the partner service. This consent link will also be provided by your partner.  
 
When these steps are complete, the users who are individually enabled via the Grant cmdlet abovem, or all of the users in the organization if the tenant is enabled, will have VTC coordinates in all the Teams meetings that they schedule. Any VTC can join these meetings via those coordinates.

## Consent

[Not sure what to put for an intro here]

[What should the headers be for this table?]

|||
|--|--|
|Calls.JoinGroupCall|Allows the app to join group calls and scheduled meetings in your organization as a directory user to meetings in your tenant.|
|Calls.JoinGroupCallasGuest|Allows the app to anonymously join group calls and scheduled meetings in your organization as a guest to meetings in your tenant.|
|Calls.AccessMedia|Allows the app to get direct access to media streams in a call, without a signed-in user.|
|OnlineMeetings.Read|Allows the app to read Online Meeting details in your organization, without a signed-in user.|

[Any related links we should add?]
