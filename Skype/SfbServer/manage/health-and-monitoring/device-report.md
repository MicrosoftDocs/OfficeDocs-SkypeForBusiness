---
title: "Device Report in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: f42e4d60-699b-4870-8bb5-13b51bb6eb2b
description: "Summary: Learn about the Device Report in Skype for Business Server."
---

# Device Report in Skype for Business Server
 
**Summary:** Learn about the Device Report in Skype for Business Server.
  
The Device Report might be better titled the Microphone and Speakers Report; that's because the Device Report retrieves call-related metrics (such as poor call percentage, echo, and voice switch time) grouped by the microphones and speakers used in the call. If you are interested in IP phones (also commonly referred to as "devices"), use the [IP Phone Inventory Report in Skype for Business Server](ip-phone-inventory-report.md) instead.
  
The Device Report is extremely useful for administrators in determining if a specific type of device is experiencing high volumes of poor quality calls than others. In turn, this could influence any decisions you must make when it comes time to buy new devices or to replace existing devices.
  
By default, the information displayed in the Device Report is also based on the microphone (the capture device) and speakers/headset (the render device) used in the call. For example, suppose you have several users who use the following capture device and the following render device: By default, the information displayed in the Device Report is also based on the microphone (the capture device) and speakers/headset (the render device) used in the call. For example, suppose you have several users who use the following capture device and the following render device:
  
- Capture device -- Microphone (SoundMAX Integrated Digital HD Audio)
    
- Render device -- Headset Earphone (Microsoft LifeChat LX-3000)
    
If those users made a total of 254 calls you'll see an entry like this in the report:
  
|**Capture device**|**Render device**|**Call volume**|
|:-----|:-----|:-----|
|Microphone (SoundMAX Integrated Digital HD Audio)  <br/> |Headset Earphone (Microsoft LifeChat LX-3000)  <br/> |254  <br/> |
   
Now, suppose you have a number of users who use that same capture device but a different render device. In that case, you'll have a second line entry in the report, one for that unique combination of capture device and render device:
  
|**Capture device**|**Render device**|**Call volume**|
|:-----|:-----|:-----|
|Microphone (SoundMAX Integrated Digital HD Audio)  <br/> |Headset Earphone (Microsoft LifeChat LX-3000)  <br/> |254  <br/> |
|Microphone (SoundMAX Integrated Digital HD Audio)  <br/> |Speakers (SoundMAX Integrated Digital HD Audio)  <br/> |319  <br/> |
   
If you would rather see combined totals for a given device (for example, for the SoundMAX capture device, regardless of the render device used), select the appropriate option from the Device type dropdown list (either Capture device or Render device). If you select Capture device in this example, that will give you output similar to this:
  
|**Capture device**|**Call volume**|
|:-----|:-----|
|Microphone (SoundMAX Integrated Digital HD Audio)  <br/> |573  <br/> |
   
## Accessing the Device Report

The Device Report is typically accessed from the Monitoring Reports home page. However, if you are viewing the [Call Detail Report in Skype for Business Server](call-detail-report.md) you can drill down to the Device Report for a specific device by clicking either of the following metrics:
  
- Capture Device
    
- Render Device
    
From the Device Report you can drill down to the [Call List Report in Skype for Business Server](call-list-report-0.md) by clicking either of the following metrics:
  
- Call volume
    
- Poor call percentage
    
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
    
> [!NOTE]
> Keep in mind that capture device names might not be the same if you are running localized versions of Skype for Business Server. A device named Aastra 6725ip Microphone (Aastra 6725ip)-V0 in US English could have a different name in French or Spanish. 
  
Often times you'll want that level of detail; at other times, however, you might only be interested in how many calls use any Aastra microphone, regardless of model number. One way to get information like that is to export the Device Report data to Microsoft Excel and then save that data to a comma-separated values file (for example, C:\Data\Devices_Report.csv). You can then use a set of commands similar to these to import the .CSV file into Windows PowerShell and report back the total number of calls made using an Aastra capture device:
  
```
$devices = Import-Csv "C:\Data\Device_Report.csv
$sum = $devices | Where-Object {$_."Capture device" -match "Aastra"}
$sum | foreach-object {[Int]$x = [Int]$x + [Int]$_."call volume"}
$x
```

That will return a single value representing the total number of calls made using an Aastra capture device. For example: 384

## Filters

Filters provide a way for you to return a more finely-targeted set of data or to view the returned data in different ways. For example, the Device Report enables you to filter on such things as call type (that is, was the call a client call), a conference call, or a public switched telephone network (PSTN) call. You can also choose how data should be grouped. In this case, devices are grouped by hour, day, week, or month.
  
The following table lists the filters that you can use with the Device Report.
  
**Device Report Filters**

|**Name**|**Description**|
|:-----|:-----|
|**From** <br/> |Start date/time for the time range. To view data by hours, enter both the start date and time as follows:  <br/> 7/7/2015 1:00 PM  <br/> If you do not enter a start time, the report automatically begins at 12:00 AM on the specified day. To view data by day, enter just the date:  <br/> 7/7/2015  <br/> To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):  <br/> 7/3/2015  <br/> Weeks always run from Sunday through Saturday.  <br/> |
|**To** <br/> |End date/time for the time range. To view data by hours, enter both the end date and time as follows:  <br/> 7/7/2015 1:00 PM  <br/> If you do not enter an end time, the report automatically ends at 12:00 AM on the specified day. To view data by day, enter just the date:  <br/> 7/7/2015  <br/> To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):  <br/> 7/3/2015  <br/> Weeks always run from Sunday through Saturday.  <br/> |
|**Voice switch cause** <br/> |Reason why a call had to be placed into half duplex mode in order to prevent echo. In half duplex mode, communication can travel in only one direction at a time, similar to the way users take turns when communicating with a walkie-talkie. Select one of the following:  <br/> [All] None Bad timestamp Echo DNLP (dynamic nonlinear processor) Low complexity Bad device state Post-AEC echo (acoustic echo cancellation) |
|**Echo cause** <br/> |Reason why echo above the accepted level was detected in a call. (In telecommunications, echo is a reflection of sound, the same phenomenon you will hear if you yell down to the bottom of a well.) Select one of the following:  <br/> [All] None Bad timestamp Post-AEC echo (acoustic echo cancellation) ANLP (adaptive nonlinear processor) DNLP (dynamic nonlinear processor) Microphone clipping |
|**Call type** <br/> |Indicates the type of call that was made. Select one of the following:  <br/> [All] Client call PSTN call Conference call |
|**Access type** <br/> |Indicates whether the client was logged on to the internal network or the external network when the call was placed. Select one of the following:  <br/> [All] Internal External |
|**Network type** <br/> |Indicates the type of network the client was connected to when the call was placed. Select one of the following:  <br/> [All] Wired Wireless |
|**VPN** <br/> |Indicates whether an external client was using a virtual private network (VPN) connection when the call was placed. Select one of the following:  <br/> [All] VPN Non-VPN |
|**Device type** <br/> |Indicates the type of device. Select one of the following:  <br/> Capture device Render device Capture/Render device pair |
|**Device name** <br/> |Name of the capture or render device. You can enter the complete device name or any portion of the device name. For example, to find the device Microphone (Microsoft LifeCam VX-1000.), you can enter the complete device name as follows:  <br/> Microphone (Microsoft LifeCam VX-1000.)  <br/> Or, you can enter just a portion of the name. For example:  <br/> LifeCam  <br/> Note that the preceding filter returns any device that contains the string "LifeCam" anywhere in its name.  <br/> |
   
## Metrics

The following table lists the information provided in the Device Report.
  
**Device Report Metrics**

|**Name**|**Can you sort on this item?**|**Description**|
|:-----|:-----|:-----|
|**Capture device** <br/> |Yes  <br/> |Device (for example, a microphone or webcam) used for transmitting audio.  <br/> |
|**Render device** <br/> |Yes  <br/> |Device (for example, a headset or speakers) used for receiving audio.  <br/> |
|**Call volume** <br/> |Yes  <br/> |Total number of calls placed.  <br/> |
|**Poor call percentage** <br/> |Yes  <br/> |Percentage of calls that were classified as "poor." A poor call is any call which at least one of the measured metrics exceeded the allowed value (for example, a call that experienced excessive jitter).  <br/> |
|**Unique users** <br/> |Yes  <br/> |Unique users who used the device. If a user used the device 13 times he or she would count as one unique user, the same as a user who only used the device a single time.  <br/> |
|**Ratio of voice switch time** <br/> |Yes  <br/> |Percentage of the call that had to be conducted in half duplex mode in order to prevent echo. In half duplex mode, communication can travel in only one direction at a time, similar to the way users take turns when communicating with a walkie-talkie.  <br/> |
|**Ratio of microphone not functioning** <br/> |Yes  <br/> |Percentage of the call in which the capture device was not functioning at an acceptable level. A high values suggests that quality issues with the call were primarily due to the capture device not working as expected.  <br/> |
|**Ratio of speaker not functioning** <br/> |Yes  <br/> |Percentage of the call in which the render device was not functioning at an acceptable level. A high values suggests that quality issues with the call were primarily due to the render device not working as expected.  <br/> |
|**Calls with voice switch (%)** <br/> |Yes  <br/> |Percentage of the total calls which had to be placed into half duplex mode. In half duplex mode, communication can travel in only one direction at a time, similar to the way users take turns when communicating with a walkie-talkie.  <br/> |
|**Echo microphone in (%)** <br/> |Yes  <br/> |Percentage of time when echo was detected in the microphone capture stream. Typically, values are low for headsets or handsets, and higher for speaker phones or stand-alone speakers. For devices that support on-board acoustic echo cancellation, high values indicate echo leak. For other devices, this metric should not be used to evaluate device quality.  <br/> |
|**Echo send (%)** <br/> |Yes  <br/> |Percentage of echo transmitted to other users.  <br/> |
|**Calls with echo (%)** <br/> |Yes  <br/> |Percentage of the total calls that had echo exceeding the acceptable level.  <br/> |
   

