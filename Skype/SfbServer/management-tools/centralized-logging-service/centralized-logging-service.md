---
title: "Centralized Logging Service in Skype for Business 2015"
ms.reviewer: 
ms.author: jambirk
author: jambirk
manager: serdars
ms.date: 2/1/2018
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: 975718a0-f3e3-404d-9453-6224e73bfdd0
description: "Summary: Learn about the service components and configuration settings for the Centralized Logging Service in Skype for Business Server 2015."
---

# Centralized Logging Service in Skype for Business 2015
 
**Summary:** Learn about the service components and configuration settings for the Centralized Logging Service in Skype for Business Server 2015.
  
The Centralized Logging Service can: 
  
- Start or stop logging on one or more computers and pools with a single command from a central location.
    
- Search logs on one or more computers and pools. You can tailor the search to return all logs on all machines, or return more concise results.
    
- Configure logging sessions as follows:
    
  - Define a **Scenario**, or use a default scenario. A scenario in Centralized Logging Service is made up of scope (global or site), a scenario name to identify the purpose of the scenario, and one or more providers. You can run the default scenario and one defined scenario at any given time on a computer.
    
  - Use an existing provider or create a new provider. Aprovider defines what the logging session collects, what level of detail, what components to trace, and what flags are applied.
    
    > [!TIP]
    >  If you are familiar with OCSLogger, the termproviders refers to the collection of **components** (for example, S4, SIPStack), a **logging type** (for example, WPP, EventLog, or IIS logfile), a **tracing level** (for example, All, verbose, debug), and **flags** (for example, TF_COMPONENT, TF_DIAG). These items are defined in the provider (a Windows PowerShell variable) and passed into the Centralized Logging Service command.
  
  - Configure logs for specific computers and pools.
    
  - Define the scope for the logging session from the options **Site** (to run logging captures on computers in that site only), or **Global** (to run logging captures on all computers in the deployment).
    
The Centralized Logging Service is a powerful troubleshooting tool for problems large or small, from root cause analysis to performance problems. All examples are shown using the Skype for Business Server Management Shell. Help is provided for the command-line tool through the tool itself, but there is a limited set of functions that you can execute from the command line. By using Skype for Business Server Management Shell, you have access to a much larger and much more configurable set of features, so that should always be your first choice. 
  
## Logging service components

 The Centralized Logging Service runs on all servers in your deployment, and is made up of the following agents and services:
  
- Centralized Logging Service Agent ClsAgent runs on every machine with Skype for Business Server deployed. It listens ( on ports **TCP 50001-50003**) for commands from ClsController over WCF and sends responses back to the controller. It manages log sessions (start/stop/update), and searches logs. It also performs housekeeping operations like log archiving and purges. 
    
- Centralized Logging Service Controller Cmdlets The Skype for Business Server Management Shell sends Start, Stop, Flush, and Search commands to the ClsAgent. When search commands are sent, the resulting logs are returned to the ClsControllerLib.dll and aggregated. The controller sends commands to the agent, receives the status of those commands and manages the search log file data as it is returned from all agents on any computer in the search scope, and aggregates the log data into a meaningful and ordered output set. The information in the following topics is focused on using the Skype for Business Server Management Shell.
    
**ClsController communications to ClsAgent**

![Relationship between CLSController and CLSAgent.](../../media/Ops_CLS_Architecture.jpg)
  
You issue commands using the Windows Server command-line interface or using the Skype for Business Server Management Shell. The commands are executed on the computer you are logged in to and sent to the ClsAgent locally or to the other computers and pools in your deployment.
  
ClsAgent maintains an index file of all .CACHE files that it has on the local machine. ClsAgent allocates them so that they are evenly distributed across volumes defined by the option CacheFileLocalFolders, never consuming more than 80% of each volume (that is, the local cache location and the percentage is configurable using the **Set-CsClsConfiguration** cmdlet). ClsAgent is also responsible for aging old cached event trace log (.etl) files off the local machine. After two weeks (that is, the timeframe is configurable using the **Set-CsClsConfiguration** cmdlet) these files are copied to a file share and deleted from the local computer. For details, see [Set-CsClsConfiguration](https://docs.microsoft.com/powershell/module/skype/set-csclsconfiguration?view=skype-ps). When a search request is received, the search criteria is used to select the set of cached .etl files to perform the search based on the values in the index maintained by the agent.
  
> [!NOTE]
> Files that are moved to the file share from the local computer can be searched by ClsAgent. Once ClsAgent moves the files to the file share, the aging and removal of files is not maintained by ClsAgent. You should define an administrative task to monitor the size of the files in the file share and delete them or archive them. 
  
The resulting log files can be read and analyzed using a variety of tools, including **Snooper.exe** and any tool that can read a text file, such as **Notepad.exe**. Snooper.exe is part of the Skype for Business Server 2015 Debug Tools and is available as a [Web download](https://go.microsoft.com/fwlink/p/?LinkId=285257).
  
Like OCSLogger, the Centralized Logging Service has several components to trace against, and provides options to select flags, such as TF_COMPONENT and TF_DIAG. Centralized Logging Service also retains the logging level options of OCSLogger.
  
The most important advantage to using the Skype for Business Server Management Shell over the command-line ClsController is that you can configure and define new scenarios using selected providers that target the problem space, custom flags, and logging levels. The scenarios available to ClsController are limited to those that are defined for the executable.
  
In previous versions, OCSLogger.exe was provided to enable administrators and support personnel to collect trace files from computers in the deployment. OCSLogger, for all of its strengths, had a shortcoming. You could only collect logs on one computer at a given time. You could log on to multiple computers by using separate copies of OCSLogger, but you ended up with multiple logs and no easy way to aggregate the results.
  
When a user requests a log search, the ClsController determines which machines to send the request to (that is, based on the scenarios selected). It also determines whether the search needs to be sent to the file share where the saved .etl files are located. When the search results are returned to the ClsController, the controller merges the results into a single time-ordered result set that is presented to the user. Users can save the search results to their local machine for further analysis.
  
When you start a logging session, you specify scenarios that are relative to the problem that you are trying to resolve. You can have two scenarios running at any time. One of these two scenarios should be the AlwaysOn scenario. As the name implies, it should always be running in your deployment, collecting information on all computers, pools, and components.
  
> [!IMPORTANT]
> By default, the AlwaysOn scenario is not running in your deployment. You must explicitly start the scenario. Once started, it will continue to run until explicitly stopped, and the running state will persist through reboots of the computers. For details on starting and stopping scenarios, see [Start or stop CLS log capture in Skype for Business Server 2015](start-or-stop-log-capture.md). 
  
When a problem occurs, start a second scenario that relates to the problem reported. Reproduce the problem, and stop the logging for the second scenario. Begin your log searches relative to the problem reported. The aggregated collection of logs produces a log file that contains trace messages from all computers in your site or global scope of your deployment. If the search returns more data than you can feasibly analyze (typically known as a signal-to-noise ratio, where the noise is too high), you run another search with narrower parameters. At this point, you can begin to notice patterns that show up and can help you get a clearer focus on the problem. Ultimately, after you perform a couple of refined searches you can find data that is relevant to the problem and figure out the root cause.
  
> [!TIP]
> When presented with a problem scenario in Skype for Business Server, start by asking yourself "What do I already know about the problem?" If you quantify the problem boundaries, you can eliminate a large part of the operational entities in Skype for Business Server. 
  
Consider an example scenario where you know that users are not getting current results when looking for a contact. There is no point in looking for problems in the media components, Enterprise Voice, conferencing, and a number of other components. What you may not know is where the problem actually is: on the client, or is this a server-side problem? Contacts are collected from Active Directory by the User Replicator and delivered to the client by way of the Address Book Server (ABServer). The ABServer gets its updates from the RTC database (where User Replicator wrote them) and collects them into address book files, by default - 1:30 AM. The Skype for Business Server clients retrieve the new address book on a randomized schedule. Because you know how the process works, you can reduce your search for the potential cause to an issue related to data being collected from Active Directory by the User Replicator, the ABServer not retrieving and creating the address book files, or the clients not downloading the address book file.
  
## Current configuration

The Centralized Logging Service is configured to define what the logging service is intended to collect, how it collects, where it will collect from, and what the log settings are. You define these settings globally (that is, for the entire deployment) or for a site (that is, a named site in your deployment). Any logging that you define will use the settings that are appropriate for the identity that you use for commands to start, stop, flush, and search logs.
  
### To display the current Centralized Logging Service configuration

1. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business 2015**, and then click **Skype for Business Server Management Shell**.
    
2. Type the following at a command-line prompt:
    
   ```
   Get-CsClsConfiguration
   ```

    > [!TIP]
    > You can narrow or expand the scope of the configuration settings that are returned by defining  `-Identity` and a scope, such as "Site:Redmond" to return only the CsClsConfiguration for the site Redmond. If you want details about a given portion of the configuration, you can pipe the output into another Windows PowerShell cmdlet. For example, to get details about the scenarios defined in the configuration for site "Redmond", type: `Get-CsClsConfiguration -Identity "site:Redmond" | Select-Object -ExpandProperty Scenarios`
  
     ![Sample output from Get-CsClsConfiguration.](../../media/Ops_Get-CsClsConfiguration_Basic.jpg)
  
    The result from the cmdlet displays the current configuration of the Centralized Logging Service.
    
|**Configuration Setting**|**Description**|
|:-----|:-----|
|**Identity** <br/> |Identifies the scope and name for this configuration. There is only one Global configuration, and one configuration per site.  <br/> |
|**Scenarios** <br/> |Listing of all scenarios that are defined for this configuration.  <br/> |
|**SearchTerms** <br/> |Defined search terms for the configuration. Office 365, not on-premises deployments.  <br/> |
|**SecurityGroups** <br/> |Defined security groups that control who (that is, members of the security groups) can see computers based on the site they are located in. Site, in this context, is the site as defined in Topology Builder.  <br/> |
|**Regions** <br/> |Defined regions are used to collect SecurityGroups into a region, for example EMEA.  <br/> |
|**EtlFileRolloverSizeMB** <br/> |The parameter indicates the maximum size of the log file before a new event trace log (.etl) file is created. A new log file is created when the defined size is reached even if the maximum time set in EtlFileRolloverMinutes has not yet been reached.  <br/> |
|**EtlFileRolloverMinutes** <br/> |Defined maximum amount of time, in minutes, that a log can elapse before a new .etl file is created. A new log file is created when the timer expires even if the maximum size set in EtlFileRolloverSizeMB has not yet been reached.  <br/> |
|**TmfFileSearchPath** <br/> |Location to search for the trace message format files.  <br/> |
|**CacheFileLocalFolders** <br/> |Defined path to the location where cache files are written on computers. CLSAgent writes the cache files and runs under the context of the Network Service. In this case, %TEMP% expands to %WINDIR%\ServiceProfiles\NetworkService\AppData\Local. By default, cache files and log files are written to the same directory.  <br/> |
|**CacheFileNetworkFolder** <br/> |You can define a universal naming convention (UNC) path to receive the cache files during logging operations.  <br/> |
|**CacheFileLocalRetentionPeriod** <br/> |Defined as the maximum time, in days, that cache files are retained.  <br/> |
|**CacheFileMaxDiskUsage** <br/> |Defined as the percentage of disk space that can be used by the cache files.  <br/> |
|**ComponentThrottleLimit** <br/> |Defined as the maximum number of traces per second that a component can produce before the automatic throttle limiter is triggered.  <br/> |
|**ComponentThrottleSample** <br/> |Number of times in 60 seconds that the ComponentThrottleLimit can be exceeded.  <br/> |
|**MinimumClsAgentServiceVersion** <br/> |The minimum version of the CLSAgent allowed to run. This element is intended for Office 365.  <br/> |
   

