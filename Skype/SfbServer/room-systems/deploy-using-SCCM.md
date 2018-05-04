Deploy Skype Room Systems v2 mass deployment guide
==================================================

This article provides all the required information to assist you create your
Skype Room Systems v2 deployments using System Center Configuration Manager.

System Center Configuration Manager allows you to create operating system
deployments and it provides easy to use methods to deploy the operating system
and other applications to multiple target devices.

Configuration Guide
===================

We provide the following approach to guide you through your Configuration
Manager configuration and provide sample packages and scripts for you to
leverage. The rest of this guidance will discuss each stage in more detail.

**Note/Important**

This solution is tested only with Surface Pro based deployments. Follow the
manufacturers guidelines for non-Surface Pro based configurations.

GRAPHIC HERE

Validate pre-requisites
-----------------------

You need to ensure the following prerequisites and requirements are met in order
to deploy Skype Room Systems v2 with Configuration Manager.

### System Center Configuration Manager requirements

-   System Center Configuration Manager version MUST be at least 1706 or above.
    Note: 1710 or later is recommended. Check out [Support for Windows 10 in
    System Center Configuration
    Manager](https://docs.microsoft.com/sccm/core/plan-design/configs/support-for-windows-10#windows-10-as-a-client)
    to learn about the Windows 10 versions that Configuration Manager supports.

-   A supported version of Windows Assessment and Deployment Kit (ADK) for
    Windows 10 MUST be installed. See the versions of the [Windows 10
    ADK](https://docs.microsoft.com/sccm/core/plan-design/configs/support-for-windows-10#windows-10-adk)
    that you can use with different versions of Configuration Manager and ensure
    your deployment includes the correct version.

-   The Site System Servers that hold the distribution point role, and the boot
    images should be enabled for [PXE
    support](https://docs.microsoft.com/sccm/osd/deploy-use/use-pxe-to-deploy-windows-over-the-network)
    to enable network-initiated deployments. Alternatively, you can use
    [bootable
    media](https://docs.microsoft.com/sccm/osd/deploy-use/use-bootable-media-to-deploy-windows-over-the-network)
    for your deployments, if PXE support is not enabled.

-   A network access account MUST be configured to support bare metal deployment
    scenarios. To learn more about the configuration of a network access
    account, see [Manage accounts to access content in System Center
    Configuration
    Manager](https://docs.microsoft.com/sccm/core/plan-design/hierarchy/manage-accounts-to-access-content#bkmk_NAA).

-   Recommended to enable [multicast
    support](https://docs.microsoft.com/sccm/osd/deploy-use/use-multicast-to-deploy-windows-over-the-network),
    if multiple SRS units are likely to deploy the same image at the same time.

### Networking requirements

-   Your network should have a Dynamic Host Configuration Protocol (DHCP)
    server, configured for automatic IP address distribution to the subnets
    where Skype Room Systems v2 units will be deployed.

    -   DHCP lease duration MUST be set to a value longer than the image
        deployment duration. Otherwise, the deployment might fail.

-   Your network, including switches and VLANs should be configured to support
    PXE. Refer to your network vendor for more details on IP helper and PXE
    configuration. Alternatively, you can use [bootable
    media](https://docs.microsoft.com/sccm/osd/deploy-use/use-bootable-media-to-deploy-windows-over-the-network)
    for your deployments, if PXE support is not enabled.

**Note**

For Surface Pro devices, booting from the network (PXE boot) is only supported
when you use an Ethernet adapter or docking station from Microsoft. Third party
ethernet adapters do not support PXE boot with Surface Pro. See [Ethernet
adapters and Surface
deployment](https://docs.microsoft.com/surface/ethernet-adapters-and-surface-device-deployment)
for details.

Configure System Center Configuration Manager for Operating System Deployment
-----------------------------------------------------------------------------

This article assumes you already have a healthy deployment of a System Center
Configuration Manager and will not detail all the steps required to deploy and
configure Configuration Manager from scratch. The [documentation and the
configuration guidance](https://docs.microsoft.com/sccm/) on the System Center
Configuration Manager is a great resource to find out more about Configuration
Manager. We recommend start with these resources if you need to deploy
Configuration Manager.

Use the following instructions to verify and configure the operating system
deployment (OSD) features are configured properly:

### Validate and upgrade Configuration Manager

1.  In the Configuration Manager console, navigate to **Administration** –
    **Updates and Servicing**.

2.  Check the installed build and applicable updates that are not installed yet.

3.  Review [Support for Windows 10 in System Center Configuration
    Manager](https://docs.microsoft.com/sccm/core/plan-design/configs/support-for-windows-10#windows-10-as-a-client)
    and if you need to upgrade your deployment, select the update you want to
    install and select **Download**.

4.  After the download is completed, select the update and select **Install
    Update Pack**.

### Configure Distribution Points to support PXE and multicast

1.  In the Configuration Manager console, navigate to **Administration** –
    **Distribution Points**.

2.  Select the distribution point server, that will serve the Skype Room Systems
    v2 deployment and then select **Properties**.

3.  Select **PXE** tab and ensure the following settings are enabled:

    1.  Enable PXE support for clients

    2.  Allow this distribution point to respond to incoming PXE requests

    3.  Enable unknown computer support

4.  *Optional:* To enable multicast support, select **Multicast** tab and ensure
    the following settings are enabled:

    1.  Enable multicast to simultaneously send data to multiple client

    2.  Configure the UDP port range as per your network team’s recommendation

### Configure Network Access Account

1.  In the Configuration Manager console, navigate to **Administration** –
    **Site Configuration** – **Sites**, and then select the site.

2.  On the **Settings** group, select **Configure Site Components** – **Software
    Distribution**.

3.  Select the **Network Access Account** tab. Set up one or more accounts, and
    then select **OK**. The accounts do not need any special rights, except for
    the **Access this computer from the network** right on the distribution
    point server. A generic domain user account will be appropriate.

For more details, see [Manage accounts to access content in System Center
Configuration
Manager](https://docs.microsoft.com/sccm/core/plan-design/hierarchy/manage-accounts-to-access-content#bkmk_NAA).

### Configure Boot Image

1.  In the Configuration Manager console, navigate to **Software Library** –
    **Operating System** – **Boot Images**.

2.  Select the **Boot image (x64)** and select **Properties**.

3.  Select **Data Source** tab and enable **Deploy this boot image from the
    PXE-enabled distribution point**.

4.  Select **Optional Components** tab to install required components.

    1.  Select the star icon and search for HTML (WinPE-HTA)

    2.  Select OK to add HTML Application support in to the boot image.

5.  Optional: to specify customizations select **Customization** tab.

    1.  Enable **command support (testing only)** if you want to have access to
        a command prompt during the deployment. When enabled, you can start a
        command prompt by pressing F8 at any time during the deployment.

    2.  You may also specify a custom background image to be displayed during
        the deployment. To set an image, enable **Specify the custom background
        image file (UNC path** and select your background.

6.  When asked, select **Yes** and distribute the updated boot image to your
    distribution points.

For more details, see [Manage boot images with System Center Configuration
Manager](https://docs.microsoft.com/sccm/osd/get-started/manage-boot-images).

Note

You can create a bootable USB media to initiate Configuration Manager task
sequence-based deployments for the environments with no PXE support. The
bootable media contains only the boot image, optional prestart commands and
their required files, and Configuration Manager binaries to support booting into
Windows PE and connect to Configuration Manager for the rest of the deployment
process. For more details, see [How to Create Bootable
Media](https://docs.microsoft.com/sccm/osd/deploy-use/create-bootable-media#BKMK_CreateBootableMedia).

Create Configuration Manager Packages
-------------------------------------

Configuration Manager requires a number of packages to deploy and configure the
Skype Room System v2 units.

You need to create and configure the following packages and then distribute to
the Configuration Manager site systems running distribution point role.

| **Package name**                     | **Type**               | **Description**                                                                        |
|--------------------------------------|------------------------|----------------------------------------------------------------------------------------|
| SRS v2 - SRS Application Package     | Software Package       | Package for the Skype Room Systems v2 deployment kit                                   |
| SRS v2 - Sysprep Package             | Software Package       | Package that holds the custom Unattended.xml to configure Skype Room Systems v2 units  |
| SRS v2 - Set-SRSComputerName Package | Software Package       | Package for the HTML application (HTA) to assign a computer name during the deployment |
| SRS v2 - OS Updates Package          | Software Package       | Package to deploy mandatory Operating System updates                                   |
| SRS v2 - Root Certificate Package    | Software Package       | Package to deploy root certificate. Not required for domain joined units               |
| SRS v2 - Microsoft OMS Agent Package | Software Package       | Package to deploy and configure Microsoft Operations Management Suit agent.            |
| SRS v2 - WinPE Background Package    | Software Package       | Package that hold the custom background image to use with boot images.                 |
| Windows 10 Enterprise                | Operating System Image | Package that holds the operating system installation file (install.wim)                |
| Surface Pro                          | Driver Package         | Package that holds the device drivers and firmware for Microsoft Surface Pro.          |
| Surface Pro 4                        | Driver Package         | Package that holds the device drivers and firmware for Microsoft Surface Pro 4.        |

For more details, see [Packages and programs in System Center Configuration
Manager](https://docs.microsoft.com/sccm/apps/deploy-use/packages-and-programs).

### Create the folders for the package source files

Configuration Manager requires package source folders during the initial package
creation and whenever a package source needs to be updated.

You need to create the following folder structure on the System Center
Configuration Manager Central Administration or Primary Site, or on a server
share to use to host package source files:

-   SRS v2 - Microsoft OMS Agent Package

-   SRS v2 - OS Updates Package

-   SRS v2 - Root Certificate Package

-   SRS v2 - Set-SRSComputerName Package

-   SRS v2 - SRS Application Package

-   SRS v2 - Sysprep Package

-   Drivers

    -   Surface Pro

    -   Surface Pro 4

-   Operating Systems

    -   Windows 10 Enterprise

### Create the Microsoft Operations Management Suite agent package

1.  Download the Operations Management Suite X-64 agent from
    <https://go.microsoft.com/fwlink/?LinkId=828603>

2.  Extract the package into SRS v2 - Microsoft OMS Agent Package folder by
    executing MMASetup-AMD64.exe /C: from a command prompt.

3.  In the Configuration Manager console, navigate to **Software Library** –
    **Application Management** – **Packages**, and then select **Create
    Package**.

4.  Use the following information to create the package.

    1.  **Name:** SRS v2 - Microsoft OMS Agent Package

    2.  **Manufacturer:** Microsoft Corporation

    3.  **Version:** 8.1.11081.0 (Provide the version of the downloaded
        installation file)

    4.  Select **This package contains source files** and provide path to the
        **SRS v2 - Microsoft OMS Agent Package** folder and select **Next**.

5.  Select **Do not create a program** and select **Next**.

6.  Review the **Confirm the settings page** and select **Next**.

7.  Select **Close**.

### Create the operating system updates package

1.  Create a new PowerShell script named **Install-SRSv2-OS-Updates.ps1** in the
    **SRS v2 - OS Updates Package** folder.

2.  Copy the script below into the **Install-SRSv2-OS-Updates.ps1** script.

>   \# Install-SRSv2-OS-Updates.ps1

>   \$strPath = split-path -parent \$MyInvocation.MyCommand.Definition

>   \$total = gci \$strPath \*.msu \| measure \| Select-Object -expand Count

>   \$i = 0

>   gci \$strPath \*.msu \| ForEach-Object {

>   \$i++

>   WUSA ""\$_.FullName /quiet /norestart""

>   Write-Progress -activity "Applying Mandatory Updates" -status "Installing
>   \$\_ .. \$i of \$total" -percentComplete ((\$i / \$total) \* 100)

>   Wait-Process -name wusa

>   }

1.  Download the mandatory Windows Update packages into the same folder. At the
    time this guide is developed, only
    [KB4056892](http://download.windowsupdate.com/c/msdownload/update/software/secu/2018/01/windows10.0-kb4056892-x64_a41a378cf9ae609152b505c40e691ca1228e28ea.msu)
    is required. Check [Configure a Skype Room Systems v2
    console](https://docs.microsoft.com/skypeforbusiness/deploy/deploy-clients/console),
    to see if there are any other update required.

2.  In the Configuration Manager console, navigate to **Software Library** –
    **Application Management** – **Packages**, and then select **Create
    Package**.

3.  Use the following information to create the package.

    1.  **Name:** SRS v2 – OS Updates Package

    2.  **Manufacturer:** Microsoft Corporation

    3.  **Version:** 1.0.0

    4.  Select **This package contains source files** and provide path to the
        **SRS v2 - OS Updates Package** folder and select **Next**.

4.  Select **Do not create a program** and select **Next**.

5.  Review the **Confirm the settings page** and select **Next**.

6.  Select **Close**.

### Create the root certificate package

**Note**

This package is to distribute the root certificate for the devices that will not
be joined to an Active Directory domain, and therefore it is optional. Create
this package only if all the conditions below are applicable.

-   Your deployment has on-premises Lync or Skype for Business Server

-   Skype Room Systems v2 units are configured to work in workgroup instead of a
    domain member.

1.  Copy the root certificate into the **SRS v2 – Root Certificate Package**
    folder.

2.  In the Configuration Manager console, navigate to **Software Library** –
    **Application Management** – **Packages**, and then select **Create
    Package**.

3.  Use the following information to create the package.

    1.  **Name:** SRS v2 – Root Certificate Package

    2.  **Manufacturer:** Your organizations name

    3.  **Version:** 1.0.0

    4.  Select **This package contains source files** and provide path to the
        **SRS v2 – Root Certificate Package** folder and select **Next**.

4.  Select **Do not create a program** and select **Next**.

5.  Review the **Confirm the settings page** and select **Next**.

6.  Select **Close**.

### Create the Skype Room Systems v2 deployment kit package

1.  Download the latest version of the **Skype Room Systems v2 deployment kit**
    from <https://go.microsoft.com/fwlink/?linkid=851168> and install to a
    workstation.

2.  Copy the content from **C:\\Program Files (x86)\\Skype Room System
    Deployment Kit** to **SRS v2 - SRS Application Package** folder.

3.  In the Configuration Manager console, navigate to **Software Library** –
    **Application Management** – **Packages**, and then select **Create
    Package**.

4.  Use the following information to create the package.

    1.  **Name:** SRS v2 – SRS Application Package

    2.  **Manufacturer:** Microsoft Corporation

    3.  **Version:** 3.1.104.0 (Provide the version of the downloaded
        installation file)

    4.  Select **This package contains source files** and provide path to the
        **SRS v2 – SRS Application Package** folder and select **Next**.

5.  Select **Do not create a program** and select **Next**.

6.  Review the **Confirm the settings page** and select **Next**.

7.  Select **Close**.

### Create the computer name assignment package

1.  Create a new HTML application named **Set-SRSComputerName.hta** in the **SRS
    v2 - Set-SRSComputerName Package** folder.

2.  Copy the script below into the **Set-SRSComputerName.hta** file.

>   \<!DOCTYPE HTML\>

>   \<html\>

>   \<head\>

>   \<title\>Set SRS Computer Name\</title\>

>   \<HTA:APPLICATION

>   APPLICATIONNAME="Set SRS Computer Name"

>   ID="SetSRSComputerName"

>   VERSION="1.0"

>   SCROLL="no"

>   SINGLEINSTANCE="yes"

>   WINDOWSTATE="maximize"

>   MaximizeButton="no"

>   MinimizeButton="no"

>   SysMenu="no"

>   ShowInTaskbar="no"

>   Caption="no"

>   /\>

>   \<style type="text/css"\>

>   body {

>   background-color: \#fdfeff;

>   color: darkblue;

>   font-family: Calibri;

>   font-size: 12pt;

>   margin: 4em 3em;

>   }

>   \</style\>

>   \</head\>

>   \<script language="VBScript"\>

>   Public strNewComputerName

>   Sub GenerateComputerName()

>   strComputer = "."

>   Set objWMIService = GetObject("winmgmts:\\\\" & strComputer &
>   "\\root\\cimv2")

>   Set colItems = objWMIService.ExecQuery("Select \* from Win32_BIOS",,48)

>   For Each objItem in colItems

>   strSerialNumber = objItem.SerialNumber

>   Next

>   strNewComputerName = "SRS-" & right(replace(strSerialNumber, "-","") ,10)

>   TextArea1.innerHTML = "The serial number of the device: " & strSerialNumber

>   strHTMLText = strHTMLText & "\<br\> Computer name to be assigned: \<font
>   color = red\>" & strNewComputerName & "\</font\>"

>   strHTMLText = strHTMLText & "\<br\>\<br\> Click Accept to use this as the
>   computer name and continue deployment, or Change to set a new name."

>   strHTMLText = strHTMLText & "\<p\>\<input type=""button"" value=""Accept""
>   name = ""Accept_Button"" onclick=""SetComputerName"" /\>"

>   strHTMLText = strHTMLText & " \<input type=""button"" value=""Change"" name
>   = ""Change_Button"" onclick=""ChangeComputerName"" /\>"

>   TextArea2.innerHTML = strHTMLText

>   End Sub

>   Sub SetComputerName()

>   dim result

>   result = MsgBox("Computer Name to be assigned: " & strNewComputerName
>   &vbcrlf & "Are you sure you want to continue?", 36)

>   If (result = vbYes) then

>   SET env = CreateObject("Microsoft.SMS.TSEnvironment")

>   env("OSDComputerName") = strNewComputerName

>   self.close

>   elseif (result = vbNo) then

>   Window_OnLoad

>   End If

>   End Sub

>   Sub UpdateComputerName()

>   strNewComputerName = newcomputername.value

>   if len(trim(strNewComputerName)) = 0 then

>   MsgBox "Computer name cannot be empty." &vbcrlf & "Update and try again.",16

>   exit sub

>   end if

>   SetComputerName

>   End Sub

>   Sub ChangeComputerName()

>   TextArea2.innerHTML = "\<p\>Type the new computer name and click Accept:
>   \<input type=""text"" name=""newcomputername"" value =" & strNewComputerName
>   & " /\>"

>   TextArea2.innerHTML = TextArea2.innerHTML & "\<br\>\<input type=""button""
>   value=""Update"" name = ""Update_Button"" onclick=""UpdateComputerName""
>   /\>"

>   End Sub

>   Sub Window_OnLoad

>   Set oTSProgressUI = CreateObject("Microsoft.SMS.TsProgressUI")

>   oTSProgressUI.CloseProgressDialog

>   GenerateComputerName

>   End Sub

>   \</script\>

>   \<body\>

>   \<span id = "TextArea1"\>\</span\>

>   \<span id = "TextArea2"\>

>   \</span\>

>   \</body\>

>   \</html\>

1.  In the Configuration Manager console, navigate to **Software Library** –
    **Application Management** – **Packages**, and then select **Create
    Package**.

2.  Use the following information to create the package.

    1.  **Name:** SRS v2 - Set-SRSComputerName Package

    2.  **Manufacturer:** Microsoft Corporation

    3.  **Version:** 1.0.0

    4.  Select **This package contains source files** and provide path to the
        **SRS v2 - Set-SRSComputerName Package** folder and select **Next**.

3.  Select **Do not create a program** and select **Next**.

4.  Review the **Confirm the settings page** and select **Next**.

5.  Select **Close**.

### Create the Sysprep package

1.  Create a new XML file named **Unattend.xml** in the **SRS v2 – Sysprep
    Package** folder.

2.  Copy the text below into the **Unattend.xml** file.

>   \<?xml version="1.0" encoding="utf-8"?\>

>   \<unattend xmlns="urn:schemas-microsoft-com:unattend"\>

>   \<servicing\>

>   \<package action="configure"\>

>   \<assemblyIdentity name="Microsoft-Windows-Foundation-Package"
>   version="10.0.15063.0" processorArchitecture="amd64"
>   publicKeyToken="31bf3856ad364e35" language="" /\>

>   \<selection name="Client-DeviceLockdown" state="true" /\>

>   \<selection name="Client-EmbeddedLogon" state="true" /\>

>   \<selection name="Client-EmbeddedBootExp" state="true" /\>

>   \<selection name="Client-EmbeddedShellLauncher" state="true" /\>

>   \<selection name="Client-KeyboardFilter" state="true" /\>

>   \<selection name="Internet-Explorer-Optional-amd64" state="false" /\>

>   \<selection name="MediaPlayback" state="false" /\>

>   \<selection name="WindowsMediaPlayer" state="false" /\>

>   \<selection name="Xps-Foundation-Xps-Viewer" state="false" /\>

>   \<selection name="WorkFolders-Client" state="false" /\>

>   \<selection name="SMB1Protocol" state="false" /\>

>   \<selection name="SearchEngine-Client-Package" state="false" /\>

>   \<selection name="Printing-Foundation-Features" state="false" /\>

>   \<selection name="FaxServicesClientPackage" state="false" /\>

>   \<selection name="Printing-Foundation-InternetPrinting-Client" state="false"
>   /\>

>   \<selection name="Printing-XPSServices-Features" state="false" /\>

>   \<selection name="Printing-PrintToPDFServices-Features" state="false" /\>

>   \<selection name="Microsoft-Hyper-V-Hypervisor" state="false" /\>

>   \<selection name="Microsoft-Hyper-V-All" state="false" /\>

>   \<selection name="Microsoft-Hyper-V" state="false" /\>

>   \</package\>

>   \</servicing\>

>   \<settings pass="auditSystem"\>

>   \<component name="Microsoft-Windows-Shell-Setup"
>   processorArchitecture="amd64" publicKeyToken="31bf3856ad364e35"
>   language="neutral" versionScope="nonSxS"
>   xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State"
>   xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"\>

>   \<AutoLogon\>

>   \<Enabled\>true\</Enabled\>

>   \<Username\>Admin\</Username\>

>   \<Password\>

>   \<Value\>cwBmAGIAUABhAHMAcwB3AG8AcgBkAA==\</Value\>

>   \<PlainText\>false\</PlainText\>

>   \</Password\>

>   \</AutoLogon\>

>   \<UserAccounts\>

>   \<LocalAccounts\>

>   \<LocalAccount wcm:action="add"\>

>   \<Password\>

>   \<Value\>cwBmAGIAUABhAHMAcwB3AG8AcgBkAA==\</Value\>

>   \<PlainText\>false\</PlainText\>

>   \</Password\>

>   \<Name\>Admin\</Name\>

>   \<Group\>Administrators\</Group\>

>   \<DisplayName\>Administrator\</DisplayName\>

>   \<Description\>Administrator\</Description\>

>   \</LocalAccount\>

>   \</LocalAccounts\>

>   \</UserAccounts\>

>   \</component\>

>   \</settings\>

>   \<settings pass="oobeSystem"\>

>   \<component name="Microsoft-Windows-Shell-Setup"
>   processorArchitecture="amd64" publicKeyToken="31bf3856ad364e35"
>   language="neutral" versionScope="nonSxS"
>   xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State"
>   xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"\>

>   \<OOBE\>

>   \<HideEULAPage\>true\</HideEULAPage\>

>   \<HideLocalAccountScreen\>true\</HideLocalAccountScreen\>

>   \<HideOEMRegistrationScreen\>true\</HideOEMRegistrationScreen\>

>   \<HideOnlineAccountScreens\>true\</HideOnlineAccountScreens\>

>   \<HideWirelessSetupInOOBE\>true\</HideWirelessSetupInOOBE\>

>   \<SkipMachineOOBE\>true\</SkipMachineOOBE\>

>   \<SkipUserOOBE\>true\</SkipUserOOBE\>

>   \<ProtectYourPC\>1\</ProtectYourPC\>

>   \</OOBE\>

>   \<AutoLogon\>

>   \<Enabled\>true\</Enabled\>

>   \<Username\>Skype\</Username\>

>   \<Password\>

>   \<Value\>UABhAHMAcwB3AG8AcgBkAA==\</Value\>

>   \<PlainText\>false\</PlainText\>

>   \</Password\>

>   \</AutoLogon\>

>   \</component\>

>   \</settings\>

>   \<cpi:offlineImage
>   cpi:source="wim://com-sccm01/_sources/capture/srscaptured.wim\#SRSImage"
>   xmlns:cpi="urn:schemas-microsoft-com:cpi" /\>

>   \</unattend\>

1.  In the Configuration Manager console, navigate to **Software Library** –
    **Application Management** – **Packages**, and then select **Create
    Package**.

2.  Use the following information to create the package.

    1.  **Name:** SRS v2 - Sysprep Package

    2.  **Manufacturer:** Microsoft Corporation

    3.  **Version:** 1.0.0

    4.  Select **This package contains source files** and provide path to the
        **SRS v2 – Sysprep Package** folder and select **Next**.

3.  Select **Do not create a program** and select **Next**.

4.  Review the **Confirm the settings page** and select **Next**.

5.  Select **Close**.

### Create the Windows 10 Enterprise package

1.  Obtain a Windows 10 Enterprise x64 media and copy the **install.wim** file
    to the **Operating Systems** – **Windows 10 Enterprise** folder.

2.  In the Configuration Manager console, navigate to **Software Library** –
    **Operating Systems** – **Operating System Images**, and then select **Add
    Operating System Image**.

3.  Specify path to the **install.wim** file you just copied, and then select
    **Next**.

4.  Update the **Version** field to match the build number of the Windows 10
    Enterprise image, and then select **Next**.

5.  Review the Details page and select **Next**.

6.  Select **Close**.

For more details, see [Manage operating system images with System Center
Configuration
Manager](https://docs.microsoft.com/sccm/osd/get-started/manage-operating-system-images).

### Create the Surface Pro device driver packages

**Note**

Skype Room Systems v2 are supported with both Surface Pro and Surface Pro 4. You
need to create a driver package for each Surface Pro model you have in your
environment.

1.  Download the latest drivers and firmware.

    1.  For Surface Pro:
        <https://www.microsoft.com/en-us/download/details.aspx?id=55484>

    2.  For Surface Pro 4:
        <https://www.microsoft.com/en-us/download/details.aspx?id=49498>

        Important

        The drivers MUST be compatible with the Windows 10 Enterprise build and
        the Skype Room Systems v2 deployment kit version. For more details, see
        [Download the latest firmware and drivers for Surface
        devices](https://docs.microsoft.com/surface/deploy-the-latest-firmware-and-drivers-for-surface-devices).

2.  Extract the downloaded driver and firmware. From a command prompt, execute;

    1.  msiexec /a C:\\SurfacePro_Win10.msi /passive TARGETDIR="
        C:\\_Sources\\Drivers\\Surface Pro"

    2.  msiexec /a C:\\SurfacePro4_Win10.msi /passive TARGETDIR="
        C:\\_Sources\\Drivers\\Surface Pro 4"

3.  In the Configuration Manager console, navigate to **Software Library** –
    **Operating Systems** – **Drivers**, and then select **Import Driver**.

4.  Select **Import all drivers in the following network path (UNC)** and select
    source folder and select **Next**. Example: C:\\_Sources\\Drivers\\Surface
    Pro

5.  On the **Specify the details for the imported drivers** window, select all
    the listed drivers and select **Enable these drivers and allow computers to
    install them**.

6.  Select **Categories** and create a new category that matches the Surface
    model and select **OK**, and then select **Next**.

7.  To create a new driver package for the selected drivers, select **New
    Package**.

8.  Specify package name that matches the Surface Pro model and provide a
    **folder path** to store the driver package files and select **OK**, and
    then select **Next**.

9.  On the **boot images** window, **do not** select any boot image and select
    **Next**.

10. Select **Close**.

11. Navigate to **Software Library** – **Operating Systems** – **Drivers**, and
    then select **Folder** – **Create Folder**, and specify a folder name that
    matches the Surface Pro model that you just imported the drivers for.

12. Move all the imported drivers to the newly created folder for easier
    navigation and operation.

13. Repeat the same steps for other Surface Pro models you might have.

For more details, see [Manage drivers in System Center Configuration
Manager](https://docs.microsoft.com/sccm/osd/get-started/manage-drivers).

Distribute Configuration Manager packages
-----------------------------------------

All the packages must be distributed to the servers running distribution point
role within the Configuration Manager hierarchy. Follow the instructions below
to initiate package distribution:

1.  Distribute Software Packages

    1.  In the Configuration Manager console, navigate to **Software Library** –
        **Application Management** – **Packages**. Select all the software
        packages you want to distribute and then select **Distribute Content**.

    2.  Review the list of packages and select **Next**.

    3.  Depending on your Configuration Manager hierarchy, add all the
        distribution point servers or distribution point groups to the list and
        select **Next**.

    4.  Select **Next** and then **Close** to initiate package distribution.

2.  Distribute Driver Packages

    1.  In the Configuration Manager console, navigate to **Software Library** –
        **Operating Systems** – **Driver Packages**. Select all the driver
        packages you want to distribute and then select **Distribute Content**.

    2.  Review the list of packages and select **Next**.

    3.  Depending on your Configuration Manager hierarchy, add all the
        distribution point servers or distribution point groups to the list and
        select **Next**.

    4.  Select **Next** and then **Close** to initiate package distribution.

3.  Distribute Operating System Packages

    1.  In the Configuration Manager console, navigate to **Software Library** –
        **Operating Systems** – **Operating System Images**. Select all the
        operating system images you want to distribute and then select
        **Distribute Content**.

    2.  Review the list of packages and select **Next**.

    3.  Depending on your Configuration Manager hierarchy, add all the
        distribution point servers or distribution point groups to the list and
        select **Next**.

    4.  Select **Next** and then **Close** to initiate package distribution.

>   **Note**

>   Package distribution may take some time, depending on the package size,
>   Configuration Manager hierarchy, number of distribution point servers and
>   networking.

>   All the packages must be distributed before you can start deploying a Skype
>   Room Systems v2 unit.

>   You can review package distribution status in the Configuration Manager
>   console, by navigating to **Monitoring** – **Distribution Status** –
>   **Content Status**.

Configuration Manager Task Sequences
------------------------------------

You need to use Task Sequences with System Center Configuration Manager to
automate steps in deploying an operating system image to a destination computer.

To deploy a Skype Room Systems v2 unit in an automated fashion, you need to
create a task sequence that references a boot image used to start the
destination Skype Room Systems v2 computer, the Windows 10 Enterprise operating
system image that you want to install, and any other additional content, such as
other applications or software updates, that you want to install.

You can download and easily import the task sequence example provided and
customize depending on your requirements. To import the sample task sequence,
follow these steps:

1.  **Download** the sample task sequence and copy the downloaded zip file onto
    a shared location.

2.  In the Configuration Manager console, navigate to **Software Library** –
    **Operating Systems** – **Task Sequences**, and then select **Import Task
    Sequence**.

3.  Select **Browse** and navigate to the shared folder and select the **Skype
    Room Systems v2 Deployment (EN-US).zip** file and select **Next**.

4.  Set **Action** to **Create New** and then select **Next**.

5.  Confirm the settings and select **Next**.

6.  Select **Close**.

After the task sequence is imported successfully, you need to edit each step to
validate the reference packages are correctly linked to each task sequence step.

1.  Select the imported task sequence and select **Edit**.

2.  **Task Sequence Editor** will launch, and you will see each sequential step
    required to deploy and configure a Skype Room Systems v2 unit.

3.  Walk through each step and complete the recommended updates. You can find
    the detailed explanations for each step, and whether there are any updates
    required.

    1.  Restart in Windows PE: This step restarts and then boots the computer
        into Windows Pre-Execution Environment. No changes are required for this
        step.

    2.  Partition Disk 0 – UEFI: This step wipes the disk configuration and
        creates partitions based on the configured settings. It is recommended
        not to make any changes to this step.

    3.  Set SRS Computer Name: This step includes an HTML application to provide
        a user interface to set a computer name for the Skype Room Systems v2
        unit during the deployment.

        1.  This is an optional step and can only be disabled if you want to
            manage computer naming through an alternate process.

        2.  Verify that the SRS v2 - Set-SRSComputerName package is selected. If
            not, select Browse and select it.

    4.  Apply Operating System: This step specifies the Operating System image
        that will be deployed, and the unattended Sysprep answer file that will
        be used.

        1.  Verify that the correct Windows 10 Enterprise operating system image
            file is selected.

        2.  Verify that Use an unattended or Sysprep answer file for a custom
            installation is enabled, and the SRS v2 - Sysprep Package is
            selected. Also ensure File Name is set to unattend.xml.

    5.  Apply Windows Settings: This step provides information related to
        Windows installation.

        1.  Provide licensing and registration information including the Product
            key, local administrator account password and the time zone
            depending on your needs.

    6.  Apply Network Settings: This step allows you specify a workgroup or
        Active Directory domain name and organizational unit.

    7.  Apply Drivers: This step and its sub steps are used to deploy applicable
        device drivers and firmware based on the Surface Pro model you have.
        Update each step to specify the relevant driver package associated with
        this deployment.

        1.  Each driver package is configured to leverage Windows Management
            Instrumentation (WMI) filters to deploy relevant drivers and
            firmware based on the Surface Pro make and model.

        2.  It is highly recommended not to alter these configuration items,
            otherwise deployment might fail.

    8.  Setup Windows and Configuration Manager: This step deploys and
        configures the Configuration Manager client. Update this step to specify
        the built-in Configuration Manager Client Package.

    9.  Install Root Certificate: This step is to distribute the root
        certificate for non-domain joined devices and therefore it is optional.

        1.  Remove or disable this step if you do not need to deploy a root
            certificate to the Skype Room Systems v2 units.

        2.  Verify the SRS v2 – Root Certificate Package is selected.

    10. Install and Configure OMS Agent: This step installs the 64-bit version
        of the Microsoft Operations Management Suite agent and configures that
        agent to connect to your Log Analytics workspace.

        1.  Disable this step only if you are going to use some other platforms
            to monitor health of your Skype Room Systems v2 units.

        2.  Edit this step and update the Command line parameters to specify
            your **Workspace ID** and **Workspace Key**.

        3.  See [Connect Windows computers to the Log Analytics service in
            Azure](https://docs.microsoft.com/skypeforbusiness/deploy/deploy-clients/with-oms#configure-test-devices-for-operations-management-suite-setup)
            for more information for obtaining the Operations Management Suite
            Workspace ID and the primary key.

        4.  Verify the SRS v2 – Microsoft OMS Agent Package is selected.

        5.  For more details on monitoring the health of your Skype Room Systems
            v2 deployment, see [Plan Skype Room Systems v2 management with
            OMS](https://docs.microsoft.com/skypeforbusiness/plan-your-deployment/clients-and-devices/oms-management)
            and [Deploy Skype Room Systems v2 management with
            OMS](https://docs.microsoft.com/skypeforbusiness/deploy/deploy-clients/with-oms#configure-test-devices-for-operations-management-suite-setup).

    11. Copy SRS v2 Configuration Files: This step copies the required setup and
        configuration files from Skype Room Systems v2 deployment kit into the
        local hard drive. No customization is required for this step.

    12. Install-SRSv2-OS-Updates: This step is to deploy any mandatory OS
        updates required with the Skype Room Systems v2 deployment. Note: If you
        have

        1.  Check [Configure a Skype Room Systems v2
            console](https://docs.microsoft.com/skypeforbusiness/deploy/deploy-clients/console),
            to see which updates are required.

        2.  Verify that your SRS v2 – OS Updates Package includes all the
            required updates.

        3.  Verify that the SRS v2 – OS Updates Package is selected.

        4.  Verify that the PowerShell execution policy is set to **Bypass**.

    13. Restart Computer: This step is to reboot the computer after the
        mandatory operating system updates are installed. No customization is
        required for this step.

    14. Add Local Skype User: This step is to create the local Skype account
        used to automatically sign into windows and start Skype Room Systems v2
        application. This step does not have any software package associated
        with it, and no customization is required for this step.

    15. Set up and configure SRS application: This step installs and configures
        the Skype Room Systems v2 application. This step uses the locally copied
        bits to install the application and therefore it doesn’t have any
        software packages associated with it. No customization is required for
        this step.

Validate and troubleshoot the solution
--------------------------------------

After you’ve completed the System Center Configuration Manager task sequences,
you will need to perform a test run to validate the task sequence is able to
deploy and configure Skype Room Systems v2 units.

1.  Connect the test device to the wired network using one of the supported
    ethernet adapters or using Microsoft Surface dock. If the PXE boot
    functionality is not configured your environment, then you can use the boot
    image on a USB stich that you created earlier to boot from USB and connect
    to the Configuration Manager

2.  Access the **firmware** and initiate **PXE boot**.

    1.  Ensure the Surface device is powered off.

    2.  Press and hold the **Volume Up** button.

    3.  Press and release the **Power** button.

    4.  After the device begins to boot, release the **Volume Up** button.

    5.  Select **Boot configuration**.

    6.  Select **PXE boot** and drag it to the top of the list. Alternatively,
        you can swipe left on network adapter to boot to the device immediately.
        This will not affect the boot order.

        1.  If the PXE boot functionality is not available, select the USB stick
            that hold the boot media.

    7.  Select **Exit** and then select **Restart Now**.

    8.  When prompted press **Enter** for network boot service.

3.  Windows PE will load into memory and Task Sequence Wizard will start. Select
    **Next** to continue.

4.  Select the **task sequence** that you imported earlier and then select
    **Next**.

5.  After the disk configuration is applied, you will be prompted to specify a
    computer name for the device. Set the computer name:

    1.  The user interface will provide you a recommended computer name based on
        the serial number of the Surface Pro device. You can either accept the
        proposed name or specify a new name.

    2.  **Follow the instructions** on the computer name assignment screen and
        the deployment will start when you select **Accept**.

6.  The rest of the deployment process is automatic and will not look for any
    user input.

7.  Wait for the deployment task sequence to finish configuring the device. When
    completed, you should see the below configuration screen that will ask you
    configure the Skype Room Systems v2 application settings.

GRAPHIC HERE

1.  Plug the Surface Pro into the Skype Room Systems v2 console and configure
    the application settings.

2.  Validate that the capabilities listed
    [here](https://support.office.com/en-us/article/Skype-Room-Systems-version-2-help-e667f40e-5aab-40c1-bd68-611fe0002ba2)
    are working on the deployed device.

To troubleshoot a failed installation, you need to check SMSTS.log file that is
used to log all the steps executed within a Configuration Manager task sequence.

The SMSTS.log file is stored on different paths depending on the build process
stage. Check the following table to identify the path to the SMSTS.log file.

| **Deployment phase**                                                        | **Task sequence log path**                         |
|-----------------------------------------------------------------------------|----------------------------------------------------|
| WinPE, before HDD format                                                    | X:\\windows\\temp\\smstslog\\smsts.log             |
| WinPE, after HDD format                                                     | C:\\_SMSTaskSequence\\Logs\\Smstslog\\smsts.log    |
| Operating System deployed, before the Configuration Manager agent installed | c:\\_SMSTaskSequence\\Logs\\Smstslog\\smsts.log    |
| Operating System and the Configuration Manager agent deployed               | %windir%\\system32\\ccm\\logs\\Smstslog\\smsts.log |
| Task Sequence execution complete                                            | %windir%\\system32\\ccm\\logs\\smsts.log           |

**Note**

You can press F8 at any time during the task sequence to start a command prompt
and get access to the SMSTS.log file.

In order to resolve PXE boot issues, you need to check two log files on the
Configuration Manager server, specific to PXE actions:

-   Pxecontrol.log – located in the Configuration Manager installation logs
    directory

-   Smspxe.log – located in Configuration Manager Management Point (MP) logs
    directory

For a full list of the log files that you can use to further troubleshoot your
Configuration Manager installation, see [Log files in System Center
Configuration
Manager](https://docs.microsoft.com/sccm/core/plan-design/hierarchy/log-files).
