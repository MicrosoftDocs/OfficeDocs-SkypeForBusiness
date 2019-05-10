---
title: Adding and updating Locations data
author: tonysmit
ms.author: tonysmit
manager: serdars
audience: Admin
ms.topic: article
ms.service: msteams
ms.reviewer: 
localization_priority: Normal
search.appverid: MET150
MS.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
description: Learn how to upload to a site.
ms.custom:
- NewAdminCenter_Update
f1keywords: ms.teamsadmincenter.locations.overview
appliesto: 
- Microsoft Teams
---

Adding and updating Locations data
============================

Locations are used in your organization to indicate the physical locations of offices, buildings, or organizational sites. The Locations page gives admins the ability to provide a text file (.csv or .tsv) containing a list of physical locations and their associated network subnets. This file is used by Call Analytics and Call Quality Dashboard for generating reports. When customers upload their subnet mapping, the reports provided by these services will contain the location names as well, making the reports easier to understand and use for remediating any potential issues.

The locations data you provide is a single data structure – there’s currently no interface available to make individual edits to location data. 

**To edit the table of subnets and locations**

1. Click **Replace locations data**.
2. In the **Replace location data** pane, click **Select a file**, and then browse to and upload your edited .csv or .tsv file. 
3. Click **Upload**. 


You can download a sample template [here](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/locations-template.zip?raw=true).

You can use the following example to help create your data file. 

> [!IMPORTANT]
> Your data file should not contain column headers (such as Network, Network Name, etc.). These are used here for informational purposes only. </br>

|Network|Network Name|Network Range|Building Name|Ownership Type|Building Type|Building Office Type|City|Zip Code|Country|State|Region|Inside Corp|Express Route|
|-|-|-|-|-|-|-|-|-|-|-|-|-|-|
|10.0.128.0	|SVC-1|32|USCAMTV001|Contoso Leased RE&F|Office|RE&F|Mountain View|94043|US|CA|US|1|1|
|10.0.130.0	|SVC-1|32|USCAMTV001|Contoso Leased RE&F|Office|RE&F|Mountain View|94043|US|CA|US|1|1|
|10.0.131.0	|SVC-1|32|USCAMTV001|Contoso Leased RE&F|Office|RE&F|Mountain View|94043|US|CA|US|1|1|
|10.0.132.0	|SVC-1|32|USCAMTV001|Contoso Leased RE&F|Office|RE&F|Mountain View|94043|US|CA|US|1|1|


For more information about formatting your data file, see [Tenant data file format and Building data file structure](turning-on-and-using-call-quality-dashboard.md#tenant-data-file-format-and-building-data-file-structure).


## Related topics

[Set up Call Analytics](set-up-call-analytics.md)
