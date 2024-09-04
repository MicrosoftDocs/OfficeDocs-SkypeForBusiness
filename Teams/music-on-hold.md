---
title: Music on Hold
author: mkbond007
ms.author: mabond
manager: pamgreen
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - Tier1
  - ContentFreshnessFY24
audience: Admin
ms.reviewer: roykuntz
ms.date: 06/27/2024
appliesto:
  - Microsoft Teams
ms.localizationpriority: medium
ms.custom:
description: Learn how to manage the Music on Hold feature in Microsoft Teams Phone.
---

# Music on Hold

When a Microsoft Teams user places an incoming call on hold, the caller can listen to selected music. 

The music that is played is either the default music provided by Microsoft, custom music that you upload and configure, or music streamed from a supported streaming music on hold partner, where you have a subscription.  

As the tenant administrator, you configure whether Music on Hold is available by creating a Teams calling policy and assigning the policy to the Teams user.

The default music supplied in Microsoft Teams call scenarios is free of any royalties payable by your organization.

Callers can listen to Music on Hold in other scenarios as well; for example, when they call into a Cloud Call Queue or when their call is parked by a Microsoft Teams user. These scenarios aren't covered or controlled by the features mentioned in this article.

## Configure Music on Hold

To configure Music on Hold:

1. In the left navigation of the Teams admin center, go to **Voice > Calling policies**.

1. On the **Manage policies** tab, select one of the existing policies or create a new one.

1. In the **Music on hold for calls** field, select **On** from the toggle.

1. Select **Save**.

You can also configure Music on Hold by using the Teams PowerShell module. In the TeamsCallingPolicy, change the `-MusicOnHoldEnabledType` parameter to **Enabled** and then grant that policy instance to one or more users.

If a Teams user has a Teams calling policy with Music on Hold turned off, then no music is played when the Teams user places the call on hold.

## Configure custom music

In addition to playing default music to callers, you can upload a custom audio file with music or other audio content and configure that audio file to be played to the caller. For example, a department or organization might want to play a custom announcement or custom music when external Public Switched Telephone Network (PSTN) callers are put on hold.

The configuration is done using call hold policies.

> [!NOTE]
> You're responsible for independently clearing and securing all necessary rights and permissions to use any music or audio file with your Microsoft Teams service. This may include intellectual property and other rights in any music, sound effects, audio, brands, names, and other content in the audio file from all relevant rights holders. Holders may include artists, actors, performers, musicians, songwriters, composers, record labels, music publishers, unions, guilds, rights societies, collective management organizations, and any other parties who own, control or license the music copyrights, sound effects, audio and other intellectual property rights.

### Use the Teams admin center

You can use the Teams admin center to configure custom music on hold for your users by creating or editing call hold policies.

To configure a new call hold policy:

1. In the Teams admin center, go to **Voice** > **Call hold policies**.

2. Select the **Add** tab.

3. Give the policy a name and a description.

4. Select **Upload file** to upload the custom music audio file.

5. Select **Apply**.

### Assign a custom call hold policy to users

[!INCLUDE [assign-policy](includes/assign-policy.md)]

### Use PowerShell

To configure custom Music on Hold, use the PowerShell cmdlets [New/Get/Set/Grant/Remove-CsTeamsCallingPolicy](/powershell/module/teams/set-csteamscallingpolicy), [New/Get/Set/Grant/Remove-CsTeamsCallHoldPolicy](/powershell/module/teams/set-csteamscallholdpolicy), and [Import/Get/Remove/Export-CsOnlineAudioFile](/powershell/module/teams/import-csonlineaudiofile) in Teams PowerShell module 3.0.0 or later.

For supported audio formats and maximum file size, see [Import-CsOnlineAudioFile](/powershell/module/teams/import-csonlineaudiofile).

1. Ensure that the Teams user has `-MusicOnHoldEnabledType` set to **Enabled** in the Teams calling policy.

2. Upload the custom audio file.

3. Create a Teams call hold policy referencing the custom audio file and assign it to the Teams user.

### Upload the custom audio file

The configuration of custom Music on Hold starts with uploading the audio file. You use the PowerShell cmdlet [Import-CsOnlineAudioFile](/powershell/module/teams/import-csonlineaudiofile) for this purpose.

An example of uploading an MP3 audio file using Windows PowerShell 5.1 is shown below. For other examples, see [Import-CsOnlineAudioFile](/powershell/module/teams/import-csonlineaudiofile).

```PowerShell
C:\> $content = [System.IO.File]::ReadAllBytes('C:\tmp\customMoH1.mp3')
C:\> $AudioFile = Import-CsOnlineAudioFile -FileName "customMoH1.mp3" -Content $content
C:\> $AudioFile
Id            : 56a56961f2794f098a359885ec1454a1
FileName      : customMoH1.mp3
ApplicationId : TenantGlobal
```

### Reference the audio file in a Teams call hold policy

After you upload the audio file, you need to reference the file in a Teams call hold policy by using the ID of the file when you create or set a Teams call hold policy.

For example, the following script creates a new TeamsCallHoldPolicy and references the custom audio file:

```PowerShell
C:\> New-CsTeamsCallHoldPolicy -Identity "CustomMoH1" -Description "Custom MoH using CustomMoH1.mp3" -AudioFileId $AudioFile.Id
```

After you create the new Teams call hold policy, you can grant it to your users using Grant-CsTeamsCallHoldPolicy with the following script:

```PowerShell
C:\> Grant-CsTeamsCallHoldPolicy -PolicyName "CustomMoH1" -Identity user1@contoso.com
```

To get information about your uploaded audio files, use the Get-CsOnlineAudioFile cmdlet.

To remove an uploaded audio file, use the Remove-CsOnlineAudioFile cmdlet. Before removing an audio file, check that you aren't using that audio file in a TeamsCallHoldPolicy.

To export an uploaded audio file, use the Export-CsOnlineAudioFile cmdlet.

## Configure streaming music

Streaming Music on Hold allows you to use a supported streaming service to play music to callers. The streaming partner gives you a URL to add to your TeamsCallingPolicy that is then used to play music. You can configure streaming Music on Hold if you have a subscription with a supported partner, such as [Easy On Hold](https://easyonhold.com/).

Once you set up the streaming content with your partner’s administration tool, you are provided with a URL for the streaming source that can then be used to configure your Teams Call Hold Policy. Streaming Music on Hold can only be configured with PowerShell.

To configure streaming Music on Hold, use the PowerShell cmdlets [New/Get/Set/Grant/Remove-CsTeamsCallingPolicy](/powershell/module/teams/set-csteamscallingpolicy) and [New/Get/Set/Grant/Remove-CsTeamsCallHoldPolicy](/powershell/module/teams/set-csteamscallholdpolicy).

1. Ensure that the Teams user has `-MusicOnHoldEnabledType` set to **Enabled** in the Teams calling policy.

1. Configure the streaming content using your subscription at one of the streaming music on hold partners and get the streaming source URL.

1. Create a Teams call hold policy referencing the streaming source URL and assign it to the Teams user.

### Reference the streaming source URL in a Teams call hold policy

After you configure the streaming content with a supported partner and receive the streaming source URL, you need to reference the URL in a Teams Call Hold Policy.  

For example, the following script creates a new TeamsCallHoldPolicy and references the streaming source URL:

```powershell
C:\> New-CsTeamsCallHoldPolicy -Identity 'StreamingMoH1' -StreamingSourceUrl 'https://teams-streaming.easyonholdcloud.com/08297e2a-61bf-480c-b7b4-0576fc3ca6ce' -StreamingSourceAuthType AzureAd
```

After you create the new Teams Call Hold Policy, you can grant it to your users using Grant-CsTeamsCallHoldPolicy with the following script:

```powershell
C:\> Grant-CsTeamsCallHoldPolicy -PolicyName "StreamingMoH1" -Identity user2@contoso.com 
```

## Feature availability

The following table indicates which features on which clients and devices support Music on Hold, Custom Music on Hold, and Streaming Music on Hold. Microsoft continues to add feature support, so check back often for additional availability.

| Feature | Desktop <br> Windows/Mac OS | Browser | Mobile <br> iOS | Mobile <br> Android | Teams Phone |
| :------------| :------- | :------- | :------- | :------- | :------- |
| Hold on 1:1 PSTN call | - Music on Hold<br>- Custom Music on Hold<br>- Streaming Music on Hold | - Music on Hold<br>- Custom Music on Hold<br>- Streaming Music on Hold | - Music on Hold<br>- Custom Music on Hold<br>- Streaming Music on Hold | - Music on Hold<br>- Custom Music on Hold<br>- Streaming Music on Hold | - Music on Hold<br>- Custom Music on Hold |
| Hold on 1:1 Teams call | - Music on Hold<br>- Custom Music on Hold<br>- Streaming Music on Hold | - Music on Hold<br>- Custom Music on Hold<br>- Streaming Music on Hold | - Music on Hold<br>- Custom Music on Hold<br>- Streaming Music on Hold | - Music on Hold<br>- Custom Music on Hold<br>- Streaming Music on Hold | - Music on Hold<br>- Custom Music on Hold |
| Hold on Transfer on 1:1 PSTN call | - Music on Hold<br>- Custom Music on Hold<br>- Streaming Music on Hold | - Music on Hold<br>- Custom Music on Hold<br>- Streaming Music on Hold | - Music on Hold<br>- Custom Music on Hold<br>- Streaming Music on Hold | - Music on Hold<br>- Custom Music on Hold<br>- Streaming Music on Hold | - Music on Hold<br>- Custom Music on Hold |
| Hold on Transfer on 1:1 Teams call | - Music on Hold<br>- Custom Music on Hold<br>- Streaming Music on Hold | - Music on Hold<br>- Custom Music on Hold<br>- Streaming Music on Hold | - Music on Hold<br>- Custom Music on Hold<br>- Streaming Music on Hold | - Music on Hold<br>- Custom Music on Hold<br>- Streaming Music on Hold | - Music on Hold<br>- Custom Music on Hold |
| Hold on Consultative Transfer on 1:1 PSTN call |- Music on Hold<br>- Custom Music on Hold<br>- Streaming Music on Hold || - Music on Hold<br>- Custom Music on Hold<br>- Streaming Music on Hold | - Music on Hold<br>- Custom Music on Hold<br>- Streaming Music on Hold | - Music on Hold<br>- Custom Music on Hold |
| Hold on Consultative Transfer on 1:1 Teams call |- Music on Hold<br>- Custom Music on Hold<br>- Streaming Music on Hold || - Music on Hold<br>- Custom Music on Hold<br>- Streaming Music on Hold | - Music on Hold<br>- Custom Music on Hold<br>- Streaming Music on Hold | - Music on Hold<br>- Custom Music on Hold |

## Restrictions

- Music on Hold is only available when the user is in TeamsOnly mode.

- If the called Teams user is enabled for Location-Based Routing, only the standard Music on Hold is played to the caller.

- Custom Music on Hold isn't available for users configured for Shared Line Appearance (delegation) and when Call Park is used. The standard Music on Hold is played.

- In some scenarios, a Direct Routing media bypass call is converted to non-media bypass for playing Music on Hold and the call stays as non-media bypass until the call is terminated.

- Streaming Music on Hold requires a subscription with a supported Streaming Music on Hold partner.

- If you have both Custom Music on Hold and Streaming Music on Hold configured within the same TeamsCallingPolicy, Streaming Music on Hold takes precedence.

## Related articles

- [Assign policies to users](policy-assignment-overview.md)

- [Get-CsTeamsCallingPolicy](/powershell/module/teams/get-csteamscallingpolicy)

- [Set-CsTeamsCallingPolicy](/powershell/module/teams/set-csteamscallingpolicy)

- [Import-CsOnlineAudioFile](/powershell/module/teams/import-csonlineaudiofile)

- [Export-CsOnlineAudioFile](/powershell/module/teams/export-csonlineaudiofile)

- [Get-CsOnlineAudioFile](/powershell/module/teams/get-csonlineaudiofile)

- [Remove-CsOnlineAudioFile](/powershell/module/teams/remove-csonlineaudiofile)

- [New-CsTeamsCallHoldPolicy](/powershell/module/teams/new-csteamscallholdpolicy)

- [Get-CsTeamsCallHoldPolicy](/powershell/module/teams/get-csteamscallholdpolicy)

- [Grant-CsTeamsCallHoldPolicy](/powershell/module/teams/grant-csteamscallholdpolicy)

- [Remove-CsTeamsCallHoldPolicy](/powershell/module/teams/remove-csteamscallholdpolicy)
