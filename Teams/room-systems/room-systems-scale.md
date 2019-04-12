---
title: "Deploy Microsoft Teams Rooms by using System Center Configuration Manager"
author: jambirk
ms.author: jambirk
ms.reviewer: Turgayo
manager: serdars
ms.date: 5/10/2018
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.custom: Strat_SB_Admin
ms.assetid: 678689e4-d547-499b-be64-7d8f16dd8668
ms.collection: M365-voice
description: "Read this topic to learn about deploying Microsoft Teams Rooms at large scale deployments."
---

# Deploy Microsoft Teams Rooms by using System Center Configuration Manager

This article gives you all the necessary information to create your Microsoft Teams Rooms deployments by using System Center Configuration Manager.

With the easy-to-use methods provided by System Center Configuration Manager, you can deploy the operating system and other applications to multiple target devices.

Use the approach illustrated below to guide you through your Configuration Manager configuration, and customize the sample packages and scripts provided throughout this guidance as needed for your organization.

![Microsoft Teams Rooms deployment process using Configuration Manager](../../media/room-systems-scale-image1.png)

> [!IMPORTANT]
> This solution has only been tested with Surface Pro–based deployments. Follow the manufacturer’s guidelines for configurations that aren’t based on Surface Pro.

## Validate prerequisites

To deploy Microsoft Teams Rooms with Configuration Manager, ensure that you meet the following prerequisites and requirements.

### System Center Configuration Manager requirements

-   System Center Configuration Manager version must be at least 1706 or above. We recommend using 1710 or later. Check out [Support for Windows 10 in System Center Configuration Manager](https://docs.microsoft.com/sccm/core/plan-design/configs/support-for-windows-10#windows-10-as-a-client) to learn about the Windows 10 versions that Configuration Manager supports.

-   A supported version of Windows Assessment and Deployment Kit (ADK) for Windows 10 must be installed. See the versions of the [Windows 10 ADK](https://docs.microsoft.com/sccm/core/plan-design/configs/support-for-windows-10#windows-10-adk) that you can use with different versions of Configuration Manager, and ensure that your deployment includes the correct version.

-   The site system servers must have been assigned the distribution point role, and the boot images should be enabled for [preboot execution environment (PXE) support](https://docs.microsoft.com/sccm/osd/deploy-use/use-pxe-to-deploy-windows-over-the-network) to enable network-initiated deployments. If PXE support isn’t enabled, you can use [bootable media](https://docs.microsoft.com/sccm/osd/deploy-use/use-bootable-media-to-deploy-windows-over-the-network) for your deployments.

-   A network access account must be configured to support new computer (bare metal) deployment scenarios. To learn more about the configuration of a network access account, see [Manage accounts to access content in System Center Configuration Manager](https://docs.microsoft.com/sccm/core/plan-design/hierarchy/manage-accounts-to-access-content#bkmk_NAA).

-   We recommend that you enable [multicast support](https://docs.microsoft.com/sccm/osd/deploy-use/use-multicast-to-deploy-windows-over-the-network), if you’re likely to deploy the same Microsoft Teams Rooms image to multiple units at the same time.

### Networking requirements

-   Your network should have a Dynamic Host Configuration Protocol (DHCP) server, configured for automatic IP address distribution to the subnets where Microsoft Teams Rooms units will be deployed.

    > [!NOTE]
    > DHCP lease duration must be set to a value longer than the image deployment duration. Otherwise, the deployment might fail.

-   Your network, including switches and virtual LANs (VLANs), should be configured to support PXE. Refer to your network vendor for more information about IP Helper and PXE configuration. Alternatively, you can use [bootable media](https://docs.microsoft.com/sccm/osd/deploy-use/use-bootable-media-to-deploy-windows-over-the-network) for your deployments, if PXE support isn’t enabled.

    > [!NOTE]
    > For Surface Pro devices, booting from the network (PXE boot) is only supported when you use an Ethernet adapter or docking station from Microsoft. Third-party Ethernet adapters don’t support PXE boot with Surface Pro. See [Ethernet adapters and Surface deployment](https://docs.microsoft.com/surface/ethernet-adapters-and-surface-device-deployment) for more information.

## Configure System Center Configuration Manager for operating system deployment

This article assumes you already have a healthy System Center Configuration Manager deployment, and doesn’t detail all the steps required to deploy and configure Configuration Manager from scratch. The [documentation and the configuration guidance](https://docs.microsoft.com/sccm/) on the System Center Configuration Manager is a great resource; we recommend you start with these resources if you haven’t yet deployed Configuration Manager.

Use the following instructions to verify that the operating system deployment (OSD) features are configured properly.

### Validate and upgrade Configuration Manager

1.  In the Configuration Manager console, go to **Administration** \> **Updates and Servicing**.

2.  Check the installed build and applicable updates that haven’t been installed yet.

3.  Review [Support for Windows 10 in System Center Configuration Manager](https://docs.microsoft.com/sccm/core/plan-design/configs/support-for-windows-10#windows-10-as-a-client); if you need to upgrade your deployment, select the update you want to install, and then select **Download**.

4.  After the download is complete, select the update, and then select **Install Update Pack**.

### Configure distribution points to support PXE and multicast

1.  In the Configuration Manager console, go to **Administration** \> **Distribution Points**.

2.  Select the distribution point server that will serve the Microsoft Teams Rooms deployment, and then select **Properties**.

3.  Select the **PXE** tab, and ensure that the following settings are enabled:
    -   Enable PXE support for clients
    -   Allow this distribution point to respond to incoming PXE requests
    -   Enable unknown computer support

4.  *Optional:* To enable multicast support, select the **Multicast** tab, and ensure that the following settings are enabled:
    -   Enable multicast to simultaneously send data to multiple clients
    -   Configure the UDP port range as per your network team’s recommendation

### Configure the Network Access Account

1.  In the Configuration Manager console, go to **Administration** \> **Site Configuration** \> **Sites**, and then select the site.

2.  In the **Settings** group, select **Configure Site Components** \> **Software Distribution**.

3.  Select the **Network Access Account** tab. Set up one or more accounts, and then select **OK**.

> [!NOTE]
> The accounts don’t need any special rights, except for the **Access this computer from the network** right on the distribution point server. A generic domain user account will be appropriate. For more information, see [Manage accounts to access content in System Center Configuration Manager](https://docs.microsoft.com/sccm/core/plan-design/hierarchy/manage-accounts-to-access-content#bkmk_NAA).

### Configure a boot image

1.  In the Configuration Manager console, go to **Software Library** \> **Operating System** \> **Boot Images**.

2.  Select **Boot image (x64)**, and then select **Properties**.

3.  Select the **Data Source** tab, and enable **Deploy this boot image from the PXE-enabled distribution point**.

4.  Select the **Optional Components** tab to install required components:

    1.  Select the star icon, and search for **HTML (WinPE-HTA)**

    2.  Select **OK** to add HTML application support in to the boot image.

5.  *Optional:* To customize the deployment experience, select the **Customization** tab.
    -   Enable **command support (testing only)** if you want to have access to a command prompt during the deployment. When this is enabled, you can start a command prompt by selecting **F8** at any time during the deployment.
    -   You can also specify a custom background image to be displayed during the deployment. To set an image, enable **Specify the custom background image file (UNC path** and select your background.

6.  When asked, select **Yes** and distribute the updated boot image to your distribution points.

For more information, see [Manage boot images with System Center Configuration Manager](https://docs.microsoft.com/sccm/osd/get-started/manage-boot-images).

> [!NOTE]
> You can create a bootable USB media to initiate Configuration Manager task sequence–based deployments for environments that have no PXE support. The bootable media contains only the boot image, optional prestart commands and their required files, and Configuration Manager binaries to support booting into Windows PE and connecting to Configuration Manager for the rest of the deployment process. For more information, see [How to Create Bootable Media](https://docs.microsoft.com/sccm/osd/deploy-use/create-bootable-media#BKMK_CreateBootableMedia).

## Create Configuration Manager packages

Configuration Manager requires a number of packages to deploy and configure the Microsoft Teams Rooms units.

You need to create and configure the following packages, and then distribute them to the Configuration Manager site systems that have been assigned the distribution point server role.

| **Package name**                     | **Type**               | **Description**                                                                           |
|--------------------------------------|------------------------|-------------------------------------------------------------------------------------------|
| SRS v2 - SRS Application Package     | Software package       | Package for the Microsoft Teams Rooms deployment kit                                      |
| SRS v2 - Sysprep Package             | Software package       | Package for the custom Unattended.xml to configure Microsoft Teams Rooms units            |
| SRS v2 - Set-SRSComputerName Package | Software package       | Package for the HTML application (HTA) to assign a computer name during the deployment    |
| SRS v2 - Configure SRS Setup         | Software package       | Package to configure deployment of the Microsoft Teams Rooms app                          |
| SRS v2 - OS Updates Package          | Software package       | Package to deploy mandatory operating system updates                                      |
| SRS v2 - Root Certificate Package    | Software package       | Optional - Package to deploy the root certificate (not required for domain-joined units)  |
| SRS v2 - Microsoft Monitoring Agent Package | Software package       | Optional - Package to deploy and configure the Microsoft Operations Management Suite agent|
| SRS v2 - WinPE Background Package    | Software package       | Package for the custom background image to use with boot images                           |
| Windows 10 Enterprise                | Operating system image | Package for the operating system installation file (install.wim)                          |
| Surface Pro                          | Driver package         | Package for the device drivers and firmware for Microsoft Surface Pro                     |
| Surface Pro 4                        | Driver package         | Package for the device drivers and firmware for Microsoft Surface Pro 4                   |

For more information, see [Packages and programs in System Center Configuration Manager](https://docs.microsoft.com/sccm/apps/deploy-use/packages-and-programs).

### Create folders for the package source files

Configuration Manager requires package source files to be organized in a specific folder structure when they’re first created and when they’re updated.

Create the following folder structure on the System Center Configuration Manager central administration site or primary site, or on a server share you’re using to host package source files:

-   SRS v2 - Microsoft Monitoring Agent Package
-   SRS v2 - OS Updates Package
-   SRS v2 - Root Certificate Package
-   SRS v2 - Set-SRSComputerName Package
-   SRS v2 - SRS Application Package
-   SRS v2 - Configure SRS Setup
-   SRS v2 - Sysprep Package
-   Drivers
    -   Surface Pro
    -   Surface Pro 4
-   Operating Systems
    -   Windows 10 Enterprise

> [!TIP]
> You may also [download](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Skype/SfbOnline/downloads/Skype-Room-Systems-v2/SRS-v2-Configuration-Manager-Files.zip?raw=true) and use the zip file that includes the folder structure for the packages, the scripts that you need to use, and the task sequence template, that you need to import.

### Create the Monitoring agent package

1. Download the Monitoring agent from <https://go.microsoft.com/fwlink/?LinkId=828603>.

2. Extract the package into the **SRS v2 - Microsoft Monitoring Agent Package** folder by opening a Command Prompt window and entering **MMASetup-AMD64.exe /C:**     at the command prompt.

3. In the Configuration Manager console, go to **Software Library** \> **Application Management** \> **Packages**, and then select **Create Package**.

4. Enter the following information to create the package:

   - Name<strong>: SRS v2 - Microsoft Monitoring Agent Package</strong>

   - Manufacturer<strong>: Microsoft Corporation</strong>

   - Version<strong>: 8.1.11081.0</strong> (enter the version of the downloaded installation file)

   - Select the **This package contains source files** check box, enter the path to the **SRS v2 - Microsoft Monitoring Agent Package** folder, and then select **Next**.

5. Select **Do not create a program**, and then select **Next**.

6. Review the **Confirm the settings** page, and then select **Next**.

7. Select **Close**.

### Create the operating system updates package

1. In the **SRS v2 - OS Updates Package** folder, create a new PowerShell script named **Install-SRSv2-OS-Updates.ps1**.

2. Copy the script below into the **Install-SRSv2-OS-Updates.ps1** script. Alternatively, you can download the Install-SRSv2-OS-Updates.ps1 script from [here](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Skype/SfbOnline/downloads/Skype-Room-Systems-v2/SRS-v2-Configuration-Manager-Files.zip?raw=true).
   ```
   # Install-SRSv2-OS-Updates.ps1
   $strPath = split-path -parent $MyInvocation.MyCommand.Definition
   $total = gci $strPath *.msu | measure | Select-Object -expand Count
   $i = 0
   gci $strPath *.msu | ForEach-Object {
     $i++
     WUSA ""$_.FullName /quiet /norestart""
     Write-Progress -activity "Applying Mandatory Updates" -status "Installing
     $_ .. $i of $total" -percentComplete (($i / $total) * 100)
     Wait-Process -name wusa
   }
   ```
3. Download the mandatory Windows Update packages into the same folder.
   > [!NOTE]
   > At the time this article was published, only [KB4056892](http://download.windowsupdate.com/c/msdownload/update/software/secu/2018/01/windows10.0-kb4056892-x64_a41a378cf9ae609152b505c40e691ca1228e28ea.msu) was required. Check [Configure a Microsoft Teams Rooms console](console.md), to see whether any other updates are required.

4. In the Configuration Manager console, go to **Software Library** \> **Application Management** \> **Packages**, and then select **Create Package**.

5. Enter the following information to create the package:
   -   Name: **SRS v2 – OS Updates Package**
   -   Manufacturer: **Microsoft Corporation**
   -   Version: **1.0.0**
   -   Select the **This package contains source files** check box, enter the path to the **SRS v2 - OS Updates Package** folder, and then select **Next**.

6. Select **Do not create a program**, and then select **Next**.

7. Review the **Confirm the settings** page, and then select **Next**.

8. Select **Close**.

### Create the root certificate package (optional)

You create this package to distribute the root certificate for devices that won’t be joined to an Active Directory domain. Create this package only if both the following conditions apply:
-   Your deployment includes on-premises Lync or Skype for Business Server.
-   Microsoft Teams Rooms units are configured to work in a workgroup instead of
    a domain member.

1.  Copy the root certificate into the **SRS v2 – Root Certificate Package** folder.

2.  In the Configuration Manager console, go to **Software Library** \> **Application Management** \> **Packages**, and then select **Create Package**.

3.  Enter the following information to create the package:
    -   Name: **SRS v2 – Root Certificate Package**
    -   Manufacturer: *Your organization’s name*
    -   Version: **1.0.0**
    -   Select the **This package contains source files** check box, enter the path to the **SRS v2 – Root Certificate Package** folder, and then select **Next**.

4.  Select **Do not create a program**, and then select **Next**.

5.  Review the **Confirm the settings** page, and then select **Next**.

6.  Select **Close**.

### Create the Microsoft Teams Rooms deployment kit package

1.  Download the latest version of the **Microsoft Teams Rooms deployment kit** from <https://go.microsoft.com/fwlink/?linkid=851168>, and install it to a workstation.

2.  Copy the content from **C:\\Program Files (x86)\\Skype Room System Deployment Kit** to the **SRS v2 - SRS Application Package** folder.

3.  In the Configuration Manager console, go to **Software Library** \> **Application Management** \> **Packages**, and then select **Create
    Package**.

4.  Enter the following information to create the package:
    -   Name: **SRS v2 – SRS Application Package**
    -   Manufacturer: **Microsoft Corporation**
    -   Version: **3.1.104.0** (enter the version of the downloaded installation file)
    -   Select the **This package contains source files** check box, enter the path to the **SRS v2 – SRS Application Package** folder, and then select **Next**.
5.  Select **Do not create a program**, and then select **Next**.

6.  Review the **Confirm the settings** page, and then select **Next**.

7.  Select **Close**.

### Create the computer name assignment package

1.  In the **SRS v2 - Set-SRSComputerName Package** folder, create a new HTML application named **Set-SRSComputerName.hta** .

2.  Copy the following script into the **Set-SRSComputerName.hta** file. Alternatively, you can download the Set-SRSComputerName.hta file from [here](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Skype/SfbOnline/downloads/Skype-Room-Systems-v2/SRS-v2-Configuration-Manager-Files.zip?raw=true).
    ```
    <!DOCTYPE HTML>
    <html>
    <head>
    <title>Set SRS Computer Name</title>
    <HTA:APPLICATION
      APPLICATIONNAME="Set SRS Computer Name"
      ID="SetSRSComputerName"
      VERSION="1.0"
      SCROLL="no"
      SINGLEINSTANCE="yes"
      WINDOWSTATE="maximize"
      MaximizeButton="no"
      MinimizeButton="no"
      SysMenu="no"
      ShowInTaskbar="no"
      Caption="no"
      />
    <style type="text/css">
    body {
    	background-color: #fdfeff;
    	color: darkblue;
    	font-family: Calibri;
    	font-size: 12pt;
    	margin: 4em 3em;
    }
    </style>
    </head>
    <script language="VBScript">
    Public strNewComputerName
    Sub GenerateComputerName()
    	strComputer = "."
    	Set objWMIService = GetObject("winmgmts:\\" & strComputer & "\root\cimv2")
    	Set colItems = objWMIService.ExecQuery("Select * from Win32_BIOS",,48)
    	For Each objItem in colItems
    		strSerialNumber = objItem.SerialNumber
    	Next
    	strNewComputerName = "SRS-"  & right(replace(strSerialNumber, "-","") ,10)
    	TextArea1.innerHTML = "The serial number of the device: " & strSerialNumber
    	strHTMLText = strHTMLText & "<br> Computer name to be assigned: <font color = red>" & strNewComputerName & "</font>"
    	strHTMLText = strHTMLText & "<br><br> Click Accept to use this as the computer name and continue deployment, or Change to set a new name."
    	strHTMLText = strHTMLText & "<p><input type=""button"" value=""Accept"" name = ""Accept_Button"" onclick=""SetComputerName"" />"
    	strHTMLText = strHTMLText & " <input type=""button"" value=""Change"" name = ""Change_Button"" onclick=""ChangeComputerName"" />"
    	TextArea2.innerHTML = strHTMLText
    End Sub

    Sub SetComputerName()
    	dim result
    	result = MsgBox("Computer Name to be assigned: " & strNewComputerName &vbcrlf & "Are you sure you want to continue?", 36)
    	If (result = vbYes) then
    		SET env = CreateObject("Microsoft.SMS.TSEnvironment")
    		env("OSDComputerName") = strNewComputerName
    		self.close
    	elseif (result = vbNo) then
    		Window_OnLoad
    	End If
    End Sub

    Sub UpdateComputerName()
    	strNewComputerName = newcomputername.value
    	if len(trim(strNewComputerName)) = 0 then
    		MsgBox "Computer name cannot be empty." &vbcrlf & "Update and try again.",16
    		exit sub
    	end if
    	SetComputerName
    End Sub

    Sub ChangeComputerName()
    	TextArea2.innerHTML = "<p>Type the new computer name and click Accept:  <input type=""text"" name=""newcomputername"" value =" & strNewComputerName & " />"
    	TextArea2.innerHTML = TextArea2.innerHTML & "<br><input type=""button"" value=""Update"" name = ""Update_Button"" onclick=""UpdateComputerName"" />"
    End Sub

    Sub Window_OnLoad
    	Set oTSProgressUI = CreateObject("Microsoft.SMS.TsProgressUI")
    	oTSProgressUI.CloseProgressDialog
    	GenerateComputerName
    End Sub
    </script>

    <body>
    <span id = "TextArea1"></span>
    <span id = "TextArea2">
    </span>
    </body>
    </html>

    ```
3.  In the Configuration Manager console, go to **Software Library** \> **Application Management** \> **Packages**, and then select **Create Package**.

4.  Enter the following information to create the package:

    -   Name: **SRS v2 - Set-SRSComputerName Package**

    -   Manufacturer: **Microsoft Corporation**

    -   Version: **1.0.0**

    -   Select the **This package contains source files** check box, enter the path to the **SRS v2 - Set-SRSComputerName Package** folder, and then select **Next**.

5.  Select **Do not create a program**, and then select **Next**.

6.  Review the **Confirm the settings** page, and then select **Next**.

7.  Select **Close**.

### Create the Sysprep package

1. In the **SRS v2 – Sysprep Package** folder, create a new XML file named **Unattend.xml** .

2. Copy the following text into the **Unattend.xml** file. Alternatively, you can download the Unattend.xml file from [here](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Skype/SfbOnline/downloads/Skype-Room-Systems-v2/SRS-v2-Configuration-Manager-Files.zip?raw=true).
   ```
   <?xml version="1.0" encoding="utf-8"?>
   <unattend xmlns="urn:schemas-microsoft-com:unattend">
   <settings pass="specialize">
       <component name="Microsoft-Windows-Embedded-BootExp" processorArchitecture="amd64" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="NonSxS" xmlns:wcm="https://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
           <DisableBootMenu>1</DisableBootMenu>
           <DisplayDisabled>1</DisplayDisabled>
       </component>
       <component name="Microsoft-Windows-powercpl" processorArchitecture="amd64" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" xmlns:wcm="https://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
           <PreferredPlan>8c5e7fda-e8bf-4a96-9a85-a6e23a8c635c</PreferredPlan>
       </component>
   </settings>
   <settings pass="oobeSystem">
       <component name="Microsoft-Windows-Shell-Setup" processorArchitecture="amd64" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" xmlns:wcm="https://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
           <OOBE>
               <HideEULAPage>true</HideEULAPage>
               <HideLocalAccountScreen>true</HideLocalAccountScreen>
               <HideOEMRegistrationScreen>true</HideOEMRegistrationScreen>
               <HideOnlineAccountScreens>true</HideOnlineAccountScreens>
               <HideWirelessSetupInOOBE>true</HideWirelessSetupInOOBE>
               <SkipMachineOOBE>true</SkipMachineOOBE>
               <SkipUserOOBE>true</SkipUserOOBE>
               <ProtectYourPC>1</ProtectYourPC>
           </OOBE>
           <AutoLogon>
               <Enabled>true</Enabled>
               <Username>Skype</Username>
               <Password>
                   <Value>UABhAHMAcwB3AG8AcgBkAA==</Value>
                   <PlainText>false</PlainText>
               </Password>
           </AutoLogon>
           <UserAccounts>
               <LocalAccounts>
                   <LocalAccount wcm:action="add">
                       <Password>
                           <Value>cwBmAGIAUABhAHMAcwB3AG8AcgBkAA==</Value>
                           <PlainText>false</PlainText>
                       </Password>
                       <Name>Admin</Name>
                       <Group>Administrators</Group>
                       <DisplayName>Administrator</DisplayName>
                       <Description>Administrator</Description>
                   </LocalAccount>
               </LocalAccounts>
           </UserAccounts>
       </component>
   </settings>
   <cpi:offlineImage cpi:source="wim:h:/install.wim#Windows 10 Enterprise" xmlns:cpi="urn:schemas-microsoft-com:cpi" />
   </unattend>
   ```
3. In the Configuration Manager console, go to **Software Library** \> **Application Management** \> **Packages**, and then select **Create Package**.

4. Enter the following information to create the package:
   -   Name: **SRS v2 - Sysprep Package**
   -   Manufacturer: **Microsoft Corporation**
   -   Version: **1.0.0**
   -   Select the **This package contains source files** check box, enter the path to the **SRS v2 – Sysprep Package** folder, and then select **Next**.
5. Select **Do not create a program**, and then select **Next**.

6. Review the **Confirm the settings** page, and then select **Next**.

7. Select **Close**.

### Create the Windows 10 Enterprise package

1.  Obtain a Windows 10 Enterprise x64 media, and copy the **install.wim** file to the **Operating Systems\\Windows 10 Enterprise** folder.

2.  In the Configuration Manager console, go to **Software Library** \> **Operating Systems** \> **Operating System Images**, and then select **Add Operating System Image**.

3.  Specify the path to the **install.wim** file you just copied, and then select **Next**.

4.  Update the **Version** field to match the build number of the Windows 10 Enterprise image, and then select **Next**.

5.  Review the **Details** page, and then select **Next**.

6.  Select **Close**.

For more information, see [Manage operating system images with System Center Configuration Manager](https://docs.microsoft.com/sccm/osd/get-started/manage-operating-system-images).

### Create Surface Pro device driver packages

Microsoft Teams Rooms is supported for both Surface Pro and Surface Pro 4. You need to create a driver package for each Surface Pro model you have in your environment.

> [!IMPORTANT]
> The drivers must be compatible with the Windows 10 Enterprise build and the Microsoft Teams Rooms deployment kit version. For more information, see [Download the latest firmware and drivers for Surface devices](https://docs.microsoft.com/surface/deploy-the-latest-firmware-and-drivers-for-surface-devices) and [Configure a console](console.md).

1.  Download the latest drivers and firmware.
    -   For Surface Pro:
        <https://www.microsoft.com/download/details.aspx?id=55484>
    -   For Surface Pro 4:
        <https://www.microsoft.com/download/details.aspx?id=49498>

2.  Extract the downloaded driver and firmware. Open a Command Prompt window and at the command prompt, enter one of the following commands:
    -   `msiexec /a C:\SurfacePro_Win10.msi /passive TARGETDIR="C:\_Sources\\Drivers\Surface Pro"`
    -   `msiexec /a C:\SurfacePro4_Win10.msi /passive TARGETDIR="C:\_Sources\\Drivers\Surface Pro 4"`

3.  In the Configuration Manager console, go to **Software Library** \> **Operating Systems** \> **Drivers**, and then select **Import Driver**.

4.  Select **Import all drivers in the following network path (UNC)**, select the source folder (for example, C:\\_Sources\\Drivers\\Surface Pro), and then select **Next**.

5.  On the **Specify the details for the imported drivers** page, select all the listed drivers, and then select **Enable these drivers and allow computers to install them**.

6.  Select **Categories**, create a new category that matches the Surface model, select **OK**, and then select **Next**.

7.  Select **New Package**.

8.  Specify the package name that matches the Surface Pro model, enter a folder path to store the driver package files in, select **OK**, and then select **Next**.

9.  On the **boot images** page, ensure that no boot images are selected, and then select **Next**.

10. Select **Close**.

11. Go to **Software Library** \> **Operating Systems** \> **Drivers**, select **Folder \> Create Folder**, and enter a folder name that matches the Surface Pro model that you just imported the drivers for.

12. Move all the imported drivers to the newly created folder for easier navigation and operation.

> [!NOTE]
> Repeat the same steps for other Surface Pro models you might have. For more information, see [Manage drivers in System Center Configuration Manager](https://docs.microsoft.com/sccm/osd/get-started/manage-drivers).

### Create Microsoft Teams Rooms Configuration Package

1.  In the Configuration Manager console, go to **Software Library** \> **Application Management** \> **Packages**, and then select **Create Package**.

2.  Enter the following information to create the package:

    -   Name: **SRS v2 - Configure SRS Setup Package**

    -   Manufacturer: **Microsoft Corporation**

    -   Version: **1.0.0**

    -   Select the **This package contains source files** check box, enter the path to the **SRS v2 - Configure SRS Setup** folder, and then select **Next**.

3.  Select **Do not create a program**, and then select **Next**.

4.  Review the **Confirm the settings** page, and then select **Next**.

5.  Select **Close**.



## Distribute Configuration Manager packages

All the packages must be distributed to the servers that have been assigned the distribution point role in the Configuration Manager hierarchy. Follow the instructions below to initiate package distribution.

1.  Distribute software packages.

    1.  In the Configuration Manager console, go to **Software Library** \> **Application Management** \> **Packages**. Select all the software packages you want to distribute, and then select **Distribute Content**.

    2.  Review the list of packages, and then select **Next**.

    3.  Add all the distribution point servers (or distribution point groups, depending on your Configuration Manager hierarchy) to the list, and then select **Next**.

    4.  Select **Next**, and then select **Close**.

2.  Distribute driver packages.

    1.  In the Configuration Manager console, go to **Software Library** \> **Operating Systems** \> **Driver Packages**. Select all the driver packages you want to distribute, and then select **Distribute Content**.

    2.  Review the list of packages, and then select **Next**.

    3.  Add all the distribution point servers (or distribution point groups, depending on your Configuration Manager hierarchy) to the list, and then select **Next**.

    4.  Select **Next**, and then select **Close**.

3.  Distribute operating system packages.

    1.  In the Configuration Manager console, go to **Software Library** \> **Operating Systems** \> **Operating System Images**. Select all the operating system images you want to distribute, and then select **Distribute Content**.

    2.  Review the list of packages, and then select **Next**.

    3.  Add all the distribution point servers (or distribution point groups, depending on your Configuration Manager hierarchy) to the list, and then select **Next**.

    4.  Select **Next**, and then select **Close**.

> [!NOTE]
> Package distribution might take some time, depending on the package size, Configuration Manager hierarchy, number of distribution point servers, and the bandwidth available in your network.
> 
> All the packages must be distributed before you can start deploying a Microsoft Teams Rooms unit.
> 
> You can review the status of your package distribution in the Configuration Manager console by going to **Monitoring** \> **Distribution Status** \> **Content Status**.

## Configuration Manager task sequences

You use task sequences with System Center Configuration Manager to automate the steps for deploying an operating system image to a destination computer. To deploy a Microsoft Teams Rooms unit in an automated fashion, you create a task sequence that references the boot image used to start the destination Microsoft Teams Rooms computer, the Windows 10 Enterprise operating system image that you want to install, and any other additional content, such as other applications or software updates.

### Import the sample task sequence

You can download and easily import a sample task sequence and customize it to meet your needs.

1.  [**Download**](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Skype/SfbOnline/downloads/Skype-Room-Systems-v2/SRS-v2-Configuration-Manager-Files.zip?raw=true) the sample task sequence, and copy the downloaded zip file to a
    shared location.
2.  In the Configuration Manager console, go to **Software Library** \> **Operating Systems** \> **Task Sequences**, and then select **Import Task Sequence**.

3.  Select **Browse**, go to the shared folder location you used in step 1, select the **Microsoft Teams Rooms Deployment (EN-US).zip** file, and then select **Next**.

4.  Set **Action** to **Create New**, and then select **Next**.

5.  Confirm the settings, and then select **Next**.

6.  Select **Close**.

### Validate that the reference packages are correctly linked to each task sequence step.

1. Select the imported task sequence, and then select **Edit**.

    The Task Sequence Editor opens and displays each sequential step that you need to deploy and configure a Microsoft Teams Rooms unit.

2. Walk through each step and complete the recommended updates:

   1. **Restart in Windows PE**: This step restarts and then boots the computer into Windows PXE. No changes are required for this step.

   2. **Partition Disk 0 – UEFI**: This step wipes the disk configuration and creates partitions based on the configured settings. We recommend that you not make any changes to this step.

   3. **Set SRS Computer Name**: This step includes an HTML application to provide a UI to set a computer name for the Microsoft Teams Rooms unit during the deployment.
      -  This is an optional step, but it can only be disabled if you want to manage computer naming through an alternate process.
      -  Verify that the **SRS v2 - Set-SRSComputerName** package is selected. If it isn’t, browse to the package and select it.

   4. **Apply Operating System**: This step specifies the operating system image to be deployed and the unattended Sysprep answer file to use.
      -  Verify that the correct Windows 10 Enterprise operating system image file is selected.
      -  Verify that **Use an unattended or Sysprep answer file for a custom installation** is enabled, and the **SRS v2 - Sysprep Package** is selected. Also ensure that **File Name** is set to **unattend.xml**.

   5. **Apply Windows Settings**: This step gathers information about the Windows installation.
      -  Provide licensing and registration information including the product key, local administrator account password, and time zone (depending on your needs).

   6. **Apply Network Settings**: This step allows you to specify a workgroup or Active Directory domain name and organizational unit.
      > [!NOTE]
      > See [Skype Room System domain joining considerations](domain-joining-considerations.md) for recommended actions you need to take in deploying Microsoft Teams Rooms units as members of an Actve Directory domain.
   7. **Apply Drivers:** This step and its sub-steps are used to deploy applicable device drivers and firmware based on the Surface Pro model you have. Update each step to specify the relevant driver package associated with this deployment.
      -   Each driver package is configured to leverage Windows Management Instrumentation (WMI) filters to deploy relevant drivers and firmware based on the Surface Pro make and model.
      -   We highly recommend that you not alter the configuration of these drivers, otherwise deployment might fail.

   8. **Set up Windows and Configuration Manager**: This step deploys and configures the Configuration Manager client. Update this step to specify the built-in Configuration Manager Client Package.

   9. **Install Root Certificate**: This step distributes the root certificate for non–domain-joined devices, and therefore is optional and disabled by default.
      -   Enable this step if you need to deploy a root certificate to the Microsoft Teams Rooms units.
      -   If you do need to perform this step, verify that the **SRS v2 – Root Certificate Package** and **Disable 64-bit file system redirection** are selected.

   10. **Install and Configure Monitoring Agent**: This step installs the 64-bit version of the Microsoft Azure Monitor agent and configures the agent to connect to your Log Analytics workspace.
       -   This step is disabled by default. Enable this step only if you’re going to use the Monitoring Agent to monitor the health of your Microsoft Teams Rooms units.
       -   Edit this step and update the command-line parameters to specify your **Workspace ID** and **Workspace Key**.
       -   See [Configure test devices for Azure Monitoring](azure-monitor.md#configure-test-devices-for-azure-monitoring) for more information about obtaining the Operations Management Suite Workspace ID and the primary key.
       -   Verify that the **SRS v2 – Microsoft Monitoring Agent Package** and **Disable 64-bit file system redirection** are selected.
       -   For more information about monitoring the health of your Microsoft Teams Rooms deployment, see [Plan Microsoft Teams Rooms management with Azure Monitor](../../plan-your-deployment/clients-and-devices/azure-monitor.md), [Deploy Microsoft Teams Rooms management with Azure Monitor](azure-monitor.md) and [Manage Microsoft Teams Rooms devices with Azure Monitor](../../manage/skype-room-systems-v2/azure-monitor.md).

   11. **Copy SRS v2 Configuration Files**: This step copies the required setup and configuration files from the Microsoft Teams Rooms deployment kit to the local hard drive. No customization is required for this step.
       -   Verify that the **SRS v2 – SRS Application Package** and **Disable 64-bit file system redirection** are selected.

   12. **Install-SRSv2-OS-Updates**: This step deploys any mandatory operating system updates required with the Microsoft Teams Rooms deployment. Do the following:
       -   Check [Configure a Microsoft Teams Rooms console](console.md) to see which updates are required.
       -   Verify that your **SRS v2 – OS Updates Package** includes all the required updates.
       -   Verify that the **SRS v2 – OS Updates Package** is selected.
       -   Verify that the PowerShell execution policy is set to **Bypass**.

   13. **Restart Computer**: This step reboots the computer after the mandatory operating system updates are installed. No customization is required for this step.

   14. **Configure Windows Components**: This step configures the required Windows features. No customization is required for this step.

   15. **Restart Computer**: This step reboots the computer after the Windows features are configured. No customization is required for this step.

   16. **Add Local Skype User**: This step creates the local Skype account used to automatically sign in to Windows and start the Microsoft Teams Rooms application. This step doesn’t have any software package associated with it, and no customization is required for it.

   17. **Set up and configure SRS application**: This step configures the Microsoft Teams Rooms application installation for the next boot of the operating system.
       -   Verify that the **SRS v2 – Configure SRS Setup Package** and **Disable 64-bit file system redirection** are selected.

> [!IMPORTANT]
> It is very important that the task sequence steps must be in the provided order. Modifying the order of steps, or configuring additional steps might break the deployment.
>
> **Set up and configure SRS application** step must be the last step in the task sequence, otherwise the deployment might fail.

### Create deployment for the task sequence

1. Select the task sequence, and then select **Deploy**.

2. Select **Browse** to select target collection for deployment.

3. Select **All Unknown Computers** and then select **OK**.

4. Select **Next**.

5. Select **Available** on the **Purpose** drop down list.

6. Select **Only Media and PXE** in the **Make available to the following**
   list, and then select **Next**.
   > [!WARNING]
   > It is very important that **Purpose** is set to **Available**. Make sure that
   the **Purpose** is **NOT** set to **Required**. Also make sure that you select **Only Media and PXE** in the **Make available to the following**.
   >
   > Setting these values to something else might cause all computers to get the Microsoft Teams Rooms deployment image when booted.
7. Do not specify any schedule and select **Next**.

8. Do not change anything within the **User Experience** section and select
   **Next**.

9. Do not change anything within the **Alerts** section and select **Next**.

10. Do not change anything within the **Distribution Points** section and select
    **Next**.

11. Confirm the settings and then select **Next**.

12. Select **Close**.

Validate and troubleshoot the solution
--------------------------------------

After you’ve completed the System Center Configuration Manager task sequences, you’ll need to perform a test run to validate that the task sequence can deploy and configure Microsoft Teams Rooms units.

1.  Connect the test device to the wired network by using one of the supported Ethernet adapters or using the Surface dock. If PXE boot functionality hasn’t been configured for your environment, you can use the boot image on the USB flash drive [that you created earlier](https://docs.microsoft.com/sccm/osd/deploy-use/create-bootable-media) to boot from USB and connect to Configuration Manager.

2.  Access the firmware and initiate PXE boot:

    1.  Ensure the Surface device is powered off.

    2.  Press and hold the **Volume Up** button.

    3.  Press and release the **Power** button.

    4.  After the device begins to boot, release the **Volume Up** button.

    5.  Select **Boot configuration**.

    6.  Do one of the following:

        -   Select **PXE boot**, and drag it to the top of the list. Alternatively, you can swipe left on the network adapter to boot to the device immediately. This won’t affect the boot order.
        -   Select the USB flash drive that holds the boot media.

3.  Select **Exit**, and then select **Restart Now**.

4.  When prompted, select **Enter** for network boot service.

5.  Windows PE will load into memory, and the Task Sequence Wizard will start. Select **Next** to continue.

6.  Select the task sequence that you imported earlier, and then select **Next**.

7.  After the disk configuration is applied, you’ll be prompted to specify a computer name for the device. The user interface will display a recommended computer name based on the serial number of the Surface Pro device. You can either accept the proposed name or specify a new one. Follow the instructions on the computer name assignment screen. When you select **Accept**, the deployment begins.

8.  The rest of the deployment process is automatic and doesn’t ask for any more user input.

9.  After the deployment task sequence finishes configuring the device, you’ll see the following configuration screen that asks you to configure the Microsoft Teams Rooms application settings.

    ![Initial setup screen for Microsoft Teams Rooms application](../../media/room-systems-scale-image2.png)

10.  Plug the Surface Pro into the Microsoft Teams Rooms console, and configure the application settings.

11.  Validate that the capabilities listed in [Microsoft Teams Rooms help](https://support.office.com/article/Skype-Room-Systems-version-2-help-e667f40e-5aab-40c1-bd68-611fe0002ba2) are working on the deployed device.


To troubleshoot a failed installation, check the **SMSTS.log** file, which logs all the steps executed in a Configuration Manager task sequence.

The SMSTS.log file is stored on one of a number of paths, depending on the stage of the build process. Check the following table to identify the path to the SMSTS.log file.


| **Deployment phase**                                                            | **Task sequence log path**                         |
|---------------------------------------------------------------------------------|----------------------------------------------------|
| WinPE, before HDD format                                                        | X:\\Windows\\Temp\\smstslog\\smsts.log             |
| WinPE, after HDD format                                                         | C:\\_SMSTaskSequence\\Logs\\Smstslog\\smsts.log    |
| Operating system deployed, before the Configuration Manager agent was installed | c:\\_SMSTaskSequence\\Logs\\Smstslog\\smsts.log    |
| Operating system and the Configuration Manager agent deployed                   | %windir%\\System32\\ccm\\logs\\Smstslog\\smsts.log |
| Task sequence execution complete                                                | %windir%\\System32\\ccm\\logs\\smsts.log           |

> [!TIP]
> You can select **F8** at any time during the task sequence to open a command console, and then get access to the SMSTS.log file.

To troubleshoot PXE boot issues, check the two log files on the Configuration Manager server that are specific to PXE actions:

-   **Pxecontrol.log**, located in the Configuration Manager installation logs directory

-   **Smspxe.log**, located in Configuration Manager Management Point (MP) logs directory

For a complete list of the log files that you can use to further troubleshoot your Configuration Manager installation, see [Log files in System Center Configuration Manager](https://docs.microsoft.com/sccm/core/plan-design/hierarchy/log-files).
