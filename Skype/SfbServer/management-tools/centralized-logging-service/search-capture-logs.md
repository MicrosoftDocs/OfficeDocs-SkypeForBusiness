---
title: "Search capture logs created by the Centralized Logging Service in Skype for Business Server 2015"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 12/20/2018
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: 1b75b218-d84f-47a7-8a0a-b7e016b1cc79
description: "Summary: Learn how to search and read Centralized Logging Service capture logs in Skype for Business Server 2015."
---

# Search capture logs created by the Centralized Logging Service in Skype for Business Server 2015
 
**Summary:** Learn how to search and read Centralized Logging Service capture logs in Skype for Business Server 2015.
  
The search features in the Centralized Logging Service are useful and powerful for the following reasons: 
  
- Your searches and the results are run on a single computer, a pool, a site, or a global scope, based on the criteria you define.
    
- Your searches can be initially broad and then narrowed down to more targeted criteria such as time, component, or computer. You search against the same logs and don't need to run a logging session again when the search criteria changes.
    
- The results of your search are gathered from all computers and pools in the scope, collected and aggregated into a single output file that represents all results of the search criteria (limited to the scenarios that have been running and the data captured by the scenarios). You use familiar tools such as **Snooper** or **Notepad** to read the output file and the trace messages from across your deployment.
    
The CLSAgent on each individual computer creates the logs based on the scenario or scenarios (two scenarios per computer can be running at any given time). The logs and their associated index and cache files are managed by the CLSAgent. When you define and execute a search, the search command instructs the CLSAgent on what information should be retrieved. The CLSAgent executes the query against the log files, cache files, and index files and returns the results of the search to the CLSContoller. The CLSController receives the search results from all computers and pools in the scope of the search. The CLSController then aggregates (combines) the logs and puts them into time delta order, oldest entry first, and proceeding in time to the most recent entry last.
  
After each search, the **Sync-CsClsLogging** cmdlet is run and it flushes the cache used by searches (not to be confused with the cache files maintained by the CLSAgent). Flushing the cache helps to ensure that there is a clean log and trace file capture buffer at the CLSController for the next search operation.
  
To get the most benefit from the Centralized Logging Service, you need a good understanding of how to configure search to return only trace messages from the computer and pool logs that are relevant to the issue that you are researching. issues
  
To run the Centralized Logging Service search functions by using the Skype for Business Server Management Shell, you must be a member of either the CsAdministrator or the CsServerAdministrator role-based access control (RBAC) security groups, or a custom RBAC role that contains either of these two groups. To return a list of all the RBAC roles that this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Skype for Business Server Management Shell or the Windows PowerShell prompt:
  
```
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Skype for Business Server 2015 cmdlet"}
```

For example:
  
```
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsClsConfiguration"}
```

The remainder of this topic focuses on how to define a search to optimize your troubleshooting.
  
### To run a basic search by using the Centralized Logging Service

1. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business 2015**, and then click **Skype for Business Server Management Shell**.
    
2. Make sure that you have the AlwaysOn scenario running in your deployment at the global scope and then type the following at a command prompt:
    
   ```
   Search-CsClsLogging -OutputFilePath <string value of path and file to write the output file>
   ```

> [!NOTE]
> By default, Search-CsClsLogging sends the results of the search to the console. If you want to save the search results to a file, use -OutputFilePath  _\<string fully qualified file path\>_. To define the -OutputFilePath parameter, supply a path and a filename as part of the parameter in a string format enclosed in quotation marks (for example; C:\LogFiles\SearchOutput.txt). In this example, you must ensure that the directory C:\LogFiles exists and that you have permissions to Read and Write (NTFS permission Modify) files in the folder. The output is appended to and is not overwritten. If you need separate files, define a distinct file name for each search. 
  
For example:
    
  ```
  Search-CsClsLogging -OutputFilePath "C:\LogFiles\logfile.txt"
  ```

### To run a basic search on a pool or computer by using the Centralized Logging Service

1. To limit the search to a specific pool or computer, use the -Computers parameter with the computer defined by a computer fully qualified name, enclosed in quotation marks and separated by a comma as follows:
    
   ```
   Search-CsClsLogging -Computers <string value of computer names> -OutputFilePath <string value of path and file to write the output file>
   ```

For example:
    
  ```
  Search-CsClsLogging -Computers "fe01.contoso.net" -OutputFilePath "C:\LogFiles\logfile.txt"
  ```

2. To search more than one computer, type multiple computer names enclosed in quotation marks and separated by commas, such as the following:
    
   ```
   Search-CsClsLogging -Computers "fe01.contoso.net", "fe02.contoso.net", "fe03.contoso.net" -OutputFilePath "C:\LogFiles\logfile.txt"
   ```

3. If you need to search an entire pool instead of a single computer, change the -Computers parameter to -Pools, remove the computer name, and replace it with the pool or pools in quotation marks separated by commas.
    
    For example:
    
   ```
   Search-CsClsLogging -Pools "pool01.contoso.net" -OutputFilePath "C:\Logfiles\logfile.txt"
   ```

4. When using the search commands, pools can be any pool in your deployment, such as Front End pools, Edge pools, Persistent Chat Server pools, or others that are defined as a pool in your deployment.
    
    For example:
    
   ```
   Search-CsClsLogging -Pools "pool01.contoso.net", "pchatpool01.contoso.net", "intedgepool01.contoso.net" -OutputFilePath "C:\Logfiles\logfile.txt"
   ```

### To run a search by using time parameters

1. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business 2015**, and then click **Skype for Business Server Management Shell**.
    
2. By default, the beginning time for a search's time-specific parameters is 25 minutes prior to five minutes after the time you initiate the search. In other words, if we search at 4:00:00 PM, then the search start time will show as 3:35:00 PM to 4:05:00 PM. If you need to search 60 minutes or 3 hours prior to the current time, use the -StartTime parameter and set the date and time string to indicate the time you want the search to start. 
    
    For example, by using -StartTime and -EndTime to define a time and date range, you can define a search between 8 AM and 9 AM on 11/20/2012 on your pool. You can set the output path to write the results to a file named c:\logfile.txt as follows:
    
   ```
   Search-CsClsLogging -Pools "pool01.contoso.net" -StartTime "11/20/2012 08:00:00 AM" -EndTime "11/20/2012 09:00:00 AM" -OutputFilePath "C:\Logfiles\logfile.txt"
   ```

> [!NOTE]
> The time and date string that you specify can be "date time" or "time date. " The command will parse the string and use the appropriate values for date and time and your locale and culture settings on the machine you are running cmdlet from. 
  
3. If you want to retrieve logs beginning at 11:00:00 AM on 11/20/2012, you define the -StartTime. The default time range for the search is 30 minutes unless you define a specific -EndTime. The resulting search will return logs from the defined computer or pools from 11:00:00 AM to 11:30:00 AM.
    
For example:
    
  ```
  Search-CsClsLogging -Pools "pool01.contoso.net" -StartTime "11/20/2012 11:00:00 AM" -OutputFilePath "C:\Logfiles\logfile.txt"
  ```

4. To conduct a search of logs within a specific period of time, define a -StartTime and an -EndTime. You need logs from 1 PM to 2:45 PM on the computer edge01.contoso.net. 
    
For example:
    
  ```
  Search-CsClsLogging -Computers "edge01.contoso.net" -StartTime "11/20/2012 1:00:00 PM" -EndTime "11/20/2012 2:45:00 PM" -OutputFilePath "C:\Logfiles\logfile.txt"
  ```

### To run an advanced search by using other criteria and matching options

1. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business 2015**, and then click **Skype for Business Server Management Shell**.
    
2. To run a command to collect traces for specific components, type the following:
    
   ```
   Search-CsClsLogging -Components <components to search on> -OutputFilePath <fully qualified path to output logs>
   ```

For example:
    
  ```
  Search-CsClsLogging -Components "SIPStack","S4","UserServices" -OutputFilePath "C:\Logfiles\logfile.txt"
  ```

The resulting search returns all log entries that have trace components for SIPStack, S4, and UserServices on all computers and pools in your deployment for the past 30 minutes.
    
3. To limit the search with the same components to just your Front End pool named pool01.contoso.net, type:
    
   ```
   Search-CsClsLogging -Components "SIPStack","S4","UserServices" -OutputFilePath "C:\Logfiles\logfile.txt"
   ```

4. The default search logic for commands with multiple parameters is to use the logical OR with each of the defined parameters. You can change this behavior by specifying the **-MatchAll** parameter. To do this, type the following:
    
   ```
   Search-CsClsLogging -CallId "d0af828e49fa4dcb99f5f80223a634bc" -Components "SIPStack","S4","UserServices" -MatchAll -OutputFilePath "C:\Logfiles\logfile.txt"
   ```

5. If your scenarios are set to run constantly, such as AlwaysOn, or you have defined a long-running scenario logs may roll off of the local machine onto the file share. You define the file share by using the CacheFileNetworkFolder parameter by using New-CsClsConfiguration to create a new configuration or modifying an existing configuration with Set-CsClsConfiguration. If you do not want the search to include the file share in the collection of logs to search, use the SkipNetworkLogs parameter as follows:
    
   ```
   Search-CsClsLogging -Components "SIPStack","S4","UserServices" -StartTime "11/1/2012 00:00:01 AM" -EndTime "11/20/2012 2:45:00 PM" -SkipNetworkLogs -OutputFilePath "C:\Logfiles\logfile.txt"
   ```

## Read capture logs from the Centralized Logging Service

You realize the real benefit of the Centralized Logging Service after you run the search and you have a file that you can use to track down a reported problem. There are a number of ways that you can read the file. The output file is in a standard text format and you can use Notepad.exe or any other programs that will allow you to open and read a text file. For larger files and more complex issues, you could use a tool like Snooper.exe that is designed to read and parse the logging output from the Centralized Logging Service. Snooper is included with the Debug Tools that are available as a separate download. You can download the Debug Tools here: [https://go.microsoft.com/fwlink/?LinkId=285257](https://go.microsoft.com/fwlink/?LinkId=285257). When you install the Debug Tools, short cuts and menu items are not created. After you install the Debug Tools, open Windows Explorer, a command-line window, or Skype for Business Server Management Shell and go to the directory (default location) C:\Program Files\Skype for Business Server 2015\Debugging Tools. Double-click Snooper.exe or type Snooper.exe, and then press ENTER if you are using the command line or Skype for Business Server Management Shell.
  
> [!IMPORTANT]
> The intent of this topic is not to detail and discuss troubleshooting techniques. Troubleshooting and the processes around it is a complex subject. For details about troubleshooting basics and troubleshooting specific workloads, see the Microsoft Lync Server 2010 Resource Kit book at [https://go.microsoft.com/fwlink/p/?linkId=211003](https://go.microsoft.com/fwlink/p/?linkId=211003). The processes and procedures still apply to Skype for Business Server 2015. 
  
### To open a log file in Snooper

1. To use Snooper and open log files, you need read access to the log files. To use Snooper and access the log files you must be a member of the CsAdministrator or the CsServerAdministrator role-based access control (RBAC) security groups, or a custom RBAC role that contains either of these two groups. 
    
2. After the installation of the Debugging Tools (LyncDebugTools.msi), change directory to the location of Snooper.exe using Windows Explorer or from the command line. By default, the debugging tools are located in C:\Program Files\Skype for Business Server 2015\Debugging Tools. Double-click or run Snooper.exe.
    
3. After Snooper is open, right-click **File**, click **OpenFile**, find your log files, select a file in the **Open** dialog box, and then click **Open**.
    
4. The log file's **Trace** messages are displayed on the **Trace** tab. Click the **Messages** tab to view the message contents of the collected traces.
    
### To display a call flow diagram

1. To use Snooper and open log files, you need read access to the log files. To use Snooper and access the log files, you need to be a member of the CsAdministrator or the CsServerAdministrator role-based access control (RBAC) security groups, or a custom RBAC role that contains either of these two groups.
    
2. Open a log file and click the **Messages** tab, select a conversation in the messages view or select a trace component on the **Trace** tab.
    
3. Click **Call Flow**.
    
> [!NOTE]
> If you click on a message or trace that is not part of a call flow, the diagram will not appear and a status message appears at the bottom of Snooper stating "This message is not eligible for callfow". Choose another message or trace and the call flow will appear if the message or trace is part of a call flow. 
  
4. Move through the Messages or the Trace lines and note whether the call flow diagram updates or changes to display a new diagram.
    
5. Hover over elements to get information about call messages, endpoints, and other components.
