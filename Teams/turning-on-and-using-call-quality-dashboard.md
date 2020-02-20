---
title: Set up Call Quality Dashboard (CQD)
ms.author: lolaj
author: LolaJacobsen
manager: serdars
ms.reviewer: mikedav, siunies, gageames
ms.topic: article
ms.assetid: 553fa13c-92d2-4d5c-a3d5-41a073cb047c
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.collection: 
  - M365-voice
search.appverid: MET150
audience: Admin
appliesto: 
  - Skype for Business
  - Microsoft Teams
localization_priority: Normal
f1.keywords: 
  - CSH
ms.custom: 
  - Reporting
  - ms.teamsadmincenter.directrouting.cqd
  - ms.lync.lac.ToolsCallQualityDashboard
description: "See how to turn on and use the Call Quality Dashboard and get summary reports of quality of calls. "
---

# Set up Call Quality Dashboard (CQD)

Open the Microsoft Call Quality Dashboard (CQD) at [https://cqd.teams.microsoft.com](https://cqd.teams.microsoft.com) (sign in with your admin credentials). Or go to the Teams admin center and select **Call Quality Dashboard**. On the page that opens, click **Sign in** and enter your Global Administrator account or Microsoft Teams Service Admin account information.

CQD shows call and meeting quality, at an org-wide level, for Microsoft Teams, Skype for Business Online, and Skype for Business Server 2019. After the first time you sign in, CQD will begin collecting and processing data. Keep in mind that it may take one or more hours to process enough data to display meaningful results in the reports.

> [!IMPORTANT]
> To use CQD with Skype for Business Server 2019, you will have to [Configure Call Data Connector](https://docs.microsoft.com/skypeforbusiness/hybrid/configure-call-data-connector). See [Plan Call Data Connector](https://docs.microsoft.com/skypeforbusiness/hybrid/plan-call-data-connector) before you start.

[Open CQD from the Skype for Business legacy portal](#open-cqd-from-the-skype-for-business-legacy-portal)

## What's the Call Quality Dashboard, and when should I use it?
  
Call Quality Dashboard (CQD) is designed to help Teams admins, Skype for Business admins, and network engineers monitor call and meeting quality at an org-wide level. You'll use CQD to help you *optimize your network*. If you need to look at call and meeting information for a *specific user*, use [per-user call analytics](use-call-analytics-to-troubleshoot-poor-call-quality.md) instead.
  
For example, using CQD, you can determine that a user's poor call quality (which you observed using per-user call analytics) is due to a network issue that also affects many other users. The individual call experience isn't visible in CQD, but the overall quality of calls made using Teams or Skype for Business is captured. With CQD, overall patterns may become apparent, so network engineers can make informed assessments of call quality. CQD provides reports of call quality metrics that give you insight into overall call quality, server-client streams, client-client streams, and voice quality [SLA](https://go.microsoft.com/fwlink/p/?linkid=846252). 
  
![Screenshot of Call Quality Dashboard.](media/teams-difference-between-call-analytics-and-call-quality-dashboard-image3.png)

In CQD, we encourage you to upload building and endpoint information, which lets you use Location-Enhanced Reports to analyze call quality and reliability within a user's building. The data can be assessed to determine if the problem is isolated to a single user or affects a larger segment of users. To turn on building or endpoint-specific views in CQD, an admin must [upload building or endpoint information](turning-on-and-using-call-quality-dashboard.md#upload-tenant-data-information) on the CQD **Tenant Data Upload** page.

![Screenshot of Call Quality Dashboard's Location-Enhanced Reports.](media/teams-difference-between-call-analytics-and-call-quality-dashboard-image4.png)

Don't miss our [Manage call and meeting quality in Teams](quality-of-experience-review-guide.md) article, which offers in-depth guidance for the Teams admin or support engineer responsible for managing service quality in Teams.

## Assign admin roles for access to CQD

If you want non-admin users (such as support engineers and helpdesk agents) to use Call Quality Dashboard, you can assign those users one of the following roles, which gives access to CQD. 


|  |View reports  |View EUII fields  |Create reports  |Upload building data  |
|---------|:-------:|:-------:|:-------:|:-------:|
|Office 365 Global Administrator     |Yes         |Yes         |Yes         |Yes         |
|Teams Service Administrator     |Yes         |Yes         |Yes         |Yes         |
|Teams Communications Administrator     |Yes         |Yes         |Yes         |Yes         |
|Teams Communications Support Engineer     |Yes         |Yes         |Yes         |No         |
|Teams Communications Support Specialist     |Yes         |No         |Yes         |No         |
|Skype for Business Administrator     |Yes         |Yes         |Yes         |Yes         |
|Azure AD Global Reader |Yes         |Yes         |Yes         |No         |
|Office 365 Reports Reader<sup>1</sup>     |Yes         |No         |Yes         |No         |

<sup>1</sup> In addition to reading CQD reports, the Office 365 Reports Reader can view all the [activity reports](https://support.office.com/article/activity-reports-0d6dfb17-8582-4172-a9a9-aed798150263) in the admin center and any reports from the [Microsoft 365 Adoption content pack](https://support.office.com/article/Office-365-Adoption-content-pack-77ff780d-ab19-4553-adea-09cb65ad0f1f).

> [!NOTE]
> If you're not seeing EUII (end-user identifiable information) and you have one of the roles that's permitted to see this information, keep in mind that CQD only keeps EUII for 30 days. Anything older than 30 days is deleted.

For more information about these roles, see [About Office 365 admin roles](/office365/admin/add-users/about-admin-roles).

## Upload Tenant Data information
<a name="BKMKTenantDataInformationUpload"></a>

The CQD Summary Reports dashboard includes a **Tenant Data Upload** page, accessed by selecting **Tenant Data Upload** from the settings menu in the top-right corner. This page is used for admins to upload tenant, building, and location information, including:

- A map of IP address and geographical information
- A map of each wireless AP and its MAC address
- A map of Endpoint to Endpoint Make/Model/Type, etc.
  
> [!NOTE]
> Reporting Labels that you upload to CQD will be handled as *Support Data* under your agreement for Office 365, including any information that would otherwise be considered *Customer Data* or *Personal Data*. Please do not include data you do not wish to provide to Microsoft as *Support Data*, as this information will be visible to Microsoft Engineers for support purposes.

  
1. On the **Tenant Data Upload** page, use the drop-down menu to choose a data file type to upload. The file data type denotes the content of the file (for example, "Building" refers to mapping of IP address and building and other geographical information, “Endpoint” refers to mapping of Endpoint Name to Endpoint Make/Model/Type information). CQD supports “Building” and “Endpoint” data types.
2. After you select the file data type, click **Browse** to choose a data file.

   - A data file must be a .tsv (tab-separated values) file or a .csv (comma-separated value) file. With a .csv file, any field that contains a comma must be surrounded by quotes or have the comma removed. For example, if your building name is NY,NY,  enter  "NY,NY" in the .csv file.
   - The data file must be no larger than 50 MB.
   - Data files have an expanded row limit of 1,000,000 to keep query performance fast. 
   - For each data file, each column in the file must match a predefined data type, discussed later in this topic.
3. Next, specify a **Start date** and, optionally, **Specify an end date**.
4. Finally, select **Upload** to upload the file to the CQD server.
    Before the file is uploaded, it is first validated. Once validated, it is stored in an Azure blob. If validation fails or the file fails to be stored in an Azure blob, an error message requests a correction to the file. The following image shows a sample error with an incorrect number of columns in the data file.

     ![Screenshot: shows an upload validation error](media/22716a32-3d3d-4870-983c-46089e8b212a.png)
  
5. If no errors occur during validation, the file upload succeeds. You can then see the uploaded data file in the **My uploads** table. The bottom of that page also shows a full list of all files uploaded for the current tenant.
    Each record shows one uploaded tenant data file, with file type, last update time, time period, description, a remove icon, and a download icon. To remove a file, select the trash bin icon in the table. To download a file, select the download icon in the **Download** column of the table.

     ![Screenshot: shows the My Uploads table](media/4168a883-bbea-461a-80b1-42eedf2e7732.png)

6. If you choose to use multiple building data files or multiple endpoint data files, some reports generate more slowly.

### Tenant data file format and structure
<a name="BKMKTenantDataFile"> </a>

#### Building data file

CQD uses a Building data file, which helps provide useful call details. The Subnet column is derived by expanding the Network+NetworkRange column, then joining the Subnet column to the call record’s First Subnet or Second Subnet column to show Building, City, Country, or Region information. The format of the data file you upload must meet the following criteria to pass the validation check before upload:

You can download a sample template [here](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/locations-template.zip?raw=true)
  
- The file must be either a .tsv file (columns are separated by a TAB) or a .csv file (columns are separated by a comma).
- The data file doesn't include a table header row. The first line of the data file is expected to be real data, not header labels like "Network".
- Data types in the file can only be String, Integer, or Boolean. For the  Integer data type, the value must be a numeric value. Boolean values must be either 0 or 1.
- If a column uses the String data type, a data field can be empty but must still be separated by a tab or comma. An empty data field just assigns an empty String value.
- There must be 14 columns for each row, each column must have the appropriate data type, and the columns must be in the order listed in the following table (comma delimited):


|Column field name|Data type|Example value|
|:--- |:--- |:--- |
|NetworkIP | String | 192.168.1.0 |
|NetworkName    | String|USA/Seattle/SEATTLE-SEA-1|
|NetworkRange|Number|26|
|BuildingName|String|SEATTLE-SEA-1|
|OwnershipType|String|Contoso|
|BuildingType|String|IT Termination|
|BuildingOfficeType|String|Engineering|
|City   |String| Seattle|
|ZipCode|String|98001|
|Country|String|US|
|State |String|WA|
|Region|String|MSUS|
|InsideCorp&dagger;|Boolean|0|
|ExpressRoute&Dagger;|Boolean|0|
|VPN (optional)|Boolean|0|
||||

&dagger; This setting can be used to reflect whether or not the subnet is inside the corporate network. You can customize usage for other purposes if you decide to.

&Dagger; This setting can be used to reflect whether or not the network uses Azure ExpressRoute. You can customize usage for other purposes if you decide to.  

**Sample row:**

`192.168.1.0,USA/Seattle/SEATTLE-SEA-1,26,SEATTLE-SEA-1,Contoso,IT Termination,Engineering,Seattle,98001,US,WA,MSUS,1,0,0`

> [!IMPORTANT]
> The network range can be used to represent a supernet (combination of several subnets with a single routing prefix). All new building uploads will be checked for any overlapping ranges. If you have previously uploaded a building file, you should download the current file and re-upload it to identify any overlaps and fix the issue before uploading again. Any overlap in previously uploaded files may result in the wrong mappings of subnets to buildings in the reports. Certain VPN implementations do not accurately report the subnet information. It is recommended that when adding a VPN subnet to the building file, instead of one entry for the subnet, separate entries are added for each address in the VPN subnet as a separate 32-bit network. Each row can have the same building metadata. For example, instead of one row for 172.16.18.0/24, you should have 256 rows, with one row for each address between 172.16.18.0/32 and 172.16.18.255/32, inclusive.
>
> The VPN column is optional and will default to 0.  If the VPN column’s value is set to 1, the subnet represented by that row will be fully expanded to match all IP addresses within the subnet.  Please use this sparingly and only for VPN subnets since fully expanding these subnets will have a negative impact on query times for queries involving building data.

#### Endpoint data file

CQD uses an Endpoint data file. The column values are used in the call record’s First Client Endpoint Name or Second Client Endpoint Name column to show Endpoint Make, Model, or Type information. The format of the data file you upload must meet the following criteria to pass the validation check before upload:

- The file must be either a .tsv file (columns are separated by a TAB) or a .csv file (columns are separated by a comma).
- The content of the data file doesn't include table headers. The first line of the data file is expected to be real data, not a header label like "EndpointName".
- All six columns use the String data type only. The maximum allowed length is 64 characters.
- A data field can be empty but must still be separated by a tab or comma. An empty data field just assigns an empty String value.
- EndpointName must be unique, otherwise the upload fails. If there is a duplicate row or two rows that use the same EndpointName the conflict will  cause incorrect joining.
- EndpointLabel1, EndpointLabel2, and EndpointLabel3 are customizable labels. They can be empty Strings or values such as “IT Department designated 2018 Laptop” or “Asset Tag 5678”.
- There must be six columns for each row and the columns must be in the following order:

  **Field order:**

EndpointName, EndpointModel, EndpointType, EndpointLabel1, EndpointLabel2,  EndpointLabel3

  **Sample row:**

`1409W3534, Fabrikam Model 123, Laptop, IT designated 2018 Laptop, Asset Tag 5678, Purchase 2018,`  


## Near-real-time (NRT) data feed

**<font color="red">(SIUNIE, we can get rid of all the v2 & v3 notes, right?)**</font>

New in November 2019, CQD uses a near-real-time (NRT) data feed. Call records are available in CQD within 30 minutes of the end of a call. Call records from the NRT pipeline are only available for a few months before they are removed from the data set. 

**(REMOVE???)**  CQD v3 merges data from the current v2 pipeline with NRT data from the v3 pipeline. Queries on the v2 and v3 portals for the data from the Archival period produce the same results. V2 and v3 data queries for the NRT Data and NRT Data + PII periods will be different.

### PII and EUII data

For compliance reasons, personally-identifiable information (PII) or end-user identifiable information (EUII) data is only kept for 30 days. As NRT data crosses the 30-day mark, fields that contain PII or EUII are cleared, resulting in PII-free NRT data. Fields that contain PII or EUII data are:

- Full IP address
- Media Access Control (MAC) Address
- Basic Service Set identifier (BSSID)
- Session Initiation Protocol (SIP) URI (Skype for Business only)
- User Principal Name (UPN)
- Machine Endpoint Name
- User Verbatim Feedback
- Object ID (the Active Directory object ID of the endpoint's user)

#### Admin roles with and without EUII access

These [RBAC](https://docs.microsoft.com/azure/role-based-access-control/overview) roles have EUII access:
- Global Admin
- Teams Service Admin
- Teams Communications Admin
- Teams Communications Support Engineer
- Global Reader
- Skype for Business Admin

These RBAC roles don't have EUII access:
- Reports Reader
- Teams Communications Support Specialist

### Date controls

CQD supports the following Rolling Trend types:

- 5-day
- 7-day
- 30-day
- 60-day
- 90-day

The URL Date parameter accepts a Day field. Rolling-day reports use dates specified in the YYYY-MM-DD format as the last day of the trend. The URL Date parameter “00”  indicates “today”.

|URL| End date of Rolling Day Trend|
|:---|:---|
|<span>https://<cqdv3>/spd/#/Dashboard/<reportid>/2019-02/</span>   |Current Day of Feb 2019|
|<span>https://<cqdv3>/spd/#/Dashboard/<reportid>/2019-02-15/</span>|Feb 15, 2019|
|<span>https://<cqdv3>/spd/#/Dashboard/<reportid>/00/</span>        |Current Day|
|||

By default, the current day of the month is used as the last day of the Rolling Day Trend.

### Drill-down functionality

CQD provides drill-down fields in several reports. This is a powerful tool that will help you zero in on problems in your org. If you select a drill-down field, the report automatically opens the appropriate tab and filters on the selected value. If that tab has its own drill-down fields and one is selected, both sets of filters are applied, progressively narrowing the resulting data set.

For example, in Quality Drill Down Reports, click a date to drill into it on the **Locations** tab.

![Screenshot: shows the drill thru report](media/CQD-drill-thru-report.png)

You can add multiple dates from the **Location** tab, such as adding 2019-09-22 to Date: 2019-09-24: 

![Screenshot: add a date to the drill thru report](media/CQD-add-date.png)

For in-depth guidance on using drill-down filters, read [Drill-down filters - narrow the focus of investigations](quality-of-experience-review-guide.md#drill-down-filters---narrow-the-focus-of-investigations).

> [!TIP]
> Don't jump directly to the last tab without first applying filters. Otherwise, the result list might be too large.

## Data available in CQD reports
<a name="BKMKFeaturesOfTheCQD"> </a>

The default summary and detailed CQD reports may be all you need to manage call quality for your org. If you need to, you can [create custom reports](#create-custom-detailed-reports).

|Feature|Summary Reports|Detailed Reports|
|:--- |:--- |:--- |
|Application sharing metric | No | Yes |
|Customer building information support | Yes | Yes |
|Customer endpoint information support | Only in <span>cqd.teams.microsoft.com<span/> | Only in <span>cqd.teams.microsoft.com<span/> |
|Drill down analysis support   | No   | Yes   |
|Media reliability metrics   | No   | Yes   |
|Out-of-the-box reports   | Yes   | Yes   |
|Overview reports   | Yes   | Yes   |
|Per-user report set   | No   | Yes   |
|Report set customization (add, delete, modify reports)   | No   | Yes   |
|Video-based screen sharing metrics   | No   | Yes   |
|Video metrics   | No   | Yes   |
|Amount of data available   | Last 12 months   | Last 12 months   |
|Microsoft Teams data   | Yes   | Yes   |
| | | |

### Out-of-the-box reports

All editions of CQD provide an experience that gives you call quality metrics without the need to create new reports. Once data is processed in the back-end, you see call quality data in the reports.

New in January 2020: [Download Power BI query templates for CQD](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/CQD-Power-BI-query-templates.zip?raw=true). Customizable Power BI templates you can use to analyze and report your CQD data.
 
### Select product data to see in reports
<a name="BKMKProductFilter"></a>

In the Summary and Location-Enhanced Reports, you can use the **Product Filter** drop-down to show all product data, only Microsoft Teams data, or only Skype for Business Online data.
  
![Screenshot: shows the Product Filter control options](media/206ad818-0f72-4c8e-b25e-3cc8fcfbef05.png)
  
In Detailed reports, you can use the **Is Teams** dimension to filter the data to Microsoft Teams or Skype for Business Online data.

## Summary Reports

These are the reports that you'll see on the CQD Dashboard when you first sign in to CQD. They give you an at-a-glance look at quality trends with daily, monthly, and table reports to assist with identifying subnets that have poor quality. 

|Tab  |  |
|---------|---------|
|Overall Call Quality     | Aggregate of the other 3 tabs        |
|Server—Client     |Details of the streams between server and client endpoints         |
|Client—Client     |Details of the streams between two client endpoints         |
|Voice Quality SLA     |Info about calls included in the Skype for Business voice quality [SLA](https://go.microsoft.com/fwlink/p/?linkid=846252)         |

### Overall Call Quality tab

Use the data on this tab to evaluate call quality status and trends based on stream counts and poor percentages. The legend in the upper-right corner shows which color and visual elements represent these metrics.
  
![Screenshot: show the Call Quality tab](media/c8d183b1-6592-49b0-a81d-35cc0568d5f0.png)
  
Streams are classified in three groups: Good, Poor, and Unclassified. There are also calculated  *Poor %*  values that give you the ratio of streams classified as *Poor*  to the total classified stream count. Since *Poor % = Poor streams/ (Poor streams+ Good streams) * 100*, the *Poor %*  is unaffected by the presence of multiple *Unclassified*  streams. To see what classifies a stream as poor or good, refer to [Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md).
  
Use the scale on the left to measure the stream count values.
  
![Screenshot: shows stream count values](media/850bd25d-d9b2-4df4-8ca6-526a528897c2.png)
  
Use the scale on the right to measure the Poor % values.
  
![Screenshot: shows poor % values](media/29795f71-ca96-4763-a76c-b4bb7c0e5828.png)
  
You can also obtain the actual numerical values by hovering the mouse over a bar.
  
> [!NOTE]
> The following example is from a very small sample data set, and the values aren't realistic for an actual deployment.
  
![Screenshot: shows mouse used to access data](media/8724b016-1a50-4d19-b48a-3b1aae4eb895.png)
  
The overall stream volume helps determine how relevant the calculated Poor percentages are. The smaller the volume of overall streams, the less reliable the reported Poor percentage values are.
  
### Server-Client tab and Client-Client tabs

These two tabs provide details for the streams that took place in their endpoint-to-endpoint scenarios. The Server-Client tab has four collapsible sections that represent four scenarios under which media streams would flow.
  
- Wired Inside
- Wired Outside
- Wifi Inside
- Wifi Outside

Similarly, the Client-Client tab has five collapsible sections:

- Wired Inside — Wired Inside
- Wired Inside — Wired Outside
- Wired Outside — Wired Outside
- Wired Inside — Wifi Inside
- Wired Inside — Wifi Outside

#### Inside versus Outside

CQD classifies a stream as  *Inside*  or *Outside*  using Building information, if it exists. Endpoints of each stream are associated with a subnet address. If the subnet is in the list of the subnets marked InsideCorp in the uploaded Building information, then it is considered *Inside*. If Building information has not yet been uploaded, then Inside Test always classifies the streams as *Outside*. 

The Inside Test for a Server-Client scenario only considers the client endpoint. Because servers are always outside from a user's perspective, this isn't accounted for in the test.
  
#### Wired versus wifi

As the names indicate, the classification criteria is based on the type of client connections. Server is always wired and it isn't included in the calculation. In a given stream, if one of the two endpoints is connected to a Wifi network, then CQD classifies it as Wifi.
  

## Reports provided with CQD

|Name  |  |
|---------|---------|
|Location-Enhanced Reports     |Shows quality trends based on location information. This report appears only if you've [uploaded your tenant data](#BKMKTenantDataInformationUpload).        |
|Reliability Reports     |Includes audio, video, video-based screen sharing (VBSS), and app sharing reports         |
|Quality of Experience Reports     |Audio quality and reliability for all clients and devices, including meeting rooms. These reports are a “slimmed-down” version of the downloadable [CQD templates](https://aka.ms/QERtemplates), focusing on key areas for analyzing audio quality and reliability.         |
|Quality Drill Down Reports     | Drill downs: Date by region, locations, subnets, hour, and users         |
|Failure Drill Down Reports     | Drill downs: Date by region, locations, subnets, hour, and users        |
|Rate My Call Reports     |Analyze user call ratings by region, location, or by user. Includes verbatim feedback.         |
|Help Desk Reports     |Help Desk Reports look at call and meeting data for individual users, groups of users, or everyone. Incorporating building and EUII data, these reports help identify possible system issues based on network location, conference details, devices, or firmware.         |
|Client Version Reports     |Client Version Summary: View the Sessions and Users counts for each client app version<br><br>Client Version by User: View user names for each client app version <br><br>Pre-built filters for Product and Client Type help focus the versions to specific clients.         |
|Endpoint Reports     |Shows call quality by machine endpoints (computer make and model). These reports include building data, if you've uploaded it.         |


## Create custom detailed reports

If the default CQD reports don't meet your needs, use these instructions to create a custom report.

From the pull-down list of reports at the top of the screen displayed at login \(the **Summary Reports** screen\) Select **Detailed Reports**  and then **New**. Click **Edit** in a report to see the Query Editor. Each report is backed by a query into the cube. A report is a visualization of the data returned by its query. The Query Editor helps you edit these queries and the display options of the report.

Point to bar charts and trend lines in the report to display detailed values. The report that has focus will show the action menu: **Edit**, **Clone**, **Delete**, **Download**, and **Export Report Tree**.


### Filtering reports

The templates provided include several built-in queries and report filters. The following sections describe the most common filters used throughout the templates.

#### URL filter

You can use a URL filter to filter every report for a specific dimension. The most common URL filters are used to filter reports to exclude federated participant telemetry, or focus on Teams or Skype for Business Online.

Excluding federated data from CQD reports is useful when you’re remediating managed buildings or networks where federated endpoints might influence your reports.

To implement a URL filter, in the browser address bar, append the following to the end of the URL:

```
/filter/[AllStreams].[Second Tenant Id]\|[YOUR TENANT ID HERE]
```

Example:  

```https://cqd.teams.microsoft.com/cqd/#/1234567/2018-08/filter/[AllStreams].[Second Tenant Id]|[TENANTID]```

To filter the reports for Teams or Skype for Business, append the following to the end of the URL:

```
/filter/[AllStreams].[Is Teams]|[TRUE | FALSE]
```

Example:

```https://cqd.teams.microsoft.com/cqd/#/1234567/2018-08/filter/[AllStreams].[Is Teams]|[TRUE]```
EndpointName, EndpointMake, EndpointModel, EndpointType, EndpointLabel1, EndpointLabel2,  EndpointLabel3


> [!NOTE]
> The URL examples above are for visual representation only. Please use the default CQD link of <https://cqd.teams.microsoft.com>.
`1409W3534, 123 manufacturer, Fabrikam Model 123, Laptop, IT designated 2018 Laptop, Asset Tag 5678, Purchase 2018

## Migrate reports from previous version of CQD

If  you created reports or uploaded tenant data (mapping) files to CQD for Skype for Business (https://cqd.lync.com) and want to migrate them to CQD for Teams (https://cqd.teams.microsoft.com), here’s how:

1.	Go to [https://cqd.lync.com/cqd/](https://cqd.lync.com/cqd/) and browse to the report set you want to export. 
2.	Hover over the report and, on the "..." menu, choose **Export Report Tree**. Save the export file.
3.	Go to [https://cqd.teams.microsoft.com/cqd/](https://cqd.teams.microsoft.com/cqd/)  and browse to the location where you want to import the reports.
4.	From the links on the left, click **Import** and select the exported file. 
5.	After the reports are imported, you'll see this message: "Report import was successful. The new report has been added at the end of report set." 


##### How to find your tenant ID

The tenant ID in CQD corresponds to the Directory ID in Azure. If you don’t know your Directory ID, you can find it in the Azure portal:

1.  Sign in to the Microsoft Azure portal: <https://portal.azure.com>

2.  Select **Azure Active Directory**.

3.  Under **Manage**, select **Properties**. Your tenant ID is in the **Directory ID** box.

You can also find your tenant ID by using PowerShell: 
  ```
  Login-AzureRmAccount
  ```

#### Query filters

Query filters are implemented by using the Query Editor in CQD. These filters are used to reduce the number of records returned by CQD, thus minimizing the report’s overall size and query times. This is especially useful for filtering out unmanaged networks. The filters listed in the following table use regular expressions (RegEx).

_Table 3 - Query filters_

| Filter         | Description          | CQD query filter example      |
|----------------|----------------------|-------------------------------|
| No blank values   | Some filters don’t have the option to filter for blank values. To filter blank values manually, use the blank expression and set the filter to Equals or Not Equals, depending on your needs.      | Second Building Name \<\> \^\\s\*\$                       |
| Exclude common subnets | Without a valid building file to separate managed from unmanaged networks, home networks will be included in the reports. These home subnets are outside the scope of IT’s control and can be quickly excluded from a report. Common subnets, as defined in this guide, are 10.0.0.0, 192.168.1.0 and 192.168.0.0. | Second Subnet \<\> 10.0.0.0 \| 192.168.0.0 \| 192.168.1.0 |
| View inside only  | Used to filter a report for managed (inside) or unmanaged (outside). The managed CQD template is already preconfigured with these filters.       | Second Inside Corp = Inside        |

#### Report filters

Report filters are implemented by adding a filter to the rendered report either in the Query Editor or directly to the report. The following report filters are used throughout the template.

_Table 4 - Report filters_

| Filter     | Description                            | CQD report filter example         |
|------------|----------------------------------------|-----------------------------------|
| Month      | Start with the year first, then month. | 2017-10                           |
| Alphabetic | Filters for any alphabetic characters. | [a-z]                             |
| Numeric    | Filters for any numeric characters.    | [0-9]                             |
| Percentage | Filters for a percentage.              | ([3-9]\\.)\|([3-9])\|([1-9][0-9]) |

## Why is CQD data from Skype for Business different than CQD data from Teams? 

If you're trying to compare data between the older CQD from the Skype for Business legacy portal (cqd.lync.com) and the latest CQD from the Teams admin center (cqd.teams.microsoft.com), you'll quickly notice that the data doesn't match. That's because the latest CQD reports on many additional calling scenarios. If you're still using reports from the older CQD, use this article to help you interpret those reports: [Call Quality Dashboard for Skype for Business Server](https://docs.microsoft.com/skypeforbusiness/management-tools/call-quality-dashboard/call-quality-dashboard).

To learn more about the differences between the older and latest CQD, read the [Introducing the Advanced Call Quality Dashboard](https://techcommunity.microsoft.com/t5/Microsoft-Teams-Blog/Introducing-the-Advanced-Call-Quality-Dashboard/ba-p/972586) blog, from November 5, 2019.


You’ll likely see more data differences between your older and newer CQD reports at the aggregated or summary level. If you compare data at a more granular level, you’ll get an “apples-to-apples” comparison. For example, if you’re looking at data for an individual building, the Percentage of Poor Quality should be the same between both the older and new CQD reports.

- Pick a scenario with a tight focus, such as corporate wired connections, Windows Desktops, or a single region or building.
- Check the Teams MR, TR, or MP IP ranges. The Teams ranges are newer than Skype for Business Online, and that can cause connectivity issues involving firewalls.
- Don't compare summary or top-level numbers. These comparisons will lead you to compare a large call volume of Skype for Business Online calls on a corporate wired connection to a small volume of Teams calls on an LTE or private network.
- Beware of location bias and population differences: There are many comparisons that are too dissimilar to be useful:
  - NOAM : APAC
  - NY : Goa
  - Wired : wifi
  - Corporate network : home network
  
### Why can't I see EUII in CQD?

These admin roles can access CQD, but they can't view EUII (end-user identifiable information):
- Office 365 Reports Reader
- Teams Communications Support Specialist

To learn more about roles that can access CQD - including EUII - read [Assign roles for accessing CQD](quality-of-experience-review-guide.md#assign-roles-for-accessing-cqd).

### Why am I seeing Skype for Business information in CQD when I've filtered for Teams only?

When you filter for Teams only in CQD reports (isTeams = 1), you're filtering for all calls where the *first endpoint* is Teams. If the *second endpoint* is Skype for Business, that information will show up in your CQD report.

CQDv2 and CQDv3 will always have different total counts since CQDv3 will have new scenarios that CQDv2 will not have. That’s why comparing Summary Total or Aggregated all-up numbers with no filters will have these expected differences.  

Depending on Customers’ scenario, CQDv3 will include SFB 2019 on-premises calls (if SFB 2019 is used with a data connector), Skype Bot calls (AA, CVI, VDI), Live Events and PSTN calls. Scenarios/Features which are available for the customers, but their data are not in CQD V2.

For instance, it is expected that your customers and you will see 200,000 audio streams, with 5000 failures in CQD V2 Summary Report; versus 300,000 audio streams with 5500 failures (coming from 2019 on-prem calls, CVI calls, PSTN calls etc) in CQD V3.

In order to determine, if there are any unexpected differences, you must look at various breakdowns of the overall data.  Compare with intent.  Slicing the data by User Agent Category Pair is one of the first things we recommend.  *First Product* and *Second Product* are also good slicers.  

## Comparing Teams and Skype for Business CQD data

Even within the latest CQD (cqd.teams.microsoft.com), you'll see differences in data between Teams and Skype for Business. Some reasons:
- Differences in the mechanisms for ensuring performance and reliability
  - Teams has auto-reconnect and fast roaming. Skype for Business doesn't.
  - Teams has dynamic bandwidth management. Skype for Business doesn't.
- Differences in [IP address ranges](Office-365-URLs-IP-address-ranges.md) between Teams and Skype for Business. The Teams IP ranges are newer, which could cause connectivity problems at the firewall.

## Open CQD from the Skype for Business legacy portal

![An icon of the Skype for Business logo](media/sfb-logo-30x30.png) **Using the Skype for Business legacy portal**

1. Sign in to your Office 365 organization using an admin account, and then select the **Admin** tile to open the Admin center.
2. In the left pane, under **Admin centers**, select **Microsoft Teams** to open the Teams admin center.
3. In the Teams admin center, select **Legacy Portal** in the left pane, select **Tools**, and then select **Skype for Business Online Call Quality Dashboard**.

     ![Screenshot: Select the Call Quality Dashboard](media/6cc7f80f-b8e2-4a9b-aab8-ac871d07a261.png)

4. On the page that opens, sign in with your Global Administrator account, and then provide the credentials for the account when prompted.

After the first time you sign in, CQD will begin collecting and processing data. As of December 2019, you can still access the older version of CQD (cqd.lync.com), although the legacy portal gives you a link to the latest CQD (cqd.teams.microsoft.com). Eventually, the older version of CQD will be decommissioned.


## Related topics

[Dimensions and measures available in Call Quality Dashboard](dimensions-and-measures-available-in-call-quality-dashboard.md)

[Stream Classification in CQD](stream-classification-in-call-quality-dashboard.md)

[Improve and monitor call quality for Teams](monitor-call-quality-qos.md)

[Call Analytics and Call Quality Dashboard](monitor-call-quality-qos.md)
 
