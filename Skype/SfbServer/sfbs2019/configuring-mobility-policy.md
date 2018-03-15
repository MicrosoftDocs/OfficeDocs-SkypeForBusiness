---
title: "Configuring mobility policy in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 595536e0-9bb3-49a3-8d13-1a77351ebc62
description: "Lync Server 2013 provides mobility policies that determine who can use mobility features, Call via Work, voice over IP (VoIP) or video, and whether WiFi will be required for either VoIP or video. The Call via Work feature enables a mobile user to make and receive calls on a mobile phone by using a work phone number instead of the mobile phone number. This feature prevents the called party from seeing the caller's mobile phone number and enables a user to avoid outbound calling charges. Configuring VoIP and video makes it possible for users to receive and make VoIP calls and video. Settings for WiFi usage define if a user's device will be required to use a WiFi network over a cellular data network."
---

# Configuring mobility policy in Lync Server 2013
[]
```
Some information in this topic pertains to Cumulative Updates for Lync Server 2013: February 2013.
```

Lync Server 2013 provides mobility policies that determine who can use mobility features, Call via Work, voice over IP (VoIP) or video, and whether WiFi will be required for either VoIP or video. The Call via Work feature enables a mobile user to make and receive calls on a mobile phone by using a work phone number instead of the mobile phone number. This feature prevents the called party from seeing the caller's mobile phone number and enables a user to avoid outbound calling charges. Configuring VoIP and video makes it possible for users to receive and make VoIP calls and video. Settings for WiFi usage define if a user's device will be required to use a WiFi network over a cellular data network.
  
By default, mobility, Call via Work, and the VoIP and video features are enabled. The settings to require WiFi for VoIp and video are disabled. Administrators can determine who has access to these features by running a cmdlet. You can turn options off globally, by site, or by user.
  
To be able to use mobility features and Call via Work, users must meet the following prerequisites:
  
- Users must be enabled for Lync Server 2013.
    
- Users must be enabled for Enterprise Voice.
    
- Users must be assigned a mobility policy that has the **EnableMobility** option set to True. 
    
For users to be able to use Call via Work, they must meet the following two additional prerequisites:
  
- Users must be assigned a voice policy that has the **Enable simultaneous ringing of phones** option selected. 
    
- Users must be assigned a mobility policy that has the **EnableOutsideVoice** option set to True. 
    
> [!NOTE]
> Users who are not enabled for Enterprise Voice can use their mobile devices to make Lync to Lync Voice over IP (VoIP) calls, or can join conferences by using the Click to Join link on their mobile devices, if you assign those users the appropriate options for voice policy. For details, see [Defining your mobility requirements for Lync Server 2013](defining-your-mobility-requirements.md). 
  
For details about enabling users for Lync Server 2013, see [Disable or re-enable user account for Lync Server 2013](disable-or-re-enable-user-account-for-lync-server.md). For details about enabling users for Enterprise Voice, see [Enable users for Enterprise Voice in Lync Server 2013](enable-users-for-enterprise-voice.md). For details about setting voice policy options, see [Modify a voice policy and configure PSTN usage records in Lync Server 2013](modify-a-voice-policy-and-configure-pstn-usage-records.md).
  
### To modify global mobility policy

1. Log on to any computer where Lync Server Management Shell and Ocscore are installed as a member of the CsAdministrator role.
    
2. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
3. Turn off access to mobility and Call via Work globally. At the command line, type:
    
  ```
  Set-CsMobilityPolicy -EnableMobility $False -EnableOutsideVoice $False
  ```

    > [!NOTE]
    > You can turn off Call via Work without turning off access to mobility. However, you cannot turn off mobility without also turning off Call via Work. 
  
### To modify mobility policy by site

1. Log on to any computer where Lync Server Management Shell and Ocscore are installed as a member of the CsAdministrator role.
    
2. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
3. Create a site-level policy, and turn off VoIP and video, and enable Require WiFi for IP Audio and for IP Video by site. At the command line, type:
    
  ```
  New-CsMobilityPolicy -Identity site:<site identifier> -EnableIPAudioVideo $False -RequireWiFiForIPAudio $True -RequireWiFiForIPVideo $True
  ```

### To modify mobility policy by user

1. Log on to any computer where Lync Server Management Shell and Ocscore are installed as a member of the CsAdministrator role.
    
2. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
3. Create user level mobility policies and turn off mobility and Call via Work by user. At the command line, type:
    
  ```
  New-CsMobilityPolicy -Identity <policy name> -EnableMobility $False -EnableOutsideVoice $False
  Grant-CsMobilityPolicy -Identity <user identifier> -PolicyName <policy name>
  
  ```

    You can turn off Call via Work without turning off access to mobility. However, you cannot turn off mobility without also turning off Call via Work.
    
    For example:
    
  ```
  New-CsMobilityPolicy "tag:disableOutsideVoice" -EnableOutsideVoice $False
  Grant-CsMobilityPolicy -Identity -MobileUser1@contoso.com -PolicyName Tag:disableOutsideVoice
  ```

## See also

#### 

[Disable or re-enable user account for Lync Server 2013](disable-or-re-enable-user-account-for-lync-server.md)
  
[Enable users for Enterprise Voice in Lync Server 2013](enable-users-for-enterprise-voice.md)
  
[Modify a voice policy and configure PSTN usage records in Lync Server 2013](modify-a-voice-policy-and-configure-pstn-usage-records.md)
#### 

[Defining your mobility requirements for Lync Server 2013](defining-your-mobility-requirements.md)
#### 

[New-CsMobilityPolicy](new-csmobilitypolicy.md)
  
[Set-CsMobilityPolicy](set-csmobilitypolicy.md)
  
[Get-CsMobilityPolicy](get-csmobilitypolicy.md)
  
[Grant-CsMobilityPolicy](grant-csmobilitypolicy.md)
  
[Remove-CsMobilityPolicy](remove-csmobilitypolicy.md)

