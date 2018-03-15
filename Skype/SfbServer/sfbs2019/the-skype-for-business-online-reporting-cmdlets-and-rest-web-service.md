---
title: "The Skype for Business Online reporting cmdlets and REST web service"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365_Hybrid
ms.assetid: cadd73a7-c08a-4102-b73a-ccb3ad4987bf
description: "In conjunction with the reporting features, Skype for Business Online provides access to five Windows PowerShell cmdlets that help generate those reports and are also can be used by administrators to return customized reporting data. Skype for Business Online also includes the REST (Representational State Transfer), which can be used by developers to retrieve customized reporting information."
---

# The Skype for Business Online reporting cmdlets and REST web service
[]
In conjunction with the reporting features, Skype for Business Online provides access to five Windows PowerShell cmdlets that help generate those reports and are also can be used by administrators to return customized reporting data. Skype for Business Online also includes the REST (Representational State Transfer), which can be used by developers to retrieve customized reporting information.
  
The reporting cmdlets available to administrators include:
  
- Get-CsActiveUserReport, which provides information about the number of active users (that is, users who have logged on to Skype for Business Online and participated in at least one conference or peer-to-peer communication session).
    
- Get-CsAVConferenceTimeReport, which provides information about the amount of time (in minutes) users spent in audio/video conferences.
    
- Get-CsConferenceReport, which provides information about the number and type of conferences that users participated in.
    
- Get-CsP2PAVTimeReport, which provides information about the amount of time (in minutes) users spent in peer-to-peer sessions that included audio and/or video.
    
- Get-CsP2PSessionReport, which provides information about the number and type of peer-to-peer sessions that users participated in.
    
Most administrators will use the reports available in the Office 365 Admin center: not only are those reports auto-generated, but they also provide a graphical representation of the data that is often easier to interpret than the raw number values returned by the reporting cmdlets. However, administrators familiar with Windows PowerShell can use the reporting cmdlets to return data that is not readily available from the Lync Online reports. For example, the reporting cmdlets return information about session duration (the amount of time, in minutes, that each session lasted). Individual session durations are not available using the Lync Online reports. Likewise, in daily view the Lync Online reports display information only for the preceding 14 days. If you would like to review the daily totals for a different day (for example, a date from four months ago) you can do so by using the reporting cmdlets.
  
Administrators might also be interested in the article [Using Excel to Retrieve Office 365 Reporting Data](https://msdn.microsoft.com/en-us/library/dn781442.aspx), which explains how to use the OData data querying feature in Microsoft Excel to create custom office 365 report. Custom reports give you the ability to dictate which data (and how much data) is returned from the Office 365 reporting service. Custom reports also enable you to do such things as specify how the data should be sorted and grouped, and provide access to information that is not displayed in the Office 365 Admin center.
  
Administrators with a development background can use the REST web service to obtain information not displayed in the Skype for Business Online admin center. The REST service is similar to the SOAP service, in that each technology provides a way to transfer XML data between a client and a server. However, the REST service has at least two advantages over the SOAP service. For one, REST performs XML data transfers using a standardized format known as the ATOM syndication format. By contrast, SOAP using a non-standard format when transferring data. In addition, REST is able to transfer data across networks that block HTTP verbs other than GET and POST.
  
## See also

#### 

[The Office 365 Reporting Web Service](https://msdn.microsoft.com/EN-US/library/office/jj984325.aspx)
  
[Learning About the Office 365 Reporting Web Service](https://msdn.microsoft.com/EN-US/library/office/jj984321.aspx)
  
[The Exchange Online Reporting Cmdlets](https://technet.microsoft.com/en-us/library/jj200780%28v=exchg.150%29.aspx)
  
[Lync Online Reporting](http://technet.microsoft.com/library/9aec7a1b-cf69-43d6-ba1a-0989cc7da283.aspx)
  
[Using Excel to Retrieve Office 365 Reporting Data](https://msdn.microsoft.com/en-us/library/dn781442.aspx)

