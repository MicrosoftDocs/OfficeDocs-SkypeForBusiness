---
title: Add and update reporting labels
author: tonysmit
ms.author: tonysmit
manager: serdars
audience: Admin
ms.topic: article
ms.service: msteams
ms.reviewer: 
localization_priority: Normal
search.appverid: MET150
ms.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
description: Learn how to upload a text file that contains a list of physical location and associated subnets to use as reporting labels for Call Analytics and Call Quality Dashboard reports. 
ms.custom:
- NewAdminCenter_Update
f1keywords: 
- ms.teamsadmincenter.locations.reportinglabels.overview
- ms.teamsadmincenter.voice.phonenumbers.searchacquire.tooltip.location
- ms.teamsadmincenter.locations.overview
appliesto: 
- Microsoft Teams
---

Add and update reporting labels
============================

Reporting labels are used in your organization to indicate the physical locations of offices, buildings, or organizational sites. The Reporting labels page in the Microsoft Teams admin center lets you provide a text file (.csv or .tsv) containing a list of physical locations and their associated network subnets. This file is used by Call Analytics and Call Quality Dashboard for generating reports. When you upload your subnet mapping, the reports provided by these services will contain the location names as well, making the reports easier to understand and use for remediating any potential issues.

The report labels and locations data you provide is a single data structure – there’s currently no interface available to make individual edits to the data.

**To edit the table of subnets and locations**

1. In the left navigation of the Microsoft Teams admin center, click **Locations** > **Reporting labels**.
2. Click **Replace locations data**.
3. In the **Replace location data** pane, click **Select a file**, and then browse to and upload your edited .csv or .tsv file.
4. Click **Upload**.

You can download a sample template [here](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/locations-template.zip?raw=true).

Use the following example to help create your data file.

> [!IMPORTANT]
> Your data file shouldn't contain column headers (such as Network, Network Name, etc.). These are used here for informational purposes only. <br>

|Network|Network Name|Network Range|Building Name|Ownership Type|Building Type|Building Office Type|City|Zip Code|Country|State|Region|Inside Corp|Express Route|
|-|-|-|-|-|-|-|-|-|-|-|-|-|-|
|10.0.128.0	|SVC-1|32|USCAMTV001|Contoso Leased RE&F|Office|RE&F|Mountain View|94043|US|CA|US|1|1|
|10.0.130.0	|SVC-1|32|USCAMTV001|Contoso Leased RE&F|Office|RE&F|Mountain View|94043|US|CA|US|1|1|
|10.0.131.0	|SVC-1|32|USCAMTV001|Contoso Leased RE&F|Office|RE&F|Mountain View|94043|US|CA|US|1|1|
|10.0.132.0	|SVC-1|32|USCAMTV001|Contoso Leased RE&F|Office|RE&F|Mountain View|94043|US|CA|US|1|1|

For more information about formatting your data file, see [Tenant data file format and Building data file structure](turning-on-and-using-call-quality-dashboard.md#tenant-data-file-format-and-structure).

## Related topics

[Set up Call Analytics](set-up-call-analytics.md)
