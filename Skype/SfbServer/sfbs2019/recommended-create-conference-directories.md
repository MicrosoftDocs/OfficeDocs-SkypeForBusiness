---
title: "(Recommended) Create Conference Directories"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 787f4c94-1c96-468a-a74d-e06b7bd4b8a3
description: "Conference directories maintain a mapping between the alphanumeric meeting ID that a participant uses to join a conference when using Lync 2013, and the numeric-only conference ID that a dial-in conferencing participant uses to join the conference. The format of the conference ID is as follows:"
---

# (Recommended) Create Conference Directories
[]
Conference directories maintain a mapping between the alphanumeric meeting ID that a participant uses to join a conference when using Lync 2013, and the numeric-only conference ID that a dial-in conferencing participant uses to join the conference. The format of the conference ID is as follows:
  
```
<housekeeping digit (1 digit)><conference directory (usually 1-2 digits)><conference number (variable number of digits><check digit (1 digit)>
```

Creating multiple conference directories will ensure that conference IDs will stay short until a significant amount of conferences have been created. In an organization with a typical number of conferences per user, we recommend that you create one conference directory for every 999 users in the pool. Using this guideline the conference IDs can generally be kept small. However, once the number of conference directories (across the pools) exceed 9, the Conference ID length will grow to support additional conferences.
  
### Creating a conference directory

- In Lync Server Management Shell, type the following cmdlet:
    
  ```
  New-CsConferenceDirectory -Identity <XdsGlobalRelativeIdentity> -HomePool <String> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]
  ```

    For example, the following creates a conference directory with the identity 42, hosted on the pool atl-cs-001.litwareinc.com:
    
  ```
  New-CsConferenceDirectory -Identity 42 -HomePool "atl-cs-001.litwareinc.com"
  
  ```

## See also

#### 

[Dial-in conferencing requirements in Lync Server 2013](dial-in-conferencing-requirements.md)
#### 

[New-CsConferenceDirectory](new-csconferencedirectory.md)

