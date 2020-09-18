---
title: Required desktop client diagnostic data for Microsoft Teams
author: MicrosoftHeidi
ms.author: heidip
manager: serdars
ms.topic: reference
ms.service: msteams
audience: admin
ms.reviewer: majaisin
description: A list of desktop properties and events for the policy controls for Microsoft Teams.
localization_priority: Priority
search.appverid: MET150
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---
# Required desktop diagnostic data for Microsoft Teams

The following article contains a list of Microsoft Teams desktop events, and lists of properties each event collects.

## Events

> [!NOTE]
> There are common properties for all events listed below, to review them, see [Properties sent with all events](#properties-sent-with-all-events).

### Logging

> [!NOTE]
> For information on the properties of Logging events, see [Properties sent with logging events](#properties-sent-with-logging-events).

- **adal-anonymous-mac.ts:this.logger.logError** - Records that a generic sso error occurred when logging in anonymously on a Mac device.
- **adalAnonymousUtil.ts:loggingService.getInstance** - Records error statement logging that the app could not launch anonymous user authentication.
- **adal-anonymous-windows.ts:this.logger.logError** - Records that a generic sso error occurred when logging in anonymously on a windows device.
- **adalBase.ts:this.loggingService.logError** - Records information needed to determine that the user profile is null or empty.
- **adal-impl-mac.ts:this.loggingService.logError** - Records the occurrence of an issue when parsing telemetry received during authentication or genaric sso error occurred when logging in on a Mac device.
- **adal-rigel-windows.ts:this.logger.logError** - General logging statement indicating a generic sso error occurred when logging in on our Meeting room device.
- **adal-sso-windows.ts:this.loggingService.logError** - Records that a generic sso error occurred when logging in on a Windows device, errors in initiating the chat service or log in failure information.
- **appOnlineService.ts:loggingService.getInstance** - Records the occurrence of an error due to settings that could not be parsed during startup or with downloading pre-user authentication, pre-authorized settings.
- **appStart.ts:loggingService.logError** - Records the occurrence of an error when the application could not launch, disk space error, valid certificate error or failed to find the correct certificate, and restarting the app.
- **browserWindowHttp.ts:this.loggingService.logError** - Records information to indicate that the application could not be updated due to issues with the file system.
- **contextInstallService.ts:loggingService.getInstance** - Records the occurrence of an error when:
  - attempting to parse or read a file or resolve a URL critical to the contextual install feature.
  - the URL shortener attempts to run the contextual install feature.
- **crashManager.ts:loggingService.logError** - Records information to determine the cause of an error when the application crashes.
- **localStorageService.ts:loggingService.getInstance** - Records the occurrence of an error when essential boot data does not load properly to run the application.
- **logProviders\pageDumpProvider.ts:loggingService.getInstance** - Records error information when the application crashes.
- **multiWindowManager.ts:this.logError** - Records the occurrence of an error when essential boot data does not load properly to run the application.
- **nativeElectronNotifications\osNotificationService.ts:this.loggingService.logError** - This event records the occurrence of an error whenattempting to launch a notification about a failure.
- **OutlookMeetingAddinHelper.ts:loggingService.getInstance** - Records the occurrence of an error when attempting to connect to a meeting using the Outlook meeting addin.
- **recoveryManager.ts:loggingService.getInstance** - Records the occurrence of an error during update rollbacks.
- **renderer\startPage\startPage.ts:this.logger.logError** - Records the occurrence of an error with the application start page.
- **settingsService.ts:loggingService.getInstance** - Records the occurrence of an error with the application settings.
- **updateInfo.ts:loggingService.getInstance** - Records the occurrence of an error with transmitting updates.
- **updatenotification.js:this._loggingService.logError** - Records the occurrence of disk space issues.
- **utility.ts:loggingService.logError** - Records an error accessing a local file (a file in the application).
- **utility.ts:loggingService.getInstance** - Records an error in  available diskspace, display issues, url issues, cookie issues, protocols, or regkey issues on machine to load the application.
- **windowmanager.js:this._loggingService.logError** - Records the occurrence of cookie issues, whitescreen issues, issues between desktop and shell communication, url issues,errors with loading page messages, errors with process rendering, and network connectivity issues.
- **windowmanager.js:loggingService.getInstance** - Records information to indicate when the recovery window cannot br shown.

### Outlook addin

> [!NOTE]
> For information on the properties of Outlook addin events, see [Properties sent with Outlook addin events](#properties-sent-with-outlook-addin-events).

- **joinmeetingoperation** - Records information needed to join a user to a meeting.
- **meetingaddinapplifecycle** - Records information regarding app state such as Launch or Exit.
- **meetingaddinloadtime** - Records the time it takes to load meeting information from Outlook.
- **openmeetingoperation** - Records information needed to open a scheduled meeting.
- **savemeetingoperation** - Records information needed to save the meeting while scheduling it.

### Scenario

> [!NOTE]
> For information on the properties of Scenario events, see [Properties sent with scenario events](#properties-sent-with-scenario-events).

- **desktop_app_load** - Records information needed to determine that the desktop application has launched, that the service should be initialized, and that it is able to be initialized.
- **desktop_app_not_ready** - Records information needed to determine that the desktop application is not ready to function.
- **desktop_install** - Records information needed to determine that the desktop application has been installed successfully, or that it failed to install.
- **desktop_previous_lifecycle_invalid** - Records information needed to determine that the desktop application restarted after it had been previously been running and then crashed.

### Tracking

> [!NOTE]
> For information on the properties of Tracking events, see [Properties sent with tracking events](#properties-sent-with-tracking-events).

- **deeplink_scenario_missing** - Teams was launched from an deeplink, but the telemetry/diagnostic is not present.
- **desktop_app_initialized** - Records information needed to determine if the application has successfully started when the desktop application is initialized.
- **desktop_app_quit_exception** - The application crashed while attempting to close.
- **desktop_blankScreenDetected** - Records information needed to determine errors when the desktop application renders a blank screen.
- **desktop_blankScreenDetectedAfterRepaint** - Detected that page was blank upon detecting rendering attempt.
- **desktop_blankScreenRecoveredAfterRepaint** - Recovered from an rendering issue where the screen was not rendered earlier.
- **desktop_configuration_failed_to_save** - Collects information needed to determine configuration errors when desktop settings have failed to save.
- **desktop_navigation_error_recovery** - Collects information needed to determine desktop navigation errors when a page fails to load after five attempts.
- **desktop_previous_gpu_crashed** - Records information needed to determine graphics processing unit errors when the desktop crashes.
- **desktop_previous_plugin_host_crashed** - Collects information need to determine media stack issues associated with desktop application crashes.
- **desktop_recovery_cleared_user_data** - Records application crashed multiple times, and app had to clear local cache to recover.
- **desktop_settings_blank_on_load** - This is an error that the applications settings are not present.
- **desktop_settings_failed_to_load** - Collects information needed to determine cause when desktop settings fail to load.
- **desktop_silent_restart** - Client update is staged and client is updated without user disruption.
- **desktop_terminated** - Records information needed to determine whether the inter-process communication has been disconnected when the user closes the desktop application.
- **desktop_uncaught_exception** Function call on an undefined object, this will result in a crash/app restart.
- **desktop_write_storage_failed** - Records information needed to determine disk errors when the desktop application fails to write to storage.
- **registration_failed** - Records information needed to resolve add-in registration failures.
- **registration_success** - Records information needed to determine whether add-in registrations where successful.
- **security_unsupported_ipc_channel** - Interprocess message that was not permitted was inbound.
- **sfb_running_not_connected** - Detected that the Skype for Business app is not running.
- **sfb_not_running** - Records that the 'wait for response' from call to Skype of Business timed out.
- **sfb_never_replied** - Tracks no API response when communicating with Skype for Business.
- **server_error_hit** - Tracks that an error from the ipc pipes communicating with Skype for Business.
- **unexpected_sfb_ipc_disconnection** - Records information needed to determine a failure to connect to the service.
- **unregister_failed** - Records information needed to determine errors in de-registering the Outlook meeting add-in.

## UserBI panelaction

> [!NOTE]
> For information on the properties of UserBI panelaction events, see [Properties sent with UserBI panelaction events](#properties-sent-with-userbi-panelaction-events).

- **inlinereply** - Records information whether a user has replied from the notification.
- **toastclick** - Records a user's click to navigate to the message entry to toast notifications to monitor service SLA and to load the appropriate response to toast notification.
- **toastdismiss** - Records information needed to determine errors and delays when the user dismisses the rendering of a toast notification.

- **toast_skip** - Records information needed to avoid transmitting a delayed toast notification.
- **toasttimeout** - Records information needed to determine errors and delays when the rendering of a toast notification has timed out.

### UserBI panelview

> [!NOTE]
> For information on the properties of UserBI panelview events, see [Properties sent with UserBI panelview events](#properties-sent-with-userbi-panelview-events).

- **toastshow** - Records information needed to determine that a toast was rendered.

## Property lists

### Properties sent with all events

| Property name                              | Description                                                        |
|--------------------------------------------|--------------------------------------------------------------------|
| EventInfo_Time                             | Event generation time                                              |
| EventInfo_Name                             | Event name - Used to differentiate between event types             |
| EventInfo_BaseType/name                    | Event type - Used to differentiate between event types in an event |
| EventInfo_Sequence                         | Sequence of the event                                              |
| userAgent                                  | Browser agent string                                               |
| userpdclevel                               | Privacy data control setting of the user                           |
| eventpdclevel                              | Privacy data control categorization level of the event             |
| AppInfo_Language                           | App language                                                       |
| clientType/AppInfo_ClientType              | Client type where the app is running                               |
| environment/AppInfo_Environment            | Engineering environment that served the user request               |
| clientVersion/appversion/AppInfo_Version/desktopBuildVersion | Version of the app                               |
| buildtime                                  | timestamp that the app was built in engineering systems            |
| osversion/DeviceInfo_OsVersion             | OS version                                                         |
| AppInfo_ProcessArchitecture                | System architecture (32bit/64bit)                                  |
| preferredLocales                           | preferred locale for the user                                      |
| locale/AppInfo_Locale                      | App locale                                                         |
| os/DeviceInfo_OsName                       | OS Name                                                            |
| UserInfo_Language                          | Selected user language                                             |
| UserInfo_Id                                | User ID                                                            |
| UserInfo_TenantId/TenantId                 | Tenant ID                                                          |
| ring/UserInfo_Ring                         | Concept that helps deliver application in a phased manner          |
| region                                     | Datacenter region that served user's request                       |
| UserInfo_ConfigIds/UserInfo_Etag           | ID that helps identify users in different experiments/rollouts     |
| DeviceInfo_BrowserName                     | Browser name                                                       |
| DeviceInfo_BrowserVersion                  | Browser version                                                    |
| DeviceInfo_Id/machineId/DeviceInfo_IdV2    | ID that helps identify the device                                  |
| totalMemory                                | Hardware memory of the device                                      |
| cores                                      | Hardware cores of the device                                       |
| cpuspeed                                   | Hardware cpu speed of the device                                   |
| DeviceInfo_CpuArchitecture/cpuarchitecture | CPU architecture of the device                                     |
| UserRole                                   | Helps identify user role in a tenant                               |
| DeviceInfo_WindowsMode                     | Helps identify Windows security mode                               |
| desktopSession/Session_Id                  | Helps identify a session                                           |
| dbOpen                                     | Captures state of the local database                               |
| UserInfo_Upn                               | One sided hash of user identifier                                  |

### Properties sent with logging events

| Property name         | Description                                                        |
|-----------------------|--------------------------------------------------------------------|
| message               | Captures a detailed message about the log                          |

### Properties sent with scenario events

| Property Name                     | Description                                                                        |
|-----------------------------------|------------------------------------------------------------------------------------|
| Scenario_Status                   | Status of a scenario                                                               |
| Scenario_Step                     | Step in a scenario                                                                 |
| sequence                          | Sequence number of the scenario                                                    |
| delta                             | Time taken to complete different steps in a scenario                               |
| elapsed                           | Time since the scenario started                                                    |
| scenario                          | Uniquely identify a scenario                                                       |
| Scenario_Name                     | Name of the scenario                                                               |
| errorInfo                         | Info of the error that might have occurred during a scenario                       |
| session                           | Unique session ID                                                                  |
| freeMemory                        | Captures free memory available                                                     |
| processMemory                     | Captures process memory                                                            |
| scenarioDelta                     | Captures time different between 2 scenario steps                                   |
| Session_DesktopId                 | Unique session ID                                                                  |
| machineLocked                     | Captures if the machine was locked or not                                          |
| windowIsVisible                   | Captures if the app window was visible to use                                      |
| appStates/webAppStates            | records a list of app states that the app went through. This helps with crash investigation because we can see what state the app was in |
| crashDesktopSession               | Captures ID of the crashed session                                                 |
| appRuntime                        | Captures runtime of the app                                                        |
| diagnosticEvents                  | Last 50 web app diagnostic events before app crash                                 |
| activities                        | Last 50 user scenario names which happened before crash                            |
| crashSession                      | Captures ID of the crashed session                                                 |
| crashId                           | Captures ID of the crashed session                                                 |
| isPreviousLifecycleValid          | Whether previous app was fully initialized and terminated successfully             |
| isSettingValid                    | Whether preauth settings are valid                                                 |
| rollbackReason                    | Reason due to which app was rolled back                                            |
| deeplinkType                      | Type of the deeplink                                                               |
| watchdogCrash                     | Whether app crashed due to hang                                                    |
| protocols                         | Protocol used to launch the app                                                    |
| electronBuild                     | Build version of electron app                                                      |
| distribution                      |  whether Teams was installed via exe or msi or dmg or pkg, etc.                    |
| updateTimeOfDay                   | Time the app was updated                                                           |
| launchPath                        | whether Teams is installed in %LOCALAPPDATA%, %PROGRAMFILES%, or other locations   |
| loggedIn                          | If the user was logged in                                                          |
| envType/complianceEnvironmentType | Commercial cloud or private (e.g. DoD, GCC-High, etc.)                              |
| cpuusage                          | CPU usage                                                                          |
| installationSource                | Type of installation user has                                                      |
| adalVersion                       | Version of the auth library                                                        |
| asyncStart                        | Is the app using synchronous or asynchronous start                                 |
| attempts                          | Number of online check attempts made for the user before showing a blocking screen |

### Properties sent with tracking events

| Property name                      | Description                                                                      |
|------------------------------------|----------------------------------------------------------------------------------|
| name2                              | Captures name of the tracking event                                              |
| numVisibleNotifications            | Number of visible application notifications                                      |
| giphyEnabled                       | Whether giphy service was enabled                                                |
| error                              | Captures error details related to the tracking event                             |
| method                             | Protocol method GET or POST                                                      |
| channel                            | Captures inter-process communication channel within the app                      |
| windowTitle                        | Type of display window associated with event                                     |
| message                            | The type of error message                                                        |
| crashSession/crashDesktopSession/crashId/Session_DesktopId/Session_DesktopBackgroundId | Captures unique ID for session debug purposes |
| responseCode                       | Captures response code for the service call                                      |
| errorUrl                           | The URL that failed to load                                                      |
| errorCode                          | Captures error code                                                              |
| ssoEventData                       | Authentication state and status                                                  |
| correlationId                      | ID to correlate events with service side for debug purposes                      |
| errorDescription                   | Captures description of the errorcode                                            |
| source                             | Method to get the Teams app and what package type Teams was installed from       |
| windowIsDestroyed                  | True/False state of Application Windows during event                             |
| windowIsFocused                    | True/False state of Application Windows during event                             |
| windowIsVisible                    | Was the application visible when event happened                                  |
| windowIsMinimized                  | True/False state of Application Windows during event                             |
| windowIsMaximized                  | True/False state of Application Windows during event                             |
| windowIsFullscreen                 | True/False state of Application Windows during event                             |
| distSrc                            | Captures the distribution source of user landing into the app                    |
| retries                            | Retry count when attempting to connect to an endpoint                            |
| uses_slimcore                      | True or false if web call is using slimcore                                      |
| persistCookieExpiresIn             | Time remaining in validity of web application cookie                             |
| tenantName                         | Name of tenant for user of the application                                       |
| appStartReason                     | How the application session started such as user initiated, after updating, etc. |
| machineLocked                      | Whether machine was locked or not locked during the event                        |
| data                               | Captures technical data for scenario investigation                               |
| appRuntime                         | Captures runtime of the app                                                      |
| activities                         | Last 50 user scenario names which happened before crash                          |
| timeSinceActivity                  | Time since last user activity                                                    |
| appStates                          | Records a list of app states that the desktop app went through, which helps with crash investigations because it shows what state the desktop app was in |
| timeSinceAppState                  | Time since the app state changed                                                 |
| webAppStates                       | Records a list of app states that the web client went through, which helps with crash investigations because it shows what state the web client app was in |
| timeSinceWebAppState               | Time since the web app state changed                                             |
| diagnosticEvents                   | Last 50 web app diagnostic events before app crash                               |
| timeSinceLastDiagnosticEvent       | Time since last diagnostic event sent                                            |
| timeSinceSecondLastDiagnosticEvent | Time since second-last diagnostic event sent                                     |
| appInitialized                     | Whether webapplication has started                                               |
| targetVersion                      | Version application is going to be updated to                                    |
| port                               | Internet message port number                                                     |
| originalUrl                        | Original location of page being rendered                                         |
| deeplinkId                         | GUID for destination type of Teams link                                          |
| appSessionEnd                      | Whether event occurred at end of application session                             |
| eventData                          | Captures machine state and app config to help debugging in case of issues        |
| deeplinkType                       | Type of the deeplink (chat, meeting, channel)                                    |
| previousUpdateUrl                  | Location where application last retrieved its update from                        |
| previousUpdateVersion              | Last version application was updated to                                          |
| previousUpdateTime                 | When application binaries were last updated                                      |
| protocol                           | Handler type for link, such as file or image                                     |
| files                              | Type of file associated with an event, such as Application cache or GPU cache    |
| Perf_WorkingSetSizeKB              | Size of memory cache                                                             |
| isTimeboxingWebAppInitialize       | Whether app initialized before time box counter ran out                          |
| isExp                              | Whether the app version in use is part of an experiment                          |
| deviceType                         | Captures type of the device                                                      |
| sanitizedErr                       | Captures sanitized version of the error information                              |
| rigelVersion                       | Captures version of rigel device                                                 |
| DeviceInfo_OsSku                   | Captures OS SKU information                                                      |
| isLoggedOut                        | Captures if the user is logged out                                               |
| complianceEnvironmentType          | Commercial cloud or private (e.g. DoD, GCC-High, etc.)                           |
| restartTimes                       | Exact times of previous restarts                                                 |
| Skype_ResultCode                   | Captures result of interop communication between Skype and Teams                 |
| cpumodel                           | Captures model of CPU                                                            |
| isSlimCoreRunningOutproc           | Whether Slimcore component is running in its own process                         |
| isSlimCoreStartedAsync             | Type of launch of internal audio/video (A/V) stack                               |
| networkState                       | Captures state of the network                                                    |
| desktopBuildAge                    | How old the application build is at event time                                   |
| vdiMode                            | Captures if the app is running in VDI mode                                       |

### Properties sent with UserBI panelview events

| Property           | Description                                              |
|--------------------|----------------------------------------------------------|
| Panel_Uri          | Uri of the panel delivered to the user                   |
| Panel_Type         | Panel type accessed by the user                          |
| Team_Id            | ID of the team in which action was performed by the user |
| Thread_Id          | ID of the thread that was accessed by user               |
| Panel_PreviousUri  | URI of the previous panel                                |
| Panel_Region       | Region where the panel was hosted in the app             |
| Panel_LaunchMethod | Method through which the panel was launched              |
| Panel_PreviousType | Type of the previous panel                               |
| Thread_Type        | Type of thread accessed by user                          |
| Panel_LaunchSource | Source information of the panel that was launched        |
| Tab_Type           | Type of the tab accessed by user                         |
| Team_Type          | Type of team accessed by user                            |

### Properties sent with UserBI panelaction events

| Property name         | Description                                                        |
|-----------------------|--------------------------------------------------------------------|
| Action_DestinationUri | Uri of the resource being accessed by user action                  |
| Panel_Uri             | Uri of the panel delivered to the user                             |
| Action_Gesture        | Type of gesture performed by user on the app                       |
| Action_ScenarioType   | Feature grouping that relates to business metric for feature       |
| Panel_Type            | Panel type accessed by the user                                    |
| Action_Outcome        | Outcome of the action performed by user                            |
| Team_Id               | ID of the team in which action was performed by the user           |
| Module_Type           | Type of the module which hosted user action                        |
| Module_Name           | Name of the module which hosted user action                        |
| Module_Summary        | Summary of the module that hosed user action                       |
| Thread_Id             | ID of the thread that was accessed by user                         |
| Panel_PreviousUri     | URI of the previous panel                                          |
| Panel_Region          | Region where the panel was hosted in the app                       |
| Panel_LaunchMethod    | Method through which the panel was launched                        |
| Panel_PreviousType    | Type of the previous panel                                         |
| Thread_Type           | Type of thread accessed by user                                    |
| Module_State          | State of the module accessed by user                               |
| Action_Scenario       | Feature inside a group of features that relates to business metric |
| Panel_LaunchSource    | Source information of the panel that was launched                  |
| Tab_Type              | Type of the tab accessed by user                                   |
| Team_Type             | Type of team accessed by user                                      |

### Properties sent with Outlook addin events

| Property Name                   | Description                                                              |
|---------------------------------|--------------------------------------------------------------------------|
| AccountComparisonFailedReason   | Addin compares the account with Teams account to see if creation is allowed, this event is sent if the comparison fails |
| AccountComparisonSuccessful     | Addin compares the account with Teams account to see if creation is allowed, this event is sent if the comparison is successful |
| AdalVersion                     | Version of the authentication library used                               |
| AddinBitness                    | Version of addin                                                         |
| AddinLanguage                   | Language of addin strings being used                                     |
| AggregatorSetupCompletedTime    | Setup time for addin loader                                              |
| AppDomainCreatedTime            | Time when addin loader initializes app domain                            |
| AppointmentDisplayTime          | Time at which the appointment item was displayed during meeting creation |
| AuthenticationCompletedTime     | Time at which authentication was provided for a given request            |
| ConnectionMode                  | Indicates the connection mode of the user's primary Exchange account     |
| ConnectionStartedTime           | Time when Outlook calls OnConnection                                     |
| ErrorDetails                    | Captures details of the error                                            |
| ErrorName                       | Captures name of the error                                               |
| ExchangeVersion                 | Captures version of Exchange                                             |
| IsSmtpFormatError               | Error in SMTP address                                                    |
| IsTeamsRunning                  | Captures if there is a Teams process running                             |
| IsTeamsUserLoggedOut            | Captures if the user is logged out of Teams                              |
| LanguageSetupCompletedTime      | Time at which language setup got completed                               |
| ManagedConnectTime              | Time when the managed add-in received the connect callback               |
| ManagedOnStartupTime            | Time when managed started the startup                                    |
| MTFetchCompleted                | Time when MT meeting options request is completed                        |
| NetFrameworkVersion             | .nET framework used                                                      |
| NetworkAvailable                | Is network available                                                     |
| OperationStartTime              |  Time when different operations started                                  |
| OsBitness                       | Bitness of OS                                                            |
| OutlookLanguage                 | Captures language of the Outlook app                                     |
| OutlookVersion                  | Captures version of Outlook app                                          |
| OwnerResolutionTime             | Time to resolve the meeting owner                                        |
| ParseResponseCompletedTime      | Time when parsing of response completed                                  |
| RecipientResolutionError        | Error details when resolving a recipient                                 |
| RecipientsResolutionTime        | Total time to resolve all recipients                                     |
| RehydrateCompletedTime          | Time when properties are read from Outlook                               |
| SaveToOutlookCompletedTime      | Time when properties are saved to Outlook                                |
| ServiceRequestStartTime         | Start time of the service request                                        |
| ServiceResponseReceiveTime      | Time of response from the service                                        |
| SettingsInitializeCompletedTime | Time when settings initialized                                           |
| SetupLoggingCompletedTime       | Time when logging was set up                                             |
| ShutdownBeginTime               | Time when shutdown of addin begins                                       |
| ShutdownCompletedTime           | Time when shutdown completed                                             |
| StartupBeginTime                | Time when startup of addin begins                                        |
| StartupCompletedTime            | Time when startup completed                                              |
| TeamsDeployment                 | Deployment of Teams client (Dev, Prod)                                   |
| TeamsRing                       | Ring of current user logged into Teams client                            |
| TeamsVersion                    | Captures version of Teams app                                            |
| TelemetrySetupCompletedTime     | Time when telemetry setup is completed                                   |
| UpnMismatch                     | Whether theres a upn mismatch between outlook and teams                  |
| UserDomain                      | Domain of the user                                                       |
| ViewUpdatedTime                 | Time when the view got updated                                           |
