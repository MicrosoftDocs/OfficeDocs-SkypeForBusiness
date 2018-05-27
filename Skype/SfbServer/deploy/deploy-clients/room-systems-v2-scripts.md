---
title: "Skype Room Systems v2 scripts"
ms.author: jambirk
author: jambirk
manager: serdars
ms.date: 5/10/2018
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Priority
ms.collection: 
- Strat_SB_Admin
ms.custom:
ms.assetid: 678689e4-d547-499b-be64-7d8f16dd8668
description: "Use this topic to obtain scripts used with Skype Room Systems v2."
---

# Skype Room Systems v2 Scripts
 
Copy each of the sections in this article into a text file named in the section heading. These files are used in deploying Skype Room Systems v2: 
* [CreateSrsMedia.ps1](#createsrsmediaps1) is a Powershell script used to create a software image for the console device.  
* [SkypeRoomProvisioningScript.ps1](#skyperoomprovisioningscriptps1) is a Powershell script used to set up Skype for Business and Exchange accounts the devices will use.  
* [SkypeRoomSystems_v2.omsview](#skyperoomsystemsv2omsview)  is used when setting up management of Skype Room Systems v2 using OMS.
  
<a name="CreateSrs"></a>
## CreateSrsMedia.ps1

```
<#
.SYNOPSIS

    Create SRSv2 media appropriate for setting up an SRSv2 device.


.DESCRIPTION

    This script automates some sanity checks and copying operations that are
    necessary to create bootable SRSv2 media. Booting an SRSv2 device using the
    media created from this process will result in the SRSv2 shutting down. The
    SRSv2 can then either be put into service, or booted with separate WinPE
    media for image capture.

    To use this script, you will need:

    1. A FAT32-formatted USB drive, inserted into this computer
    2. An SRSv2 deployment kit MSI file, placed into the same directory as this
       script.
    3. Windows 10 Enterprise or Windows 10 Enterprise IoT media, which must be
       accessible from this computer (you will be prompted for a path). The
       Windows media build number must match the build required by the SRSv2
       deployment kit.
    4. A driver pack MSI appropriate to your SRSv2 device, placed into the
       same directory as this script. The drivers must match both the SRSv2
       hardware you intend to use, and the build of Windows being used.
    5. If using Windows 10 Enterprise IoT, an ePKEA (volume license key)

.EXAMPLE
    .\CreateSrsMedia

    Prompt for required information, validate provided inputs, and (if all
    validations pass) create media on the specified USB device.

.NOTES

    This script supports the creation of media for the following SRSv2
    hardware:

        - Surface Pro 4 (SRSv2 dock-based solution)
        - Surface Pro (2017) (SRSv2 dock-based solution)

    If you are using a supported SRSv2 device not listed above, please check
    for a newer version of this script.

    This script requires that you provide Windows media targeted for the x64
    architecture.

    Only one driver pack can be used at a time. Each unique supported SKU of
    SRSv2 computer hardware must have its own, separate image.

    The build number of the Windows media being used *must* match the build
    required by the SRSv2 deployment kit.

    The build number of the Windows media being used *must* match the build
    required by any drivers being used.

#>

<#
Revision history
    1.0.0  - Initial release
    1.0.1  - Support source media with WIM >4GB
    1.1.0  - Switch Out-Null to Write-Debug for troubleshooting
             Record transcripts for troubleshooting
             Require the script be run from a path without spaces
             Require the script be run from an NTFS filesystem
             Soft check for sufficient scratch space
             Warn that the target USB drive will be wiped
             Rethrow exceptions after cleanup on main path

#>
[CmdletBinding()]
param()

$ErrorActionPreference = "Stop"
$DebugPreference = if($PSCmdlet.MyInvocation.BoundParameters["Debug"]) { "Continue" } else { "SilentlyContinue" }
Set-StrictMode -Version Latest

$CreateSrsMediaScriptVersion = "1.1.0"

function Remove-Directory {
  <#
    .SYNOPSIS
        
        Recursively remove a directory and all its children.

    .DESCRIPTION

        Powershell can't handle 260+ character paths, but robocopy can. This
        function allows us to safely remove a directory, even if the files
        inside exceed Powershell's usual 260 character limit.
  #>
param(
    [parameter(Mandatory=$true)]
    [string]$path <# The path to recursively remove #>
)

    # Make an empty reference directory
    $cleanup = Join-Path $PSScriptRoot "empty-temp"
    if (Test-Path $cleanup) {
        Remove-Item -Path $cleanup -Recurse -Force
    }
    New-Item -ItemType Directory $cleanup | Write-Debug

    # Use robocopy to clear out the guts of the victim path
    & robocopy $cleanup $path /mir | Write-Debug

    # Remove the folders, now that they're empty.
    Remove-Item $path -Force
    Remove-Item $cleanup -Force
}

function Test-OsPath {
  <#
    .SYNOPSIS
        
        Test if $OsPath contains valid Windows setup media for SRSv2.

    .DESCRIPTION

        Tests if the provided path leads to Windows setup media that meets
        requirements for SRSv2 installation. Specifically, the media must:

          - Appear to have the normal file layout for Windows media
          - Be Enterprise (not Pro, Home, etc.)
          - Be Enterprise IoT (not plain Enterprise)
          - Be targeted for x64
          - Match the version number the SRSv2 deployment kit requires

    .OUTPUTS bool

        $true if $OsPath refers to valid Windows installation media, $false otherwise.
  #>
param(
  [parameter(Mandatory=$true)]
  $OsPath,
  [parameter(Mandatory=$true)]
  $KitOsRequired,
  [parameter(Mandatory=$false)]
  [switch]$IsOem
)

    if (!(Test-Path $OsPath)) {
        Write-Host "The path provided does not exist. Please specify a path that is the root of the Windows installation media you wish to use."
        return $false
    }

    # Save some paths we'll re-use.
    $OsSources = (Join-Path $OsPath "sources")
    $InstallWim = (Join-Path $OsSources "install.wim")

    # Basic sanity check -- does this look like Windows install media?
    if (
        (!(Test-Path (Join-Path $OsPath "boot"))) -or
        (!(Test-Path (Join-Path $OsPath "efi"))) -or
        (!(Test-Path $OsSources)) -or
        (!(Test-Path (Join-Path $OsPath "support" ))) -or
        (!(Test-Path (Join-Path $OsPath "autorun.inf"))) -or
        (!(Test-Path (Join-Path $OsPath "bootmgr"))) -or
        (!(Test-Path (Join-Path $OsPath "bootmgr.efi"))) -or
        (!(Test-Path (Join-Path $OsPath "setup.exe"))) -or
        (!(Test-Path $InstallWim))
        ) {
        Write-Host "The path provided does not seem to point to valid Windows installation media. Please specify a path that is the root of the Windows installation media you wish to use."
        return $false
    }

    # Windows 10 Enterprise has EI.CFG, but Windows 10 Enterprise IoT does not.
    # This check allows us to determine IoT vs. non-IoT without having to mount
    # either Boot.wim or Install.wim.
    $IsIoT = !(Test-Path (Join-Path $OsSources "EI.CFG"))

    # OEMs need to use IoT.
    if ($IsOem -and !$IsIoT) {
        Write-Host "You appear to have specified a path to Windows 10 Enterprise media. However, you need to use Windows 10 Enterprise IoT media."
        return $false
    }

    # Non-OEMs need to use normal Windows 10 Enterprise.
    if (!$IsOem -and $IsIoT) {
        Write-Host "You appear to have specified a path to Windows 10 Enterprise IoT media. However, you need to use Windows 10 Enterprise media."
        return $false
    }

    # Basic sanity checks passed -- load up the install.wim metadata
    $img = Get-WindowsImage -ImagePath $InstallWim -Name "Windows 10 Enterprise"

    # We only accept x64-arch media. 9 == x64
    if ($img.Architecture -ne 9) {
        Write-Host ("Your Windows installation media is targeted for the {0} architecture. SRSv2 requires x64 targeted installation media." -f $img.Architecture)
        return $false
    }

    # We only accept media with a version number matching the version required
    # by the SRSv2 kit.
    if ($img.Version -ne $KitOsRequired) {
        Write-Host ("Your Windows installation media is version {0}. Your SRSv2 kit requires version {1}." -f $img.Version, $KitOsRequired)
        return $false
    }

    # We only accept "Enterprise" media (not, e.g., Pro, Home, or Eval)
    if ($img.EditionId -ne "Enterprise") {
        Write-Host ("You need to acquire Enterprise edition installation media. The installation media provided is '{0}', not Enterprise." -f $img.EditionId)
        return $false
    }

    return $true
}

function Test-ePKEA {
  <#
    .SYNOPSIS

        Determine if $key is in the correct format of a Windows license key.

    .DESCRIPTION

        Determines if $key follows the basic Windows license key format of five
        dash-separated groups of five alphanumeric characters each. This
        function does *not* test if the key is a valid key -- only that it
        follows the correct formatting.

    .OUTPUTS bool

        $true if $key is in the correct format to be a Windows license key, $false otherwise.
  #>
param(
    [parameter(Mandatory=$true)]
    [AllowEmptyString()]
    [string]$key <# The Windows license key to check. #>
)

    # Could make the regex case insensitive, but this is fast and easy.
    $key = $key.ToUpperInvariant()

    $result = ($key -match '^([A-Z0-9]{5}-){4}[A-Z0-9]{5}$')
    if (!$result) {
        Write-Host ""
        Write-Host "Not a valid ePKEA. Please enter a value in the form of:"
        Write-Host "xxxxx-xxxxx-xxxxx-xxxxx-xxxxx"
        Write-Host "Where each digit represented by an 'x' is an alphanumeric (A-Z or 0-9) value."
        Write-Host ""
    }
    return $result
}

function Test-Unattend-Compat {
    <#
        .SYNOPSIS
        
            Test to see if this script is compatible with a given SRSv2 Unattend.xml file.

        .DESCRIPTION

            Looks for metadata in the $xml parameter indicating the lowest version of
            the CreateSrsMedia script the XML file will work with.

        .OUTPUTS bool
            
            Return $true if CreateSrsMedia is compatible with the SRSv2
            Unattend.xml file in $xml, $false otherwise.
    #>
param(
    [parameter(Mandatory=$true)]
    [System.Xml.XmlDocument]$Xml, <# The SRSv2 AutoUnattend to check compatibility with. #>
    [parameter(Mandatory=$true)]
    [int]$Rev <# The maximum compatibility revision this script supports. #>
)
    $nodes = $Xml.SelectNodes("//comment()[starts-with(normalize-space(translate(., 'ABCDEFGHIJKLMNOPQRSTUVWXYZ', 'abcdefghijklmnopqrstuvwxyz')), 'srsv2-compat-rev:')]")

    # If the file has no srsv2-compat-rev value, assume rev 0, which all scripts work with.
    if ($nodes -eq $null -or $nodes.Count -eq 0) {
        return $true
    }

    $URev = 0

    # If there is more than one value, be conservative: take the biggest value
    $nodes | 
    ForEach-Object {
        $current = $_.InnerText.Split(":")[1]
        if ($URev -lt $current) {
            $URev = $current
        }
    }

    return $Rev -ge $URev

}

function Remove-Xml-Comments {
  <#
    .SYNOPSIS
        
        Remove all comments that are direct children of $node.

    .DESCRIPTION
        
        Remove all the comment children nodes (non-recursively) from the specified $node.
  #>
param(
    [parameter(Mandatory=$true)]
    [System.Xml.XmlNode]$node <# The XML node to strip comments from. #>
)
    $node.SelectNodes("comment()") |
    ForEach-Object {
        $node.RemoveChild($_) | Write-Debug
    }
}

function Add-AutoUnattend-Key {
  <#
    .SYNOPSIS
        
        Inject $key as a product key into the AutoUnattend XML $xml.

    .DESCRIPTION
        
        Injects the $key value as a product key in $xml, where $xml is an
        AutoUnattend file already containing a Microsoft-Windows-Setup UserData
        node. Any comments in the UserData node are stripped.

        If a ProductKey node already exists, this function does *not* remove or
        replace it.
  #>
param(
    [parameter(Mandatory=$true)]
    [System.Xml.XmlDocument]$xml, <# The SRSv2 AutoUnattend to modify. #>
    [parameter(Mandatory=$true)]
    [string]$key <# The Windows license key to inject. #>
)

    $XmlNs = @{"u"="urn:schemas-microsoft-com:unattend"}
    $node = (Select-Xml -Namespace $XmlNs -Xml $xml -XPath "//u:settings[@pass='windowsPE']/u:component[@name='Microsoft-Windows-Setup']/u:UserData").Node
    Remove-Xml-Comments $node
    $NWillShowUi = $xml.CreateElement("", "WillShowUi", $XmlNs["u"])
    $NWillShowUi.InnerText = "OnError"
    $NKey = $xml.CreateElement("", "Key", $XmlNs["u"])
    $NKey.InnerText = $key
    $NProductKey = $xml.CreateElement("", "ProductKey", $XmlNs["u"])
    $NProductKey.AppendChild($NWillShowUi) | Write-Debug
    $NProductKey.AppendChild($NKey) | Write-Debug
    $node.PrependChild($NProductKey) | Write-Debug
}

function Set-AutoUnattend-Sysprep-Mode {
  <#
    .SYNOPSIS
        
        Set the SRSv2 sysprep mode to "reboot" or "shutdown" in the AutoUnattend file $xml.

    .DESCRIPTION
        
        Sets the SRSv2 AutoUnattend represented by $xml to either reboot (if
        -Reboot is used), or shut down (if -shutdown is used). Any comments
        under the containing RunSynchronousCommand node are stripped.

        This function assumes that a singular sysprep command is specified in
        $xml with /generalize and /oobe flags, in the auditUser pass,
        Microsoft-Windows-Deployment component. It further assumes that the
        sysprep command has the /reboot option specified by default.
  #>
param(
    [parameter(Mandatory=$true)]
    [System.Xml.XmlDocument]$Xml, <# The SRSv2 AutoUnattend to modify. #>
    [parameter(Mandatory=$true,ParameterSetName='reboot')]
    [switch]$Reboot, <# Whether sysprep should perform a reboot or a shutdown. #>
    [parameter(Mandatory=$true,ParameterSetName='shutdown')]
    [switch]$Shutdown <# Whether sysprep should perform a shutdown or a reboot. #>
)
    $XmlNs = @{"u"="urn:schemas-microsoft-com:unattend"}
    $node = (Select-Xml -Namespace $XmlNs -Xml $Xml -XPath "//u:settings[@pass='auditUser']/u:component[@name='Microsoft-Windows-Deployment']/u:RunSynchronous/u:RunSynchronousCommand/u:Path[contains(translate(text(), 'ABCDEFGHIJKLMNOPQRSTUVWXYZ', 'abcdefghijklmnopqrstuvwxyz'), 'sysprep') and contains(translate(text(), 'ABCDEFGHIJKLMNOPQRSTUVWXYZ', 'abcdefghijklmnopqrstuvwxyz'), 'generalize') and contains(translate(text(), 'ABCDEFGHIJKLMNOPQRSTUVWXYZ', 'abcdefghijklmnopqrstuvwxyz'), 'oobe')]").Node
    Remove-Xml-Comments $node.ParentNode
    if ($Shutdown -or !$Reboot) {
        $node.InnerText = $node.InnerText.ToLowerInvariant() -replace ("/reboot", "/shutdown")
    }
}

function Get-TextListSelection {
  <#
    .SYNOPSIS

        Prompt the user to pick an item from an array.


    .DESCRIPTION

        Given an array of items, presents the user with a text-based, numbered
        list of the array items. The user must then select one item from the
        array (by index). That index is then returned.

        Invalid selections cause the user to be re-prompted for input.


    .OUTPUTS int

        The index of the item the user selected from the array.
  #>
  param(
    [parameter(Mandatory=$true)]<# The list of objects to select from #>
    $Options,
    [parameter(Mandatory=$false)]<# The property of the objects to use for the list #>
    $Property = $null,
    [parameter(Mandatory=$false)]<# The prompt to display to the user #>
    $Prompt = "Selection",
    [parameter(Mandatory=$false)]<# Whether to allow a blank entry to make the default selection #>
    [switch]
    $AllowDefault = $true,
    [parameter(Mandatory=$false)]<# Whether to automatically select the default value, without prompting #>
    [switch]
    $AutoDefault = $false
  )

  $index = 0
  $response = -1
  $DefaultValue = $null
  $DefaultIndex = -1

  if ($AllowDefault) {
    $DefaultIndex = 0
    if ($AutoDefault) {
      return $DefaultIndex
    }
  }

  $Options | Foreach-Object -Process {
    $value = $_
    if ($Property -ne $null) {
      $value = $_.$Property
    }
    if ($DefaultValue -eq $null) {
      $DefaultValue = $value
    }
    Write-Host("[{0,2}] {1}" -f $index, $value)
    $index++
  } -End {
    if ($AllowDefault) {
      Write-Host("(Default: {0})" -f $DefaultValue)
    }
    while ($response -lt 0 -or $response -ge $Options.Count) {
      try {
        $response = Read-Host -Prompt $Prompt -ErrorAction SilentlyContinue
        if ([string]::IsNullOrEmpty($response)) {
          [int]$response = $DefaultIndex
        } else {
          [int]$response = $response
        }
      } catch {}
    }
  }

  return $response
}

function SyncSubdirectory {
  <#
    .SYNOPSIS
        Sync a single subdirectory from a source directory to a destination.

    .DESCRIPTION
        Given a source directory Src with a subdirectory Subdir, recreate Subdir
        as a subdirectory under Dst.
  #>
  param(
    [parameter(Mandatory=$true)] <# The source directory containing the subirectory to sync. #>
    $Src,
    [parameter(Mandatory=$true)] <# The destination directory that may or may not yet contain the subdirectory being synchronized #>
    $Dst,
    [parameter(Mandatory=$true)] <# The name of the subdirectory to synchronize #>
    $Subdir,
    [parameter(Mandatory=$false)] <# Any additional flags to pass to robocopy #>
    $Flags
  )

  $Paths = Join-Path -Path @($Src, $Dst) -ChildPath $Subdir
  & robocopy /mir $Paths $Flags | Write-Debug
}

function SyncSubdirectories {
  <#
    .SYNOPSIS
        Recreate each subdirectory from the source in the destination.

    .DESCRIPTION
        For each subdirectory contained in the source, synchronize with a
        corresponding subdirectory in the destination. This does not synchronize
        non-directory files from the source to the destination, nor does it
        purge "extra" subdirectories in the destination where the source does
        not contain such directories.
  #>
  param(
    [parameter(Mandatory=$true)] <# The source directory #>
    $Src,
    [parameter(Mandatory=$true)] <# The destination directory #>
    $Dst,
    [parameter(Mandatory=$false)] <# Any additional flags to pass to robocopy #>
    $Flags
  )

  Get-ChildItem $Src -Directory | ForEach-Object { SyncSubdirectory $Src $Dst $_.Name $Flags }
}

function PrintWhereToGetLangpacks {
param(
    [parameter(Mandatory=$false)]
    [switch]$IsOem
)
    if ($IsOem) {
        Write-Host ("   OEMs:            http://go.microsoft.com/fwlink/?LinkId=131359")
        Write-Host ("   System builders: http://go.microsoft.com/fwlink/?LinkId=131358")
    } else {
        Write-Host ("   MPSA customers:         http://go.microsoft.com/fwlink/?LinkId=125893")
        Write-Host ("   Other volume licensees: http://www.microsoft.com/licensing/servicecenter")
    }
}

function PrintWhereToGetDrivers {
    Write-Host "   New Surface Pro: https://www.microsoft.com/en-us/download/details.aspx?id=55484"
    Write-Host "   Surface Pro 4:   https://www.microsoft.com/en-us/download/details.aspx?id=49498"
}

function PrintWhereToGetSrsV2 {
    Write-Host "   https://go.microsoft.com/fwlink/?linkid=851168"
}

function PrintWhereToGetScript {
    Write-Host "The latest version of this script can always be found at:"
    Write-Host "https://go.microsoft.com/fwlink/?linkid=867842"
}





####
## Start of main script
####

Start-Transcript

try {
    $AutoUnattendCompatLevel = 0

    if (-NOT ([Security.Principal.WindowsPrincipal] [Security.Principal.WindowsIdentity]::GetCurrent()).IsInRole(`
        [Security.Principal.WindowsBuiltInRole] "Administrator")) {
        Write-Host "This script must be run from an elevated console."
        exit
    }

    Write-Host ("Script version {0}" -f $CreateSrsMediaScriptVersion)
    PrintWhereToGetScript
    Write-Host ""

    # Initial sanity checks

    # There is difficulty invoking msiexec if the MSI's path contains a space.
    if ($PSScriptRoot.Contains(" ")) {
        # Much gratitude to
        # The person who can remove
        # This limitation
        Write-Host "Please run this script from a path that does not contain spaces."
        exit
    }

    $ScriptDrive = [System.IO.DriveInfo]::GetDrives() |? { (Split-Path -Path $_.Name -Qualifier) -eq (Split-Path -Path $PSScriptRoot -Qualifier) }

    if ($ScriptDrive.DriveFormat -ne "NTFS") {
        Write-Host "This script must be run from an NTFS filesystem, as it can potentially cache very large files."
        exit
    }

    # Perform an advisory space check
    $EstimatedCacheSpace =  (1024*1024*1024*1.5) + # Estimated unpacked driver size
                            (1024*1024*1024*16) +  # Estimated exported WIM size
                            (1024*1024*100)        # Estimated unpacked SRSv2 kit size
    if ($ScriptDrive.AvailableFreeSpace -lt $EstimatedCacheSpace) {
        Write-Warning "The drive this script is running from may not have enough free space for the script to complete successfully."
        Write-Warning ("You should ensure at least {0:F2}GiB are available before continuing." -f ($EstimatedCacheSpace / (1024*1024*1024)) )
        Write-Warning "Would you like to proceed anyway?"
        do {
            $confirmation = (Read-Host -Prompt "YES or NO")
            if ($confirmation -eq "YES") {
                Write-Warning "Proceeding despite potentially insufficient scratch space."
                break
            }

            if ($confirmation -eq "NO") {
                Write-Host "Please re-run the script after you make more space available on the current drive, or move the script to a drive with more available space."
                exit
            }

            Write-Host "Invalid option."
        } while ($true)
    }

    # Determine OEM status
    $IsOem = $null
    Write-Host "What type of customer are you?"
    do {
        switch (Read-Host -Prompt "OEM or Enterprise") {
            "OEM" {
                $IsOem = $true
            }

            "Enterprise" {
                $IsOem = $false
            }

            Default {
                $IsOem = $null
            }
        }
    } while ($IsOem -eq $null)


    if ($true) {
        $i = 1

        Write-Host ("Please make sure you have all of the following available:")
        Write-Host ("")
        Write-Host ("{0}. A FAT32-formatted USB drive." -f $i++)
        Write-Host ("   The contents of this drive WILL BE LOST!")
        Write-Host ("{0}. Your SRSv2 deployment kit MSI" -f $i++)
        PrintWhereToGetSrsV2
    if ($IsOem) {
        Write-Host ("{0}. Windows 10 Enterprise IoT media that matches your SRSv2 deployment kit." -f $i++)
    } else {
        Write-Host ("{0}. Windows 10 Enterprise media that matches your SRSv2 deployment kit." -f $i++)
    }
        Write-Host ("{0}. Driver MSI appropriate for your hardware, and that matches your Windows media." -f $i++)
        PrintWhereToGetDrivers
    if ($IsOem) {
        Write-Host ("{0}. your ePKEA license key." -f $i++)
    }
        Write-Host ("{0}. Any language pack (LP and/or LIP) files to be included." -f $i++)
        PrintWhereToGetLangpacks -IsOem:$IsOem
        Write-Host ("{0}. The necessary cumulative update MSU (if applicable)." -f $i++)
        Write-Host ("   Cumulative updates can be downloaded from the catalog at https://www.catalog.update.microsoft.com/Home.aspx")
        Write-Host ("")
        Write-Host ("Please do not continue until you have all these items in order.")
        Write-Host ("")
    }


    # Acquire the SRS deployment kit
    Write-Host "Looking for an SRS deployment kit..."
    $SrsKitPattern = "SRSDeploymentKit-*.msi"
    $SRSDKS = @(Get-Item -Path (Join-Path $PSScriptRoot $SrsKitPattern))

    if ($SRSDKS -eq $null -or $SRSDKS.Count -eq 0) {
        Write-Host "Could not locate an SRS deployment kit."
        Write-Host "Please place your SRSDeploymentKit MSI file in the same directory as this script."
        Write-Host ("SRS deployment kits have names of the form '{0}'." -f $SrsKitPattern)
        Write-Host "You can download the latest SRS deployment kit from:"
        PrintWhereToGetSrsV2
        exit
    }

    if ($SRSDKS.Count -eq 1) {
        $SRSDK = $SRSDKS[0]
        Write-Host ("Located deployment kit {0}" -f $SRSDK.Name)
    } else {
        Write-Host "Located multiple deployment kits. Please select one."
        $SRSDK = $SRSDKS[(Get-TextListSelection $SRSDKS -Property "Name")]
    }


    ## Extract the deployment kit.
    $RigelMedia = Join-Path $PSScriptRoot "SRSv2"

    if (Test-Path $RigelMedia) {
      Remove-Directory $RigelMedia
    }

    Write-Host "Extracting the deployment kit... " -NoNewline
    Start-Process "msiexec" -ArgumentList ("/a {0} /qn TARGETDIR={1}" -f $SRSDK.FullName, $RigelMedia) -NoNewWindow -Wait
    Write-Host "done."


    ## Pull relevant values from the deployment kit
    $RigelMedia = Join-Path $RigelMedia "Skype Room System Deployment Kit"

    $UnattendFile = Join-Path $RigelMedia "AutoUnattend.xml"

    $xml = New-Object System.Xml.XmlDocument
    $XmlNs = @{"u"="urn:schemas-microsoft-com:unattend"}
    $xml.Load($UnattendFile)

    # Check if we're compatible with this kit.
    if (!(Test-Unattend-Compat -Xml $xml -Rev $AutoUnattendCompatLevel)) {
        Write-Host "This version of CreateSrsMedia is not compatible with your deployment kit."
        PrintWhereToGetScript
        exit
    }

    $SrsKitOs = (Select-Xml -Namespace $XmlNs -Xml $xml -XPath "//u:assemblyIdentity/@version").Node.Value
    $DriverDest = ((Select-Xml -Namespace $XmlNs -Xml $xml -XPath "//u:DriverPaths/u:PathAndCredentials/u:Path/text()").ToString())

    Write-Host "This deployment kit is built for Windows build $SrsKitOs."
    Write-Host "This deployment kit draws its drivers from $DriverDest."

    $DriverDest = $DriverDest.Replace("%configsetroot%", $RigelMedia)

    # Acquire the driver pack
    Write-Host "Looking for a driver pack..."
    $DriverPattern = ("*_Win10_{0}_*_*.msi" -f ($SrsKitOs.Split(".")[2]))
    $DriverPacks = @(Get-Item -Path (Join-Path $PSScriptRoot $DriverPattern))

    if ($DriverPacks -eq $null -or $DriverPacks.Count -eq 0) {
        Write-Host "Could not locate a driver pack."
        Write-Host "Please place your OS-appropriate driver pack in the same directory as this script."
        Write-Host ("You need a driver pack with a name in the form of '{0}'." -f $DriverPattern)
        Write-Host "REMEMBER, you MUST use a driver pack that matches the hardware this installation media will be used with."
        Write-Host "You can download an appropriate driver pack from one of the following locations:"
        PrintWhereToGetDrivers
        exit
    }

    if ($DriverPacks.Count -eq 1) {
        $DriverPack = $DriverPacks[0]
        Write-Host ("Located Driver Pack {0}" -f $DriverPack.Name)
    } else {
        Write-Host "Located multiple driver packs. Please select one."
        $DriverPack = $DriverPacks[(Get-TextListSelection $DriverPacks -Property "Name")]
    }


    ## Extract the driver pack
    $DriverMedia = Join-Path $PSScriptRoot "Drivers"

    if (Test-Path $DriverMedia) {
      Remove-Directory $DriverMedia
    }

    Write-Host "Extracting the drivers... " -NoNewline
    Start-Process "msiexec" -ArgumentList ("/a {0} /qn TARGETDIR={1}" -f $DriverPack.FullName, $DriverMedia) -NoNewWindow -Wait
    Write-Host "done."

    # Acquire the language packs
    $LanguagePacks = @(Get-Item -Path (Join-Path $PSScriptRoot "*.cab"))
    $InstallLP = New-Object System.Collections.ArrayList
    $InstallLIP = New-Object System.Collections.ArrayList

    Write-Host "Identifying language packs... "
    ForEach ($LanguagePack in $LanguagePacks) {
        $package = (Get-WindowsPackage -Online -PackagePath $LanguagePack)
        if ($package.ReleaseType -ine "LanguagePack") {
            Write-Warning "$LanguagePack is not a language pack."
            continue
        }
        $parts = $package.PackageName.Split("~")
        if ($parts[2] -ine "amd64") {
            Write-Warning "$LanguagePack is not for the right architecture."
            continue
        }
        if ($parts[4] -ine $SrsKitOs) {
            Write-Warning "$LanguagePack is not for the right OS version."
            continue
        }
        $type = ($package.CustomProperties |? {$_.Name -ieq "LPType"}).Value
        if ($type -ieq "LIP") {
            $InstallLIP.Add($LanguagePack) | Write-Debug
        } elseif ($type -ieq "Client") {
            $InstallLP.Add($LanguagePack) | Write-Debug
        } else {
            Write-Warning "$LanguagePack is of unknown type."
        }
    }
    Write-Host "... done identifying language packs."


    # Acquire the updates
    Write-Host "Identifying updates... " -NoNewline
    $InstallUpdates = @(Get-Item -Path (Join-Path $PSScriptRoot "*.msu"))
    Write-Host "done."

    if ($InstallLP.Count -eq 0 -and $InstallLIP.Count -eq 0 -and $InstallUpdates -ne $null) {
        Write-Warning "THIS IS YOUR ONLY CHANCE TO PRE-INSTALL LANGUAGE PACKS."
        Write-Host "Because you are pre-installing an update, you will NOT be able to pre-install language packs to the image at a later point."
        Write-Host "You are currently building an image with NO pre-installed language packs."
        Write-Host "Are you ABSOLUTELY SURE this is what you intended?"

        do {
            $confirmation = (Read-Host -Prompt "YES or NO")
            if ($confirmation -eq "YES") {
                Write-Warning "PROCEEDING TO GENERATE SLIPSTREAM IMAGE WITH NO PRE-INSTALLED LANGUAGE PACKS."
                break
            }

            if ($confirmation -eq "NO") {
                Write-Host "Please place the LP and LIP cab files you wish to use in this directory, and run the script again."
                Write-Host ""
                Write-Host "You can download language packs from the following locations:"
                PrintWhereToGetLangpacks -IsOem:$IsOem
                exit
            }

            Write-Host "Invalid option."
        } while ($true)
    }

    # Discover and prompt for selection of a reasonable target drive
    $TargetDrive = $null

    $ValidTargetDrives = @([System.IO.DriveInfo]::getdrives() | ? { $_.DriveType -eq "Removable" -and $_.DriveFormat -eq "FAT32" })

    if ($ValidTargetDrives.Count -eq 0) {
        Write-Host "You do not have any valid media plugged in. Ensure that you have a FAT32 formatted removable drive inserted into the computer."
        exit
    }

    Write-Host ""
    Write-Host "Reminder: all data on the drive you select will be lost!"
    Write-Host ""

    $TargetDrive = ($ValidTargetDrives[(Get-TextListSelection -Options $ValidTargetDrives -Property "Name" -Prompt "Please select a target drive" -AllowDefault:$false)]).RootDirectory.FullName

    # Acquire the Windows install media root
    do {
        $WindowsMedia = Read-Host -Prompt "Please enter the path to the root of your Windows install media"
    } while (!(Test-OsPath -OsPath $WindowsMedia -KitOsRequired $SrsKitOs -IsOem:$IsOem))

    # Acquire the ePKEA
    $LicenseKey = ""
    if ($IsOem) {
        do {
            $LicenseKey = Read-Host -Prompt "Please enter your ePKEA"
        } while (!(Test-ePKEA $LicenseKey))
    }

    ###
    ## Let the user know what we've discovered
    ###

    Write-Host ""
    if ($IsOem) {
        Write-Host "Creating OEM media."
    } else {
        Write-Host "Creating Enterprise media."
    }
    Write-Host ""
    Write-Host "Using SRSv2 kit:      " $SRSDK
    Write-Host "Using driver pack:    " $DriverPack
    Write-Host "Using Windows media:  " $WindowsMedia

    Write-Host "Using language packs: "
    ForEach ($pack in $InstallLP) {
        Write-Host "    $pack"
    }
    ForEach ($pack in $InstallLIP) {
        Write-Host "    $pack"
    }

    Write-Host "Using updates:        "
    ForEach ($update in $InstallUpdates) {
        Write-Host "    $update"
    }
    Write-Host "Writing stick at:     " $TargetDrive
    Write-Host ""


    ###
    ## Make the stick.
    ###

    # Windows
    Write-Host "Copying Windows... " -NoNewline
    ## Exclude install.wim, since apparently some Windows source media are not USB EFI compatible (?) and have WIMs >4GB in size.
    & robocopy $WindowsMedia $TargetDrive /mir /xf install.wim | Write-Debug
    Write-Host "done."

    $NewInstallWim = (Join-Path $PSScriptRoot "install.wim")
    $InstallWimMnt = (Join-Path $PSScriptRoot "com-mnt")

    try {
        mkdir $InstallWimMnt | Write-Debug

        Write-Host "Copying the installation image... " -NoNewline
        Export-WindowsImage -DestinationImagePath "$NewInstallWim" -SourceImagePath (Join-Path (Join-Path $WindowsMedia "sources") "install.wim") -SourceName "Windows 10 Enterprise" | Write-Debug
        Write-Host "done."

        # Image update
        if ($InstallLP.Count -gt 0 -or $InstallLIP.Count -gt 0 -or $InstallUpdates -ne $null) {
            Write-Host "Mounting the installation image... " -NoNewline
            Mount-WindowsImage -ImagePath "$NewInstallWim" -Path "$InstallWimMnt" -Name "Windows 10 Enterprise" | Write-Debug
            Write-Host "done."

            Write-Host "Applying language packs... " -NoNewline
            ForEach ($pack in $InstallLP) {
                Add-WindowsPackage -Path "$InstallWimMnt" -PackagePath "$pack" -ErrorAction Stop | Write-Debug
            }
            ForEach ($pack in $InstallLIP) {
                Add-WindowsPackage -Path "$InstallWimMnt" -PackagePath "$pack" -ErrorAction Stop | Write-Debug
            }
            Write-Host "done."

            Write-Host "Applying updates... " -NoNewline
            ForEach ($update in $InstallUpdates) {
                Add-WindowsPackage -Path "$InstallWimMnt" -PackagePath "$update" -ErrorAction Stop | Write-Debug
            }
            Write-Host "done."

            Write-Host "Cleaning up the installation image... " -NoNewline
            Set-ItemProperty (Join-Path (Join-Path $TargetDrive "sources") "lang.ini") -name IsReadOnly -value $false
            & dism /quiet /image:$InstallWimMnt /gen-langini /distribution:$TargetDrive
            & dism /quiet /image:$InstallWimMnt /cleanup-image /startcomponentcleanup /resetbase
            Write-Host "done."

            Write-Host "Unmounting the installation image... " -NoNewline
            Dismount-WindowsImage -Path $InstallWimMnt -Save | Write-Debug
            rmdir $InstallWimMnt
            Write-Host "done."
        }

        Write-Host "Splitting the installation image... " -NoNewline
        Split-WindowsImage -ImagePath "$NewInstallWim" -SplitImagePath (Join-Path (Join-Path $TargetDrive "sources") "install.swm") -FileSize 2047 | Write-Debug
        del $NewInstallWim
        Write-Host "done."
    } catch {
        try { Dismount-WindowsImage -Path $InstallWimMnt -Discard -ErrorAction SilentlyContinue } catch {}
        del $InstallWimMnt -Force -ErrorAction SilentlyContinue
        del $NewInstallWim -Force -ErrorAction SilentlyContinue
        throw
    }

    # Drivers
    Write-Host "Injecting drivers... " -NoNewline
    & robocopy $DriverMedia $DriverDest /mir | Write-Debug
    Write-Host "done."

    # Rigel
    Write-Host "Copying Rigel build... " -NoNewline
    SyncSubdirectories $RigelMedia $TargetDrive | Write-Debug
    & robocopy $RigelMedia $TargetDrive /xd * | Write-Debug
    Write-Host "done."

    # Snag and update the unattend
    Write-Host "Configuring unattend files... " -NoNewline

    $RootUnattendFile = ([io.path]::Combine($TargetDrive, 'AutoUnattend.xml'))
    $InnerUnattendFile = ([io.path]::Combine($TargetDrive, '$oem$', '$1', 'Rigel', 'x64', 'Scripts', 'Provisioning', 'AutoUnattend.xml'))

    ## Handle the root unattend
    $xml = New-Object System.Xml.XmlDocument
    $xml.Load($RootUnattendFile)
    if ($IsOem) {
        Add-AutoUnattend-Key $xml $LicenseKey
    }
    Set-AutoUnattend-Sysprep-Mode -Xml $xml -Shutdown
    $xml.Save($RootUnattendFile)

    ## Handle the inner unattend
    $xml = New-Object System.Xml.XmlDocument
    $xml.Load($InnerUnattendFile)
    if ($IsOem) {
        Add-AutoUnattend-Key $xml "NJMFF-TXKRR-VG2JY-KMV92-FX8WP"
    }
    Set-AutoUnattend-Sysprep-Mode -Xml $xml -Reboot
    $xml.Save($InnerUnattendFile)

    Write-Host "done."


    Write-Host "Cleaning up... " -NoNewline

    Remove-Directory $DriverMedia
    Remove-Directory $RigelMedia

    Write-Host "done."


    Write-Host ""
    Write-Host "Please safely eject your USB stick before removing it."

    if ($InstallUpdates -ne $null) {
        Write-Warning "DO NOT PRE-INSTALL LANGUAGE PACKS AFTER THIS POINT"
        Write-Warning "You have applied a Windows Update to this media. Any pre-installed language packs must be added BEFORE Windows updates."
    }
} finally {
    Stop-Transcript
}

```

<a name="CreateRoom"></a>
## SkypeRoomProvisioningScript.ps1

```
#requires -version 3

<#
//    Copyright (c) Microsoft Corporation. All rights reserved.
//    This code is licensed under the Microsoft Public License.
//    THIS CODE IS PROVIDED *AS IS* WITHOUT WARRANTY OF
//    ANY KIND, EITHER EXPRESS OR IMPLIED, INCLUDING ANY
//    IMPLIED WARRANTIES OF FITNESS FOR A PARTICULAR
//    PURPOSE, MERCHANTABILITY, OR NON-INFRINGEMENT.
//
//    Skype Room Devices Provisioning Script Version 0.33

#>
###############################################################################
#
#    Prerequisites for Office 365
#
#    Connect to Office 365 using Windows PowerShell: http://go.microsoft.com/fwlink/p/?LinkID=614839 
#
#    Connect to Exchange Online using Windows PowerShell: http://go.microsoft.com/fwlink/p/?LinkId=396554
#
#    Connect to Skype for Business Online using Windows PowerShell: http://go.microsoft.com/fwlink/p/?LinkId=691607
#1
###############################################################################

#
# Global Constants
#

$script:strDevice = $null
$script:credAD = $null
$script:credExchange = $null
$script:credSkype = $null
$script:credNewAccount = $null
$script:strHybrid = $null
$script:strEasPolicy = $null
$script:strDatabase = $null
$status = @{}

###############################################################################
#
#    COMMON FUNCTIONS
#
###############################################################################

function CountDown() {
    param($timeSpan)

    while ($timeSpan -gt 0)
  {
    Write-Host '.' -NoNewline
    $timeSpan = $timeSpan - 1
    Start-Sleep -Seconds 1
  }
}
	
function CleanupAndFail {
  # Cleans up and prints an error message
    
  param
  (
    $strMsg
  )
  if ($strMsg)
    {
        PrintError -strMsg ($strMsg)

    }
    Cleanup
    exit 1
}

function Cleanup () {
  # Cleans up set state such as remote powershell sessions
    if ($sessExchange)
    {
        Remove-PSSession -Id $sessExchange
    }
    if ($sessCS)
    {
        Remove-PSSession -Id $sessSkype
    }
}

function PrintError {
    
  param
  (
    $strMsg
  )
  Write-Host $strMsg
}

function PrintSuccess {
    
  param
  (
    $strMsg
  )
  Write-Host $strMsg
}

function PrintAction {
    
  param
  (
    $strMsg
  )
  Write-Host $strMsg
}

function ExitIfError {
    
  param
  (
    $strMsg
  )
  if ($Error)
    {
        CleanupAndFail -strMsg ($strMsg)

    }
}

function DisplayIntroduction {
  #Welcome Screen
  Clear-Host
  Write-Host '*********************************************************************'
  Write-Host ' Microsoft Surface Hub and Skype Room Systems v2 Provisioning Script '
  Write-Host '*********************************************************************'
  Write-Host ''
}

function DeviceChoice {
  Write-Host 'Welcome.'
  Write-Host 'Do you want to provision a'
  Write-Host 'Microsoft Surface Hub or a Skype Room Systems v2 device.'
  $script:strDevice = Read-Host -Prompt 'Enter 1 for a Surface Hub or 2 for a Skype Room Systems v2 device. Or enter 9 to exit and do nothing.'
  if ($script:strDevice -eq 1)
    {
      SHRoutine
    }
    else
    {	
      if ($script:strDevice -eq 2)
        {
          SRSRoutine
        }
        else
        {
          if ($script:strDevice -eq 9)
            {
              Terminate
            }
            else
            {
              Clear-Host
              Write-Host 'Sorry, invalid entry'
              Start-Sleep -Seconds 1
              Clear-Host
              DeviceChoice
            }
        }
    }
}

function SHRoutine {
  Clear-Host
  Write-Host '*********************'
  Write-Host 'Microsoft Surface Hub'
  Write-Host '*********************'
  Write-Host 'You can create just the AD account(s), Exchange account(s),'
  Write-Host 'Skype account(s), or all of the above.'
  $strProvisionMode = Read-Host -Prompt 'Enter 1 for ALL, 2 for AD only, 3 for Exchange only or 4 for Skype only'
  if ($strProvisionMode -eq 1)
    {
      ProvisionAll
    }
    else
    {	
      if ($strProvisionMode -eq 2)
        {
          ProvisionAD
        }
        else
        {
          if ($strProvisionMode -eq 3)
            {
              ProvisionExchange
            }
            else
            {
              if ($strProvisionMode -eq 4)
                {
                  ProvisionSkype
                }
                else
                {
                  Clear-Host
                  Write-Host 'Sorry, invalid entry'
                  Start-Sleep -Seconds 1
                  Clear-Host
                  SHRoutine
                }
            }
        }
    }
		
	
}

function SRSRoutine {
  Clear-Host
  Write-Host '*********************'
  Write-Host 'Skype Room Systems v2'
  Write-Host '*********************'
  Write-Host 'You can Create just the AD account(s), Exchange account(s),'
  Write-Host 'Skype account(s), or all of the above.'
  $strProvisionMode = Read-Host -Prompt 'Enter 1 for ALL, 2 for AD only, 3 for Exchange only or 4 for Skype only'
  if ($strProvisionMode -eq 1)
    {
      ProvisionAll
    }
    else
    {	
      if ($strProvisionMode -eq 2)
        {
          ProvisionAD
        }
        else
        {
          if ($strProvisionMode -eq 3)
            {
              ProvisionExchange
            }
            else
            {
              if ($strProvisionMode -eq 4)
                {
                  ProvisionSkype
                }
                else
                {
                  Clear-Host
                  Write-Host 'Sorry, invalid entry'
                  Start-Sleep -Seconds 1
                  Clear-Host
                  SRSRoutine
                }
            }
        }
    }
}

function ProvisionAll {
  ProvisionAD
  ProvisionExchange
  ProvisionSkype
}

function ProvisionAD {
  Clear-Host
  Write-Host '*************************************'
  Write-Host 'Provision Active Directory / Azure AD'
  Write-Host '*************************************'
  Write-Host 'Will you be creating your AD user on premises or in the cloud?'
  $strADUser = Read-Host -Prompt 'Enter 1 for on premises or 2 for in the cloud.'
  if ($strADUser -eq 1)
    {
      ProvisionLocalAD
    }
    else
    {
      if ($strADUser -eq 2)
        {
          ProvisionCloudAD
        }
        else
        {
          Clear-Host
          Write-Host 'Sorry, invalid entry'
          Start-Sleep -Seconds 1
          Clear-Host
          ProvisionAD
        }
    }
}

function ProvisionLocalAD {
  Clear-Host
  Write-Host '********************************'
  Write-Host 'Provision Local Active Directory'
  Write-Host '********************************'
  GatherHybridState
  GatherLocalADCreds
  CreateLocalAD
	
  if ($strHybrid -eq 1 -and $strProvisionMode -eq 1)
  {
    Write-Host 'Please wait for an AADSync to occur and validate the user has been replicated.'
    Write-Host 'Once you ensure the account exists in Office 365 please continue.'
    Pause
  }
}

function GatherHybridState {
  $script:strHybrid = Read-Host -Prompt 'Are the users in your tenant synced to Office 365? 1 for Yes 2 for No'
  if (!($strHybrid -eq 1 -or $strHybrid -eq 2))
    {
      Clear-Host
      Write-Host 'Sorry, invalid entry'
      Start-Sleep -Seconds 1
      Clear-Host
      GatherHybridState
    }

}

function GatherLocalADCreds () {
  #	$credAD = $null
  $script:credAD = Get-Credential -Message 'Enter credentials of an Domain Admin or a user with account creation rights'
  if (!$credAD)
  {
      CleanupAndFail -strMsg ('Valid credentials are required to create and prepare the account.')

  }
}

function CreateLocalAD () {
  ## Collect account data ##
  $script:credNewAccount = (Get-Credential -Message 'Enter the desired UPN and password for this new account')
  $strUpn = $credNewAccount.UserName
  $strAlias = $credNewAccount.UserName.substring(0,$credNewAccount.UserName.indexOf('@'))
  $strDisplayName = Read-Host -Prompt "Please enter the display name you would like to use for $strUpn"1
  if (!$credNewAccount -Or [string]::IsNullOrEmpty($strDisplayName) -Or [string]::IsNullOrEmpty($credNewAccount.UserName) -Or $credNewAccount.Password.Length -le 0)
  {
      CleanupAndFail -strMsg 'Please enter all of the requested data to continue.'
      exit 1
  }
    if ($strProvisionMode -eq 1 -or $strProvisionMode -eq 2)
    {
    New-ADUser -UserPrincipalName $credNewAccount.UserName -SamAccountName $strAlias -AccountPassword $credNewAccount.Password -Name $strDisplayName -DisplayName $strDisplayName -PasswordNeverExpires $true -CannotChangePassword $true -Enabled $false
    }
    Countdown -timeSpan 30
}

function CaptureRoomUPN {
  ## Collect account data ##
  $script:credNewAccount = (Get-Credential -Message 'Enter the existing UPN and password for the room account')
}

function ProvisionCloudAD {
  Clear-Host
  Write-Host '********************************'
  Write-Host 'Provision Azure Active Directory'
  Write-Host '********************************'
  GatherHybridState
  GatherCloudADCreds
  Connect2AzureAD
  CreateCloudAD
  AssignPrimaryCloudLicenses
	
  if ($strHybrid -eq 1 -and $strProvisionMode -eq 1)
  {
    Write-Host 'Please wait for an AADSync to occur and vaidate the user has been replicated.'
    Write-Host 'Once you ensure the account exists in Office 365 the script will continue.'
    Pause
  }
}

function GatherCloudADCreds () {
  #	$credAD = $null
  $script:credAD = Get-Credential -Message 'Please enter the credentials of an O365 Global Administrator'
  if (!$credAD)
  {
      CleanupAndFail -strMsg ('Valid credentials are required to create and prepare the room account.')

  }
}

function Connect2AzureAD {
  try
  {
      Connect-MsolService -Credential $credAD
  }
  catch
  {
      CleanupAndFail -strMsg "Failed to connect to Azure Active Directory. Please check your credentials and try again. Error message: $_"
  }
}

function CreateCloudAD {
  ## Collect account data ##
  $script:credNewAccount = (Get-Credential -Message 'Enter the desired UPN and password for this new room account')
  $strUpn = $credNewAccount.UserName
  $strAlias = $credNewAccount.UserName.substring(0,$credNewAccount.UserName.indexOf('@'))
  $strDisplayName = Read-Host -Prompt "Please enter the display name you would like to use for $strUpn"
  if (!$credNewAccount -Or [string]::IsNullOrEmpty($strDisplayName) -Or [string]::IsNullOrEmpty($credNewAccount.UserName) -Or $credNewAccount.Password.Length -le 7)
  {
    CleanupAndFail -strMsg 'Please enter all of the requested data to continue.'
    exit 1
  }
  if ($strProvisionMode -eq 1 -or $strProvisionMode -eq 2)
  {
    try 
    {
      $Error.Clear()
      $strPlainPass = $credNewAccount.GetNetworkCredential().Password
      New-MsolUser -UserPrincipalName $credNewAccount.UserName -DisplayName $strDisplayName -Password $strPlainPass -PasswordNeverExpires $True -ForceChangePassword $false -UsageLocation US
    }
    catch
    {
    }
    if ($Error)
    {
      $Error.Clear()
      $status['Azure Account Create'] = 'Failed to create Azure AD room account. Please validate if you have the appropriate access.'
    }
          else
      {
        $status['Azure Account Create'] = "Successfully added $strDisplayName to Azure AD"
      }
  }
}

function AssignPrimaryCloudLicenses {
  Clear-Host
    PrintAction -strMsg 'We found the following licenses available for your tenant:'
    $skus = (Get-MsolAccountSku | Where-Object { !$_.AccountSkuID.Contains('INTUNE') -and !$_.AccountSkuID.Contains('PSTN')})
    $i = 1
    Foreach ($strSKU in $skus)
  {
    Write-Host -NoNewline $i
    Write-Host -NoNewLine ': AccountSKUID: '
    Write-Host -NoNewLine $strSKU.AccountSkuid
    Write-Host -NoNewLine ' Active Units: '
    Write-Host -NoNewLine $strSKU.ActiveUnits
    Write-Host -NoNewLine ' Unassigned Units: '
    $iUnassigned = $strSKU.ActiveUnits - $strSKU.ConsumedUnits
    Write-Host $iUnassigned
    $i++
  }
	
  $iLicenseIndex = 0

      do
      {
        $iLicenseIndex = Read-Host -Prompt 'Choose the number for the SKU you want to assign to the room account'
      }
		
    while ($iLicenseIndex -lt 1 -or $iLicenseIndex -gt $skus.Length)
      $strLicenses = $skus[$iLicenseIndex - 1].AccountSkuId
    $strSkuPartNumber = $skus[$iLicenseIndex - 1].SkuPartNumber

      if (![string]::IsNullOrEmpty($strLicenses))
      {
          try 
          {
              $Error.Clear()
              Set-MsolUserLicense -UserPrincipalName $credNewAccount.UserName -AddLicenses $strLicenses
          }
          catch
          {
          }
			
          if ($Error)
          {
              $Error.Clear()
              $status['Office 365 License'] = 'Failed to add a license to the room account. Please make verify if you have enough unassigned licenses.'
          }
          else
            {
                $status['Office 365 License'] = "Successfully added $strSkuPartNumber the account"
          $strMoreLicenses = Read-Host -Prompt 'Would you like to add another SKU such as PSTN Calling? Enter 1 for Yes or 2 for No'
          if ($strMoreLicenses -eq 1)
          {
            AssignOtherCloudLicenses
          }	
            else
            {
              if (!($strMoreLicenses -eq 2))
              {
                Clear-Host
                Write-Host 'Sorry, invalid entry'
                Start-Sleep -Seconds 1
                Clear-Host
                ProvisionAD
                }
            }
            }
    }
}

function AssignOtherCloudLicenses {

    PrintAction -strMsg 'We found the following licenses available for your tenant:'
    $skus = (Get-MsolAccountSku | Where-Object { !$_.AccountSkuID.Contains('INTUNE')
  })
    $i = 1
    Foreach ($strSKU in $skus)
  {
    $iUnassigned = $strSKU.ActiveUnits - $strSKU.ConsumedUnits
    	
	  Write-Host -NoNewLine $i
	  Write-Host -NoNewLine ': AccountSKUID: '
	  Write-Host -NoNewLine $strSKU.AccountSkuID
	  Write-Host -NoNewLine ' Acctive Units: '
	  Write-Host -NoNewLine $strSKU.ActiveUnits
	  Write-Host -NoNewLine ' Unassigned Units '
	  Write-Host $iUnassigned
	
	
    $i++
  }
	
  $iLicenseIndex = 0

      do
      {
        $iLicenseIndex = Read-Host -Prompt 'Choose the number for the SKU you want to add'
      }
		
    while ($iLicenseIndex -lt 1 -or $iLicenseIndex -gt $skus.Length)
      $strLicenses = $skus[$iLicenseIndex - 1].AccountSkuId
    $strSkuPartNumber = $skus[$iLicenseIndex - 1].SkuPartNumber

      if (![string]::IsNullOrEmpty($strLicenses))
      {
          try 
          {
              $Error.Clear()
              Set-MsolUserLicense -UserPrincipalName $credNewAccount.UserName -AddLicenses $strLicenses
          }
          catch
          {
          }
			
          if ($Error)
          {
              $Error.Clear()
              $status['Office 365 License'] = 'Failed to add the additional license to the room account. Please verify if you have enough unassigned licenses.'
          }
          else
            {
                $status['Office 365 Additional License'] = "Successfully added $strSkuPartNumber to the account"
          $strMoreLicenses = Read-Host -Prompt 'Would you like to add any other SKU to the room account? Enter 1 for Yes or 2 for No'
          if ($strMoreLicenses -eq 1)
          {
            AssignOtherCloudLicenses
          }	
            else
            {
              if (!($strMoreLicenses -eq 2))
              {
                Clear-Host
                Write-Host 'Sorry, invalid entry'
                Start-Sleep -Seconds 1
                Clear-Host
                ProvisionAD
                }
            }

            }
    }
}

function ProvisionExchange {
  if (!$credNewAccount)
  {
    CaptureRoomUPN
  }
  Clear-Host
  Write-Host '********************************'
  Write-Host 'Provision Exchange Room Mailbox'
  Write-Host '********************************'
  Write-Host 'Will you be creating your Exchange user on premises or in the cloud?'
  $strExchangeUser = Read-Host -Prompt 'Enter 1 for on premises / hybrid or 2 for in the cloud.'
  if ($strExchangeUser -eq 1)
    {
      ProvisionLocalExchange
    }
    else
    {
      if ($strExchangeUser -eq 2)
        {
          ProvisionCloudExchange
        }
        else
        {
          Clear-Host
          Write-Host 'Sorry, invalid entry'
          Start-Sleep -Seconds 1
          Clear-Host
          ProvisionExchange
        }
    }
}

function ProvisionLocalExchange {
  Clear-Host
  Write-Host '*************************************'
  Write-Host 'Provision Local Exchange Room Mailbox'
  Write-Host '*************************************'
  if (!$credAD)
    {
      CaptureExchangeCreds
    }
    else
    {
      Write-Host 'Are the Exchange user with mailbox creation rights different than the AD credentials?'
      $strSameCreds = Read-Host -Prompt 'Enter 1 for Yes and 2 for No'
      if ($strSameCreds -eq 1)
      {
        CaptureExchangeCreds
      }
      else
      {
        if ($strSameCreds -eq 2)
        {
          $script:credExchange = $credAD
        }
        else
        {
          Clear-Host
          Write-Host 'Sorry, invalid entry'
          Start-Sleep -Seconds 1
          Clear-Host
          ProvisionLocalExchange
        }
      }

    }
	
  $strExchangeServer = Read-Host -Prompt 'Please enter the FQDN of your exchange server (e.g. exch.contoso.com)'
  PrintAction -strMsg 'Connecting to remote sessions. This can occasionally take a while - please do not enter input...'
	
  try 
  {
      $sessExchange = New-PSSession -ConfigurationName microsoft.exchange -Credential $credExchange -AllowRedirection -Authentication Kerberos -ConnectionUri "http://$strExchangeServer/powershell" -WarningAction SilentlyContinue
  }
	
  catch
  {
      CleanupAndFail -strMsg ("Failed to connect to exchange. Please check your credentials and try again. If this continues to fail, you may not have permission for remote powershell - if not, please perform the setup manually. Error message: $_")
  }
	
  PrintSuccess -strMsg 'Connected to Remote Exchange Shell'
  Import-PSSession -Session $sessExchange -AllowClobber -WarningAction SilentlyContinue
	
  # In case there was any uncaught errors
  # ExitIfError -strMsg ('Remote connections failed. Please check your credentials and try again.')
	
  ExchangeDBs
  if($script:strDevice -eq 1)
  {
    EASPolicy
  }
		
  $Error.Clear()
  PrintAction -strMsg 'Creating a new account...'
	
  try
  {
      Enable-Mailbox $credNewAccount.UserName -Alias $credNewAccount.UserName.substring(0,$credNewAccount.UserName.indexOf('@')) -Database $strDatabase
      Clear-Host
    PrintAction -strMsg 'Creating Mailbox'
    Countdown -timeSpan 30
    if($script:strDevice -eq 1) {Set-CASMailbox $credNewAccount.UserName -ActiveSyncMailboxPolicy $strEASpolicy}
    Set-Mailbox $credNewAccount.UserName -Type Room -EnableRoomMailboxAccount $true -RoomMailboxPassword $credNewAccount.Password
    #Need to capture error and give direction
    #You don't have permission to directly change a mailbox account password without providing old password. Reset Password role is required for directly changing password.
  }
	
  catch
  {
  }
	
  ExitIfError -strMsg 'Failed to create a new mailbox on exchange.'

	
  $status['Mailbox Setup'] = 'Successfully created a mailbox for the new account'
  Clear-Host
  $mailbox = Get-Mailbox $credNewAccount.UserName
  $strEmail = $mailbox.WindowsEmailAddress
  PrintSuccess -strMsg "The following mailbox has been created for this room: $strEmail"
  ExchMBXProps
}

function ProvisionCloudExchange {
  Clear-Host
  Write-Host '*************************************'
  Write-Host 'Provision O365 Exchange Room Mailbox'
  Write-Host '*************************************'
  if (!$credAD)
    {
      CaptureEXOCreds
    }
    else
    {
      Write-Host 'Is the Exchange Online admin account different than the Global Administrator account?'
      $strSameCreds = Read-Host -Prompt 'Enter 1 for Yes and 2 for No'
      if ($strSameCreds -eq 1)
      {
        CaptureEXOCreds
        Countdown -timeSpan 120
      }
      else
      {
        if ($strSameCreds -eq 2)
        {
          $script:credExchange = $credAD
          Write-Host 'Waiting for Exchange Online Mailbox to be provisioned'
          Countdown -timeSpan 120
        }
        else
        {
          Clear-Host
          Write-Host 'Sorry, invalid entry'
          Start-Sleep -Seconds 1
          Clear-Host
          ProvisionCloudExchange
        }
      }

    }
  Connect2EXO
  if ($script:strDevice -eq 1) { EASPolicy }
  $Error.Clear()
  PrintAction -strMsg 'Converting user mailbox to a room account...'  
  PrintAction -strMsg 'This process will take around 10 minutes to sync the newly created mailbox to O365 servers.'  
  PrintAction -strMsg 'Please wait.' 
  Countdown -timeSpan 600
  try
  {
      $mailbox = $null
      $mailbox = (Set-Mailbox -Identity $credNewAccount.UserName -MicrosoftOnlineServicesID $credNewAccount.UserName -Type Room)
      $mailbox = Get-Mailbox -Identity $credNewAccount.UserName
    if ($script:strDevice -eq 1) { Set-CASMailbox $credNewAccount.UserName -ActiveSyncMailboxPolicy $strEASpolicy }
    Countdown -timeSpan 120
		
  }

  catch
  {
    PrintAction -strMsg 'Converting mailbox to a room account failed you can do this step manually.' 
  
  }
  ExitIfError -strMsg 'Failed to configure a new room mailbox on exchange.'
  
  $status['Mailbox Setup'] = "Successfully configured a room mailbox for the account $($credNewAccount.UserName)"

  $strEmail = $mailbox.WindowsEmailAddress
  Clear-Host
  PrintSuccess -strMsg "The following mailbox has been created for this room: $strEmail"

  ExchMBXProps
}

function Connect2EXO {
  try
  {
    $sessEXO = New-PSSession -ConfigurationName microsoft.exchange -Credential $credExchange -AllowRedirection -Authentication basic -ConnectionUri 'https://outlook.office365.com/powershell-liveid/' -WarningAction SilentlyContinue
    Import-PSSession -Session $sessEXO -AllowClobber -WarningAction SilentlyContinue
  }
  catch
  {
    CleanupAndFail -strMsg "Failed to connect to Exchange Online. Please check your credentials and try again. Error message: $_"
  }
}

function CaptureExchangeCreds {
  $script:credExchange = Get-Credential -Message 'Enter credentials of an Exchange user with mailbox creation rights'
  if (!$credExchange)
  {
      CleanupAndFail -strMsg ('Valid credentials are required to create and prepare the account.')

  }
}

function CaptureEXOCreds () {
  #	$credAD = $null
  $script:credExchange = Get-Credential -Message 'Enter credentials of an Exchange Online Administrator'
  if (!$credExchange)
  {
      CleanupAndFail -strMsg ('Valid credentials are required to create and prepare the account.')

  }
}

function ExchangeDBs {
  Clear-Host
  PrintAction -strMsg 'We found the following databases in you on premises Exchange environment:'
  $exDBs = (Get-MailboxDatabase)
  $i = 1
  Foreach ($DB in $exDBs)
  {
    Write-Host -NoNewline $i
    Write-Host -NoNewLine ': Database Name: '
    Write-Host $DB.Name
    $i++
  }
	
    $iDatabaseIndex = 0

    do

  {
        $iDatabaseIndex = Read-Host -Prompt 'Choose the database you want the Room Mailbox created in'
    }
  while ($iDatabaseIndex -lt 1 -or $iDatabaseIndex -gt $exDBs.Length)
    $script:strDatabase = $exDBs[$iDatabaseIndex - 1].Name
}

function EASPolicy {
  Clear-Host
  PrintAction -strMsg 'A valid Exchange Active Sync Policy is Required. Would you like to use an existing Policy or Create a new one?'
  $strEASDecision = Read-Host -Prompt 'Enter 1 for Existing or 2 for New'
  if ($strEASDecision -eq 1)
    {
    EASPolicyExisting
    }
    else
    {
      if ($strEASDecision -eq 2)
        {
        EASPolicyNew
        }
        else
        {
          Clear-Host
          Write-Host 'Sorry, invalid entry'
          Start-Sleep -Seconds 1
          Clear-Host
          ProvisionExchange
        }
    }
					
}

function EASPolicyExisting {
  PrintAction -strMsg 'A valid Exchange Active Sync Policy is Required - the following policies were found:'
  $exEasPol = (Get-MobileDeviceMailboxPolicy)
  $i = 1
  Foreach ($POL in $exEasPol)
  {
    if ($POL.PasswordEnabled -eq $false)
    {
      $strValidity = 'Valid, will work'
    }
    else
    {
      $strValidity = 'Password Policy Enabled, will not work'
    }
    Write-Host -NoNewline $i
    Write-Host -NoNewLine ': Policy Name: '
    Write-Host -NoNewline $POL.Name
    Write-Host -NoNewline ' - '
    Write-Host $strValidity
    $i++
  }
	
    $iPolicyIndex = 0

    do
  {
        $iPolicyIndex = Read-Host -Prompt 'Choose the Exchange Policy you would like to use:'
    }

  while ($iPolicyIndex -lt 1 -or $iPolicyIndex -gt $exEasPol.Length)
    $script:strEasPolicy = $exEasPol[$iPolicyIndex - 1].Name
}

function EASPolicyNew {
  $script:strEasPolicy = (New-MobileDeviceMailboxPolicy -Name 'SurfaceHubs' -PasswordEnabled $false)
}

function ExchMBXProps {
  PrintAction -strMsg 'You may optionally configure Mailbox Room Properties using this script (or manually at a later time)'
  PrintAction -strMsg 'Microsoft recommends enabling Automatic Calendar Processing with a response - would you like to configure'
  PrintAction -strMsg 'these options now via the script?'
  $strMBXPropsDecision = Read-Host -Prompt 'Enter 1 for Yes or 2 for No'
  if ($strMBXPropsDecision -eq 1)
    {
  
      Set-CalendarProcessing -Identity $credNewAccount.UserName -AutomateProcessing AutoAccept -AddOrganizerToSubject $false -AllowConflicts $false -DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false
      Set-CalendarProcessing -Identity $credNewAccount.UserName -AddAdditionalResponse $true -AdditionalResponse 'This is a <tla rid="Skype Meeting"/> capable room!'
    }
    else
    {
      if (!($strMBXPropsDecision -eq 2))
        {
          Clear-Host
          Write-Host 'Sorry, invalid entry'
          Start-Sleep -Seconds 1
          Clear-Host
          ProvisionExchange
        }
    }
}

function ProvisionSkype {
  if (!$credNewAccount)
  {
    CaptureRoomUPN
  }
  Clear-Host
  Write-Host '********************************'
  Write-Host 'Provision Skype'
  Write-Host '********************************'
  Write-Host 'Will you be creating your Skype user on premises or in the cloud?'
  $strSkypeUser = Read-Host -Prompt 'Enter 1 for on premises / hybrid or 2 for in the cloud.'
  if ($strSkypeUser -eq 1)
    {
      ProvisionLocalSkype
    }
    else
    {
      if ($strSkypeUser -eq 2)
        {
          ProvisionCloudSkype
        }
        else
        {
          Clear-Host
          Write-Host 'Sorry, invalid entry'
          Start-Sleep -Seconds 1
          Clear-Host
          ProvisionSkype
        }
    }
}

function ProvisionLocalSkype {
  Clear-Host
  Write-Host '*************************************'
  Write-Host 'Provision Local Skyp User'
  Write-Host '*************************************'
  if (!$credAD)
    {
      CaptureSkypeCreds
    }
    else
    {
      Write-Host 'Are the Skype Administrator credentials different than the AD credentials?'
      $strSameCreds = Read-Host -Prompt 'Enter 1 for Yes and 2 for No'
      if ($strSameCreds -eq 1)
      {
        CaptureSkypeCreds
      }
      else
      {
        if ($strSameCreds -eq 2)
        {
          $script:credSkype = $credAD
        }
        else
        {
          Clear-Host
          Write-Host 'Sorry, invalid entry'
          Start-Sleep -Seconds 1
          Clear-Host
          ProvisionLocalExchange
        }
      }

    }
	
  $strSkypeFQDN = Read-Host -Prompt 'Please enter the FQDN of a Skype server (e.g. skype.contoso.com) for Remote PowerShell'
  PrintAction -strMsg 'Connecting to remote session. This can occasionally take a while - please do not enter input...'
	
  try 
  {
      $sessSkype = New-PSSession -Credential $credSkype -ConnectionURI "https://$strSkypeFQDN/OcsPowershell" -AllowRedirection -WarningAction SilentlyContinue
  }
	
  catch
  {
      CleanupAndFail -strMsg ("Failed to connect to exchange. Please check your credentials and try again. If this continues to fail, you may not have permission for remote powershell - if not, please perform the setup manually. Error message: $_")
  }
	
  PrintSuccess -strMsg 'Connected to Remote Skype Shell'
  Import-PSSession -Session $sessSkype -AllowClobber -WarningAction SilentlyContinue
	
  # In case there was any uncaught errors
  ExitIfError -strMsg ('Remote connections failed. Please check your credentials and try again.')
	
  $Error.Clear()
  PrintAction -strMsg 'Configuring account for Skype for Business.'
	
  # Getting registrar pool
  Clear-Host
  $strRegPool = $strSkypeFQDN
  $Error.Clear()
  $strRegPoolEntry = Read-Host -Prompt "Enter a Skype for Business Registrar Pool, or leave blank if [$strRegPool] is a Standard Editon Pool"
	
  if (![string]::IsNullOrEmpty($strRegPoolEntry))
  {
      $strRegPool = $strRegPoolEntry
  }
	
  PrintAction -strMsg 'Enabling Skype for Business...'
  $Error.Clear()

	
  try
  {
      Enable-CsMeetingRoom -Identity $credNewAccount.UserName -RegistrarPool $strRegPool -SipAddressType EmailAddress
    Countdown -timeSpan 30
  }
	
  catch
  {
  } 

  if ($Error)
  {
      PrintError -strMsg 'Failed to setup the Skype for Business meeting room resource - you can run this Skype Room Provisioning Script to try again.'
      $Error.Clear()

  }
  else
  {
      PrintSuccess -strMsg 'Successfully enabled the account as a Skype for Business meeting room'
    ProvisionSkypeEV
  }
	
}

function ProvisionCloudSkype {
  Clear-Host
  Write-Host '*******************************************'
  Write-Host 'Provision Skype for Business Online Account'
  Write-Host '*******************************************'
  if (!$credAD)
    {
      CaptureS4BOCreds
    }
    else
    {
      Write-Host 'Is the Skype for Business Online admin account different than the Global Administrator account?'
      $strSameCreds = Read-Host -Prompt 'Enter 1 for Yes and 2 for No'
      if ($strSameCreds -eq 1)
      {
        CaptureS4BOCreds
      }
      else
      {
        if ($strSameCreds -eq 2)
        {
          $script:credSkype = $credAD
        }
        else
        {
          Clear-Host
          Write-Host 'Sorry, invalid entry'
          Start-Sleep -Seconds 1
          Clear-Host
          ProvisionCloudExchange
        }
      }

    }
  Connect2S4BO
  # Getting registrar pool
	
    try
      {
       PrintAction -strMsg 'We have now connected to Skype for Business, please wait while we attempt to set up the meeting room' 
       Countdown -timeSpan 300
 
        $strRegPool = $null

        $strRegPool = (Get-CsTenant).TenantPoolExtension
    }
	
    catch
    {
    }
    
  if ($Error)
    {
        $Error.Clear()

        $strRegPool = ''

        Write-Host 'We failed to lookup your Skype for Business Registrar Pool, but you can still enter it manually'
    }
	
    else
    {
        $strRegPool = $strRegPool[0].Substring($strRegPool[0].IndexOf(':') + 1)
    }
	
  $Error.Clear()
  try
  {
    Enable-CsMeetingRoom -Identity $credNewAccount.UserName -RegistrarPool $strRegPool -SipAddressType EmailAddress
  }
	
  catch
  {
  }

  ExitIfError -strMsg ('Failed to setup Skype for Business meeting room')

  PrintSuccess -strMsg "Successfully enabled $strRoomUri as a Skype for Business meeting room"
  ProvisionSkypeEV
}

function Connect2S4BO {
  try
  {
    $sessSkype = New-CsOnlineSession -Credential $credSkype
    Import-PSSession -Session $sessSkype -AllowClobber -WarningAction SilentlyContinue
  }
  catch
  {
    CleanupAndFail -strMsg "Failed to connect to Skype for Business Online. Please check your credentials and try again. Error message: $_"
  }
}

function ProvisionSkypeEV {
  Clear-Host
  PrintAction -strMsg 'Would you like to configure Enterprise Voice for the Room?'
  $strSkypeEVDecision = Read-Host -Prompt 'Enter 1 for Yes or 2 for No'
    if ($strSkypeEVDecision -eq 1)
    {
      PrintAction -strMsg 'A valid E.164 number is required (ex. 15255551000 or 1525551000;ext=1000)'
      $strEVInput = Read-Host -Prompt 'Enter a valid E.164 number'
      if (!$strEVInput)
        {
          Clear-Host
          Write-Host 'Sorry, invalid entry'
          Start-Sleep -Seconds 1
          Clear-Host
          ProvisionSkypeEV
        }
        else
        {
          try
          {
            $LineURI = 'tel:+' + $strEVInput
            PrintAction -strMsg "Your LineURI will be configured as $LineURI - is that correct?"
            $strEVOkay = Read-Host -Prompt 'Enter 1 for Accept and configure or 2 to Go Back'
            if ($strEVOkay -eq 1)
              {
                Set-CsMeetingRoom -Identity $credNewAccount.UserName -LineURI $LineURI -EnterpriseVoiceEnabled $true
              }
              else
              {
              if ($strEVOkay -eq 2)
                {
                  ProvisionSkypeEV
                }
                else
                {
                  Clear-Host
                  Write-Host 'Sorry, invalid entry'
                  Start-Sleep -Seconds 1
                  Clear-Host
                  ProvisionSkypeEV
                }
              }
          }
          catch
          {
          }
        }
					
    }
    else
    {
      if (!($strSkypeEVDecision -eq 2))
        {
          Clear-Host
          Write-Host 'Sorry, invalid entry'
          Start-Sleep -Seconds 1
          Clear-Host
          ProvisionExchange
        }
    }
}

function CaptureS4BOCreds () {
  #	$credAD = $null
  $script:credSkype = Get-Credential -Message 'Enter credentials of an Skype for Business Online Administrator'
  if (!$credSkype)
  {
      CleanupAndFail -strMsg ('Valid credentials are required to create and prepare the account.')

  }
}

function Terminate {
  Clear-Host
  Write-Host 'Application Terminated as Requested'
  Start-Sleep -Seconds 1
  Exit 1
}

DisplayIntroduction
DeviceChoice
Cleanup
Clear-Host
PrintAction -strMsg 'Summary for Actions'
if ($status.Count -gt 0)
{
    ForEach($k in $status.Keys) 
    {
        $v = $status[$k]
        $color = 'yellow'
        if ($v[0] -eq 'S') { $color = 'green' }
        elseif ($v[0] -eq 'F') 
        {
            $color = 'red' 
            $v += ' Go to http://aka.ms/shubtshoot for help'
        }

        Write-Host $v
    }
}
else
{
    PrintError -strMsg 'The process could not be completed'
}

```
<a name="OMSVIEW"></a>
## SkypeRoomSystems_v2.omsview

```
{
    "$schema": "http://schema.management.azure.com/schemas/2015-01-01/deploymentTemplate.json#",
    "contentVersion": "1.0.0.0",
    "parameters": {
        "location": {
            "type": "string",
            "defaultValue": ""
        },
        "resourcegroup": {
            "type": "string",
            "defaultValue": ""
        },
        "subscriptionId": {
            "type": "string",
            "defaultValue": ""
        },
        "workspace": {
            "type": "string",
            "defaultValue": ""
        },
        "workspaceapiversion": {
            "type": "string",
            "defaultValue": ""
        }
    },
    "resources": [
        {
            "apiVersion": "[parameters('workspaceapiversion')]",
            "name": "[parameters('workspace')]",
            "type": "Microsoft.OperationalInsights/workspaces",
            "location": "[parameters('location')]",
            "id": "[Concat('/subscriptions/', parameters('subscriptionId'), '/resourceGroups/', parameters('resourcegroup'), '/providers/Microsoft.OperationalInsights/workspaces/', parameters('workspace'))]",
            "resources": [
                {
                    "apiVersion": "2015-11-01-preview",
                    "name": "Skype Room Systems",
                    "type": "views",
                    "location": "[parameters('location')]",
                    "id": "[Concat('/subscriptions/', parameters('subscriptionId'), '/resourceGroups/', parameters('resourcegroup'), '/providers/Microsoft.OperationalInsights/workspaces/', parameters('workspace'),'/views/Skype Room Systems')]",
                    "dependson": [
                        "[Concat('/subscriptions/', parameters('subscriptionId'), '/resourceGroups/', parameters('resourcegroup'), '/providers/Microsoft.OperationalInsights/workspaces/', parameters('workspace'))]"
                    ],
                    "properties": {
                        "Id": "Skype Room Systems",
                        "Name": "Skype Room Systems",
                        "Author": "turgayo@microsoft.com",
                        "Source": "Local",
                        "Version": 2,
                        "Dashboard": [
                            {
                                "Id": "NumberTileListBuilderBlade",
                                "Type": "Blade",
                                "Version": 0,
                                "Configuration": {
                                    "General": {
                                        "title": "Heartbeat Status",
                                        "newGroup": true,
                                        "icon": "",
                                        "useIcon": false
                                    },
                                    "Tile": {
                                        "Legend": "Active devices (heartbeat sent in the last 20 minutes)",
                                        "Query": "Event | where EventLog == \"Skype Room System\" and SRSOperationName_CF == \"Heartbeat\" and TimeGenerated > ago(20m) | summarize AggregatedValue = count() by Computer | count",
                                        "NavigationSelect": {}
                                    },
                                    "List": {
                                        "Query": "Event | where EventLog == \"Skype Room System\" and SRSOperationName_CF == \"Heartbeat\" and TimeGenerated > ago(20m) | summarize TimeGenerated = max(TimeGenerated) by Computer | order by TimeGenerated",
                                        "HideGraph": false,
                                        "enableSparklines": false,
                                        "ColumnsTitle": {
                                            "Name": "Display Name",
                                            "Value": "Last Heartbeat"
                                        },
                                        "Color": "#0072c6",
                                        "thresholds": {
                                            "isEnabled": false,
                                            "values": [
                                                {
                                                    "name": "Normal",
                                                    "threshold": "Default",
                                                    "color": "#009e49",
                                                    "isDefault": true
                                                },
                                                {
                                                    "name": "Warning",
                                                    "threshold": "60",
                                                    "color": "#fcd116",
                                                    "isDefault": false
                                                },
                                                {
                                                    "name": "Error",
                                                    "threshold": "90",
                                                    "color": "#ba141a",
                                                    "isDefault": false
                                                }
                                            ]
                                        },
                                        "NameDSVSeparator": "",
                                        "NavigationQuery": "search {selected item} | where EventLog == \"Skype Room System\" and SRSOperationName_CF == \"Heartbeat\" | summarize arg_max(TimeGenerated, *) by Computer | project TimeGenerated, Computer, SRSDisplayName_CF, SRSAlias_CF, SRSAppVersion_CF, SRSOSVersion_CF, SRSOSLongVersion_CF, SRSIPv4Address_CF, SRSIPv6Address_CF, SRSOperationName_CF, SRSOperationResult_CF, SRSResourceState_CF, SRSEventDescription_CF",
                                        "NavigationSelect": {
                                            "NavigationQuery": "search {selected item} | where EventLog == \"Skype Room System\" and SRSOperationName_CF == \"Heartbeat\" | summarize arg_max(TimeGenerated, *) by Computer | project TimeGenerated, Computer, SRSDisplayName_CF, SRSAlias_CF, SRSAppVersion_CF, SRSOSVersion_CF, SRSOSLongVersion_CF, SRSIPv4Address_CF, SRSIPv6Address_CF, SRSOperationName_CF, SRSOperationResult_CF, SRSResourceState_CF, SRSEventDescription_CF"
                                        }
                                    }
                                }
                            },
                            {
                                "Id": "NumberTileListBuilderBlade",
                                "Type": "Blade",
                                "Version": 0,
                                "Configuration": {
                                    "General": {
                                        "title": "",
                                        "newGroup": false,
                                        "icon": "",
                                        "useIcon": false
                                    },
                                    "Tile": {
                                        "Query": "Event | where EventLog == \"Skype Room System\" and SRSOperationName_CF == \"Heartbeat\" | summarize LastHB = max(TimeGenerated) by Computer | where LastHB < ago(20m) | count",
                                        "Legend": "Inactive Devices (no heartbeat message sent in the last 20 minutes)",
                                        "NavigationSelect": {}
                                    },
                                    "List": {
                                        "Query": "Event | where EventLog == \"Skype Room System\" and SRSOperationName_CF == \"Heartbeat\" | summarize TimeGenerated = max(TimeGenerated) by Computer | where TimeGenerated < ago(20m) | order by TimeGenerated",
                                        "HideGraph": false,
                                        "enableSparklines": false,
                                        "operation": "Summary",
                                        "ColumnsTitle": {
                                            "Name": "Display Name",
                                            "Value": "Last Heartbeat"
                                        },
                                        "Color": "#0072c6",
                                        "thresholds": {
                                            "isEnabled": false,
                                            "values": [
                                                {
                                                    "name": "Normal",
                                                    "threshold": "Default",
                                                    "color": "#009e49",
                                                    "isDefault": true
                                                },
                                                {
                                                    "name": "Warning",
                                                    "threshold": "60",
                                                    "color": "#fcd116",
                                                    "isDefault": false
                                                },
                                                {
                                                    "name": "Error",
                                                    "threshold": "90",
                                                    "color": "#ba141a",
                                                    "isDefault": false
                                                }
                                            ]
                                        },
                                        "NameDSVSeparator": "",
                                        "NavigationQuery": "search {selected item} | where EventLog == \"Skype Room System\" and SRSOperationName_CF == \"Heartbeat\" | summarize arg_max(TimeGenerated, *) by Computer | project TimeGenerated, Computer, SRSDisplayName_CF, SRSAlias_CF, SRSAppVersion_CF, SRSOSVersion_CF, SRSOSLongVersion_CF, SRSIPv4Address_CF, SRSIPv6Address_CF, SRSOperationName_CF, SRSOperationResult_CF, SRSResourceState_CF, SRSEventDescription_CF",
                                        "NavigationSelect": {
                                            "NavigationQuery": "search {selected item} | where EventLog == \"Skype Room System\" and SRSOperationName_CF == \"Heartbeat\" | summarize arg_max(TimeGenerated, *) by Computer | project TimeGenerated, Computer, SRSDisplayName_CF, SRSAlias_CF, SRSAppVersion_CF, SRSOSVersion_CF, SRSOSLongVersion_CF, SRSIPv4Address_CF, SRSIPv6Address_CF, SRSOperationName_CF, SRSOperationResult_CF, SRSResourceState_CF, SRSEventDescription_CF"
                                        }
                                    }
                                }
                            },
                            {
                                "Id": "NumberTileListBuilderBlade",
                                "Type": "Blade",
                                "Version": 0,
                                "Configuration": {
                                    "General": {
                                        "title": "Hardware Errors",
                                        "newGroup": true,
                                        "icon": "",
                                        "useIcon": false
                                    },
                                    "Tile": {
                                        "Query": "Event | where EventLog == \"Skype Room System\" and EventLevelName == \"Error\" and EventID == \"3001\" and TimeGenerated > ago(1h) | summarize AggregatedValue = count() by Computer | count",
                                        "Legend": "Devices that experienced a hardware error in the last hour",
                                        "NavigationSelect": {}
                                    },
                                    "List": {
                                        "Query": "Event | where EventLog == \"Skype Room System\" and EventLevelName == \"Error\" and EventID == \"3001\" and TimeGenerated > ago(1h) | summarize TimeGenerated = max(TimeGenerated) by Computer",
                                        "HideGraph": false,
                                        "enableSparklines": false,
                                        "operation": "Summary",
                                        "ColumnsTitle": {
                                            "Name": "Display Name",
                                            "Value": "Last Error"
                                        },
                                        "Color": "#0072c6",
                                        "thresholds": {
                                            "isEnabled": false,
                                            "values": [
                                                {
                                                    "name": "Normal",
                                                    "threshold": "Default",
                                                    "color": "#009e49",
                                                    "isDefault": true
                                                },
                                                {
                                                    "name": "Warning",
                                                    "threshold": "60",
                                                    "color": "#fcd116",
                                                    "isDefault": false
                                                },
                                                {
                                                    "name": "Error",
                                                    "threshold": "90",
                                                    "color": "#ba141a",
                                                    "isDefault": false
                                                }
                                            ]
                                        },
                                        "NameDSVSeparator": "",
                                        "NavigationQuery": "search {selected item} | where EventLog == \"Skype Room System\" and EventID == 3001 and EventLevelName == \"Error\" | summarize arg_max(TimeGenerated, *) by Computer | project TimeGenerated, Computer, SRSDisplayName_CF, SRSAlias_CF, SRSAppVersion_CF, SRSOSVersion_CF, SRSOSLongVersion_CF, SRSIPv4Address_CF, SRSIPv6Address_CF, SRSOperationName_CF, SRSOperationResult_CF, SRSResourceState_CF, SRSConfMicrophoneStatus_CF, SRSConfSpeakerStatus_CF, SRSDefaultSpeakerStatus_CF, SRSCameraStatus_CF, SRSFORDStatus_CF, SRSMotionSensorStatus_CF, SRSHDMIIngestStatus_CF, SRSEventDescription_CF | sort by TimeGenerated desc",
                                        "NavigationSelect": {
                                            "NavigationQuery": "search {selected item} | where EventLog == \"Skype Room System\" and EventID == 3001 and EventLevelName == \"Error\" | summarize arg_max(TimeGenerated, *) by Computer | project TimeGenerated, Computer, SRSDisplayName_CF, SRSAlias_CF, SRSAppVersion_CF, SRSOSVersion_CF, SRSOSLongVersion_CF, SRSIPv4Address_CF, SRSIPv6Address_CF, SRSOperationName_CF, SRSOperationResult_CF, SRSResourceState_CF, SRSConfMicrophoneStatus_CF, SRSConfSpeakerStatus_CF, SRSDefaultSpeakerStatus_CF, SRSCameraStatus_CF, SRSFORDStatus_CF, SRSMotionSensorStatus_CF, SRSHDMIIngestStatus_CF, SRSEventDescription_CF | sort by TimeGenerated desc"
                                        }
                                    }
                                }
                            },
                            {
                                "Id": "SingleQueryDonutBuilderBladeV1",
                                "Type": "Blade",
                                "Version": 0,
                                "Configuration": {
                                    "General": {
                                        "title": "Skype Room Systems v2 application details",
                                        "newGroup": true,
                                        "icon": "",
                                        "useIcon": false
                                    },
                                    "Header": {
                                        "Title": "Application versions",
                                        "Subtitle": "Devices running specific application versions"
                                    },
                                    "Donut": {
                                        "Query": "Event | where EventLog == \"Skype Room System\" and SRSOperationName_CF == \"Heartbeat\" | summarize App_Version = max(SRSAppVersion_CF) by Computer | summarize AggregatedValue = count() by App_Version | sort by App_Version asc",
                                        "CenterLegend": {
                                            "Text": "Devices",
                                            "Operation": "Sum",
                                            "ArcsToSelect": []
                                        },
                                        "Options": {
                                            "colors": [
                                                "#00188f",
                                                "#0072c6",
                                                "#00bcf2"
                                            ],
                                            "valueColorMapping": []
                                        },
                                        "NavigationSelect": {}
                                    },
                                    "List": {
                                        "Query": "Event | where EventLog == \"Skype Room System\" and SRSOperationName_CF == \"Heartbeat\" | summarize SRSAppVersion_CF = max(SRSAppVersion_CF) by Computer | sort by Computer asc",
                                        "HideGraph": true,
                                        "enableSparklines": false,
                                        "operation": "Summary",
                                        "ColumnsTitle": {
                                            "Name": "Display Name",
                                            "Value": ""
                                        },
                                        "Color": "#0072c6",
                                        "thresholds": {
                                            "isEnabled": false,
                                            "values": [
                                                {
                                                    "name": "Normal",
                                                    "threshold": "Default",
                                                    "color": "#009e49",
                                                    "isDefault": true
                                                },
                                                {
                                                    "name": "Warning",
                                                    "threshold": "60",
                                                    "color": "#fcd116",
                                                    "isDefault": false
                                                },
                                                {
                                                    "name": "Error",
                                                    "threshold": "90",
                                                    "color": "#ba141a",
                                                    "isDefault": false
                                                }
                                            ]
                                        },
                                        "NameDSVSeparator": "",
                                        "NavigationQuery": "search {selected item} | where EventLog == \"Skype Room System\" and SRSOperationName_CF == \"Heartbeat\" | summarize arg_max(TimeGenerated, *) by Computer | project TimeGenerated, Computer, SRSDisplayName_CF, SRSAlias_CF, SRSAppVersion_CF, SRSOSVersion_CF, SRSOSLongVersion_CF, SRSIPv4Address_CF, SRSIPv6Address_CF, SRSOperationName_CF, SRSOperationResult_CF, SRSResourceState_CF, SRSEventDescription_CF",
                                        "NavigationSelect": {
                                            "NavigationQuery": "search {selected item} | where EventLog == \"Skype Room System\" and SRSOperationName_CF == \"Heartbeat\" | summarize arg_max(TimeGenerated, *) by Computer | project TimeGenerated, Computer, SRSDisplayName_CF, SRSAlias_CF, SRSAppVersion_CF, SRSOSVersion_CF, SRSOSLongVersion_CF, SRSIPv4Address_CF, SRSIPv6Address_CF, SRSOperationName_CF, SRSOperationResult_CF, SRSResourceState_CF, SRSEventDescription_CF"
                                        }
                                    }
                                }
                            },
                            {
                                "Id": "NumberTileListBuilderBlade",
                                "Type": "Blade",
                                "Version": 0,
                                "Configuration": {
                                    "General": {
                                        "title": "",
                                        "newGroup": false,
                                        "icon": "",
                                        "useIcon": false
                                    },
                                    "Tile": {
                                        "Query": "Event | where EventLog == \"Skype Room System\" and EventLevelName == \"Error\" and EventID == \"2001\" and TimeGenerated > ago(1h) | summarize AggregatedValue = count() by Computer | count",
                                        "Legend": "Devices that experienced an application error in the last hour",
                                        "NavigationSelect": {}
                                    },
                                    "List": {
                                        "Query": "Event | where EventLog == \"Skype Room System\" and EventLevelName == \"Error\" and EventID == \"2001\" and TimeGenerated > ago(1h) | summarize TimeGenerated = max(TimeGenerated) by Computer | order by TimeGenerated",
                                        "HideGraph": false,
                                        "enableSparklines": false,
                                        "operation": "Summary",
                                        "ColumnsTitle": {
                                            "Name": "Display Name",
                                            "Value": "Last Error"
                                        },
                                        "Color": "#0072c6",
                                        "thresholds": {
                                            "isEnabled": false,
                                            "values": [
                                                {
                                                    "name": "Normal",
                                                    "threshold": "Default",
                                                    "color": "#009e49",
                                                    "isDefault": true
                                                },
                                                {
                                                    "name": "Warning",
                                                    "threshold": "60",
                                                    "color": "#fcd116",
                                                    "isDefault": false
                                                },
                                                {
                                                    "name": "Error",
                                                    "threshold": "90",
                                                    "color": "#ba141a",
                                                    "isDefault": false
                                                }
                                            ]
                                        },
                                        "NameDSVSeparator": "",
                                        "NavigationQuery": "search {selected item} | where EventLog == \"Skype Room System\" and EventID == 2001 and EventLevelName == \"Error\" | summarize arg_max(TimeGenerated, *) by Computer | project TimeGenerated, Computer, SRSDisplayName_CF, SRSAlias_CF, SRSAppVersion_CF, SRSOSVersion_CF, SRSOSLongVersion_CF, SRSIPv4Address_CF, SRSIPv6Address_CF, SRSOperationName_CF, SRSOperationResult_CF, SRSResourceState_CF, SRSEventDescription_CF | sort by TimeGenerated desc",
                                        "NavigationSelect": {
                                            "NavigationQuery": "search {selected item} | where EventLog == \"Skype Room System\" and EventID == 2001 and EventLevelName == \"Error\" | summarize arg_max(TimeGenerated, *) by Computer | project TimeGenerated, Computer, SRSDisplayName_CF, SRSAlias_CF, SRSAppVersion_CF, SRSOSVersion_CF, SRSOSLongVersion_CF, SRSIPv4Address_CF, SRSIPv6Address_CF, SRSOperationName_CF, SRSOperationResult_CF, SRSResourceState_CF, SRSEventDescription_CF | sort by TimeGenerated desc"
                                        }
                                    }
                                }
                            },
                            {
                                "Id": "NumberTileListBuilderBlade",
                                "Type": "Blade",
                                "Version": 0,
                                "Configuration": {
                                    "General": {
                                        "title": "",
                                        "newGroup": false,
                                        "icon": "",
                                        "useIcon": false
                                    },
                                    "Tile": {
                                        "Query": "Event | where EventLog == \"Skype Room System\" and EventID == \"4000\" and TimeGenerated > ago(24h) | summarize AggregatedValue = count() by Computer | count",
                                        "Legend": "Devices where the application was restarted in the last 24 hours, and number of restarts",
                                        "NavigationSelect": {}
                                    },
                                    "List": {
                                        "Query": "Event | where EventLog == \"Skype Room System\" and EventID == \"4000\" and TimeGenerated > ago(24h) | order by TimeGenerated | summarize AggregatedValue = count(EventID) by Computer",
                                        "HideGraph": false,
                                        "enableSparklines": false,
                                        "operation": "Summary",
                                        "ColumnsTitle": {
                                            "Name": "Display Name",
                                            "Value": "Restarts"
                                        },
                                        "Color": "#0072c6",
                                        "thresholds": {
                                            "isEnabled": false,
                                            "values": [
                                                {
                                                    "name": "Normal",
                                                    "threshold": "Default",
                                                    "color": "#009e49",
                                                    "isDefault": true
                                                },
                                                {
                                                    "name": "Warning",
                                                    "threshold": "60",
                                                    "color": "#fcd116",
                                                    "isDefault": false
                                                },
                                                {
                                                    "name": "Error",
                                                    "threshold": "90",
                                                    "color": "#ba141a",
                                                    "isDefault": false
                                                }
                                            ]
                                        },
                                        "NameDSVSeparator": "",
                                        "NavigationQuery": "search {selected item} | where EventLog == \"Skype Room System\" and EventID == \"4000\" and TimeGenerated > ago(24h) | project TimeGenerated, Computer, SRSDisplayName_CF, SRSAlias_CF, SRSAppVersion_CF, SRSOSVersion_CF, SRSOSLongVersion_CF, SRSIPv4Address_CF, SRSIPv6Address_CF, SRSOperationName_CF, SRSOperationResult_CF, SRSResourceState_CF, SRSEventDescription_CF ",
                                        "NavigationSelect": {
                                            "NavigationQuery": "search {selected item} | where EventLog == \"Skype Room System\" and EventID == \"4000\" and TimeGenerated > ago(24h) | project TimeGenerated, Computer, SRSDisplayName_CF, SRSAlias_CF, SRSAppVersion_CF, SRSOSVersion_CF, SRSOSLongVersion_CF, SRSIPv4Address_CF, SRSIPv6Address_CF, SRSOperationName_CF, SRSOperationResult_CF, SRSResourceState_CF, SRSEventDescription_CF "
                                        }
                                    }
                                }
                            }
                        ],
                        "Filters": [],
                        "OverviewTile": {
                            "Id": "DoubleNumberBuilderTile",
                            "Type": "OverviewTile",
                            "Version": 2,
                            "Configuration": {
                                "TileOne": {
                                    "Legend": "Devices that sent a heartbeat at least once within the last month",
                                    "Query": "Event | where EventLog == \"Skype Room System\" and TimeGenerated > ago(30d) | summarize TotalSRSDevices = dcount(Computer)"
                                },
                                "TileTwo": {
                                    "Legend": "Active devices that sent a heartbeat within the last hour",
                                    "Query": "Event | where EventLog == \"Skype Room System\" and SRSOperationName_CF == \"Heartbeat\" and TimeGenerated > ago(1h) | summarize TotalSRSDevices = dcount(Computer)"
                                },
                                "Advanced": {
                                    "DataFlowVerification": {
                                        "Enabled": false,
                                        "Query": "search * | limit 1 | project TimeGenerated",
                                        "Message": ""
                                    }
                                }
                            }
                        }
                    }
                }
            ]
        }
    ]
}
```
  
## See also

#### 

[Plan for Skype Room Systems v2](../../plan-your-deployment/clients-and-devices/skype-room-systems-v2-0.md)
  
[Configure a Skype Room Systems v2 console](console.md)
  
[Manage Skype Room Systems v2](../../manage/skype-room-systems-v2/skype-room-systems-v2.md)

