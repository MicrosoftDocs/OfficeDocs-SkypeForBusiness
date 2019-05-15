---
title: "Use Config.xml to perform installation tasks in Skype for Business clients"
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.reviewer: PhillipGarding
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 0813184a-ab40-417c-b3a3-c2090766b831
description: "Summary: How to use the Config.xml file to specify additional installation instructions."
---

# Use Config.xml to perform installation tasks in Skype for Business clients

**Summary:** How to use the Config.xml file to specify additional installation instructions.

Although the Office Customization Tool (OCT) is the primary tool for customization installation, administrators can use the Config.xml file to specify additional installation instructions that are not available in the OCT. The following customizations can only be made by using the Config.xml file:

- Specify the path of the network installation point.

- Select the products to install.

- Configure logging and the location of the Setup customization file and software updates.

- Specify installation options, such as user name.

- Copy the local installation source (LIS) to the user's computer without installing Office.

- Add or remove languages from the installation.

We recommend that you use the Config.xml file to configure Skype for Business silent installation. 

By default, the Config.xml file that is stored in the core product folder (for example, \ _product_.WW) directs Setup to install that product. For example, the Config.xml file in the following folder installs Skype for Business:

- \\server\share\Skype15\Skype.WW \Config.xml

The Config.xml elements most commonly used for Skype for Business installation are listed in the following table.

**Config.xml elements**


| **Element**              | **Description**                                                                                                                                                                                                                                                                                         |
|:-------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Configuration  <br/>     | Top-level element (required). Contains the Product attribute, for example: Product=Lync (This will work for Skype for Business clients)  <br/>                                                                                                                                                          |
| OptionState  <br/>       | Specifies how specific product features are handled during installation. Use the following attributes to prevent installation of Business Connectivity Services, which includes shared components that interfere with Outlook: <br/>  Id="LOBiMain" <br/>  State="Absent" <br/>  Children="Force" <br/> |
| Display  <br/>           | The level of UI that Setup displays to the user. Typical attributes include the following: <br/>  CompletionNotice="Yes"                                                                                                                                                                                |
| Logging  <br/>           | Options for the kind of logging that Setup performs. Typical attributes include the following: <br/>  Type ="Off"                                                                                                                                                                                       |
| Setting  <br/>           | Specifies values for Windows Installer properties. Typical attributes include the following: <br/>  Setting Id=" *name*" (the name of the Windows Installer property)  <br/>  Value=" *value*" (the value to assign to the property)  <br/>                                                             |
| DistributionPoint  <br/> | The fully qualified path of the network installation point from which the installation is to run. Includes the Location attribute: <br/>  Location=" *path*"  <br/>                                                                                                                                     |

The following example shows a Config.xml file for a typical silent installation of the Skype for Business client. 

```
<Configuration Product="Lync"> 
  <OptionState Id="LOBiMain" State="Absent" Children="Force" /> 
  <Display Level="None" CompletionNotice="No" AcceptEula="Yes" /> 
  <Logging Type="verbose" Path="%temp%" Template="LyncSetupVerbose(*).log" />
  <Setting Id="SETUP_REBOOT" Value="Never" /> 
  <DistributionPoint Location="\\server\share\Skype15" /> 
</Configuration>
```

Detailed information about using the Config.xml file to perform Office installation and maintenance tasks is available at [https://go.microsoft.com/fwlink/p/?linkid=267514](https://go.microsoft.com/fwlink/p/?linkid=267514).

## To customize the Config.xml file

1. Open the Config.xml file by using a text editor tool, such as Notepad.

2. Locate the lines that contain the elements you want to change.

3. Modify the element entry with the silent options that you want to use. Make sure that you remove the comment delimiters, "\<!--" and "--\>". For example, use the following syntax:

   <pre>
   < DistributionPoint Location="\\server\share\Skype15" />
   </pre>

4. Save the Config.xml file.


