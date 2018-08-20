---
title: "Configure Cloud Auto Attendant"
ms.author: jambirk
author: jambirk
manager: serdars
ms.date: 8/1/2018
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
description: "Instructions for implementing a Cloud Auto Attendant."
---
 
[!INCLUDE [disclaimer](../disclaimer.md)]

# Configure cloud auto attendant

In Skype for Business Server 2019 you are able to use the cloud auto attendant feature described in [What are Phone System auto attendants?](../../SfbOnline/what-is-phone-system-in-office-365/what-are-phone-system-auto-attendants.md).

Specific configuration of Skype for Business Server 2019 is not needed to use Cloud Auto Attendant, but you will need to either export an existing Auto Attendant implemented in Exchange UM or implement a new  Auto Attendant using the Office Online Admin portal. 

## Server Configuration steps

**Server-side configuration needed for interop with Cloud Auto Attendant. Current assumption is that there is no additional config needed if Cloud voice is implemented.**

## Online Configuration steps 

For a new implementation, review [Do's and Don'ts for Auto Attendant scripts](plan-cloud-auto-attendant.md#dos-and-donts-for-auto-attendant-scripts) then see [Set up a Phone System auto attendant](../../SfbOnline/what-is-phone-system-in-office-365/set-up-a-phone-system-auto-attendant.md).  


## Migrating an Exchange UM Auto Attendant

### Export an existing Auto Attendant 

You can either use the new tool or use the cmdlets mentioned. 

#### Use OCSAAEXPORT.EXE to select the Dial Plans and associated Auto Attendants to export data as XML.

The tool does the following for every AA:
* Exports the properties of the AA object into an XML file.
* Creates a disabled user object for the AA. [**cmdlet for this?**]
    * For AAs with multiple numbers, multiple disabled user objects are created, distinguishable by numbered suffixes (AA1, AA2, and so on).
    * No suffix is required for an AA with a single number.
* Adds the name of the disabled user object(s) to a txt file, along with the associated numbers. 
    * Each row is on a new line.
* Creates a folder for each disabled user object, containing the associated files (XML and recorded custom greetings files) for the AA.
* Deletes the contact object associated with the AA.
* Wraps the txt file and folders in a zip file, and deposits this zip file in a specified location. **Where? Default? user-specified?**

When the operation is complete, a success message is shown, along with the file name and location of the zip file created.


#### Use Skype OnPrem Admin Shell  
The admin executes the cmdlet `Export -CsAutoAttendant` with Dial Plan name and AA name (the ones that need export) as parameters **(requirements for cmdlet? Logged in to which server with what privelege level)**. Passing only Dial Plan name exports all associated AAs by default.


### Import an existing Exchange UM Auto Attendant in to a new Phone System Auto Attendant

**The following assumes you are logged in to the Skype Online Admin Shell as a  ____ level admin.**

Before importing the XML file, the AAD administrator must schedule a Full sync for AAD Connect, using the following cmdlet:
```
Start-ADSyncSyncCycle -PolicyType Initial
```
This will kick off an immediate Full sync, which is necessary whenever objects are added.

Import Auto Attendants Using Skype Admin Center: <BR/> **is this change to Admin center live yet or are we running the cmdlet from a prompt?**

1. Navigate to the Voice Features tab.
2. Select the **Import** button, (next to the **Refresh** button). A file browser pops up, choose the zip file containing the files Exported from Exchange UM.

The Skype Admin Center then executes the cmdlet `Import -CsAutoAttendant` that:
* Unzips the archive file
* Reads the list of AAs from the txt file, looks up the folder for each AA and populates the DUO for the AA with required properties from the XML as well as the appropriate files, such as custom greetings.

Once the population of DUOs is complete, a success message is shown to the admin and the list of AAs is shown in the Skype Admin Center.

**Using Skype Online Admin Shell** – The after logging in as Admin,  execute the cmdlet `Import -CsAutoAttendant` with the path of the zip file passed as a parameter. Successful completion returns a list of AAs in the shell.

## See Also

[Plan Cloud Voicemail service](plan-cloud-voicemail.md)

[Configure Cloud Voicemail service](configure-cloud-voicemail.md)