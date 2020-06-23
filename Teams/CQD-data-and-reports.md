---
title: Data and reports in Call Quality Dashboard (CQD)
ms.author: lolaj
author: LolaJacobsen
manager: serdars
ms.reviewer: mikedav, siunies, gageames
ms.topic: article
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
  - seo-marvel-apr2020
description: Learn about the data and reports available in Microsoft Call Quality Dashboard (CQD).
---

# Data and reports in Call Quality Dashboard (CQD)

Microsoft Call Quality Dashboard (CQD) uses a near-real-time (NRT) data feed. Call records are available in CQD within 30 minutes of the end of a call. Call records from the NRT pipeline are only available for a few months before they are removed from the data set. 


> [!NOTE]
> Advanced CQD (new in November 2019) merges data from the older CQD pipeline (which made call records available in about 24 hours) with NRT data from the Advanced CQD pipeline. Queries on the older and Advanced portals for the data from the Archival period produce the same results. Queries on either portal for the NRT Data and NRT Data + EUII periods will be different.

## Many ways to access CQD data

You can access CQD data by several different avenues. Pick the one that best meets your needs:

|  |  |
|---------|---------|
|Teams admin center [(https://admin.teams.microsoft.com)](https://admin.teams.microsoft.com)    | CQD data is included on the **Users** page in the Teams admin center, showing the most common data you need in an easy-to-read format. You can't customize CQD data that you find under **Users**.  |
|CQD portal [(https://cqd.teams.microsoft.com)](https://cqd.teams.microsoft.com)     | Robust summary and detailed reports that meet most needs, with drill-through filtering. You can also customize reports in the CQD portal. <br><br>Get two [CQD report templates](#import-the-cqd-report-templates) to help you analyze data in the CQD portal.       |
|Power BI     | Use direct queries to view your CQD data in Power BI using [customizable Power BI templates](CQD-Power-BI-query-templates.md). [Download Power BI query templates for CQD](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/CQD-Power-BI-query-templates.zip?raw=true).<br><br>You can also [use the REST API to access CQD data](https://docs.microsoft.com/skypeforbusiness/management-tools/call-quality-dashboard/data-api) through Power BI. Use this method if you want to download your CQD data so you can work on it offline.        |
|Graph API     | Access call quality data yourself using the [Graph API](https://docs.microsoft.com/graph/api/resources/callrecords-api-overview?view=graph-rest-beta). This is the most complex method, but it gives you the most control and flexibility in analyzing your call quality data.  For example, if you need to join it with other data for your organization, you can use the Graph API to create a data model and incorporate call quality data.        |

## Import the CQD report templates

Download [two curated CQD report templates](https://aka.ms/qertemplates) (All Networks and Managed Networks) to help you get up to speed quickly with CQD. The All Networks template, though optimized to work with a building data file, can be used while you work toward collecting and uploading building information into CQD, as described in the next section.

**To import the templates (.CQDX) into CQD**

1. In CQD, select **Detailed Reports** from the menu at the top of the page.

2. In the left panel, select **Import**. Browse to the first CQDX template and select **Open**.

3. After the template is uploaded, a pop-up window will display the message "Report import was successful." 

4. Repeat steps 2 and 3 for the second CQD template.

> [!NOTE]
> Each user must import the CQD templates into their CQD instance. 



## EUII data

For compliance reasons, end-user identifiable information (EUII) data (also known as personally-identifiable information or PII) is only kept for 30 days. As NRT data crosses the 30-day mark, fields that contain EUII are cleared, resulting in EUII-free NRT data. Fields that contain EUII data are:

- Full IP address
- Media Access Control (MAC) Address
- Basic Service Set identifier (BSSID)
- Session Initiation Protocol (SIP) URI (Skype for Business only)
- User Principal Name (UPN)
- Machine Endpoint Name
- User Verbatim Feedback
- Object ID (the Active Directory object ID of the endpoint's user)

### Admin roles with and without EUII access

These [RBAC](https://docs.microsoft.com/azure/role-based-access-control/overview) roles **DO** have EUII access:
- Global Admin
- Teams Service Admin
- Teams Communications Admin
- Teams Communications Support Engineer
- Global Reader
- Skype for Business Admin

These RBAC roles **DON'T** have EUII access:
- Reports Reader
- Teams Communications Support Specialist
- 5-day
- 7-day
- 30-day
- 60-day
- 90-day


## Date controls

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


## Data available in CQD reports

The default summary and detailed CQD reports may be all you need to manage call quality for your org. If you need to, you can [create custom reports](#create-custom-detailed-reports). 

If you want to use Power BI to analyze your CQD data, read [Use Power BI to analyze CQD data for Teams](CQD-Power-BI-query-templates.md).

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


 
### Select product data to see in reports

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
- WiFi Inside
- WiFi Outside

Similarly, the Client-Client tab has five collapsible sections:

- Wired Inside — Wired Inside
- Wired Inside — Wired Outside
- Wired Outside — Wired Outside
- Wired Inside — WiFi Inside
- Wired Inside — WiFi Outside

#### Inside versus Outside

CQD classifies a stream as  *Inside*  or *Outside*  using Building information, if it exists. Endpoints of each stream are associated with a subnet address. If the subnet is in the list of the subnets marked InsideCorp in the uploaded Building information, then it is considered *Inside*. If Building information has not yet been uploaded, then Inside Test always classifies the streams as *Outside*. 

The Inside Test for a Server-Client scenario only considers the client endpoint. Because servers are always outside from a user's perspective, this isn't accounted for in the test.
  
#### Wired versus WiFi

As the names indicate, the classification criteria is based on the type of client connections. Server is always wired and it isn't included in the calculation. In a given stream, if one of the two endpoints is connected to a WiFi network, then CQD classifies it as WiFi.
> [!NOTE]
> Given a stream, if one of the two endpoints is connected to a WiFi network, then it is classified as WiFi in CQD.
  
  
## Tenant Data information

The CQD Summary Reports dashboard includes a **Tenant Data Upload** page, accessed by selecting **Tenant Data Upload** from the settings menu in the top-right corner. This page is used for admins to upload their own information, such as:

- A map of IP address and geographical information
- A map of each wireless AP and its MAC address
- A map of Endpoint to Endpoint Make/Model/Type, etc.
  
We recommend that you upload your tenant, building, and location data so CQD can include this information in your reports. If you haven't already uploaded this data, read [Upload tenant and building data](CQD-upload-tenant-building-data.md). 


## Detailed reports

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

If the default CQD reports don't meet your needs, use these instructions to create a custom report. Or (as of January 2020) [Use Power BI for CQD reports ](cqd-power-bi-query-templates.md)instead.

From the pull-down list of reports at the top of the screen displayed at login \(the **Summary Reports** screen\) Select **Detailed Reports**  and then **New**. Click **Edit** in a report to see the Query Editor. Each report is backed by a query into the cube. A report is a visualization of the data returned by its query. The Query Editor helps you edit these queries and the display options of the report.
> [!IMPORTANT]
> The network range can be used to represent a supernet (combination of several subnets with a single routing prefix). All new building uploads will be checked for any overlapping ranges. If you have previously uploaded a building file, you should download the current file and re-upload it to identify any overlaps and fix the issue before uploading again. Any overlap in previously uploaded files may result in the wrong mappings of subnets to buildings in the reports. Certain VPN implementations do not accurately report the subnet information. It is recommended that when adding a VPN subnet to the building file, instead of one entry for the subnet, separate entries are added for each address in the VPN subnet as a separate 32-bit network. Each row can have the same building metadata. For example, instead of one row for 172.16.18.0/24, you should have 256 rows, with one row for each address between 172.16.18.0/32 and 172.16.18.255/32, inclusive.
>
> The VPN column is optional and will default to 0.  If the VPN column's value is set to 1, the subnet represented by that row will be fully expanded to match all IP addresses within the subnet.  Please use this sparingly and only for VPN subnets since fully expanding these subnets will have a negative impact on query times for queries involving building data.

Point to bar charts and trend lines in the report to display detailed values. The report that has focus will show the action menu: **Edit**, **Clone**, **Delete**, **Download**, and **Export Report Tree**.



## Query filters

Query filters are implemented by using the Query Editor in CQD. These filters are used to reduce the number of records returned by CQD, thus minimizing the report’s overall size and query times. This is especially useful for filtering out unmanaged networks. The filters listed in the following table use regular expressions (RegEx).


| Filter         | Description          | CQD query filter example      |
|----------------|----------------------|-------------------------------|
| No blank values   | Some filters don’t have the option to filter for blank values. To filter blank values manually, use the blank expression and set the filter to Equals or Not Equals, depending on your needs.      | Second Building Name \<\> \^\\s\*\$                       |
| Exclude common subnets | Without a valid building file to separate managed from unmanaged networks, home networks will be included in the reports. These home subnets are outside the scope of IT’s control and can be quickly excluded from a report. Common subnets, as defined in this guide, are 10.0.0.0, 192.168.1.0 and 192.168.0.0. | Second Subnet \<\> 10.0.0.0 \| 192.168.0.0 \| 192.168.1.0 |
| View inside only  | Used to filter a report for managed (inside) or unmanaged (outside). The managed CQD template is already preconfigured with these filters.       | Second Inside Corp = Inside        |

## Report filters

Use CQD report filters to narrow the focus of your investigations. Use report filters by adding a filter to the rendered report either in the Query Editor or directly in the report. The following report filters are used throughout the [CQD templates](https://aka.ms/QERtemplates).


| Filter     | Description                            | CQD report filter example         |
|------------|----------------------------------------|-----------------------------------|
| Month      | Start with the year first, then month. | 2017-10                           |
| Alphabetic | Filters for any alphabetic characters. | [a-z]                             |
| Numeric    | Filters for any numeric characters.    | [0-9]                             |
| Percentage | Filters for a percentage.              | ([3-9]\\.)\|([3-9])\|([1-9][0-9]) |


### Drill-down filters

CQD reports feature several drill-down filters, which are powerful tools for narrowing the focus of your call-quality investigations. If you select a drill-down field, the report automatically opens the appropriate tab and filters on the selected value. If that tab has its own drill-down fields and one is selected, both sets of filters are applied, progressively narrowing the resulting data set.

![Diagram illustrating drill-down report flow](media/qerguide-image-drillthrureportflow.png)


#### Adding and editing drill-down fields

When editing a report, you have the option to specify drill-down fields of your own using the Query Editor.

Start by clicking **…** for the report you want to edit, then select **Edit**.

![Screenshot of editing a drill-down field](media/qerguide-image-addeditdrilldownfields.png)

Select a Dimension from the list on the left side of the Query Editor. Then click on the dropdown below the **Navigate To** label and select the tab and expander group that you want that Dimension to drill through to. Note: Presently, drill-down functionality only works by navigating to different tabs. Support for drilling through to a specific expander will be added later. Finally, click **Close** to save your changes to the Dimension, then click **Save** to save and close the Query Editor.

![Screenshot of selecting a dimension in the Query Editor](media/qerguide-image-selectquerydimension.png)

### Multi-select filters

In addition to drill-down functionality, CQD also supports specifying Filters with multiple values (OR filters).

In order to select multiple filter values, begin by adding a new filter to the report. Click **+** beside the **Filters** label, enter the name of the Dimension you want to use, and click **Add**.

![Screenshot of adding a multi-select filter](media/qerguide-image-addmultiselectfilter.png)

Then, click **Search** (a magnifying glass icon next to the new filter). You'll see a text field, and a number of options, including **Select All** and **Invert**. Enter a value,  and click **Search** next to that field to search. Alternatively, leave the text field empty and click **Search** to view up to the first 100 options.

```PowerShell
/filter/[AllStreams].[Second Tenant Id]\|[YOUR TENANT ID HERE]
```

Example:  

![Screenshot of adding a query filter](media/qerguide-image-addfilter.png)

### Dashboard level filters
Certain CQD reports have dashboard-level filters added to them, making it easy to filter by common parameters. These filters appear outside the regular report tabs and directly beneath the Product filter, and they apply to all filters in the Dashboard.

![Screenshot of a dashboard filter](media/qerguide-image-dashboardfilters.png)
```PowerShell
/filter/[AllStreams].[Is Teams]|[TRUE | FALSE]
```

### URL filters

CQD supports adding filters to the URL. This makes it easy to share or bookmark a CQD query. You can define parameters in the URL, such as Trending Month, tenant ID, or language. You can also add Product or Dashboard level filters to the URL.
Excluding federated data from CQD reports is useful when you're remediating managed buildings or networks where federated endpoints might influence your reports.

To add a filter, append the following to the end of the URL:

```
/filter/[AllStreams].[Second Tenant Id]\|[YOUR TENANT ID HERE]
```

Example:  

```https://cqd.teams.microsoft.com/cqd/#/1234567/2018-08/filter/[AllStreams].[Second Tenant Id]|[TENANTID]```

To add a Dashboard-level filter to a URL, that filter must exist in CQD as either a Product or Dashboard level filter. Add these filters to the URL after the Trending Month and before the URL parameters:

```filter/DATA_MODEL_NAME|VALUE```

For example, to apply a Product filter value of Microsoft Teams, you'd add the following:

```filter/[AllStreams].[Is%20Teams]|[True]```

Your entire URL would look something like this:

```https://cqd.teams.microsoft.com/spd/#/Dashboard/2624085/2018-9/filter/[AllStreams].[Is%20Teams]|[True]```

To apply URL filters with multi-select values, separate each value with a pipe ( | ) character. For example:

```filter/[AllStreams].[Media%20Type]|[Video]|[Audio]|[VBSS]```

If you specify an invalid name or value, the URL filter won't be applied.


You can use a URL filter to filter every report for a specific dimension. The most common URL filters are used to filter reports to exclude federated participant telemetry, or focus on only Teams or Skype for Business Online. Excluding federated data from CQD reports is useful when you're remediating managed buildings or networks where federated endpoints might influence your reports.

| Filter         | Description          | CQD query filter example      |
|----------------|----------------------|-------------------------------|
| No blank values   | Some filters don't have the option to filter for blank values. To filter blank values manually, use the blank expression and set the filter to Equals or Not Equals, depending on your needs.      | Second Building Name \<\> \^\\s\*\$                       |
| Exclude common subnets | Without a valid building file to separate managed from unmanaged networks, home networks will be included in the reports. These home subnets are outside the scope of IT's control and can be quickly excluded from a report. Common subnets, as defined in this article, are 10.0.0.0, 192.168.1.0 and 192.168.0.0. | Second Subnet \<\> 10.0.0.0 \| 192.168.0.0 \| 192.168.1.0 |
| View inside only  | Used to filter a report for managed (inside) or unmanaged (outside). The managed CQD template is already preconfigured with these filters.       | Second Inside Corp = Inside        |


#### How to find your tenant ID

The tenant ID in CQD corresponds to the Directory ID in Azure. If you don't know your Directory ID, you can find it in the Azure portal:

1.  Sign in to the Microsoft Azure portal: <https://portal.azure.com>

2.  Select **Azure Active Directory**.

3.  Under **Manage**, select **Properties**. Your tenant ID is in the **Directory ID** box.

You can also find your tenant ID by using PowerShell: 
  ```
  Login-AzureRmAccount
  ```



## Frequently asked questions

### Why does CQD mark a call as "Good" if one or more meeting participants had a poor experience?

Check out the rules CQD uses for [stream classification](stream-classification-in-call-quality-dashboard.md).
 
For audio streams, any of the 5 classifiers, which are calculated for the average based on the length of the call, could all be within "good" parameters. It doesn't mean the users didn't experience something that contributed to an audio drop out, static, or glitch. 

To determine if it was a network problem, look at the delta between the average values for the session and the max values. Max values are the maximum detected and reported during the session.
 
Here's an example of how to troubleshoot this situation. Let's say you take a network trace during a call and the first 20 minutes there are no lost packets but then you have a gap of 1.5 seconds of packets and then good for the remainder of the call. The average is going to be <10% (0.1) Packet loss even in a Wireshark trace RTP analysis. What was the Max Packet Loss? 1.5 Seconds in a 5-second period would be 30% (0.3). Did that occur within the five second sampling period (maybe or it could be split over the sampling period)?
 
If network metrics look good in the averages and max values, then look to other telemetry data: 
- Check CPU Insufficient Event Ratio to see if the detected CPU resources available were insufficient and caused poor quality. 
- Was the audio device in Half Duplex mode to prevent feedback due to microphones that are to close to speakers? 
- Check the Device Half Duplex AEC Event Ratio. Was the device glitching or the microphone glitching introducing noise or static due to USB Audio Drop outs when plugged into a Hub or Docking Station:  
- Check the Device Glitches and Microphone glitches event ratios. Was the device itself functioning properly?  
- Check the Capture and Render Device Not Functioning Event Ratios.


For more on dimensions and measures available in CQD telemetry, read [Dimensions and measurements available in Call Quality Dashboard](dimensions-and-measures-available-in-call-quality-dashboard.md).

For background noise, check mute event ratio to see the length of time participants were muted.
 
Create detailed reports in CQD and filter on Meeting ID to look at all users and streams in a meeting and add the fields you are interested in. A user reporting the issue may not be the one that was having the issue. They are just reporting the experience.
 
The telemetry will not necessarily call out the issue, but it can help you better understand where to look and inform your decisions. Is it network, device, driver or firmware updates, usage, or user?

### Why do I see upto 0.2% difference in call and user count values on measures and how to get most accurate volumes? 
To compute call count and user count measures, a distinct countif operation is performed against the call or user identifiers in the data set. On large data sets, there is an up to 0.2% error inherent with the distinct countif operation. For the most accurate volume, you should rely on stream count measures since they do not rely on this distinct countif operation. Filtering to reduce the data volume may reduce the error but may not eliminate this source of error in distinct call and user counts. Refer to [Dimensions and measurements available in Call Quality Dashboard](dimensions-and-measures-available-in-call-quality-dashboard.md) for which measures are impacted.

### Why does my CQD v2 report data look different than the CQD v3 report data? 

If you see data differences between CQD v2 and v3, make sure that data comparison or validation is done on an 'apples-to-apples'  and narrow level, not an aggregated level. For example, if you filter both reports for MSIT 'Building 30' WiFi Teams Desktop client data, the Percentage of Poor Quality should be the same between v2 and v3.

CQDv2 classification for CallSetup failure is only considered for "Audio" modality, in CQDv3 this classification happens for every modality (Audio, Video and Appsharing) and is represented in the respective modality stream. 

For Teams, CQDv2 applies the same user feedback to all modalities CQDv3 applies feedback base on modality for Teams.

CQD V3 includes 
1. Skype for Business Server 2019 calls, 
2. Skype Bot calls, such as:auto attendant, call queue, conference announcement service, 
3. Virtual Desktop Interface,
4. Conference Video Interop,
3. Live Events Publisher and Presenter calls, and 
4. PSTN calls. 

To learn how to use these Power BI templates to analyze and report your CQD data, read [Use Power BI for CQD reports](cqd-power-bi-query-templates.md).


### Why is CQD data from Skype for Business different than CQD data from Teams? 

If you're trying to compare data between the older CQD from the Skype for Business legacy portal (cqd.lync.com) and the latest CQD from the Teams admin center (cqd.teams.microsoft.com), you'll quickly notice that the data doesn't match. That's because the latest CQD reports on many additional calling scenarios. If you're still using reports from the older CQD, use this article to help you interpret those reports: [Call Quality Dashboard for Skype for Business Server](https://docs.microsoft.com/skypeforbusiness/management-tools/call-quality-dashboard/call-quality-dashboard).
Here's an example of applying specific filters to compare CQD v2 and CQD v3 data:

1. QoE Record Available = True

2. Add Is Server Pair filter with value: Client:Client and Client:Server. Most tenants prefer to exclude Server:Server calls.

3. Add a filter for User Agent Category and filter out Auto Attendant, Call Queue, Bot, Room system, MediationServer, Conference Announcement service, VDI, etc.

:::image type="content" source="media/turning-on-and-using-call-quality-dashboard1.png" alt-text="Screenshot of applying specific filters in CQD v3":::

:::image type="content" source="media/turning-on-and-using-call-quality-dashboard2.png" alt-text="Screenshot of applying specific filters in CQD v2":::

### Other expected differences between CQD v2 and CQD v3

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
- Microsoft 365 Reports Reader
- Teams Communications Support Specialist

To learn more about roles that can access CQD - including EUII - read [Assign roles for accessing CQD](#assign-roles-for-accessing-cqd).

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

[Improve and monitor call quality for Teams](monitor-call-quality-qos.md)

[What is CQD?](CQD-what-is-call-quality-dashboard.md)

[Set up Call Quality Dashboard (CQD)](turning-on-and-using-call-quality-dashboard.md)

[Upload tenant and building data](CQD-upload-tenant-building-data.md)

[Use CQD to manage call and meeting quality](quality-of-experience-review-guide.md)

[Dimensions and measures available in CQD](dimensions-and-measures-available-in-call-quality-dashboard.md)

[Stream Classification in CQD](stream-classification-in-call-quality-dashboard.md)

[Use Power BI to analyze CQD data](CQD-Power-BI-query-templates.md)
