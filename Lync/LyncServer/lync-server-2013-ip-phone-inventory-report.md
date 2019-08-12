---
title: 'Lync Server 2013: IP Phone Inventory Report'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: IP Phone Inventory Report
ms:assetid: aa7d6b31-cb09-4e68-b020-aa5dd0081c20
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg615027(v=OCS.15)
ms:contentKeyID: 48185044
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# IP Phone Inventory Report in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-11-12_

The IP Phone Inventory Report reports information about the IP phones currently in use in your organization. The IP Inventory Report provides a detailed list of the IP phones that were actually used during the specified reporting period. Among other things, this report lets administrators know if there are any old, outdated phones still in use that should be replaced; it can also alert administrators to the fact that there are expensive phones in the organization that are rarely being used. That type of information can be invaluable when it comes time to purchase new phones or to redistribute existing phones. (For example, a user who rarely uses his or her expensive phone might be asked to swap phones with a user who uses his or her phone much more frequently.)

It should be noted that this report does have a few limitations when it comes to being used as a true inventory report. For one thing, the IP Phone Report simply lists all the phones that logged on to Lync Server during the specified time period, sorted by their last logon time. If a phone did not log on during the specified time period then it will not be listed in the inventory report. That includes phones that logged on before the time period started and were still logged on during the specified time interval. For example, suppose you wanted to look at all the phone inventory for July, 2012. Suppose, as well, that several phones logged on to Lync Server on June 30, 2012 and were still logged on as of July 1st. Those phones will not show up on the inventory report for July 1st.

It's also important to note that the inventory report could include phones that your organization no longer uses. For example, suppose a number of Fabrikam phones logged on to the system on July 1, 2012; 5 days later your organization got rid of all those Fabrikam phones and replaced them with a newer Contoso model. The Fabrikam phones will still appear on the "inventory" report simply because they logged on to the system during the month of July.

In addition, the IP Phone Inventory Report does not report summary totals for the different types of phones. For example, suppose you have 105 Polycom CX600 phones. The report will not tell you that you have 105 of these phones; instead, you will simply see 105 separate entries for the Polycom Cx600. The only way to know that there are 105 entries for the Polycom Cx600 would be to count each of those entries manually.

<div>


> [!WARNING]  
> Or, export the data and use Microsoft Excel or Windows PowerShell to do that counting for you.



</div>

<div>

## Accessing the IP Phone Inventory Report

The IP Phone Inventory Report is accessed from the Monitoring Reports home page. If you click the User URI metric you can access the User Activity Report for that user. Clicking the Last activity metric for a peer-to-peer call will take you to the Peer-to-Peer Session Detail Report; clicking that same metric for a conference will take you to the Conference Detail Report.

</div>

<div>

## Making the Best Use of the IP Phone Inventory Report

If you're only interested in usage information for one particular kind of phone (for example, "How often are users using a Polycom CX600 phone?") you can get that information directly from the IP Phone Inventory Report by filtering for that particular kind of phone. However, if you want summary information for all your phones (how many people are using a Polycom CX600, how many are using an LG-Nortel IP8540, etc.) then you will need to export the data and use another application (such as Windows PowerShell) to do that type of analysis. For example, suppose you export the data to a comma-separated values file (C:\\Data\\IP\_Phone\_Inventory\_Report.csv). In that case, you could use these two commands to provide summary data for all your phones:

    $phones = Import-Csv "C:\Data\IP_Phone_Inventory_Report.csv"
    $phones |Group-Object Manufacturer, "Hardware version" | Select-Object Count, Name | Sort-Object Count -Descending

That will return data similar to this:

    Count    Name
    -----    ----
      267    POLYCOM, CX700
      267    POLYCOM, CX600
      166    POLYCOM, C
       68    Microsoft, CPE
       64    LG-Nortel, IP8540
       59    Aastra, 6725ip
       37    LG-Nortel, IP
       22    POLYCOM, CX3000
       11    Microsoft, CPE_A
        9    POLYCOM, CX500
        7    Aastra, 6721ip

Similarly, these two commands tell you which phones logged on to the system but were never actually used to make a call (the value of the Last activity metric is blank, indicating that there hasn't been any last activity):

    $phones = Import-Csv "C:\Data\IP_Phone_Inventory_Report.csv"
    $phones | Where-Object {$_."Last activity" -eq ""}

That returns data similar to this for each phone that has not been used:

    Manufacturer     : POLYCOM
    Hardware version : CX600
    MAC address      : 00-04-F2-00-01-76
    User URI         : 422
    User agent       : CPE/4.0.7423.1 OCPhone/4.0.7423.1 (Microsoft Lync 2010 (Beta) Phone Edition)
    Last logon time  : 8/30/2010 4:44:48 PM
    Last logoff time : 8/30/2010 5:59:07 PM
    Last activity    :

Another interesting way to use the IP Phone Inventory Report is this: if you have the MAC address of an IP Phone you can find out the user who last used that phone simply by entering that address in the MAC address text box. The IP Phone Inventory report will then report back (among other things) the SIP address of the user who last logged on with that phone. Alternatively, you can enter a user SIP address (in the User URI prefix box) to find out all the phones that have been used by that user.

</div>

<div>

## Filters

Filters provide a way for you to return a more finely-targeted set of data or to view the returned data in different ways. For example, the IP Phone Inventory enables you to view only the phones manufactured by a specific company, or even a specific version of those phones. You can also choose how data should be grouped. In this case, registrations are grouped by hour, day, week, or month.

The following table lists the filters that you can use with the IP Phone Inventory Report.

### IP Phone Inventory Report Filters

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>From</strong></p></td>
<td><p>Start date/time for the time range. To view data by hours, enter both the start date and time as follows:</p>
<p>7/7/2012 1:00 PM</p>
<p>If you do not enter a start time, the report automatically begins at 12:00 AM on the specified day. To view data by day, enter just the date:</p>
<p>7/7/2012</p>
<p>To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):</p>
<p>7/3/2012</p>
<p>Weeks always run from Sunday through Saturday.</p></td>
</tr>
<tr class="even">
<td><p><strong>To</strong></p></td>
<td><p>End date/time for the time range. To view data by hours, enter both the end date and time as follows:</p>
<p>7/7/2012 1:00 PM</p>
<p>If you do not enter an end time, the report automatically ends at 12:00 AM on the specified day. To view data by day, enter just the date:</p>
<p>7/7/2012</p>
<p>To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):</p>
<p>7/3/2012</p>
<p>Weeks always run from Sunday through Saturday.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Manufacturer</strong></p></td>
<td><p>Name of the company that manufactured the IP phone. The values for this filter are automatically populated for you based on the IP phones that are currently in the database.</p></td>
</tr>
<tr class="even">
<td><p><strong>Hardware version</strong></p></td>
<td><p>Version number of the IP phone; by using the Manufacturer and the Hardware version filters you can uniquely identity a particular type of phone. The values for this filter are automatically populated for you based on the IP phones that are currently in the database.</p></td>
</tr>
<tr class="odd">
<td><p><strong>User agent</strong></p></td>
<td><p>Identifier for the software used by the IP phone. The values for this filter are automatically populated for you based on the IP phones currently in the database.</p></td>
</tr>
<tr class="even">
<td><p><strong>MAC address</strong></p></td>
<td><p>Unique identifier for the network interface on the IP phone. The Media Access Control (MAC) address is typically assigned at the time the phone is manufactured and is hard-wired into the device hardware.</p>
<p>To search for records pertaining to a specific MAC address simply enter that address. For example:</p>
<p>00-08-5D-16-16-48</p>
<p>You must enter the complete address. A partial address (for example 00-08-5D) does not return any data.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Last activity before days</strong></p></td>
<td><p>Select one of the following values:</p>
<ul>
<li><p>[All]</p></li>
<li><p>10</p></li>
<li><p>20</p></li>
<li><p>30</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>Last logoff time before days</strong></p></td>
<td><p>Select one of the following values:</p>
<ul>
<li><p>[All]</p></li>
<li><p>10</p></li>
<li><p>20</p></li>
<li><p>30</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><strong>User URI prefix</strong></p></td>
<td><p>SIP address of the user who used the IP phone.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Metrics

The following table lists the information provided in the IP Phone Inventory Report.

### IP Phone Inventory Report Metrics

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Can you sort on this item?</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Manufacturer</strong></p></td>
<td><p>Yes</p></td>
<td><p>Name of the company that manufactured the IP phone.</p></td>
</tr>
<tr class="even">
<td><p><strong>Hardware version</strong></p></td>
<td><p>Yes</p></td>
<td><p>Version number of the IP phone.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MAC address</strong></p></td>
<td><p>Yes</p></td>
<td><p>Unique identifier for the network interface on the IP phone. The MAC address is typically assigned at the time the phone is manufactured and is hard-wired into the device hardware.</p></td>
</tr>
<tr class="even">
<td><p><strong>User URI</strong></p></td>
<td><p>Yes</p></td>
<td><p>SIP address of the user who used the IP phone.</p></td>
</tr>
<tr class="odd">
<td><p><strong>User agent</strong></p></td>
<td><p>Yes</p></td>
<td><p>Identifier for the software used by the IP phone.</p></td>
</tr>
<tr class="even">
<td><p><strong>Last logon time</strong></p></td>
<td><p>Yes</p></td>
<td><p>Date and time that the IP phone last logged on to Lync Server.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Last logoff time</strong></p></td>
<td><p>Yes</p></td>
<td><p>Date and time that the IP phone last logged off from Lync Server.</p></td>
</tr>
<tr class="even">
<td><p><strong>Last activity</strong></p></td>
<td><p>Yes</p></td>
<td><p>Date and time that the IP phone was last used.</p></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

