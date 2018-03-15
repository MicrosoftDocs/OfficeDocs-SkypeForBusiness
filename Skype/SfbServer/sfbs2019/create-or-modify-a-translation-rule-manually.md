---
title: "Create or modify a translation rule manually in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 049d1db3-af58-48c5-be89-52e1d068a4bd
description: "Follow these steps if you want to define a translation rule by writing a regular expression for the matching pattern and translation rule. Alternatively, you can enter a set of values in the Build a Translation Rule tool and enable Lync Server Control Panel to generate the corresponding matching pattern and translation rule for you. For details, see Create or modify a translation rule by using the Build a Translation Rule tool in Lync Server 2013."
---

# Create or modify a translation rule manually in Lync Server 2013
[]
Follow these steps if you want to define a translation rule by writing a regular expression for the matching pattern and translation rule. Alternatively, you can enter a set of values in the **Build a Translation Rule** tool and enable Lync Server Control Panel to generate the corresponding matching pattern and translation rule for you. For details, see [Create or modify a translation rule by using the Build a Translation Rule tool in Lync Server 2013](create-or-modify-a-translation-rule-by-using-the-build-a-translation-rule-tool.md).
  
### To define a translation rule manually

1. Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the CsVoiceAdministrator, CsServerAdministrator, or CsAdministrator role. For details, see [Delegate setup permissions in Lync Server 2013](delegate-setup-permissions.md).
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. To begin defining a translation rule, follow the steps in [Configure a trunk with media bypass in Lync Server 2013](configure-a-trunk-with-media-bypass.md) through step 10 or [Configure a trunk without media bypass in Lync Server 2013](configure-a-trunk-without-media-bypass.md) through step 9. 
    
4. In the **Name** field on the **New Translation Rule** or **Edit Translation Rule** page, type a name that describes the number pattern being translated. 
    
5. (Optional) In **Description**, type a description of the translation rule, for example US International long-distance dialing.
    
6. Click **Edit** at the bottom of the **Build a Translation Rule** section. 
    
7. Enter the following in **Type a Regular Expression**:
    
  - In **Match this pattern**, specify the pattern that will be used to match the numbers to be translated.
    
  - In **Translation rule**, specify a pattern for the format of translated numbers.
    
    For example, if you enter ^\+(\d{9}\d+)$ in **Match this pattern** and 011$1 in **Translation rule**, the rule will translate +441235551010 to 011441235551010.
    
8. Click **OK** to save the translation rule. 
    
9. Click **OK** to save the trunk configuration. 
    
10. On the **Trunk Configuration** page, click **Commit**, and then click **Commit all**. 
    
    > [!NOTE]
    > Whenever you create or modify a translation rule, you must run the **Commit all** command to publish the configuration change. For details, see [Publish pending changes to the voice routing configuration in Lync Server 2013](publish-pending-changes-to-the-voice-routing-configuration.md) in the Operations documentation. 
  
## See also

#### 

[Create or modify a translation rule by using the Build a Translation Rule tool in Lync Server 2013](create-or-modify-a-translation-rule-by-using-the-build-a-translation-rule-tool.md)
  
[Configure a trunk with media bypass in Lync Server 2013](configure-a-trunk-with-media-bypass.md)
  
[Configure a trunk without media bypass in Lync Server 2013](configure-a-trunk-without-media-bypass.md)
  
[Publish pending changes to the voice routing configuration in Lync Server 2013](publish-pending-changes-to-the-voice-routing-configuration.md)
#### 

[Global media bypass options in Lync Server 2013](global-media-bypass-options.md)

