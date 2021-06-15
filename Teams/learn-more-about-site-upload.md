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
  - M365-collaboration
description: Learn how to add and update reporting labels by uploading a text file that contains a list of physical locations and associated subnets.
f1.keywords:
- CSH
ms.custom:
  - NewAdminCenter_Update
  - ms.teamsadmincenter.locations.reportinglabels.overview
  - ms.teamsadmincenter.voice.phonenumbers.searchacquire.tooltip.location
  - ms.teamsadmincenter.locations.overview
  - seo-marvel-mar2020
appliesto: 
  - Microsoft Teams
---

# Add and update reporting labels


Reporting labels are used in your organization to indicate the physical locations of offices, buildings, or organizational sites. The Reporting labels page in the Microsoft Teams admin center lets you provide a text file (.csv or .tsv) containing a list of physical locations and their associated network subnets. This file is used by Call Analytics for generating reports. When you upload your subnet mapping, the reports provided by these services will contain the location names as well, making the reports easier to understand and use for remediating any potential issues.

> [!IMPORTANT]
> Reporting Labels that you upload will be handled as *Support Data* under your agreement for Office 365, including any information that would otherwise be considered *Customer Data* or *Personal Data*. Please don't include data you do not wish to provide to Microsoft as *Support Data*, as this information will be visible to Microsoft Engineers for support purposes.

The report labels and locations data you provide is a single data structure – there's currently no interface available to make individual edits to the data.

**To edit the table of subnets and locations**

1. In the left navigation of the Microsoft Teams admin center, click **Locations** > **Reporting labels**.
2. Click **Upload data**.
3. In the **Upload data** pane, click **Select a file**, and then browse to and upload your edited .csv or .tsv file.
4. Click **Upload**.

You can download a sample template [here](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/locations-template.zip?raw=true).

Use the following example to help create your data file.

> [!IMPORTANT]
> Your data file shouldn't contain column headers (such as Network, Network Name, etc.). These are used here for informational purposes only. <br>

|Network|Network Name|Network Range|Building Name|Ownership Type|Building Type|Building Office Type|City|Zip Code|Country|State|Region|Inside Corp|Express Route|
|-|-|-|-|-|-|-|-|-|-|-|-|-|-|
|10.0.128.0    |SVC-1|32|USCAMTV001|Contoso Leased RE&F|Office|RE&F|Mountain View|94043|US|CA|US|1|1|
|10.0.130.0    |SVC-1|32|USCAMTV001|Contoso Leased RE&F|Office|RE&F|Mountain View|94043|US|CA|US|1|1|
|10.0.131.0    |SVC-1|32|USCAMTV001|Contoso Leased RE&F|Office|RE&F|Mountain View|94043|US|CA|US|1|1|
|10.0.132.0    |SVC-1|32|USCAMTV001|Contoso Leased RE&F|Office|RE&F|Mountain View|94043|US|CA|US|1|1|

For more information about formatting your data file, see [Tenant data file format and Building data file structure](CQD-upload-tenant-building-data.md#upload-building-data-file).

## Related topics

[Set up Call Analytics](set-up-call-analytics.md)

[Use call analytics to troubleshoot poor call quality](use-call-analytics-to-troubleshoot-poor-call-quality.md)
