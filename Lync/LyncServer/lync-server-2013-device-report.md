---
title: 'Lync Server 2013: Device Report'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Device Report
ms:assetid: f42e4d60-699b-4870-8bb5-13b51bb6eb2b
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg615049(v=OCS.15)
ms:contentKeyID: 48185807
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Device Report in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-11-12_

The Device Report might be better titled the Microphone and Speakers Report; that's because the Device Report retrieves call-related metrics (such as poor call percentage, echo, and voice switch time) grouped by the microphones and speakers used in the call. If you are interested in IP phones (also commonly referred to as "devices"), use the [IP Phone Inventory Report in Lync Server 2013](lync-server-2013-ip-phone-inventory-report.md) instead.

The Device Report is extremely useful for administrators in determining if a specific type of device is experiencing high volumes of poor quality calls than others. In turn, this could influence any decisions you must make when it comes time to buy new devices or to replace existing devices.

By default, the information displayed in the Device Report is also based on the microphone (the capture device) and speakers/headset (the render device) used in the call. For example, suppose you have several users who use the following capture device and the following render device: By default, the information displayed in the Device Report is also based on the microphone (the capture device) and speakers/headset (the render device) used in the call. For example, suppose you have several users who use the following capture device and the following render device:

  - Capture device -- Microphone (SoundMAX Integrated Digital HD Audio)

  - Render device -- Headset Earphone (Microsoft LifeChat LX-3000)

If those users made a total of 254 calls you'll see an entry like this in the report:


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Capture device</th>
<th>Render device</th>
<th>Call volume</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Microphone (SoundMAX Integrated Digital HD Audio)</p></td>
<td><p>Headset Earphone (Microsoft LifeChat LX-3000)</p></td>
<td><p>254</p></td>
</tr>
</tbody>
</table>


Now, suppose you have a number of users who use that same capture device but a different render device. In that case, you'll have a second line entry in the report, one for that unique combination of capture device and render device:


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Capture device</th>
<th>Render device</th>
<th>Call volume</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Microphone (SoundMAX Integrated Digital HD Audio)</p></td>
<td><p>Headset Earphone (Microsoft LifeChat LX-3000)</p></td>
<td><p>254</p></td>
</tr>
<tr class="even">
<td><p>Microphone (SoundMAX Integrated Digital HD Audio)</p></td>
<td><p>Speakers (SoundMAX Integrated Digital HD Audio)</p></td>
<td><p>319</p></td>
</tr>
</tbody>
</table>


If you would rather see combined totals for a given device (for example, for the SoundMAX capture device, regardless of the render device used), select the appropriate option from the Device type dropdown list (either Capture device or Render device). If you select Capture device in this example, that will give you output similar to this:


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Capture device</th>
<th>Call volume</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Microphone (SoundMAX Integrated Digital HD Audio)</p></td>
<td><p>573</p></td>
</tr>
</tbody>
</table>


<div>

## Accessing the Device Report

The Device Report is typically accessed from the Monitoring Reports home page. However, if you are viewing the [Call Detail Report in Lync Server 2013](lync-server-2013-call-detail-report.md) you can drill down to the Device Report for a specific device by clicking either of the following metrics:

  - Capture Device

  - Render Device

From the Device Report you can drill down to the [Call List Report in Lync Server 2013](lync-server-2013-call-list-report.md) by clicking either of the following metrics:

  - Call volume

  - Poor call percentage

</div>

<div>

## Making the Best Use of the Device Report

When it comes to device names, the Device Report is extremely detailed; for example, suppose you have the following capture devices:

  - Aastra 3002 Microphone (2- Aastra 3002)

  - Aastra 3002 Microphone (3- Aastra 3002)

  - Aastra 3002 Microphone (Aastra 3002)

  - Aastra 6725ip

  - Aastra 6725ip Microphone (10- Aastra 6725ip)

  - Aastra 6725ip Microphone (10- Aastra 6725ip)-V0

  - Aastra 6725ip Microphone (2- Aastra 6725ip)

  - Aastra 6725ip Microphone (3- Aastra 6725ip)

  - Aastra 6725ip Microphone (4- Aastra 6725ip)

  - Aastra 6725ip Microphone (5- Aastra 6725ip)

  - Aastra 6725ip Microphone (6- Aastra 6725ip)

  - Aastra 6725ip Microphone (7- Aastra 6725ip)

  - Aastra 6725ip Microphone (9- Aastra 6725ip)

  - Aastra 6725ip Microphone (9- Aastra 6725ip)-V0

  - Aastra 6725ip Microphone (Aastra 6725ip)

  - Aastra 6725ip Microphone (Aastra 6725ip)-V0

  - Aastra 6725ip Microphone (USB Audio Device)

  - Aastra 6725ip Microphone (USB Audio Device)-V0

<div>


> [!NOTE]  
> Keep in mind that capture device names might not be the same if you are running localized versions of Lync Server 2013. A device named Aastra 6725ip Microphone (Aastra 6725ip)-V0 in US English could have a different name in French or Spanish.



</div>

Often times you'll want that level of detail; at other times, however, you might only be interested in how many calls use any Aastra microphone, regardless of model number. One way to get information like that is to export the Device Report data to Microsoft Excel and then save that data to a comma-separated values file (for example, C:\\Data\\Devices\_Report.csv). You can then use a set of commands similar to these to import the .CSV file into Windows PowerShell and report back the total number of calls made using an Aastra capture device:

    $devices = Import-Csv "C:\Data\Device_Report.csv
    $sum = $devices | Where-Object {$_."Capture device" -match "Aastra"}
    $sum | foreach-object {[Int]$x = [Int]$x + [Int]$_."call volume"}
    $x

That will return a single value representing the total number of calls made using an Aastra capture device. For example:

    384

</div>

<div>

## Filters

Filters provide a way for you to return a more finely-targeted set of data or to view the returned data in different ways. For example, the Device Report enables you to filter on such things as call type (that is, was the call a client call), a conference call, or a public switched telephone network (PSTN) call. You can also choose how data should be grouped. In this case, devices are grouped by hour, day, week, or month.

The following table lists the filters that you can use with the Device Report.

### Device Report Filters

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
<td><p><strong>Voice switch cause</strong></p></td>
<td><p>Reason why a call had to be placed into half duplex mode in order to prevent echo. In half duplex mode, communication can travel in only one direction at a time, similar to the way users take turns when communicating with a walkie-talkie. Select one of the following:</p>
<dl>
<dt><span></span></dt>
<dd><p>[All]</p>
</dd>
<dt><span></span></dt>
<dd><p>None</p>
</dd>
<dt><span></span></dt>
<dd><p>Bad timestamp</p>
</dd>
<dt><span></span></dt>
<dd><p>Echo</p>
</dd>
<dt><span></span></dt>
<dd><p>DNLP (dynamic nonlinear processor)</p>
</dd>
<dt><span></span></dt>
<dd><p>Low complexity</p>
</dd>
<dt><span></span></dt>
<dd><p>Bad device state</p>
</dd>
<dt><span></span></dt>
<dd><p>Post-AEC echo (acoustic echo cancellation)</p>
</dd>
</dl></td>
</tr>
<tr class="even">
<td><p><strong>Echo cause</strong></p></td>
<td><p>Reason why echo above the accepted level was detected in a call. (In telecommunications, echo is a reflection of sound, the same phenomenon you will hear if you yell down to the bottom of a well.) Select one of the following:</p>
<dl>
<dt><span></span></dt>
<dd><p>[All]</p>
</dd>
<dt><span></span></dt>
<dd><p>None</p>
</dd>
<dt><span></span></dt>
<dd><p>Bad timestamp</p>
</dd>
<dt><span></span></dt>
<dd><p>Post-AEC echo (acoustic echo cancellation)</p>
</dd>
<dt><span></span></dt>
<dd><p>ANLP (adaptive nonlinear processor)</p>
</dd>
<dt><span></span></dt>
<dd><p>DNLP (dynamic nonlinear processor)</p>
</dd>
<dt><span></span></dt>
<dd><p>Microphone clipping</p>
</dd>
</dl></td>
</tr>
<tr class="odd">
<td><p><strong>Call type</strong></p></td>
<td><p>Indicates the type of call that was made. Select one of the following:</p>
<dl>
<dt><span></span></dt>
<dd><p>[All]</p>
</dd>
<dt><span></span></dt>
<dd><p>Client call</p>
</dd>
<dt><span></span></dt>
<dd><p>PSTN call</p>
</dd>
<dt><span></span></dt>
<dd><p>Conference call</p>
</dd>
</dl></td>
</tr>
<tr class="even">
<td><p><strong>Access type</strong></p></td>
<td><p>Indicates whether the client was logged on to the internal network or the external network when the call was placed. Select one of the following:</p>
<dl>
<dt><span></span></dt>
<dd><p>[All]</p>
</dd>
<dt><span></span></dt>
<dd><p>Internal</p>
</dd>
<dt><span></span></dt>
<dd><p>External</p>
</dd>
</dl></td>
</tr>
<tr class="odd">
<td><p><strong>Network type</strong></p></td>
<td><p>Indicates the type of network the client was connected to when the call was placed. Select one of the following:</p>
<dl>
<dt><span></span></dt>
<dd><p>[All]</p>
</dd>
<dt><span></span></dt>
<dd><p>Wired</p>
</dd>
<dt><span></span></dt>
<dd><p>Wireless</p>
</dd>
</dl></td>
</tr>
<tr class="even">
<td><p><strong>VPN</strong></p></td>
<td><p>Indicates whether an external client was using a virtual private network (VPN) connection when the call was placed. Select one of the following:</p>
<dl>
<dt><span></span></dt>
<dd><p>[All]</p>
</dd>
<dt><span></span></dt>
<dd><p>VPN</p>
</dd>
<dt><span></span></dt>
<dd><p>Non-VPN</p>
</dd>
</dl></td>
</tr>
<tr class="odd">
<td><p><strong>Device type</strong></p></td>
<td><p>Indicates the type of device. Select one of the following:</p>
<dl>
<dt><span></span></dt>
<dd><p>Capture device</p>
</dd>
<dt><span></span></dt>
<dd><p>Render device</p>
</dd>
<dt><span></span></dt>
<dd><p>Capture/Render device pair</p>
</dd>
</dl></td>
</tr>
<tr class="even">
<td><p><strong>Device name</strong></p></td>
<td><p>Name of the capture or render device. You can enter the complete device name or any portion of the device name. For example, to find the device Microphone (Microsoft LifeCam VX-1000.), you can enter the complete device name as follows:</p>
<p>Microphone (Microsoft LifeCam VX-1000.)</p>
<p>Or, you can enter just a portion of the name. For example:</p>
<p>LifeCam</p>
<p>Note that the preceding filter returns any device that contains the string &quot;LifeCam&quot; anywhere in its name.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Metrics

The following table lists the information provided in the Device Report.

### Device Report Metrics

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
<td><p><strong>Capture device</strong></p></td>
<td><p>Yes</p></td>
<td><p>Device (for example, a microphone or webcam) used for transmitting audio.</p></td>
</tr>
<tr class="even">
<td><p><strong>Render device</strong></p></td>
<td><p>Yes</p></td>
<td><p>Device (for example, a headset or speakers) used for receiving audio.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Call volume</strong></p></td>
<td><p>Yes</p></td>
<td><p>Total number of calls placed.</p></td>
</tr>
<tr class="even">
<td><p><strong>Poor call percentage</strong></p></td>
<td><p>Yes</p></td>
<td><p>Percentage of calls that were classified as &quot;poor.&quot; A poor call is any call which at least one of the measured metrics exceeded the allowed value (for example, a call that experienced excessive jitter).</p></td>
</tr>
<tr class="odd">
<td><p><strong>Unique users</strong></p></td>
<td><p>Yes</p></td>
<td><p>Unique users who used the device. If a user used the device 13 times he or she would count as one unique user, the same as a user who only used the device a single time.</p></td>
</tr>
<tr class="even">
<td><p><strong>Ratio of voice switch time</strong></p></td>
<td><p>Yes</p></td>
<td><p>Percentage of the call that had to be conducted in half duplex mode in order to prevent echo. In half duplex mode, communication can travel in only one direction at a time, similar to the way users take turns when communicating with a walkie-talkie.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Ratio of microphone not functioning</strong></p></td>
<td><p>Yes</p></td>
<td><p>Percentage of the call in which the capture device was not functioning at an acceptable level. A high values suggests that quality issues with the call were primarily due to the capture device not working as expected.</p></td>
</tr>
<tr class="even">
<td><p><strong>Ratio of speaker not functioning</strong></p></td>
<td><p>Yes</p></td>
<td><p>Percentage of the call in which the render device was not functioning at an acceptable level. A high values suggests that quality issues with the call were primarily due to the render device not working as expected.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Calls with voice switch (%)</strong></p></td>
<td><p>Yes</p></td>
<td><p>Percentage of the total calls which had to be placed into half duplex mode. In half duplex mode, communication can travel in only one direction at a time, similar to the way users take turns when communicating with a walkie-talkie.</p></td>
</tr>
<tr class="even">
<td><p><strong>Echo microphone in (%)</strong></p></td>
<td><p>Yes</p></td>
<td><p>Percentage of time when echo was detected in the microphone capture stream. Typically, values are low for headsets or handsets, and higher for speaker phones or stand-alone speakers. For devices that support on-board acoustic echo cancellation, high values indicate echo leak. For other devices, this metric should not be used to evaluate device quality.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Echo send (%)</strong></p></td>
<td><p>Yes</p></td>
<td><p>Percentage of echo transmitted to other users.</p></td>
</tr>
<tr class="even">
<td><p><strong>Calls with echo (%)</strong></p></td>
<td><p>Yes</p></td>
<td><p>Percentage of the total calls that had echo exceeding the acceptable level.</p></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

