---
title: "Deploy the Lync VDI plug-in with Skype for Business Server"
ms.author: v-lanac
author: lanachin
manager: serdars
ms.reviewer: krishra
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 11d3bd5d-6dd3-471c-b842-b072fa197714
description: "This topic discusses deployment procedures for using Skype for Business while connecting to a remote virtual desktop."
---

# Deploy the Lync VDI plug-in with Skype for Business Server
 
This topic discusses deployment procedures for using Skype for Business while connecting to a remote virtual desktop. Planning considerations are at [Plan for Skype for Business in VDI environments](../../plan-your-deployment/clients-and-devices/vdi-environments.md).
  
A Virtual Desktop Infrastructure (VDI) environment is used in some organizations where security and compliance issues are especially sensitive. Their users are on local Windows computers and using clients on a virtual desktop. Using Skype for Business on a connection like that requires additional VDI plug-in software.
  
There are two solutions available for the VDI plug-in component - one offered by Microsoft and one offered by Citrix. Microsoft recommends using the new HDX RealTime Optimization Pack solution in new deployments but will continue to support the original Lync VDI Plug-in for the remainder of its lifecycle. 
  
This topic provides details on deploying the Microsoft Lync VDI plug-in, which is only supported on Windows 7 and Windows 8 or Windows Server 2008, and only supports Lync 2013 or Skype for Business clients. There are no plans to update this plugin, but the [Citrix HDX RealTime Optimization Pack](../../plan-your-deployment/clients-and-devices/vdi-environments.md#Citrix_RT) for Skype for Business will be updated as needed.
  
## Prepare your environment for the Lync VDI plug-in
<a name="Prepare_vdi"> </a>

1. In Skype for Business Server, ensure that EnableMediaRedirection is set to TRUE for all Lync VDI plug-in users. For details, see the Help topics for the [New-CsClientPolicy](https://docs.microsoft.com/powershell/module/skype/new-csclientpolicy?view=skype-ps) cmdlet and the [Set-CsClientPolicy](https://docs.microsoft.com/powershell/module/skype/set-csclientpolicy?view=skype-ps) cmdlet.
    
2. On the data center server, install the Skype for Business client on all virtual desktops.
    
3. On the local computers, install the Lync VDI plug-in.
    
    Users should now connect a device like a headset or webcam to their local computer.
    
## Configure Remote Desktop Connection settings
<a name="Prepare_vdi"> </a>

To prepare Remote Desktop Connection for the Lync VDI plug-in, follow these steps on the local computer:
  
1. If the local computer is running Windows 8, skip this step. If the local computer is running Windows 7 with SP1, install the latest Windows 8 version of the [Remote Desktop Services client](https://go.microsoft.com/fwlink/p/?LinkId=268032).
    
2. Start the Remote Desktop Services client by clicking **Start**, and then clicking **Remote Desktop Connection**.
    
3. Click **Options**.
    
4. Click the **Local Resources** tab. Under **Remote audio**, click **Settings**, and then do the following:
    
   - Under **Remote audio playback**, select **Play on this computer**.
    
   - Under **Remote audio recording**, select **Do not record**.
    
   - Click **OK**.
    
5. Click the **Experience** tab. Under **Performance**, clear the **Persistent bitmap caching** check box.
    
6. Click the **General** tab. In **Computer**, type the name of the virtual desktop, and then click **Connect**. 
    
## Sign in and use Skype for Business on the virtual desktop
<a name="SfB_signin"> </a>

After the Lync VDI plug-in is enabled, the user follows these steps when signing in to Skype for Business on the virtual desktop.
  
1. The user types his or her credentials in to the Skype for Business client running on the virtual desktop.
    
2. After Skype for Business detects the Lync VDI plug-in, Skype for Business prompts the user to re-enter the credentials. In this dialog box, we recommend that the user select the **Save my password** check box so that he or she will not be required to enter credentials during subsequent sign in.
    
3. Skype for Business begins pairing with the Lync VDI plug-in. While that happens, the client displays two icons in the Skype for Business status bar. The icon in the lower left indicates that no audio devices are available, and the blinking icon in the lower right indicates that VDI pairing is in progress:
    a. After VDI pairing is successful, the icons change to indicate the audio device that will be used for calls and the VDI pairing success:
    b. The user can now see his or her presence on Skype for Business compatible devices that are connected to the local computer, and place and answer calls as usual.
    
## Troubleshoot the Lync VDI plug-in
<a name="tshoot_VDI"> </a>

Refer to the following sections if you encounter issues after installing the Lync VDI plug-in.
  
### Issues with installing the Lync VDI Plug-in

If there are issues with installing the Lync VDI plug-in, check the following:
  
- Ensure that there is sufficient space in the folder that you specified in the TEMP and TMP system variables.
    
- Ensure that write-protect is turned off. Refer to your device manufacturer's documentation for instructions.
    
### Troubleshooting Issues with Pairing

When Lync VDI plug-in pairing fails, the pairing icon in the lower right displays as a red "X" as shown: 
  
The following are possible reasons for failures and the actions you can take to correct the problem. 
  
- **The user entered incorrect credentials during sign-in.**
    
    The user should sign out of Skype for Business and sign in again with the correct credentials. The pairing dialog box will reappear and show whether pairing is successful.
    
- **Another instance of the remote desktop client is running.**
    
    If they are using Remote Desktop Connection in Windows, users should do the following:
    
1. Start Task Manager: Press **Alt+Ctrl+Delete**, and then click **Start Task Manager**.
    
2. Click the **Processes** tab and look for all processes named **mstsc.exe** in the list.
    
3. Highlight each **mstsc.exe** process and then click **End Process**. 
    
4. Start a new remote desktop session and try connecting again. 
    
- **The necessary files did not install correctly.**
    
    After the plug-in is installed on the local computer, check to make sure that these files are present under C:\Program Files\Microsoft Office\Office15 (or the appropriate drive letter):
    
  - LyncVdiPlugin.dll
    
  - UcVdi.dll
    
- **The Skype for Business client is running on the local computer.**
    
    To use the Lync VDI plug-in, a Skype for Business client must not be running on the local computer, otherwise pairing will fail. As a best practice, the user should not install a Skype for Business client on the local computer.
    
## See also
<a name="tshoot_VDI"> </a>

[Plan for Skype for Business in VDI environments](../../plan-your-deployment/clients-and-devices/vdi-environments.md)
