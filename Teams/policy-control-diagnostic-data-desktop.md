---
title: Required desktop diagnostic data for Microsoft Teams
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

### PanelAction

> [!NOTE]
> For information on the properties of PanelAction events, see [Properties sent with panelaction events](#properties-sent-with-panelaction-events).


- **desktop_app_initialized+J11A2:J12A2A2:J10** - Records information needed to determine if the application has successfully started when the desktop application is initialized.
- **security_unsupported_ipc_channel** - ???
- **desktop_silent_restart** - ???
- **desktop_write_storage_failed** - Records information needed to determine disk errors when the desktop application fails to write to storage.
- **desktop_navigation_error_recovery** - Collects information needed to determine desktop navigation errors when a page fails to load after five attempts.
- **desktop_configuration_failed_to_save** - Collects information needed to determine configuration errors when desktop settings have failed to save.
- **desktop_settings_failed_to_load** - Collects information needed to determine cause when desktop settings fail to load.
- **desktop_uncaught_exception** - Collects information needed to determine desktop crashes.
- **desktop_previous_gpu_crashed** - Records information needed to determine graphics processing unit errors when the desktop crashes.
- **desktop_previous_plugin_host_crashed** - Collects information need to determine media stack issues associated with desktop application crashes.
- **desktop_blankScreenDetected** - Records information needed to determine errors when the desktop application renders a blank screen.
- **desktop_blankScreenDetectedAfterRepaint** - Records information needed to determine whether a blank screen is rendered after an application crashes.
- **desktop_app_quit_exception** - ???
- **desktop_recovery_cleared_user_data** - Records information needed to determine whether a blank screen is rendered after an application crashes.
- **desktop_blankScreenRecoveredAfterRepaint** - ???
- **deeplink_scenario_missing** - ???
- **desktop_settings_blank_on_load** - Records information needed to determine whether service settings and application policy settings have successfully loaded after ___. ???
- **desktop_terminated** - Records informations needed to determine whether the inter-process communication has been disconnected when the user closes the desktop application.
- **unexpected_sfb_ipc_disconnection** - Records information needed to determine a failure to connect to the service.
- **sfb_running_not_connected** - Records information needed to determine that the desktop application is not running.
- **sfb_not_running** - Records information needed to determine that a response expected from the desktop application has timed out.
- **sfb_never_replied** - Records information needed to determine that the application never connected to the service.
- **server_error_hit** - Records the existance of a server error.
- **registration_failed** - Records information needed to resolve add-in registration failures.
- **registration_success** - Records information needed to determine whether add-in registrations where sucessful.
- **unregister_failed** - Records information needed to determine errors in de-registering the Outlook meeting add-in.
- **desktop_app_load** - Records information needed to determine that the desktop application has launched and the service should be initialized. !!!
- **desktop_app_not_ready** - Records information needed to determine that the desktop application is not ready. !!!
- **desktop_install** - Records information needed to determine that the desktop application has been installed successfully. !!!
- **desktop_previous_lifecycle_invalid** - Records information needed to determine that the desktop application restarted after it had been previously been running and then crashed. !!!
- **toastshow** - Records information needed to determine that a toast was rendered. !!!
- **toasttimeout** - Records information needed to determine errors and delays when the rendering of a toast timeout.
- **toastdismiss** - Records information needed to determine errors and delays when the user dismisses the rendering of a toast notification.
- **toastclick** - Records a user's response to toast notifications to monitor service SLA and to load the appropriate response to toast notification.
- **inlinereply** - Records information needed to determine whether to send a toast notification to the user.
- **toastclick** - Records a user's response to toast notifications to monitor service SLA and to load the appropriate response to toast notification.
- **toast_skip** - Records information needed to avoid transmitting a delayed toast notification.
- **toastdismiss** - Records information needed to determine errors and delays when the user dismisses the rendering of a toast notification.
- **toasttimeout** - Records information needed to determine errors and delays when the rendering of a toast notification has timed out.
- **toastshow** - Records information needed to determine that a toast notification was rendered. !!!
- **inlinereply** - Records information needed to determine whether to send a toast notification to the user.
- **openmeetingoperation** - Records information needed to open a scheduled meeting.
- **savemeetingoperation** - Records information needed to save the meeting while scheduling it.
- **joinmeetingoperation** - Records information needed to join a user to a meeting.
- **meetingaddinapplifecycle** - Records information regarding app state, such as launch or exit.
- **meetingaddinloadtime** - Records the time it takes to load meeting information from Outlook.
- **adal-anonymous-mac.ts:47:this.logger.logError** - Records that a generic sso error occurred when logging in anonymously on a Mac device.
- **adal-anonymous-windows.ts:61:this.logger.logError** - Records that a generic sso error occurred when logging in anonymously on a windows device.
- **adal-impl-mac.ts:56:this.loggingService.logError** - Records the occurrence of an issue when parsing telemetry received during authentication.
- **adal-impl-mac.ts:164:this.loggingService.logError** - Records that a generic sso error occurred when logging in on a Mac device.
- **adal-rigel-windows.ts:85:this.logger.logError** - ???
- **adal-sso-windows.ts:358:this.loggingService.logError** - Records that a generic sso error occurred when logging in on a Windows device.
- **adal-sso-windows.ts:800:this.loggingService.logError** - Records login failure information.
- **adal-sso-windows.ts:951:this.loggingService.logError** - Records errors in initiating the chat service.
- **adalAnonymousUtil.ts:55:loggingService.getInstance** - ???
- **adalAnonymousUtil.ts:58:loggingService.getInstance** - ???
- **adalBase.ts:898:this.loggingService.logError** - Records information needed to determine that the user profile is null or empty.
- **appOnlineService.ts:68:loggingService.getInstance** - Records the occurrence of an error with downloading preauthorized settings.
- **appOnlineService.ts:73:loggingService.getInstance** - Records the occurrence of an error with downloading preauthorized settings.
- **appOnlineService.ts:138:loggingService.getInstance** - Records the occurrence of an error due to settings that could not be parsed during startup.
- **appOnlineService.ts:191:loggingService.getInstance** - Records the occurrence of an error due to settings that could not be parsed during startup.
- **appStart.ts:344:loggingService.logError** - Records the occurrence of an error when the application could not launce due to disk space issues.
- **appStart.ts:1701:loggingService.logError** - Records the occurrence of an error when an application with a valid certificate fails to launch.
- **appStart.ts:1731:loggingService.logError** - Records when the application restarts upon initial launch due to failure to find the correct certificate.
- **browserWindowHttp.ts:46:this.loggingService.logError** - Records information to indicate that the application could not be updated due to issues with the file system.
- **contextInstallService.ts:227:loggingService.getInstanceA67:D67** - Records the occurrence of an error when attempting to parse a file critical to the contextual install feature.
- **contextInstallService.ts:359:loggingService.getInstance** - Records the occurrence of an error when attempting to read or resolve a URL critical to the contextual install feature.
- **contextInstallService.ts:507:loggingService.getInstance** - Records the occurrence of an error when the URL shortener attempts to run the contextual install feature.
- **contextInstallService.ts:514:loggingService.getInstance** - Records the occurrence of an error during the contextual install feature.
- **contextInstallService.ts:517:loggingService.getInstance** - Records the occurrence of an error when the URL shortener attempts to run the contextual install feature.
- **contextInstallService.ts:524:loggingService.getInstance** - Records the occurrence of an error when the URL shortener attempts to run the contextual install feature.
- **contextInstallService.ts:541:loggingService.getInstance** - Records the occurrence of an error when the URL shortener attempts to run the contextual install feature.
- **contextInstallService.ts:542:lo+A3ggingService.getInstance** - Records the occurrence of an error during the contextual install feature.
- **contextInstallService.ts:616:loggingService.getInstance** - Records the occurrence of an error during the contextual install feature.
- **contextInstallService.ts:660:loggingService.getInstance** - Records the occurrence of an error during the contextual install feature.
- **crashManager.ts:80:loggingService.logError** - Records information to determine the cause of an error when the application crashes.
- **crashManager.ts:139:loggingService.logError** - Records information to determine the cause of an error when the application crashes.
- **crashManager.ts:359:loggingService.logError** - Records information to determine the cause of an error when the application crashes.
- **localStorageService.ts:46:loggingService.getInstance** - Records the occurrence of an error when essential boot data does not load properly to run the application.
- **localStorageService.ts:48:loggingService.getInstance** - Records the occurrence of an error when essential boot data does not load properly to run the application.
- **localStorageService.ts:124:loggingService.getInstance** - Records the occurrence of an error when essential boot data does not load properly to run the application.
- **localStorageService.ts:146:loggingService.getInstance** - Records the occurrence of an error when essential boot data does not load properly to run the application.
- **logProviders\pageDumpProvider.ts:30:loggingService.getInstance** - Records error information when the application crashes.
- **multiWindowManager.ts:282:this.logError** - Records the occurrence of an error when the application fails to run multiple windows.
- **multiWindowManager.ts:310:this.logError** - Records the occurrence of an error when the application fails to run multiple windows.
- **multiWindowManager.ts:353:this.logError** - Records the occurrence of an error when the application fails to run multiple windows.
- **multiWindowManager.ts:356:this.logError** - Records the occurrence of an error when the application fails to run multiple windows.
- **multiWindowManager.ts:359:this.logError** - Records the occurrence of an error when the application fails to run multiple windows.
- **multiWindowManager.ts:394:this.logError** - Records the occurrence of an error when the application fails to run multiple windows.
- **multiWindowManager.ts:415:private logError** - Records the occurrence of an error when the application fails to run multiple windows.
- **multiWindowManager.ts:426:this.logger.logError** - Records the occurrence of an error when the application fails to run multiple windows.
- **multiWindowManager.ts:553:this.logError** - Records the occurrence of an error when the application fails to run multiple windows.
- **multiWindowManager.ts:575:this.logError** - Records the occurrence of an error when the application fails to run multiple windows.
- **multiWindowManager.ts:639:this.logError** - Records the occurrence of an error when the application fails to run multiple windows.
- **multiWindowManager.ts:665:this.logError** - Records the occurrence of an error when the application fails to run multiple windows.
- **multiWindowManager.ts:667:this.logError** - Records the occurrence of an error when the application fails to run multiple windows.
- **multiWindowManager.ts:695:this.logError** - Records the occurrence of an error when the application fails to run multiple windows.
- **multiWindowManager.ts:707:this.logError** - Records the occurrence of an error when the application fails to run multiple windows.
- **multiWindowManager.ts:710:this.logError** - Records the occurrence of an error when the application fails to run multiple windows.
- **multiWindowManager.ts:741:this.logError** - Records the occurrence of an error when the application fails to run multiple windows.
- **multiWindowManager.ts:744:this.logError** - Records the occurrence of an error when the application fails to run multiple windows.
- **multiWindowManager.ts:771:this.logError** - Records the occurrence of an error when the application fails to run multiple windows.
- **nativeElectronNotifications\osNotificationService.ts:282:self.loggingService.logError** - Records the occurrence of an error when attempting to launch a notification about a failure.
- **nativeElectronNotifications\osNotificationService.ts:378:this.loggingService.logError** - Records the occurrence of an error when attempting to launch a notification about a failure.
- **OutlookMeetingAddinHelper.ts:100:loggingService.getInstance** - Records the occurrence of an error when attempting to connect to a meeting using the Outlook meeting addin.
- **OutlookMeetingAddinHelper.ts:111:loggingService.getInstance** - Records the occurrence of an error when attempting to connect to a meeting using the Outlook meeting addin.
- **OutlookMeetingAddinHelper.ts:202:loggingService.getInstance** - Records the occurrence of an error when attempting to connect to a meeting using the Outlook meeting addin.
- **OutlookMeetingAddinHelper.ts:227:loggingService.getInstance** - Records the occurrence of an error when attempting to connect to a meeting using the Outlook meeting addin.
- **OutlookMeetingAddinHelper.ts:256:loggingService.getInstance** - Records the occurrence of an error when attempting to connect to a meeting using the Outlook meeting addin.
- **recoveryManager.ts:86:loggingService.getInstance** - Records the occurrence of an error during update rollbacks.
- **recoveryManager.ts:108:loggingService.getInstance** - Records the occurrence of an error during update rollbacks.
- **recoveryManager.ts:155:loggingService.getInstance** - Records the occurrence of an error during update rollbacks.
- **renderer\startPage\startPage.ts:23:this.logger.logError** - Records the occurrence of an error with the application start page.
- **renderer\startPage\startPage.ts:50:this.logger.logError** - Records the occurrence of an error with the application start page.
- **renderer\startPage\startPage.ts:69:this.logger.logError** - Records the occurrence of an error with the application start page.
- **renderer\startPage\startPage.ts:80:this.logger.logError** - Records the occurrence of an error with the application start page.
- **renderer\startPage\startPage.ts:125:this.logger.logError** - Records the occurrence of an error with the application start page.                                                                                  |
- **settingsService.ts:132:loggingService.getInstance** - Records the occurrence of an error with the application settings.
- **settingsService.ts:490:loggingService.getInstance** - Records the occurrence of an error with the application settings.
- **settingsService.ts:691:loggingService.getInstance** - Records the occurrence of an error when attempting to save application settings.
- **updateInfo.ts:42:loggingService.getInstance** - Records the occurrence of an error with transmitting updates.
- **updateInfo.ts:62:loggingService.getInstance** - Records the occurrence of an error with transmitting updates.
- **updatenotification.js:267:this._loggingService.logError - Records the occurrence of disk space issues.
- **updatePolicyManager.ts:319:loggingService.getInstance** - Records the occurrence of errors with scheduled updates.
- **updatePolicyManager.ts:324:loggingService.getInstance** - Records the occurrence of errors with scheduled updates.
- **updatePolicyManager.ts:329:loggingService.getInstance** - Records the occurrence of errors with scheduled updates.
- **utility.ts:231:loggingService.logError** - ???
- **utility.ts:264:loggingService.logError** - ???
- **utility.ts:418:loggingService.getInstance** - Records the occurrence of insufficient disk space to load the application.
- **utility.ts:583:loggingService.getInstance** - Records the occurrence of display issues.
- **utility.ts:930:loggingService.getInstance** - Records the occurrence of protocol issues.
- **utility.ts:933:loggingService.getInstance** - Records the occurrence of url issues.
- **utility.ts:1009:loggingService.getInstance** - Records the occurrence of protocol issues.
- **utility.ts:1012:loggingService.getInstance** - Records the occurrence of url issues.
- **utility.ts:1119:loggingService.getInstance** - ???
- **utility.ts:1356:loggingService.getInstance** - Records the occurrence of url issues.
- **utility.ts:1382:loggingService.getInstance** - Records the occurrence of url issues.
- **utility.ts:1471:loggingService.getInstance** - Records the occurrence of cookie issues.
- **utility.ts:1515:loggingService.getInstance** - Records the occurrence of cookie issues.
- **utility.ts:1524:loggingService.getInstance** - Records the occurrence of cookie issues.
- **utility.ts:1553:loggingService.getInstance** - Records the occurrence of cookie issues.
- **utility.ts:1566:loggingService.getInstance** - Records the occurrence of cookie issues.
- **utility.ts:1588:loggingService.getInstance** - Records the occurrence of cookie issues.
- **utility.ts:1637:loggingService.getInstance** - Records the occurrence of regkey issues.
- **utility.ts:1647:loggingService.getInstance** - ???
- **utility.ts:1682:loggingService.getInstance** - Records the occurrence of regkey issues.
- **utility.ts:1726:loggingService.getInstance** - ???
- **windowmanager.js:306:this._loggingService.logError** - Records the occurrence of cookie issues.
- **windowmanager.js:311:this._loggingService.logError** - Records the occurrence of cookie issues.
- **windowmanager.js:338:this._loggingService.logError** - Records the occurrence of whitescreen issues.
- **windowmanager.js:551:this._loggingService.logError** - Records the occurrence of shell communication issues.
- **windowmanager.js:568:this._loggingService.logError** - Records the occurrence of errors with rendering multiple windows.
- **windowmanager.js:607:this._loggingService.logError** - Records the occurrence of shell communication issues.
- **windowmanager.js:1333:this._loggingService.logError** - Records the occurrence of url issues.
- **windowmanager.js:1337:this._loggingService.logError** - Records the occurrence of url issues.
- **windowmanager.js:1645:this._loggingService.logError** - Records the occurrence of errors with loading page messages.
- **windowmanager.js:2124:this._loggingService.logError** - Records the occurrence of process rendering issues.
- **windowmanager.js:2176:this._loggingService.logError** - Records the occurrence of network connectivity issues.
- **windowmanager.js:2354:loggingService.getInstance** - Records information to indicate when the recovery window cannot be shown.

### Logging

- **adal-anonymous-mac.ts:47:this.logger.logError** - A general logging statement indicating a generic sso error occurred when logging in anonymously on a Mac.
- **adal-anonymous-windows.ts:61:this.logger.logError** - A general logging statement indicating a generic sso error occurred when logging in anonymously on Windows.
- **adal-impl-mac.ts:56:this.loggingService.logError** - A statement indicating an issue occurred when parsing some telemetry returned from the authentication service.
- **adal-impl-mac.ts:164:this.loggingService.logError** - A general logging statement indicating a generic sso error occurred when logging in on a Mac.
- **adal-rigel-windows.ts:85:this.logger.logError** - A general logging statement indicating a generic sso error occurred when logging in on our Rigel machines. ???
- **adal-sso-windows.ts:358:this.loggingService.logError** - A general logging statement indicating a generic single sign-on (SSO) error occurred when logging in on Windows.
- **adal-sso-windows.ts:800:this.loggingService.logError** - A statement describing why the user failed to log in through the authentication service.
- **adal-sso-windows.ts:951:this.loggingService.logError** - An issue fetching the chat service aggregator resource, which is an optional resource.
- **adalAnonymousUtil.ts:55:LoggingService.getInstance** - An error statement logging that the app could not launch in the anonymous authentication context.
- **adalAnonymousUtil.ts:58:LoggingService.getInstance** - An error statement logging that the app could not launch in the anonymous authentication context.
- **adalBase.ts:898:this.loggingService.logError** - An error statement describing that the user profile is null or empty.
- **appOnlineService.ts:68:LoggingService.getInstance** - An error occurred attempting to download our preauth settings in the background.
- **appOnlineService.ts:73:LoggingService.getInstance** - An error occurred attempting to download our preauth settings in the background.
- **appOnlineService.ts:138:LoggingService.getInstance** - An error statement that occurs when some settings could not be parsed on startup.
- **appOnlineService.ts:191:LoggingService.getInstance** - An error statement that occurs when some settings could not be parsed on startup.
- **appStart.ts:344:loggingService.logError** - Message describing that the app could not launch due to disk space issues.
- **appStart.ts:1701:loggingService.logError** - Failed to launch the app with a valid certificate on the machine.
- **appStart.ts:1731:loggingService.logError** - Failed to find the correct certificate, and restarting the app.
- **browserWindowHttp.ts:46:this.loggingService.logError** - Information describing that the app could not be updated due to an issue with the file system.
- **contextInstallService.ts:227:loggingService.getInstance** - An error attempting to parse a file critical to the contextual install feature.
- **contextInstallService.ts:359:loggingService.getInstance** - An error attempting to read or resolve a url critical to the contextual install feature.
- **contextInstallService.ts:507:loggingService.getInstance** - An error from the Url Shortener, a partner service, attempting to run the contextual install feature.
- **contextInstallService.ts:514:loggingService.getInstance** - An error during the contextual install feature.
- **contextInstallService.ts:517:loggingService.getInstance** - An error from the Url Shortener, a partner service, attempting to run the contextual install feature.
- **contextInstallService.ts:524:loggingService.getInstance** - An error from the Url Shortener, a partner service, attempting to run the contextual install feature.
- **contextInstallService.ts:541:loggingService.getInstance** - An error from the Url Shortener, a partner service, attempting to run the contextual install feature.
- **contextInstallService.ts:542:loggingService.getInstance** - An error occurred during the contextual install feature.
- **contextInstallService.ts:616:loggingService.getInstance** - An error occurred during the contextual install feature.
- **contextInstallService.ts:660:loggingService.getInstance** - An error occurred during the contextual install feature.
- **crashManager.ts:80:loggingService.logError** - Error information about the crash diagnostics in the app.
- **crashManager.ts:139:loggingService.logError** - Error information about the crash diagnostics in the app.
- **crashManager.ts:359:loggingService.logError** - Error information about the crash diagnostics in the app.
- **localStorageService.ts:46:LoggingService.getInstance** - An error occurred loading up essential app boot data, necessary for properly running the app.
- **localStorageService.ts:48:LoggingService.getInstance** - An error occurred loading up essential app boot data, necessary for properly running the app.
- **localStorageService.ts:124:LoggingService.getInstance** - An error occurred loading up essential app boot data, necessary for properly running the app.
- **localStorageService.ts:146:LoggingService.getInstance** - An error occurred loading up essential app boot data, necessary for properly running the app.
- **logProviders\pageDumpProvider.ts:30:loggingService.getInstance** - Error information about a crash occurring in the web application.
- **multiWindowManager.ts:282:this.logError** - Error information describing a failure to run the multiple window experience.
- **multiWindowManager.ts:310:this.logError** - Error information describing a failure to run the multiple window experience.
- **multiWindowManager.ts:353:this.logError** - Error information describing a failure to run the multiple window experience.
- **multiWindowManager.ts:356:this.logError** - Error information describing a failure to run the multiple window experience.
- **multiWindowManager.ts:359:this.logError** - Error information describing a failure to run the multiple window experience.
- **multiWindowManager.ts:394:this.logError** - Error information describing a failure to run the multiple window experience.
- **multiWindowManager.ts:415:private logError** - Error information describing a failure to run the multiple window experience.
- **multiWindowManager.ts:426:this.logger.logError** - Error information describing a failure to run the multiple window experience.
- **multiWindowManager.ts:553:this.logError** - Error information describing a failure to run the multiple window experience.
- **multiWindowManager.ts:575:this.logError** - Error information describing a failure to run the multiple window experience.
- **multiWindowManager.ts:639:this.logError** - Error information describing a failure to run the multiple window experience.
- **multiWindowManager.ts:665:this.logError** - Error information describing a failure to run the multiple window experience.
- **multiWindowManager.ts:667:this.logError** - Error information describing a failure to run the multiple window experience.
- **multiWindowManager.ts:695:this.logError** - Error information describing a failure to run the multiple window experience.
- **multiWindowManager.ts:707:this.logError** - Error information describing a failure to run the multiple window experience.
- **multiWindowManager.ts:710:this.logError** - Error information describing a failure to run the multiple window experience.
- **multiWindowManager.ts:741:this.logError** - Error information describing a failure to run the multiple window experience.
- **multiWindowManager.ts:744:this.logError** - Error information describing a failure to run the multiple window experience.
- **multiWindowManager.ts:771:this.logError** - Error information describing a failure to run the multiple window experience.
- **nativeElectronNotifications\osNotificationService.ts:282:self.loggingService.logError** - Error information attempting to launch the notifications, with information about the failure.
- **nativeElectronNotifications\osNotificationService.ts:378:this.loggingService.logError** - Error information attempting to launch the notifications, with information about the failure.
- **OutlookMeetingAddinHelper.ts:100:LoggingService.getInstance** - Error information about connecting with the Outlook meeting addin.
- **OutlookMeetingAddinHelper.ts:111:LoggingService.getInstance** - Error information about connecting with the Outlook meeting addin.
- **OutlookMeetingAddinHelper.ts:202:LoggingService.getInstance** - Error information about connecting with the Outlook meeting addin.
- **OutlookMeetingAddinHelper.ts:227:LoggingService.getInstance** - Error information about connecting with the Outlook meeting addin.
- **OutlookMeetingAddinHelper.ts:256:LoggingService.getInstance** - Error information about connecting with the Outlook meeting addin.
- **recoveryManager.ts:86:LoggingService.getInstance** - Update rollback.
- **recoveryManager.ts:108:LoggingService.getInstance** - Update rollback.
- **recoveryManager.ts:155:LoggingService.getInstance** - Update rollback.
- **renderer\startPage\startPage.ts:23:this.logger.logError** - App start page issues.
- **renderer\startPage\startPage.ts:50:this.logger.logError** - App start page issues.
- **renderer\startPage\startPage.ts:69:this.logger.logError** - App start page issues.
- **renderer\startPage\startPage.ts:80:this.logger.logError** - App start page issues.
- **renderer\startPage\startPage.ts:125:this.logger.logError** - App start page issues.
- **settingsService.ts:132:LoggingService.getInstance** - Settings issues.
- **settingsService.ts:490:LoggingService.getInstance** - Compare settings issues.
- **settingsService.ts:691:LoggingService.getInstance** - Save settings issues.
- **updateInfo.ts:42:LoggingService.getInstance** - An update broken issue.
- **updateInfo.ts:62:LoggingService.getInstance** - An update broken issue.
- **updatenotification.js:267:this._loggingService.logError** - A disk space issue.
- **updatePolicyManager.ts:319:LoggingService.getInstance** - Scheduled update issues.
- **updatePolicyManager.ts:324:LoggingService.getInstance** - Scheduled update issues.
- **updatePolicyManager.ts:329:LoggingService.getInstance** - Scheduled update issues.
- **utility.ts:231:loggingService.logError** - Disk IO for app data deletion.
- **utility.ts:264:loggingService.logError** - Disk IO for app data deletion.
- **utility.ts:418:LoggingService.getInstance** - Cannot get disk space.
- **utility.ts:583:LoggingService.getInstance** - Display issues.
- **utility.ts:930:LoggingService.getInstance** - Protocol issues.
- **utility.ts:933:LoggingService.getInstance** - URL issues.
- **utility.ts:1009:LoggingService.getInstance** - Protocol issues.
- **utility.ts:1012:LoggingService.getInstance** - URL issues.
- **utility.ts:1119:LoggingService.getInstance** - Unable to check if a user is an admin.
- **utility.ts:1356:LoggingService.getInstance** - URL issues.
- **utility.ts:1382:LoggingService.getInstance** - URL issues.
- **utility.ts:1471:LoggingService.getInstance** - Cookie issues.
- **utility.ts:1515:LoggingService.getInstance** - Cookie issues.
- **utility.ts:1524:LoggingService.getInstance** - Cookie issues.
- **utility.ts:1553:LoggingService.getInstance** - Cookie issues.
- **utility.ts:1566:LoggingService.getInstance** - Cookie issues.
- **utility.ts:1588:LoggingService.getInstance** - Cookie issues.
- **utility.ts:1637:LoggingService.getInstance** - Regkey issues.
- **utility.ts:1647:LoggingService.getInstance** - App distribution source read issues.
- **utility.ts:1682:LoggingService.getInstance** - Regkey issues.
- **utility.ts:1726:LoggingService.getInstance** - A nativeutils exception.
- **windowmanager.js:306:this._loggingService.logError** - Cookie issues.
- **windowmanager.js:311:this._loggingService.logError** - Cookie issues.
- **windowmanager.js:338:this._loggingService.logError** - Whitescreen issues.
- **windowmanager.js:551:this._loggingService.logError** - Shell communication issues.
- **windowmanager.js:568:this._loggingService.logError** - Multi-window issues.
- **windowmanager.js:607:this._loggingService.logError** - Shell communication issues.
- **windowmanager.js:1333:this._loggingService.logError** - URL issues.
- **windowmanager.js:1337:this._loggingService.logError** - URL issues.
- **windowmanager.js:1645:this._loggingService.logError** - Page load message.
- **windowmanager.js:2124:this._loggingService.logError** - Renderer process issues.
- **windowmanager.js:2176:this._loggingService.logError** - Network connection issues.
- **windowmanager.js:2354:LoggingService.getInstance** - Need to know if recovery window cannot be shown.

### Scenario

> [!NOTE]
> For information on the properties of PanelAction events, see [Properties sent with scenario events](#properties-sent-with-scenario-events).

- **desktop_app_load** - Once the application is launched, able to initialize the service.
- **desktop_app_not_ready** - Error, application is not ready to function.
- **desktop_install** - Install success or failure.
- **desktop_previous_lifecycle_invalid** - Application started and, after deadlock or crash, application restarted.

### Tracking

- **adal-anonymous-mac.ts:47:this.logger.logError** - A general logging statement indicating a generic single sign-on (SSO) error occurred when logging in anonymously on Mac.
- **adal-anonymous-windows.ts:61:this.logger.logError** - A general logging statement indicating a generic sso error occurred when logging in anonymously on Windows.
- **adal-impl-mac.ts:56:this.loggingService.logError** - A statement indicating an issue occurred when parsing some telemetry returned from the Authentication Service.
- **adal-impl-mac.ts:164:this.loggingService.logError** - A general logging statement indicating a generic sso error occurred when logging in on Mac.
- **adal-rigel-windows.ts:85:this.logger.logError** - A general logging statement indicating a generic sso error occurred when logging in on our Rigel machines. ???
- **adal-sso-windows.ts:358:this.loggingService.logError** - A general logging statement indicating a generic single sign-on (SSO) error occurred when logging in on Windows.
- **adal-sso-windows.ts:800:this.loggingService.logError** - A statement describing why the user failed to log in through the authentication service.
- **adal-sso-windows.ts:951:this.loggingService.logError** - An issue fetching the chat service aggregator resource, which is an optional resource.
- **adalAnonymousUtil.ts:55:LoggingService.getInstance** - An error statement logging that the app could not launch in the anonymous authentication context.
- **adalAnonymousUtil.ts:58:LoggingService.getInstance** - An error statement logging that the app could not launch in the anonymous authentication context.
- **adalBase.ts:898:this.loggingService.logError** - An error statement describing that the user profile is null or empty.
- **appOnlineService.ts:68:LoggingService.getInstance** - An error occurred attempting to download our pre-auth settings in the background.
- **appOnlineService.ts:73:LoggingService.getInstance** - An error occurred attempting to download our pre-auth settings in the background.
- **appOnlineService.ts:138:LoggingService.getInstance** - An error statement that occurs when some settings could not be parsed on startup.
- **appOnlineService.ts:191:LoggingService.getInstance** - An error statement that occurs when some settings could not be parsed on startup.
- **appStart.ts:344:loggingService.logError** - A message describing that the app could not launch due to disk space issues.
- **appStart.ts:1701:loggingService.logError** - Failed to launch the app with a valid certificate on the machine.
- **appStart.ts:1731:loggingService.logError** - Failed to find the correct certificate, and restarting the app.
- **browserWindowHttp.ts:46:this.loggingService.logError** - Information describing that the app could not be updated due to an issue with the file system.
- **contextInstallService.ts:227:loggingService.getInstance** - An error attempting to parse a file critical to the contextual install feature.
- **contextInstallService.ts:359:loggingService.getInstance** - An error attempting to read or resolve a url critical to the contextual install feature.
- **contextInstallService.ts:507:loggingService.getInstance** - An error from the Url Shortener, a partner service, attempting to run the contextual install feature.
- **contextInstallService.ts:514:loggingService.getInstance** - An error during the contextual install feature.
- **contextInstallService.ts:517:loggingService.getInstance** - An error from the Url Shortener, a partner service, attempting to run the contextual install feature.
- **contextInstallService.ts:524:loggingService.getInstance** - An error from the Url Shortener, a partner service, attempting to run the contextual install feature.
- **contextInstallService.ts:541:loggingService.getInstance** - An error from the Url Shortener, a partner service, attempting to run the contextual install feature.
- **contextInstallService.ts:542:loggingService.getInstance** - An error occurred during the contextual install feature.
- **contextInstallService.ts:616:loggingService.getInstance** - An error occurred during the contextual install feature.
- **contextInstallService.ts:660:loggingService.getInstance** - An error occurred during the contextual install feature.
- **crashManager.ts:80:loggingService.logError** - Error information about the crash diagnostics in the app.
- **crashManager.ts:139:loggingService.logError** - Error information about the crash diagnostics in the app.
- **crashManager.ts:359:loggingService.logError** - Error information about the crash diagnostics in the app.
- **localStorageService.ts:46:LoggingService.getInstance** - An error occurred loading up essential app boot data, necessary for properly running the app.
- **localStorageService.ts:48:LoggingService.getInstance** - An error occurred loading up essential app boot data, necessary for properly running the app.
- **localStorageService.ts:124:LoggingService.getInstance** - An error occurred loading up essential app boot data, necessary for properly running the app.
- **localStorageService.ts:146:LoggingService.getInstance** - An error occurred loading up essential app boot data, necessary for properly running the app.
- **logProviders\pageDumpProvider.ts:30:loggingService.getInstance** - Error information about a crash occurring in the web application.
- **multiWindowManager.ts:282:this.logError** - Error information describing a failure to run the multiple window experience.
- **multiWindowManager.ts:310:this.logError** - Error information describing a failure to run the multiple window experience.
- **multiWindowManager.ts:353:this.logError** - Error information describing a failure to run the multiple window experience.
- **multiWindowManager.ts:356:this.logError** - Error information describing a failure to run the multiple window experience.
- **multiWindowManager.ts:359:this.logError** - Error information describing a failure to run the multiple window experience.
- **multiWindowManager.ts:394:this.logError** - Error information describing a failure to run the multiple window experience.
- **multiWindowManager.ts:415:private logError** - Error information describing a failure to run the multiple window experience.
- **multiWindowManager.ts:426:this.logger.logError** - Error information describing a failure to run the multiple window experience.
- **multiWindowManager.ts:553:this.logError** - Error information describing a failure to run the multiple window experience.
- **multiWindowManager.ts:575:this.logError** - Error information describing a failure to run the multiple window experience.
- **multiWindowManager.ts:639:this.logError** - Error information describing a failure to run the multiple window experience.
- **multiWindowManager.ts:665:this.logError** - Error information describing a failure to run the multiple window experience.
- **multiWindowManager.ts:667:this.logError** - Error information describing a failure to run the multiple window experience.
- **multiWindowManager.ts:695:this.logError** - Error information describing a failure to run the multiple window experience.
- **multiWindowManager.ts:707:this.logError** - Error information describing a failure to run the multiple window experience.
- **multiWindowManager.ts:710:this.logError** - Error information describing a failure to run the multiple window experience.
- **multiWindowManager.ts:741:this.logError** - Error information describing a failure to run the multiple window experience.
- **multiWindowManager.ts:744:this.logError** - Error information describing a failure to run the multiple window experience.
- **multiWindowManager.ts:771:this.logError** - Error information describing a failure to run the multiple window experience.
- **nativeElectronNotifications\osNotificationService.ts:282:self.loggingService.logError** - Error information attempting to launch the notifications, with information about the failure.
- **nativeElectronNotifications\osNotificationService.ts:378:this.loggingService.logError** - Error information attempting to launch the notifications, with information about the failure.
- **OutlookMeetingAddinHelper.ts:100:LoggingService.getInstance** - Error information about connecting with the Outlook meeting addin.
- **OutlookMeetingAddinHelper.ts:111:LoggingService.getInstance** - Error information about connecting with the Outlook meeting addin.
- **OutlookMeetingAddinHelper.ts:202:LoggingService.getInstance** - Error information about connecting with the Outlook meeting addin.
- **OutlookMeetingAddinHelper.ts:227:LoggingService.getInstance** - Error information about connecting with the Outlook meeting addin.
- **OutlookMeetingAddinHelper.ts:256:LoggingService.getInstance** - Error information about connecting with the Outlook meeting addin.
- **recoveryManager.ts:86:LoggingService.getInstance** - Update rollback.
- **recoveryManager.ts:108:LoggingService.getInstance** - Update rollback.
- **recoveryManager.ts:155:LoggingService.getInstance** - Update rollback.
- **renderer\startPage\startPage.ts:23:this.logger.logError** - App start page issues.
- **renderer\startPage\startPage.ts:50:this.logger.logError** - App start page issues.
- **renderer\startPage\startPage.ts:69:this.logger.logError** - App start page issues.
- **renderer\startPage\startPage.ts:80:this.logger.logError** - App start page issues.
- **renderer\startPage\startPage.ts:125:this.logger.logError** - App start page issues.
- **settingsService.ts:132:LoggingService.getInstance** - Settings issues.
- **settingsService.ts:490:LoggingService.getInstance** - Compare settings issues.
- **settingsService.ts:691:LoggingService.getInstance** - Save settings issues.
- **updateInfo.ts:42:LoggingService.getInstance** - Update broken issue. ???
- **updateInfo.ts:62:LoggingService.getInstance** - Update broken issue. ???
- **updatenotification.js:267:this._loggingService.logError** - Disk space issue.
- **updatePolicyManager.ts:319:LoggingService.getInstance** - Scheduled update issues.
- **updatePolicyManager.ts:324:LoggingService.getInstance** - Scheduled update issues.
- **updatePolicyManager.ts:329:LoggingService.getInstance** - Scheduled update issues.
- **utility.ts:231:loggingService.logError** - Disk IO for app data deletion.
- **utility.ts:264:loggingService.logError** - Disk IO for app data deletion.
- **utility.ts:418:LoggingService.getInstance** - Can't get disk space.
- **utility.ts:583:LoggingService.getInstance** - Display issues.
- **utility.ts:930:LoggingService.getInstance** - Protocol issues.
- **utility.ts:933:LoggingService.getInstance** - URL issues.
- **utility.ts:1009:LoggingService.getInstance** - Protocol issues.
- **utility.ts:1012:LoggingService.getInstance** - URL issues.
- **utility.ts:1119:LoggingService.getInstance** - Can't check if user is an admin.
- **utility.ts:1356:LoggingService.getInstance** - URL issues.
- **utility.ts:1382:LoggingService.getInstance** - URL issues.
- **utility.ts:1471:LoggingService.getInstance** - Cookie issues.
- **utility.ts:1515:LoggingService.getInstance** - Cookie issues.
- **utility.ts:1524:LoggingService.getInstance** - Cookie issues.
- **utility.ts:1553:LoggingService.getInstance** - Cookie issues.
- **utility.ts:1566:LoggingService.getInstance** - Cookie issues.
- **utility.ts:1588:LoggingService.getInstance** - Cookie issues.
- **utility.ts:1637:LoggingService.getInstance** - Regkey issues.
- **utility.ts:1647:LoggingService.getInstance** - App distribution source read issues.
- **utility.ts:1682:LoggingService.getInstance88** - Regkey issues.
- **utility.ts:1726:LoggingService.getInstance** - Nativeutils exception.
- **windowmanager.js:306:this._loggingService.logError** - Cookie issues.
- **windowmanager.js:311:this._loggingService.logError** - Cookie issues.
- **windowmanager.js:338:this._loggingService.logError** - Whitescreen issues.
- **windowmanager.js:551:this._loggingService.logError** - Shell communication issues.
- **windowmanager.js:568:this._loggingService.logError** - Multi-window issues.
- **windowmanager.js:607:this._loggingService.logError** - Shell communication issues.
- **windowmanager.js:1333:this._loggingService.logError** - URL issues.
- **windowmanager.js:1337:this._loggingService.logError** - URL issues.
- **windowmanager.js:1645:this._loggingService.logError** - Page load message.
- **windowmanager.js:2124:this._loggingService.logError** - Renderer process issues.
- **windowmanager.js:2176:this._loggingService.logError** - Network connection issues.
- **windowmanager.js:2354:LoggingService.getInstance** - The need to know if recovery window can't be shown.

### UserBI

- **toastshow** - Initiated by service to render a toast (purple toast). !!!
- **toasttimeout** - After rendering of toast, log whether the toast was timedout so the service can monitor errors and delays (purple toast).
- **toastdismiss** - After rendering of toast, log whether the toast was dismissed by user so service can monitor errors and delays (purple toast).
- **toastclick** - Navigation after clicking on toast to appropriate message/entity and loading of the message for user to view (purple toast).
- **inlinereply** - Need to send reply back as a message and logs for same (purple toast).
- **toastreply** - Log toasts clicks for monitoring service SLA and navigation to load the corresponding message/entity (os toast)
- **toastskip** - Log skipping of toast popup when delayed notifications come in from service (os toast).
- **toastdismiss** - After rendering of toast, log whether the toast was dismissed by user so service can monitor errors and delays (os toast).
- **toasttimeout** - After rendering of toast, log whether the toast was timed out so the service can monitor errors and delays (os toast).
- **inlinereply** - Need to send reply back as a message and logs for same (purple toast)

## Property lists

### Properties sent with all events

| Property name                    | Description                                                          |
|----------------------------------|----------------------------------------------------------------------|
| EventInfo_Time                   | Event generation time                                                |
| EventInfo_Name                   | Event name - Used to differentiate between event types               |
| EventInfo_BaseType/name          | Event type - Used to differentiate between event types in an event   |
| EventInfo_Source                 | Source of the event generation                                       |
| AppInfo_Language                 | App language                                                         |
| AppInfo_ETag                     | Experiment ID assigned to a user                                     |
| DeviceInfo_OsBuild               | Build version of the OS                                              |
| UserInfo_Mri                     | Type a user ID                                                       |
| Session_RunId                    | Type of a session ID                                                 |
| DeviceInfo_DetailModel           | Model of the device                                                  |
| UserInfo_TimeZone                | Time zone of the user                                                |
| DeviceInfo_OsName                | Device OS name                                                       |
| DeviceInfo_NetworkProvider       | Device network provider                                              |
| DeviceInfo_Model                 | Device Model                                                         |
| DeviceInfo_NetworkType           | Device network type                                                  |
| UserInfo_Language                | User language - similar to app language                              |
| client_ring/UserInfo_Ring        | User ring that helps to release features to early adopters           |
| UserInfo_Id                      | User ID                                                              |
| UserInfo_TenantId                | Tenant ID                                                            |
| EventInfo_SdkVersion             | SDK version used to generate the event                               |
| DeviceInfo_Id                    | Device ID provided by device OS                                      |
| eventpriority                    | Priority of an event                                                 |
| DeviceInfo_Make                  | Device manufacturer                                                  |
| AppInfo_Version                  | Version of the app                                                   |
| DeviceInfo_OsVersion             | Device OS version                                                    |
| Session_Id/SessionId             | Session ID of the request                                            |
| Session_Environment              | Session Environment                                                  |
| isNetworkIssue                   | Captures info if there was a network issue while serving the request |
| UserRole                         | User role in a tenant                                                |
| Tenant_Model                     | Captures if the account is a freemium or enterprise account          |
| licenseType/UserInfo_LicenseType | Licence type assigned to the user                                    |
| UserLocale                       | Locale in which app is being accessed                                |
| Intune_sdkVersion                | Version of the Intune SDK                                            |
| Intune_sdkBundleVersion          | Detailed version of the Intune SDK                                   |
| AppInfo_Environment              | Environment in which the app is being access                         |

### Properties sent with panelaction events

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
| Module_Summary        | Summary of the module that hosted user action                      |
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

### Properties sent with panelview events

| Panel_Uri          | Uri of the panel delivered to the user                   |
|--------------------|----------------------------------------------------------|
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

### Properties sent with scenario events

| Property name        | Description |
|----------------------|-------------|
| Scenario_Status      | Status of a scenario - Abandon/OK/ERROR |
| Scenario_Step        | When a scenario contains multiple steps with different failure points, this property captures details about the step |
| Scenario_StatusCode  | Property records status code of the scenario based on scenario success or failure |

### Properties sent with trace events

| Property name | Description                                                                                    |
|---------------|------------------------------------------------------------------------------------------------|
| Trace_message | Contains error string and details about the reasons due to which a failure might have happened |
