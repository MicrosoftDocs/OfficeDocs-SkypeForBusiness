---
title:  Bulk deploy the new Microsoft Teams desktop client
author: MicrosoftHeidi
ms.author: heidip
manager: jtremper
ms.topic: article
ms.date: 11/30/2023
ms.service: msteams
audience: admin
ms.collection: 
- Teams_ITAdmin_GuestAccess
- M365-collaboration
- m365initiative-deployteams
ms.reviewer: 
search.appverid: MET150
f1.keywords:
- NOCSH
description: Bulk upgrade to the new Microsoft Teams client.
appliesto: 
- Microsoft Teams
ms.localizationpriority: high
---

# Bulk upgrade to the new Microsoft Teams client

Direct or "bulk" upgrades are helpful because users don't need to manually download and install the Teams client. Microsoft provides an executable (.exe) file for the new Teams client so you can upgrade the application directly to the computers in your organization using your choice of software management tools, such as Intune or Configuration Manager.

The Teams installer installs the Teams MSIX package on a target computer, making sure that Teams can interoperate correctly with Office and other Microsoft software.

>[!Note]
>**New.** An offline installer option is now available. Learn more: [Download and install new Teams using an offline installer](#option-1b-download-and-install-new-teams-using-an-offline-installer)

## How it works

**TeamsBootstrapper** is a lightweight online installer with a headless command-line interface. It allows admins to provision (install) the app for all users on a given target computer.

When **teamsbootstrapper.exe** is run on a computer:

- The installer downloads the latest Teams MSIX package from Microsoft
- The installer installs the Teams application for all users on the computer, and any users who may be added afterwards.

>[!Important]
>Users who have installed a different Teams version will have their version replaced with the provisioned version.

- Modifies the registry to allow Teams to work with Office and other computer applications.
- Displays success or failure message on the command line

>[!Important]
>You must use the latest version of the bootstrapper.exe. If you have downloaded the .exe previously, verify you have the latest version by viewing **Properties > Details > Product version** on your version and compare it to the properties on the latest download.

## Prerequisites for target computers

For new Teams to be successfully installed, computers must meet the minimum requirements listed here.

### Required system and app requirements

|Requirement|Version/Description|
|:-----|:-----|
|Windows| Windows 10 version 10.0.19041 or higher (excluding Windows 10 LTSC for Teams desktop app)|
|Classic Teams app|Version 1.6.00.4472 or later to see the *Try the new Teams* toggle.</br>**Important:** Classic Teams is only a requirement if you want users to be able to switch between classic Teams and new Teams. This prerequisite is optional if you only want your users to see the new Teams client.|
|Office |Microsoft 365 Apps or Office LTSC 2021 Learn more: [Office versions and connectivity to Microsoft 365 services](/deployoffice/endofsupport/microsoft-365-services-connectivity)|
|Settings|Turn on the "Show Notification Banners" setting in **System > Notifications > Microsoft Teams** to receive Teams Notifications.|
|Webview2|Update to the most current version. Learn more: [Enterprise management of WebView2 Runtimes](/microsoft-edge/webview2/concepts/enterprise)|
|Delivery optimization (DO)|DO powers Teams automatic updates, which are required as part of the [Servicing Agreement](/microsoftteams/new-teams-automatic-upgrade-announced#servicing-agreement).</br></br>Overview: [What is Delivery Optimization?](/windows/deployment/do/waas-delivery-optimization)</br></br>Recommended settings: [Set up Delivery Optimization](/windows/deployment/do/waas-delivery-optimization-setup#recommended-delivery-optimization-settings)<br></br>**Note:** Download Mode 100 (Bypass) isn't supported.|

>[!Note]
>Learn more: [**Update History for Microsoft 365 Apps**](/officeupdates/update-history-microsoft365-apps-by-date#supported-versions).

## Step 1: Upgrade the new Teams application

All steps must be completed to successfully upgrade to the new Teams.

>[!Important]
>You must run the latest version of the bootstrapper.exe to avoid any issues that may have been already fixed. If you have downloaded the file previously, confirm you have the latest version by checking **Properties > Details > Product version** on your version and compare it to the latest download.

### Option 1A: Download and install new Teams for a single computer

To install new Teams on a single computer with many users, follow these steps:

1. [Download the .exe installer](https://go.microsoft.com/fwlink/?linkid=2243204&clcid=0x409). If you have downloaded this file previously confirm you have the latest version by comparing the properties on each file.
2. Open the Command Prompt as an Admin.
3. At the prompt enter: **.\teamsbootstrapper.exe -p**
4. A success or fail status displays. If you receive an error, learn more at [Common HRESULT values](/windows/win32/seccrypto/common-hresult-values).
</br>
   :::image type="content" source="media/new-teams-direct-deploy-cmd-feedback.png" alt-text="command line prompt feedback":::

#### Option 1B: Download and install new Teams using an offline installer

Admins can also use a local teams MSIX to provision new Teams. This option minimizes the amount of bandwidth used for the initial installation. The MSIX can exist in a local path or UNC.

1. [Download the .exe installer.](https://go.microsoft.com/fwlink/?linkid=2243204&clcid=0x409). If you have downloaded this file previously confirm you have the latest version by comparing the properties on each file.
2. Download the MSIX:</br>- [MSIX x86](https://go.microsoft.com/fwlink/?linkid=2196060&clcid=0x409)</br>- [MSIX x64](https://go.microsoft.com/fwlink/?linkid=2196106)</br>- [ARM64](https://go.microsoft.com/fwlink/?linkid=2196207&clcid=0x409)
3. Open the Command Prompt as an Admin.
4. Depending on where your MSIX is located, do the following:
</br>

 **For local path, enter:** *.\teamsbootstrapper.exe -p -o "c:\path\to\teams.msix"*

   *Example:*

   :::image type="content" source="media/new-teams-bulk-offline-localpath.png" alt-text="local path location for offline installer":::

   **For UNC, enter:** *.\teamsbootstrapper.exe -p -o "\\unc\path\to\teams.msix"*

   *Example:*

   :::image type="content" source="media/new-teams-bulk-offline-unc.png" alt-text="offline location using unc":::

#### Option B: Upgrade to the new Teams across your organization

To deploy this installer to a group of computers, or your entire organization, follow these steps:

1. [Download the .exe installer](https://go.microsoft.com/fwlink/?linkid=2243204&clcid=0x409). If you have downloaded this file previously confirm you have the latest version by comparing the properties on each file.
2. Use [Intune](/mem/intune/apps/apps-add-office365), [Microsoft Endpoint Configuration Manager](/configmgr/core/understand/introduction), [Group Policy](/troubleshoot/windows-server/group-policy/use-group-policy-to-install-software), or third-party distribution software, to distribute the installer to your target computers.
3. Run the installer on each computer.

##### Gov cloud updates for PC and Mac

###### PC update

If the customer tenant is on the GCCH, DoD, or Gallatin, the customer may need to set the initial cloud endpoint through the registry key listed below. Setting the endpoint with the registry key restricts teams to connecting to the correct cloud endpoint for pre-sign-in connectivity with Teams, as shown in the following:

```console
HKEY_CURRENT_USER\SOFTWARE\Policies\Microsoft\Office\16.0\Teams
Value = CloudType
value type = DWORD
  1 = Commercial, 2 = GCC, 3 = GCCH, 4 = DOD, 7 = Gallatin
```

###### Mac update

If the customer tenant is on the GCCH, DoD, or Gallatin, the customer may need to set the initial cloud endpoint through the .plist configuration key listed below. Setting the endpoint with the .plist configuration restricts teams to connecting to the correct cloud endpoint for pre-sign-in connectivity with Teams, as shown in the following:

```console
Domain: com.microsoft.teams2
Key: CloudType
Data Type: Int
Value: {Enter number associated with the cloud}
  1 = Commercial, 2 = GCC, 3 = GCCH, 4 = DOD, 7 = Gallatin
```

The .plist configuration can be propagated to managed devices using Intune as described in [Add preference file settings to macOS devices in Microsoft Intune](/mem/intune/configuration/preference-file-settings-macos).

## Step 2: Set new Teams as the default

>[!Note]
>Admin policies may also be set using PowerShell. Learn more: [Set the policies to upgrade to the new Teams client - Powershell method](new-teams-deploy-using-policies.md)

1. Sign in to the [Microsoft Teams admin center](https://admin.teams.microsoft.com).
2. Select **Teams > Teams Update policies** from the left navigation pane.
3. Select Add to create a new policy or select an existing policy to open Update policy.
4. Name the update policy, add a description, and select the setting for “Use new Teams client”, as shown below.

|Setting|Description|
|:-----|:-----|
|New Teams as default|Sets the new Teams as default. **Note:** This option is currently being rolled out|
|Classic Teams as default|Use this value to have classic Teams the default version. The new Teams toggle switch displays to let users opt into the new Teams and switch back if needed.|

>[!Note]
>This option was previously called **Users can choose**.

5. Once the policy is defined, you can assign it to a **user or user group** with the Group policy assignment. To assign it to a group, select **Group policy assignment** and then **Add**,  or select one of the groups listed.  Select a policy to assign to the group.
6. Once the policy is defined, you can assign it to a specific user under **Users> Manage users**.

>[!Note]
>If you update the policy setting in the Teams Admin Center, the new setting can take up to 24 hours to go into effect. The user doesn't have to restart the app.

## Remove new Teams for all users

To uninstall and deprovision the new Teams for all users, use the following command:

```powershell
.\teamsbootstrapper.exe -x
```

## Remove classic Teams for all users
>[!Important]
> Important: this command option requires a minimum bootstrapper version of 1.0.2414501 or higher.

Once the new Teams version has been installed, use the following command to uninstall the classic Teams machine-wide installer and classic Teams app for all users on the device:
```powershell
./teamsbootstrapper -u
```
## End user experience:  Launching the new Teams

After new Teams is deployed to your target computers, users will sign in as usual. For first use, the user can launch new Teams in one of two ways:

**Option 1:** Users can launch classic Teams, and then switch the toggle to go to new Teams.

**Option 2:** Users can directly launch new Teams:

1. In Windows, select **Start** **> new Microsoft Teams**.
2. Select "Yes" at the confirmation prompt screen.
3. Once confirmed, the new Teams launches and is the default version.
