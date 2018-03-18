---
title: "Install and configure Busy Options for Skype for Business Server"
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 7/6/2016
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.custom: Strat_SB_Admin
ms.assetid: fb0faac8-ca1c-4abb-9959-d19def294c64
description: "Read about how to install and configure Busy Options in Skype for Business Server 2015."
---

# Install and configure Busy Options for Skype for Business Server
 
Read about how to install and configure Busy Options in Skype for Business Server 2015.
  
Busy Options is a new voice policy introduced in the July 2016 Cumulative Update that allows you to configure how incoming calls are handled when a user is already in a call or conference or has a call placed on hold. New or incoming calls can be rejected with a busy signal or forwarded to voice mail. 
  
If Busy Options is enabled for the organization, all users at the Enterprise, both Enterprise Voice and non-Enterprise Voice users, can use the following configuration options:
  
- Busy on Busy - In which new incoming calls will be rejected with a busy signal if the user is busy.
    
- Voicemail on Busy - In which new incoming calls will be forwarded to voice mail if the user is busy.
    
Regardless of how their busy options are configured, users in a call or conference, or those with a call on hold, are not prevented from initiating new calls or conferences. 
  
For more information about the Busy Options feature, see [Plan for Busy Options for Skype for Business Server](../../plan-your-deployment/enterprise-voice-solution/busy-options.md).
  
## Install

Make sure you have the latest version of Skype for Business Server installed and that you have installed the most recent patch. To do this, first stop all services, and then run the Skype for Business Server update installer as follows:
  
1. Run the Stop-CsWindowsService command.
    
2. Run the SkypeServerUpdateInstaller.exe installer on each Front End server in a pool.
    
3. Run the SkypeServerUpdateInstaller.exe installer on each Survivable Branch Server (SBS), if you want to ensure support for failover on SBS.
    
The installer will deploy the latest version of the Busy Options application. However, the application is not enabled by default. To enable the application, perform the following steps:
  
1. Run the [Set-CsVoicePolicy](../../manage/management-shell/set-csvoicepolicy.md) cmdlet to globally enable Busy Options as shown in the following example:
    
  ```
  Set-CsVoicePolicy -EnableBusyOptions $true
  ```

2. Next, if the site has a voice policy is place, you must enable Busy Options for the voice policy as follows:
    
    First, run [Get-CsSite](../../manage/management-shell/get-cssite.md) to retrieve the name of the site:
    
   ```
   Get-CsSite
   ```

    Use the Identity value (for example: Site:Redmond1) retrieved from Get-CsSite to retrieve the voice policy of the site as follows:
    
   ```
   Get-CsVoicePolicy -Identity Site:Redmond1
   ```

    If a voice policy exists for the site, run the following command:
    
   ```
   Set-CsVoicePolicy -Identity Site:Redmond1 -EnableBusyOptions $true
   ```

3. Next, run the [New-CsServerApplication](../../manage/management-shell/new-csserverapplication.md) cmdlet to add Busy Options to the list of server applications as shown in the following example:
    
   ```
   New-CsServerApplication -Identity 'Service:Registrar:%FQDN%/BusyOptions' -Uri http://www.microsoft.com/LCS/BusyOptions -Critical $False -Enabled $True -Priority (Get-CsServerApplication -Identity 'Service:Registrar:%FQDN%/UserServices').Priority
   ```

    > [!NOTE]
    > You must replace %FQDN% with the fully-qualified domain name of a specific pool. 
  
4. Next, run the [Update-CsAdminRole](../../manage/management-shell/update-csadminrole.md) cmdlet to update the Role-based access control (RBAC) roles for the Busy Options cmdlets as shown in the following example:
    
   ```
   Update-CsAdminRole
   ```

5. Finally, start the Skype for Business Server Windows services on all the Front End servers in all the pools where Busy Options was installed and enabled by running the [Start-CsWindowsService](../../manage/management-shell/start-cswindowsservice.md) command:
    
   ```
   Start-CsWindowsService
   ```

## Configure

To configure Busy Options, use the [Set-CsBusyOptions](http://technet.microsoft.com/library/8ffbb832-3e55-4d6c-9a7c-5ce2df22de2e.aspx) cmdlet.
  
For example, the following command configures busy options for the user "Ken Myer". In this configuration, any call to "Ken Myer" will return a busy signal when he is already in a call:
  
```
Set-CsBusyOptions -Identity "Ken Myer"  -ActionType BusyOnBusy

```

In the next example, the command configures busy options for the user "Chrystal Velasquez". In this configuration, new incoming calls to "Chrystal Velasquez" will be forwarded to voice mail when she is already in a call:
  
```
Set-CsBusyOptions -Identity "Chrystal Velasquez" -ActionType VoicemailOnBusy 

```

You can retrieve configuration information about Busy Options by using the [Get-CsBusyOptions](http://technet.microsoft.com/library/ff0e3b1c-c41d-41e4-9468-0cb057aef9fb.aspx) cmdlet. The following example returns the Busy Options setting for "KenMyer@Contoso.com":
  
```
Get-CsBusyOptions -Identity sip:KenMyer@Contoso.com
```

You can remove Busy Options by using the [Remove-CsBusyOptions](http://technet.microsoft.com/library/159e5931-10f1-4226-bcc4-38548f88f0d4.aspx) cmdlet. The following command removes Busy Options for "Ken Myer":
  
```
Remove-CsBusyOptions -Identity "Ken Myer"

```

For detailed information about the cmdlets you use to configure Busy Options, see the technical reference content for [Set-CsBusyOptions](http://technet.microsoft.com/library/8ffbb832-3e55-4d6c-9a7c-5ce2df22de2e.aspx), [Get-CsBusyOptions](http://technet.microsoft.com/library/ff0e3b1c-c41d-41e4-9468-0cb057aef9fb.aspx), and [Remove-CsBusyOptions](http://technet.microsoft.com/library/159e5931-10f1-4226-bcc4-38548f88f0d4.aspx).
  
## Enable logging

To enable logging for Busy Options by using the Centralized Logging Service, specify the following:
  
```
$p1 = New-CsClsProvider -Name S4 -Type WPP -Level Info -Flags All
$p2 = New-CsClsProvider -Name Sipstack -Type WPP -Level Info -Flags
 "TF_PROTOCOL,TF_CONNECTION,TF_SECURITY,TF_DIAG,TF_SHOW_CONFERENCE,TF_SHOW_ALLREQUESTS,TF_SHOW_ALLSIPHEADERS" -Role Registrar
$p3 = New-CsClsProvider -Name BusyOptions -Type WPP -Level Verbose -Flags All
New-CsClsScenario -Parent Global -Name BusyOptions -Provider @{Add=$p1,$p2,$p3} 

```

## Verify and troubleshoot

After installing Busy Options, you can verify that the installation was successful by using the [Get-CsServerApplication](../../manage/management-shell/get-csserverapplication.md) cmdlet to retrieve the list of server applications. If Busy Options is installed properly, the output of the cmdlet should show the Busy Options configuration as follows:
  
|||
|:-----|:-----|
|Identity  <br/> | : Service:Registrar:pool0.vdomain.com/BusyOptions <br/> |
|Priority  <br/> | : 5 <br/> |
|Uri  <br/> |: http://www.microsoft.com/LCS/BusyOptions  <br/> |
|Name  <br/> | : BusyOptions <br/> |
|Enabled  <br/> |: True  <br/> |
|Critical  <br/> |: False  <br/> |
|ScriptName  <br/> | : <br/> |
|Script  <br/> | : <br/> |
   
You can also use Windows Event Viewer to verify that the Busy Options installation was successful and that Skype for Business Server successfully loaded Busy Options. To verify Busy Options, open **Event Viewer -\> Application and Services Logs -\> Skype (or Lync) Server** and search for Event ID = 30253.
  

