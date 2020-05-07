---
title: Policy control properties and events for Microsoft Teams
author: MicrosoftHeidi
ms.author: heidip
manager: serdars
ms.topic: reference
ms.service: msteams
audience: admin
ms.reviewer: majaisin
description: A list of properties and events for the policy controls for Microsoft Teams.
localization_priority: Priority
search.appverid: MET150
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---
# Policy control events for Microsoft Teams

The following article contains lists of the properties sent with various events, and lists of the events themselves, arranged by product.

## Property lists

### Properties sent with all events

| Property name                    | Description                                                          |
|----------------------------------|----------------------------------------------------------------------|
| EventInfo_Time                   | Event generation time                                                |
| EventInfo_Name                   | Event name - Used to differentiate between event types               |
| EventInfo_BaseType/name          | Event type - Used to differentiate between event types in an event   |
| EventInfo_Source                 | Source of the event generation                                       |
| AppInfo_Language                 | App language                                                        |
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
| AppInfo_Version                  | Version of the app                                                    |
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
| Module_Summary        | Summary of the module that hosted user action                       |
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

| Property name       | Description                                                                                                          |
|---------------------|----------------------------------------------------------------------------------------------------------------------|
| Scenario_Status     | Status of a scenario - Abandon/OK/ERROR                                                                              |
| Scenario_Step       | When a scenario contains multiple steps with different failure points, this property captures details about the step |
| Scenario_StatusCode | Property records status code of the scenario based on scenario success or failure                                    |

### Properties sent with trace events

| Property name | Description                                                                                    |
|---------------|------------------------------------------------------------------------------------------------|
| Trace_message | Contains error string and details about the reasons due to which a failure might have happened |

## Events

LIST IN PROGRESS

