---
title: Configure a Skype Room Systems v2 console
ms.prod: SKYPEFORBUSINESS
ms.assetid: dae1bfb6-7262-4030-bf53-dc3b3fe971ea
---


# Configure a Skype Room Systems v2 console
[]This article describes how to set up the Skype Room Systems v2 console device and its peripherals.
You should only perform these steps if the necessary Skype for Business and Exchange accounts have already been created and tested as described in  [Deploy Skype Room Systems v2](deploy-skype-room-systems-v2.md). You will need the hardware and software described in  [Skype Room Systems v2 requirements](skype-room-systems-v2-requirements.md). This topic contains the following sections:
  
    
    


-  [Prepare the installation image](configure-a-skype-room-systems-v2-console.md#Prep_Image)
    
  
-  [Install a private CA certificate on the Surface Pro 4 device](configure-a-skype-room-systems-v2-console.md#Certs)
    
  
-  [Install Windows 10 and the Skype Room Systems v2 console app ](configure-a-skype-room-systems-v2-console.md#Reimage)
    
  
-  [Initial set up of the Console ](configure-a-skype-room-systems-v2-console.md#Initial)
    
  
-  [Skype Room Systems v2 Deployment Checklist](configure-a-skype-room-systems-v2-console.md#Checklist)
    
  

> [!NOTE]
> Skype Room Systems v2 will only work in a properly configured Skype for Business environment where the device accounts are set up correctly as described in  [Deploy Skype Room Systems v2](deploy-skype-room-systems-v2.md). 
  
    
    


## Prepare the installation image
<a name="Prep_Image"> </a>

Installing the Skype Room Systems v2 app on a Surface Pro 4 requires a USB storage device with at least 8 GB of memory formatted as a FAT32 disk. There should be no other files on the device.
  
    
    

> [!NOTE]
> Failure to create your console image according to these instructions will likely result in unexpected behavior. Windows 10 Enterprise Creators Update (build 1703) is not supported for Skype Room Systems v2 image creation. 
  
    
    


1. Attach the USB disk to your computer ( **not** to the Surface 4 that you will use for the console, a combination of the Skype Room Systems v2, software a Surface Pro 4 and an approved Skype Room Systems v2 dock). The following command examples assume the USB disk is recognized as **F:**.
    
  
2. Obtain a copy of the 64-bit version of Windows 10 Enterprise Anniversary edition (English language, build 1607). 
    
  
3. Mount the Windows 10 Enterprise ISO file (Right click the ISO file and select **Mount**.) and copy everything on it to the USB disk ( **F:** ).
    
  
4. Download the  [Skype Room Systems v2 installation package](https://go.microsoft.com/fwlink/?linkid=851168) and install it to your computer as follows:
    
    > [!IMPORTANT]
      > If you've installed the SRS Deployment Kit previously, uninstall it. Do not install it on the device you plan to set up as a console, or on the USB disk recognized as **F:**

1. Run the .msi installer. Click **Next**.
    
  
2. Accept the EULA agreement and click **Next**.
    
  
3. Select a destination folder on your computer and note its location.
    
  
4. Click **Next**.
    
  
5. Click **Install**.
    
  
6. Click **Finish**.
    
  
5. Navigate to the directory folder you selected as the destination folder for the .msi installer package. Select all files in the directory and copy them to the root **F:** directory.
    
    > [!IMPORTANT]
      > Do not copy the installation folder, just the files contained in it. Copying the folder to **F:** will cause setup of a Skype Room Systems v2 device to fail.
6. Download the  [Surface Pro 4 drivers](http://download.microsoft.com/download/6/a/c/6acb37c4-e4c1-4e0e-bbae-ac7a0c303593/SurfacePro4_Win10_1701001_0.zip). 
    
  
7. Open the driver ZIP file and copy the folder  *SurfacePro4_Win10_** to the directory " *F:*  \\AutoUnattend_Files\\DistShare\\Out-of-Box Drivers" on the USB disk.
    
  
8. In the root of your USB drive, there is a file named AutoUnattend.xml: Open it with a text editor. There are two commands referring to Sysprep.exe, they are next to each other in the file. Examine them and comment or uncomment (using the strings <!--  *command*  -->) the command appropriate for the following tasks:
    
  - If you intend to capture a WIM for mass-imaging Skype Room Systems v2 devices, find the following line: 
    
    <!-- <Path>%SystemRoot%\\System32\\Sysprep\\Sysprep.exe /generalize /oobe /shutdown /unattend:%SystemDrive%\\Rigel\\x64\\Scripts\\Provisioning\\audit.xml</Path> -->
    
    And edit it to read
    
    <Path>%SystemRoot%\\System32\\Sysprep\\Sysprep.exe /generalize /oobe /shutdown /unattend:%SystemDrive%\\Rigel\\x64\\Scripts\\Provisioning\\audit.xml</Path>
    
  
  - If you intend to image devices one at a time, make sure the following line is not enclosed in XML comments, as shown: 
    
    <Path>%SystemRoot%\\System32\\Sysprep\\Sysprep.exe /oobe /reboot /unattend:%SystemDrive%\\Rigel\\x64\\Scripts\\Provisioning\\audit.xml</Path>
    
  

    > [!NOTE]
      > Be sure that whichever Sysprep.exe command you are not using is commented out. 
9. Remove the USB disk from your computer and proceed to  [Install Windows 10 and the Skype Room Systems v2 console app ](configure-a-skype-room-systems-v2-console.md#Reimage).
    
  

## Install Windows 10 and the Skype Room Systems v2 console app
<a name="Reimage"> </a>

You now need to apply the image you've created. The Surface Pro 4 will run as an appliance and the default user will be set to only run the Skype Room Systems v2 app. 
  
    
    

1. The Surface Pro 4 should be connected to a power source. Start from a completely powered-off state. If necessary, press and keep pressing the Power button until the Surface Pro 4 switches off.
    
  
2. Plug your USB Setup disk into the Surface Pro 4.
    
  
3. Press and continue to hold the volume down (-) button on the Surface Pro 4. 
    
  
4. Press and release the power button on the Surface Pro 4.
    
  
5. Once Windows setup is booted, release the volume down (-) button.
    
  
6. When the Skype Room Systems v2 device starts for the first time, its behavior will depend on which version of Sysprep.exe is used in the AutoUnattend.xml file (see step 8 of  [Prepare the installation image](configure-a-skype-room-systems-v2-console.md#Prep_Image)):
    
  - If the /shutdown version of the command was enabled, the system will proceed with installation and eventually shut down. Once it is shut down, you may boot to external media containing Windows PE and use DISM to install language packs, apply images, capture your reference image from the machine, or perform other actions.
    
  
  - If the /reboot version of the command was enabled, the system will proceed with installation, and eventually ask the user to select their locale settings. After making this selection, the Skype Room Systems v2 device will boot into its initial startup process. See  [Initial set up of the Console ](configure-a-skype-room-systems-v2-console.md#Initial)
    
  
After the system has shut down or rebooted, it is safe to remove the USB Setup Disk. At this point, you can place the Surface Pro 4 in the dock and attach the peripherals needed for your meeting room. Refer to the manufacturer instructions.
  
    
    

### Adding Languages

IT professionals should download LIPs and their attendant LPs from the  [Windows 10 Language Interface Packs](https://www.microsoft.com/OEM/en/installation/downloads/Pages/Windows-10-Language-Interface-Packs.aspx) page.
  
    
    
LIPs (and their parent LPs) can be installed using the  [instructions on how to install a LIP to an offline Windows image](https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/add-language-interface-packs-to-windows).
  
    
    

## Initial set up of the Console
<a name="Initial"> </a>

After Windows is installed, the Skype Room Systems v2 app will go into its initial Setup process when it is started next or if the /reboot option was chosen.
  
    
    

1. The User Account screen appears. Enter the Skype sign-in address (in user@domain format) of the room account to be used with the device.
    
  
2. Enter the password for the room account, and re-enter it to verify.
    
  
3. Under "Configure Domain," set the FQDN for the Skype for Business Server. If the Skype for Business SIP domain is different from the Exchange domain of the user, enter the Exchange domain in this field.
    
  
4. Click **Next**.
    
  
5. Select the indicated devices on the Features screen and click **Next**. The default is to have Auto Screen sharing set to On and Hide meeting names set to Off. The devices to select are:
    
  - Microphone for Conferencing: the default microphone for this conference room.
    
  
  - Speaker for Conferencing: the default speaker for conferencing. 
    
  
  - Default Speaker: the speaker used for audio from the HDMI ingest.
    
  

    Each item has a drop-down menu of options to select from. You must make a selection for each device.
    
  
6. Click **Finish**.
    
  
The app should immediately start signing in to Skype for Business Server 2015 with the credentials entered above, and should also begin syncing its calendar with Exchange using those same credentials. For details on using the app, refer to the  [Skype Room Systems version 2 help](https://support.office.com/en-US/article/Skype-Room-Systems-version-2-help-e667f40e-5aab-40c1-bd68-611fe0002ba2).
  
    
    

> [!IMPORTANT]
> Skype Room Systems v2 relies on the presence of certified console hardware (the Logitech SmartDock). Even a correctly created image containing the the Skype Room Systems v2 app loaded on a Surface Pro 4 will not boot past the initial setup procedure unless the console hardware is detected. 
  
    
    


> [!NOTE]
> Some non-English language users may need a physical keyboard connected to the Console during initial setup in the event that symbols are not supported on the touch keyboard. 
  
    
    


### Install a private CA certificate on the Surface Pro 4 device
<a name="Certs"> </a>

The Skype Room Systems v2 device needs to trust the certificates used by the Skype for Business and Exchange servers it connects to. For O365 this is done automatically, since these servers are using public Certificate Authorities and these are automatically trusted by Windows 10. In a case where the Certificate Authority is private, for instance an on-premises deployment with Active Directory and the Windows Certificate Authority, you can add the certificate to the Skype Room Systems v2 device in a couple of ways:
  
    
    

- You can join the device to Active Directory and that will automatically add the required certificates given the Certificate Authority is published to Active Directory (normal deployment option).
    
  
- You can install the certificate manually after the imaging process. Before you do this, you must complete  [Initial set up of the Console ](configure-a-skype-room-systems-v2-console.md#Initial). 
    
  

### To manually install the certificate


1. Download the CA certificate to your computer and save it to "C:\\Skype Room Systems\\x64\\Scripts\\Provisioning\\CAcertificate.cer".
    
  
2. Place the Surface 4 in admin mode (see  [Admin mode and device management](manage-skype-room-systems-v2.md#AdminMode)).
    
  
3. Run the following command:
    
  ```
  
certutil -addstore -f -enterprise root "C:\\Skype Room Systems\\x64\\Scripts\\Provisioning\\CAcertificate.cer"
  ```


### Join an Active Directory Domain (Optional)
<a name="Certs"> </a>

You can join Skype Room Systems v2 devices to your domain. Skype Room Systems v2 devices should be placed in a separate OU from your PC workstations because many workstation policies are not compatible with Skype Room Systems v2. A common example are password enforcement policies that will prevent Skype Room Systems v2 from starting up automatically. For information about the management of GPO settings, please refer to  [Manage Skype Room Systems v2](manage-skype-room-systems-v2.md). 
  
    
    

### To join Skype Room System v2 to a domain


1. Sign into the console from the admin account (see  [Admin mode and device management](manage-skype-room-systems-v2.md#AdminMode)).
    
  
2. Launch elevated Powershell command prompt.
    
  
3. Enter the following command in Powershell:
    
  ```
  Add-Computer -DomainName <Fully qualified domain> -OUPath "OU=<Child OU>, … ,OU=<Top level OU>,DC=<child domain>,…,DC=<top level domain>"
  ```

For example, if your fully qualified domain is redmond.corp.microsoft.com and you want your Skype Room Systems v2 devices to be in a "Skype Room Systems v2" OU that is a child of a "Resources" OU, the command will be:
  
    
    



```
Add-Computer -DomainName redmond.corp.microsoft.com -OUPath "OU=Skype_Room_System,OU=Resources,DC=redmond,DC=corp,DC=microsoft,DC=com"
```

 If you would like to rename the computer when joining it to a domain, use the -NewName flag followed by the computer's new name.
  
    
    

## Skype Room Systems v2 Deployment Checklist
<a name="Checklist"> </a>

Use the following checklist while doing a final verification that the console device and all its peripherals are fully configured:
  
    
    


||**Application Settings**|
|:-----|:-----|
|☐  <br/> |Room account name and phone # (if PSTN enabled) are correctly displayed in top right of console screen  <br/> |
|☐  <br/> |Windows computer name is set correctly (useful for remote administration)  <br/> |
|☐  <br/> |Administrator account password set and verified  <br/> |
|☐  <br/> |All Surface Pro 4 System Updates have been applied  <br/> |
|||
||**Audio/Video Peripherals**|
|:-----|:-----|
|☐  <br/> |Camera peripheral firmware version is correct (if applicable)  <br/> |
|☐  <br/> |Camera functional and positioned optimally  <br/> |
|☐  <br/> |Settings for Playback Default Device and Playback Default Communications Device set to intended audio peripheral  <br/> |
|☐  <br/> |Settings for Recording Default Communication Device set to the intended audio peripheral  <br/> |
|☐  <br/> |Audio peripheral firmware version is correct (if applicable)  <br/> |
|☐  <br/> |Audio input device functional and optimally positioned  <br/> |
|☐  <br/> |Audio output device functional and optimally positioned  <br/> |
|||
||**Dock**|
|:-----|:-----|
|☐  <br/> |Cables are secure and not pinched  <br/> |
|☐  <br/> |Audio ingest over HDMI is functional  <br/> |
|☐  <br/> |Video ingest over HDMI is functional  <br/> |
|☐  <br/> |Dock can swivel freely  <br/> |
|☐  <br/> |Display brightness is acceptable for environment  <br/> |
   

## See also
<a name="Checklist"> </a>


#### 


  
    
    
 [Plan for Skype Room Systems v2](plan-for-skype-room-systems-v2.md)
  
    
    
 [Deploy Skype Room Systems v2](deploy-skype-room-systems-v2.md)
  
    
    
 [Configure a Skype Room Systems v2 console](configure-a-skype-room-systems-v2-console.md)
  
    
    
 [Manage Skype Room Systems v2](manage-skype-room-systems-v2.md)
