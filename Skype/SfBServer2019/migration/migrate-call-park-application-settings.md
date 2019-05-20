---
title: "Migrate Call Park application settings"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "The migration of the Call Park application includes provisioning the Skype for Business Server 2019 pool with any custom music on hold files that have been uploaded in the legacy install, restoring the service level settings and retargeting all Call Park orbits to the Skype for Business Server 2019 pool. If customized music-on-hold files have been configured in the pool, these files need to be copied to the new Skype for Business Server 2019 pool. Additionally, it is recommended that you back up any Call Park customized music-on-hold files from to another destination to keep a separate backup copy of any customized music-on-hold files that have been uploaded for Call Park. The customized music-on-hold files for the Call Park application are stored in the file store of the pool. To copy the audio files from a pool file store to a Skype for Business Server 2019 file store, use the Xcopy command with the following parameters:"
---

# Migrate Call Park application settings

The migration of the Call Park application includes provisioning the Skype for Business Server 2019 pool with any custom music-on-hold files that have been uploaded in the legacy install, restoring the service-level settings and re-targeting all Call Park orbits to the Skype for Business Server 2019 pool. If customized music-on-hold files have been configured in the pool, these files need to be copied to the new Skype for Business Server 2019 pool. Additionally, it is recommended that you back up any Call Park customized music-on-hold files to another destination to keep a separate backup copy of any customized music-on-hold files that have been uploaded for Call Park. The customized music-on-hold files for the Call Park application are stored in the file store of the pool. To copy the audio files from a pool file store to a Skype for Business Server 2019 file store, use the **Xcopy** command with the following parameters: 

```
Xcopy <Source: legacy Pool CPS File Store Path> <Destination: Skype for Business Server 2019 Pool CPS File Store Path>
```

```
Example usage:  Xcopy "<legacy File Store Path>\OcsFileStore\coX-ApplicationServer-X\AppServerFiles\CPS\"  "<Skype for Business Server 2019 File Store Path>\OcsFileStore\coX-ApplicationServer-X\AppServerFiles\CPS\" 
```

When all customized audio files have been copied to the Skype for Business Server 2019 file store, the Call Park application settings of the Skype for Business Server 2019 pool must be configured, and the Call Park orbit ranges that are associated with the legacy pool must be reassigned to the Skype for Business Server 2019 pool.

The Call Park application settings include the pickup timeout threshold, enabling or disabling music on hold, the maximum call pickup attempts, and the timeout request. You must manage Call Park application settings by using the Skype for Business Server Management Shell to run the **Set-CsCpsConfiguration** cmdlet. You cannot manage the Call Park application settings using the Skype for Business Server Control Panel. 

## Reconfigure the Call Park Service Settings

1. From the Skype for Business Server 2019 Front End Server, open the Skype for Business Server Management Shell.

2. At the command line, type the following:

    > [!NOTE]
    > If your Skype for Business Server 2019 Call Park application settings are identical to the legacy settings, you can skip this step. If Call Park application settings are different for the Skype for Business Server 2019 and legacy environments, use the cmdlet below as a template to update those changes. 

   ```
   Set-CsCpsConfiguration -Identity "<LS2013 Call Park Service ID>" -CallPickupTimeoutThreshold "<LS2010 CPS TimeSpan>" -EnableMusicOnHold "<LS2010 CPS value>" -MaxCallPickupAttempts "<LS2010 CPS pickup attempts>" -OnTimeoutURI "<LS2010 CPS timeout URI>"
   ```

To reassign all Call Park orbit ranges from the legacy pool to the Skype for Business Server 2019 pool, you can use either the Skype for Business Server Control Panel or the Skype for Business Server Management Shell. 

## Reassign all Call Park Orbit Ranges using Skype for Business Server Control Panel

1. Open Skype for Business Server Control Panel.

2. In the left pane, select **Voice Features**.

3. Select the **Call Park** tab. 

4. For each Call Park orbit range assigned to a legacy pool, edit the **FQDN of destination server** setting and select the Skype for Business Server 2019 pool that will process the Call Park requests. 

5. Select **Commit** to save the changes. 

## Reassign all Call Park Orbit Ranges using Skype for Business Server Management Shell

1. Open Skype for Business Server Management Shell.

2. At the command line, type the following:

   ```
   Get-CsCallParkOrbit
   ```

    This cmdlet lists all of the Call Park orbit ranges in the deployment. All Call Park orbits that have the **CallParkServiceId** and **CallParkServerFqdn** parameters set as the legacy pool must be reassigned. 

    To reassign the legacy Call Park orbit ranges to the Skype for Business Server 2019 pool, at the command line, type the following:

   ```
   Set-CsCallParkOrbit -Identity "<Call Park Orbit Identity>" -CallParkService "service:ApplicationServer:<Skype for Business Server 2019 Pool FQDN>"
   ```

After reassigning all Call Park orbit ranges to the Skype for Business Server 2019 pool, the migration process for the Call Park application will be completed and the Skype for Business Server 2019 pool will handle all future Call Park requests.


