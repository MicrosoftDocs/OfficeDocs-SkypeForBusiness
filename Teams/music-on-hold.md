---
title: Music on Hold
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.collection: 
  - M365-voice
audience: Admin
ms.reviewer: roykuntz
appliesto:
  - Microsoft Teams
ms.localizationpriority: medium
ms.custom:
description: Learn how to manage the Music on Hold feature in Phone System.
---

# Music on Hold

When a Microsoft Teams user places an incoming call on hold, the caller can listen to selected music.

The music that is played is either the default music provided by Microsoft or custom music that you upload and configure. As the tenant administrator, you configure whether Music on Hold is available by creating a Teams calling policy and assigning the policy to the Teams user.

The default music supplied in Microsoft Teams call scenarios is free of any royalties payable by your organization.

Note that callers can listen to Music on Hold in other scenarios as well; for example, when they call into a Cloud Call Queue or when their call is parked by a Microsoft Teams user. These scenarios are not covered or controlled by the features mentioned in this article.

## Configure Music on Hold

To configure Music on Hold:

1.	In the left navigation of the Teams admin center, go to **Voice > Calling policies**.

2.	On the **Manage policies** tab select one of the existing policies or create a new one.

3.	In the **Music on hold for PSTN callers** field select **Enabled** in the drop-down menu.

You can also configure Music on Hold by using the Teams PowerShell module. In the TeamsCallingPolicy, change the MusicOnHoldEnabledType parameter to Enabled and then grant that policy instance to one or more users.

If a Teams user has a Teams calling policy with Music on Hold set to Disabled, then no music will be played when the Teams user places the call on hold.

## Configure custom music

In addition to playing default music to callers, you can upload a custom audio file with music or other audio content and configure that audio file to be played to the caller.
For example a department or organization might want to play a custom announcement or custom music when external PSTN callers are put on hold.  

> [!NOTE]
> You are responsible for independently clearing and securing all necessary rights and permissions to use any music or audio file with your Microsoft Teams service. This may include intellectual property and other rights in any music, sound effects, audio, brands, names, and other content in the audio file from all relevant rights holders. Holders may include artists, actors, performers, musicians, songwriters, composers, record labels, music publishers, unions, guilds, rights societies, collective management organizations, and any other parties who own, control or license the music copyrights, sound effects, audio and other intellectual property rights.

To configure custom Music on Hold, use the PowerShell cmdlets New/Get/Set/Grant/Remove-CsTeamsCallHoldPolicy and Import/Get/Remove/Export-CsOnlineAudioFile in Teams PowerShell module 3.0.0 or later.

For supported audio formats and maximum file size, please see [Import-CsOnlineAudioFile](/powershell/module/skype/import-csonlineaudiofile)


1. Ensure that the Teams user has Music on hold for PSTN callers set to Enabled in the Teams calling policy. 

2. Upload the custom audio file.

3. Create a Teams Call Hold policy referencing the custom audio file and assign it to the Teams user.

### Upload the custom audio file

The configuration of custom Music on Hold starts with uploading the audio file. You use the PowerShell cmdlet [Import-CsOnlineAudioFile](/powershell/module/skype/import-csonlineaudiofile) for this purpose.

An example of uploading an MP3 audio file using Windows PowerShell 5.1 is shown below. For other examples, see [Import-CsOnlineAudioFile](/powershell/module/skype/import-csonlineaudiofile).

```PowerShell
C:\> $content = Get-Content "C:\tmp\customMoH1.mp3" -Encoding byte -ReadCount 0
C:\> $AudioFile = Import-CsOnlineAudioFile -FileName "customMoH1.mp3" -Content $content
C:\> $AudioFile
Id            : 56a56961f2794f098a359885ec1454a1
FileName      : customMoH1.mp3
ApplicationId : TenantGlobal
```

### Reference the audio file in a Teams Call Hold Policy

After you have uploaded the audio file, you need to reference the file in a Teams Call Hold Policy by using the Id of the file when you create or set a Teams Call Hold Policy. For example:

```PowerShell
C:\> New-CsTeamsCallHoldPolicy -Identity "CustomMoH1" -Description "Custom MoH using CustomMoH1.mp3" -AudioFileId $AudioFile.Id
```

After you have created the new Teams Call Hold Policy, you can grant it to your users using Grant-CsTeamsCallHoldPolicy as follows:

```PowerShell
C:\> Grant-CsTeamsCallHoldPolicy -PolicyName "CustomMoH1" -Identity user1@contoso.com
```

To get information about your uploaded audio files, use the Get-CsOnlineAudioFile cmdlet.

To remove an uploaded audio file, use the Remove-CsOnlineAudioFile cmdlet. Before removing an audio file, check that you are not using that audio file in a TeamsCallHoldPolicy.

To export an uploaded audio file, use the Export-CsOnlineAudioFile cmdlet.

## Feature availability

The following table indicates which features on which clients and devices support Music on Hold and Custom Music on Hold. Microsoft continues to add feature support, so check back often for additional availability.


| Feature | Desktop <br> Windows/Mac OS | Browser | Mobile <br> iOS | Mobile <br> Android | Teams Phone |
| :------------| :------- | :------- | :------- | :------- | :------- |
| Hold on 1:1 PSTN call | -Music on Hold<br>-Custom Music on Hold | -Music on Hold<br>-Custom Music on Hold | -Music on Hold<br>-Custom Music on Hold | -Music on Hold<br>-Custom Music on Hold | -Music on Hold<br>-Custom Music on Hold |
| Hold on 1:1 Teams call | -Music on Hold<br>-Custom Music on Hold | -Music on Hold<br>-Custom Music on Hold | -Music on Hold<br>-Custom Music on Hold | -Music on Hold<br>-Custom Music on Hold | -Music on Hold<br>-Custom Music on Hold |
| Hold on Consultative Transfer on 1:1 PSTN call |-Music on Hold<br>-Custom Music on Hold || -Music on Hold<br>-Custom Music on Hold | -Music on Hold<br>-Custom Music on Hold | -Music on Hold<br>-Custom Music on Hold |
| Hold on Consultative Transfer on 1:1 Teams call |-Music on Hold<br>-Custom Music on Hold || -Music on Hold<br>-Custom Music on Hold | -Music on Hold<br>-Custom Music on Hold | -Music on Hold<br>-Custom Music on Hold |

## Restrictions

- Music on Hold is only available in commercial and GCC cloud instances.

- Music on Hold is only available when the user is in TeamsOnly mode.

- If the called Teams user is enabled for Location-Based Routing, Music on Hold cannot be played to the caller.

- Custom Music on Hold is not available for users configured for Shared Line Appearance (delegation) and when Call Park is used. The standard Music on Hold will be played.

- In some scenarios, a Direct Routing media bypass call will be converted to non-media bypass for playing Music on Hold and the call will stay as non-media bypass until the call is terminated.

## Related topics

- [Assign policies to users](policy-assignment-overview.md)

- [Get-CsTeamsCallingPolicy](/powershell/module/skype/get-csteamscallingpolicy)

- [Set-CsTeamsCallingPolicy](/powershell/module/skype/set-csteamscallingpolicy)

- [Import-CsOnlineAudioFile](/powershell/module/skype/import-csonlineaudiofile)

- [Export-CsOnlineAudioFile](/powershell/module/skype/export-csonlineaudiofile)

- [Get-CsOnlineAudioFile](/powershell/module/skype/get-csonlineaudiofile)

- [Remove-CsOnlineAudioFile](/powershell/module/skype/remove-csonlineaudiofile)

- [New-CsTeamsCallHoldPolicy](/powershell/module/skype/new-csteamscallholdpolicy)

- [Get-CsTeamsCallHoldPolicy](/powershell/module/skype/get-csteamscallholdpolicy)

- [Grant-CsTeamsCallHoldPolicy](/powershell/module/skype/grant-csteamscallholdpolicy)

- [Remove-CsTeamsCallHoldPolicy](/powershell/module/skype/remove-csteamscallholdpolicy)

