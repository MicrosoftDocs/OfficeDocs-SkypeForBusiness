---
title: Teams meeting add-in security in Outlook.
author: MSFTTracyP
ms.author: tracyp
manager: dansimp
ms.topic: how-to
ms.service: msteams
audience: admin
ms.reviewer: 
description: Protect your Teams meeting add-in in the Outlook desktop client on Windows. Use Outlook's Trust-Center to load signed DLLs from only trusted publishers, group policies to trust a publisher, or AppLocker to prevent untrusted DLLs from being loaded.
ms.localizationpriority: high
search.appverid: MET150
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
  - remotework
  - teams-security
ms.custom: 
- Security
appliesto: 
  - Microsoft Teams
---

# Teams meeting add-in security when using your Outlook client

The Teams meeting add-in (or TMA) is used to schedule meetings in Teams from the Outlook desktop client on Windows.

TMA coordinates between the Outlook and Teams services, so it's important to keep TMA secure. Taking security measures helps lower the risk of cybersecurity attack.

Here are the ways to secure your Teams meeting add-in covered in this article:

1. (Recommended) Use Microsoft Outlook Trust Center to prevent Outlook from loading TMA when the TMA DLLs aren’t signed with a certificate from a trusted publisher.
    1. Use group policies for the domain and update the *Root certificate* and *trusted publisher*, especially since it prevents users from being prompted to trust the publisher.
1. AppLocker can also be used to stop DLLs from untrusted publishers from being loaded.

## Microsoft Outlook Trust Center group policies

You can use **Trust Center group policies** for add-in management:

- To make sure only add-ins trusted by the organization are loaded
- To stop add-ins from unspecified locations from loading  

This practice helps protect against malware compromising the COM registration to load from another location with planted DLLs.

Here are the steps:

1. **Protect Outlook from add-ins that aren't secure**
    1. Go to the Outlook Trust Center, [https://www.microsoft.com/en-us/trust-center](https://www.microsoft.com/en-us/trust-center).
    1. When you arrive, select **File > Options > Trust Center**.
    1. Select **Microsoft Outlook Trust Center**.
    1. Under Microsoft Outlook Trust Center in the left menu, select **Trust Center Settings**.
    1. Under **Macro Settings**, select **Notifications for digitally signed macros, all other macros disabled**.
    1. Admins must select **Apply macro security settings to installed add-ins** in this case.
    1. Select the **OK** button to make these changes and exit the trust center, and select **OK** again, to close options.

The choices persist from there.

Now, outside of the Outlook Trust Center:

1. Restart Outlook on your client.
1. When Outlook reopens, the application asks permission to load each add-in, automatically disabling any add-in that *isn't* signed.
    1. The image below is what the user experience of TMA looks like:
    :::image type="content" source="media/TMA/outlook-security-notice-and-how-trust-all-docs-from-this-publisher-and-enable-application-add-in-will-work.png" alt-text="Outlook security notice and how Trust all docs from this publisher, and Enable applications add-in works.":::
    2. End-users see a Microsoft Outlook Security Notice that may read *Microsoft Office has identified a potential security concern* listing Microsoft.Teams.AddinLoader.dll. The options are:
        1. **Trust all documents from this Publisher.**
            1. Selecting this option trusts the certificate’s publisher and the user won’t be prompted again until the certificate changes.
        1. **2.	Enable application add-in.**
            1. This option only enables on a case-by-case basis, so this add-in enables for this single time, and the user will be prompted again.
        1. **3.	Disable application add-in.**
            1. Disables the add-in.
    1. Follow the steps to **[set up Group Policy to automatically trust a specific root certificate Authority](/windows-server/identity/ad-fs/deployment/distribute-certificates-to-client-computers-by-using-group-policy)**.
        1. Open the Group Policy Management Console on your domain controller (DC).
        2. Create a new Group Policy Object (GPO) or edit an existing GPO that you want to use to configure the settings.
        3. Next go to Computer Configuration > Policies > Windows Settings > Security Settings > Public Key Policies.
        4. Right-click on Trusted Root Certification Authorities and select Import.
        5. Browse to the root certificate Microsoft Root Certificate Authority 2010 file for the certificate publisher you want to trust and import it.
        6. Link the GPO to the appropriate organizational unit to apply the settings to the computers that you want to use the policy. For more information on this process, see: [Deploy the Applocker Policy into production](/windows/security/threat-protection/windows-defender-application-control/applocker/deploy-the-applocker-policy-into-production)
    1. Next, follow the steps to set up Group Policy to automatically trust the publisher.
        1. Open the Group Policy Management Console on your domain controller.
        2. Create a new GPO or edit an existing GPO that you want to use to configure the settings.
        3. Navigate to Computer Configuration > Policies > Windows Settings > Security Settings > Public Key Policies.
        4. Right-click on Trusted Publishers and select Import.
        5. Browse to the leaf certificate Microsoft Corporation file for the certificate publisher you want to trust and import it.
        6. Link the GPO to the appropriate organizational unit to apply the settings to the computers you choose.
        
2.	**Add-in Management through Group Policies**
    1. [Download Administrative Template files (ADMX/ADML)](https://www.microsoft.com/en-us/download/details.aspx?id=49030) for Microsoft 365 Apps for enterprise/Office LTSC 2021/Office 2019/Office 2016 and the Office Customization Tool for Office 2016.
    1. Add the ADMX/ADML template files to the Group Policy Management:
        1. Under **User Configuration > Administrative Templates > Microsoft Outlook (version number) > Security > Trust Center**.
            1. *Apply Macro security settings to Macros, add-ins and additional actions*: This policy setting controls whether Outlook also applies the Macro security settings to installed COM add-ins and additional actions.
                1. **Set to:** Enabled
            1. *Security setting for macros*: This policy setting controls the security level for macros in Outlook.
                1. **Set to:** Warning for signed, disable unsigned.
                    1. This option corresponds to the *Notifications for digitally signed macros, all other macros disabled* option in the Trust Center. If an add-in is digitally signed by a trusted publisher, the add-in can run signed by a trusted publisher.
        1. Additional Group Policies around Add-ins.
            1. Under **User Configuration > Administrative Templates > Microsoft Outlook 2016 > Security**
                1. *Configure add-in trust level*: All installed trusted COM add-ins can be trusted. Exchange Settings for the add-ins still override if present and this option is selected.
            1. Under **User Configuration > Administrative Templates > Microsoft Outlook 2016 > Miscellaneous**
                1. *Block all unmanaged add-ins*: This policy setting Blocks all add-ins that aren't managed by the "List of managed add-ins" policy setting.
                1. *List of managed add-ins*: This policy setting allows you to specify which add-ins are always enabled, always disabled (blocked), or configurable by the user.
                    To block add-ins that aren't managed by this policy setting, you must also configure the "Block all unmanaged add-ins" policy setting.
            1. Under **User Configuration > Administrative Templates > Microsoft Outlook 2016 > Security > Security Form Settings > Programmatic Security > Trusted Add-ins**
                1. *Configure Trusted Add-ins*: This policy setting is used to specify a list of Trusted Add-ins that can be run without being restricted by the security measures in Outlook.

## AppLocker

The AppLocker application control policies help you control which apps and files users can run. These file types include executable files, scripts, Windows Installer files, dynamic-link libraries (DLLs), packaged apps, and packaged app installers.

Let's focus on using AppLocker to *stop* DLLs that aren't signed by a trusted publisher from loading.

#### Use AppLocker to stop unsigned DLLs from loading.

To use Applocker to stop your unsigned DLLs from loading, you have to create a new DLL rule in your Local or Group Policy.

> [!NOTE]
> The pre-requisites for this section are Windows 10 Enterprise and, Education or Windows Server 2012 or later.

To set up AppLocker on *Windows 10 or Windows 11* for a specific DLL, follow these steps:

1. Open policy editor.
    1. Local Machine
       1. Open the Local Security Policy editor. Type secpol.msc into the Run dialog box or the Start menu search bar, and then press Enter.
   1. Group Policy
       1. Edit an AppLocker policy Through Group Policies | Microsoft Learn
1. In the Local Security Policy editor, navigate go to Application Control Policies > AppLocker > DLL Rules.
    1. If you're using a supported edition of Windows and still don't see DLL rules, it's possible that AppLocker isn't enabled or configured on your system. In this case, you can follow these steps to enable AppLocker:
        1. Open the Local Security Policy editor. Type secpol.msc into the Run dialog box or the Start menu search bar, then press Enter.
        1. In the Local Security Policy editor, navigate to Application Control Policies > AppLocker.
        1. Right-click on AppLocker and select Properties.
        1. Under AppLocker Properties, in the Enforcement tab:
            1. Select Configured next to Configure rule enforcement.
            2. Configure extra policies such as rule collections as audit-only mode.
            3. Once this is verified, it can be updated to Enforce
            4. Select OK to save the changes.
            5. Be sure the Application Identity service is [running](/windows/security/threat-protection/windows-defender-application-control/applocker/configure-the-application-identity-service).
1. Create a new DLL Rule
    1. From the Local Security Policy editor
        1. Right-click on DLL Rules and select Create New Rule.
        1. In the Create DLL Rule wizard, select Use an Existing File and browse to the DLL file that you want to create a rule for.
        1. Select the type of rule that you want to create (such as to allow or deny) and configure any other rule conditions that are needed.
        1. Complete the wizard and save the new rule.
    1. Or from PowerShell:
        1. The PowerShell cmdlets that are needed to create a new DLL Rule can be piped together.
1. Add-in Management through AppLocker Group Policies
    1. **Get-ChildItem** - Gets the object for the file
    1. **Get-AppLockerFileInformation** - Gets the file information necessary to create AppLocker rules from a list of files or an event log
    1. **New-AppLockerPolicy** - Creates a new AppLocker policy from a list of file information and other rule creation options.
        1. RuleType needs to be published and this enforces code signing.
        1. User can be an individual user or group, all examples use Everyone.
        1. AllowWindows indicates that the AppLocker policy allows all local Windows components. 
    1. To create the DLL rule per file 
        1. TMA file location depends on the installation type
            1. Per user installation
                1. Install location: %localappdata%\Microsoft\TeamsMeetingAddin
            1. Per machine installation
                1. Install location: C:\Program Files(x86)\TeamsMeetingAddin
        1. `Get-ChildItem <TMAFileLocation>\Microsoft.Teams.AddinLoader.dll | Get-AppLockerFileInformation | New-AppLockerPolicy  -RuleType Publisher, Hash -User Everyone -RuleNamePrefix TeamsMeetingAddin -AllowWindows -Xml | Out-File .\TMA.xml`
        1. Set the policy:
            1. Local Machines
                i.`Set-AppLockerPolicy -XmlPolicy .\TMA.xml -Merge`
            1. Group Policy
                i. `Set-AppLockerPolicy -XMLPolicy .\TMA.xm -LDAP "<LDAP Info for Group Policy>"`
        1. Steps 1 and 2 need to be completed for each DLL under x64 and x86 directories for TMA.
    1. Create **all DLL rules at once**:
        1. Get-AppLockerFileInformation -Directory  .\Microsoft\TeamsMeetingAddin\1.0.23089.2 -Recurse | New-AppLockerPolicy -Verbose -RuleType Publisher, Hash -User Everyone -RuleNamePrefix TeamsMeetingAddin -AllowWindows -Xml | Out-File .\TMA.xml`
        2. `Set-AppLockerPolicy -XmlPolicy .\TMA.xml  -Merge`
            3. LDAP info is needed to perform Group Policy updates.

Important things to know:

1. It’s assumed that if AppLocker is turned on in an environment, then the IT department is familiar with AppLocker. They're aware it’s designed to use an Allow model and anything not Allowed will be blocked.
1. Hash rules are provided for fallback when Publisher rule fails. Hash rules need to be updated every time TMA updates.
1. The [PowerShell](https://microsoft.sharepoint.com/sites/knowledgecenter/SitePages/PowerShell.aspx) command for adding AppLocker policies will be set up to match only the exact version of the DLL being added > go into the Allow Properties for the Publisher Rule and change the File Versions options for scope to And Above the listed version.
1. To make AppLocker accept a wider range of DLL versions for Publisher Rules, go to the Allow Properties for the Publisher Rule and change the drop-down for File version to *And above* (from *Exactly*).
    :::image type="content" source="media/TMA/make-applocker-accept-a-wider-range-of-dll-versions-for-publisher-rules.png" alt-text="Make AppLocker accept a wider range of DLL versions for publisher rules.":::
1. Once enabled if the AppLocker policy blocks the add-in, it will not show, and inspecting COM add-ins will show:
    :::image type="content" source="media/TMA/once-enabled-if-the-applocker-policy-blocks-the-add-in-it-will-not-show-and-inspecting-com-add-ins-will-show-the-add-in-as-unavailable.png" alt-text="Once enabled, if the AppLocker policy blocks the add-in it won't show, and inspecting COM add-ins will show the add-in as unavailable.":::

## For more information
[Enable or disable macros in Microsoft 365 files](https://support.microsoft.com/office/enable-or-disable-macros-in-microsoft-365-files-12b036fd-d140-4e74-b45e-16fed1a7e5c6#:~:text=Change%20macro%20settings%20in%20the%20Trust%20Center%201,the%20selections%20that%20you%20want%2C%20then%20click%20OK.) - Microsoft Support
[AppLocker (Windows) ](/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview)| Microsoft Learn
