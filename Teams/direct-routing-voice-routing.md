---
title: "Configure voice routing for Direct Routing"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
audience: ITPro
ms.topic: article
ms.service: msteams
localization_priority: Normal
search.appverid: MET150
ms.collection: 
  - M365-voice
appliesto: 
  - Microsoft Teams
f1.keywords:
- NOCSH
description: "Learn how to configure voice routing with Microsoft Phone System Direct Routing."
---

# Configure voice routing for Direct Routing

This article describes how to configure voice routing for Phone System Direct Routing.  This is step 3 of the following steps for configuring Direct Routing:

- Step 1. [Connect the SBC with Microsoft Phone System and validate the connection](direct-routing-connect-the-sbc.md) 
- Step 2. [Enable users for Direct Routing, voice, and voicemail](direct-routing-enable-users.md)    
- **Step 3. Configure voice routing** (This article)
- Step 4. [Translate numbers to an alternate format](direct-routing-translate-numbers.md) 

For information on all the steps required for setting up Direct Routing, see [Configure Direct Routing](direct-routing-configure.md).

## Voice routing overview

Microsoft Phone System has a routing mechanism that allows a call to be sent to a specific Session Border Controller (SBC) based on: 

- The called number pattern 
- The called number pattern plus the specific user who makes the call
 
SBCs can be designated as active and backup. When the SBC that is configured as active is not available for a specific call route, then the call will be routed to a backup SBC.
 
Voice routing is made up of the following elements: 

- **Voice routing policy** – A container for PSTN Usages, which can be assigned to a user or to multiple users. 

- **PSTN usages** – A container for voice routes and PSTN usages, which can be shared in different voice routing policies. 

- **Voice Routes** – A number pattern and set of online PSTN gateways to use for calls where the calling number matches the pattern.

- **Online PSTN gateway** - A pointer to an SBC that also stores the configuration that is applied when a call is placed through the SBC, such as forward P-Asserted-Identity (PAI) or Preferred Codecs; can be added to voice routes.

## Example 1: Voice routing with one PSTN Usage

The following diagram shows two examples of voice routing policies in a call flow.

**Call Flow 1 (on the left):** If a user makes a call to +1 425 XXX XX XX or +1 206 XXX XX XX, the call is routed to SBC sbc1.contoso.biz or sbc2.contoso.biz. If neither sbc1.contoso.biz nor sbc2.contoso.biz are available, the call is dropped. 

**Call Flow 2 (on the right):** If a user makes a call to +1 425 XXX XX XX or +1 206 XXX XX XX, the call is first routed to SBC sbc1.contoso.biz or sbc2.contoso.biz. If neither SBC is available, the route with lower priority will be tried (sbc3.contoso.biz and sbc4.contoso.biz). If none of the SBCs are available, the call is dropped. 

![Shows voice routing policy examples](media/ConfigDirectRouting-VoiceRoutingPolicyExamples.png)

In both examples, while the voice route is assigned priorities, the SBCs in the routes are tried in random order.

  > [!NOTE]
  > Unless the user also has a Microsoft Calling Plan license, calls to any number except numbers matching the patterns +1 425 XXX XX XX or +1 206 XXX XX XX in the example configuration are dropped. If the user has a Calling Plan license, the call is automatically routed according to the policies of the Microsoft Calling Plan. The Microsoft Calling Plan applies automatically as the last route to all users with the Microsoft Calling Plan license and does not require additional call routing configuration.

In the example shown in the following diagram, a voice route is added to send calls to all other US and Canadian numbers (calls that go to called number pattern +1 XXX XXX XX XX).

![Shows voice routing policy with a third route](media/ConfigDirectRouting-VoiceRoutingPolicywith3rdroute.png)

For all other calls:

- If a user has both licenses (Microsoft Phone System and Microsoft Calling Plan), the automatic route is used. 
- If nothing matches the number patterns in the administrator-created online voice routes, then the call is routed through Microsoft Calling Plan.
- If the user only has Microsoft Phone System, the call is dropped because no matching rules are available.

  > [!NOTE]
  > The Priority value for route "Other +1" doesn’t matter in this case because there is only one route that matches the pattern +1 XXX XXX XX XX. If a user makes a call to +1 324 567 89 89 and both sbc5.contoso.biz and sbc6.contoso.biz are unavailable, the call is dropped.

The following table summarizes the configuration using three voice routes. In this example, all three routes are part of the same PSTN Usage "US and Canada".  All routes are associated with the PSTN Usage "US and Canada" and the PSTN Usage is associated with the Voice Routing Policy "US Only." 

|**PSTN usage**|**Voice route**|**Number pattern**|**Priority**|**SBC**|**Description**|
|:-----|:-----|:-----|:-----|:-----|:-----|
|US only|"Redmond 1"|^\\+1(425\|206)(\d{7})$|1|sbc1.contoso.biz<br/>sbc2.contoso.biz|Active route for called numbers +1 425 XXX XX XX or +1 206 XXX XX XX|
|US only|"Redmond 2"|^\\+1(425\|206)(\d{7})$|2|sbc3.contoso.biz<br/>sbc4.contoso.biz|Backup route for called numbers +1 425 XXX XX XX or +1 206 XXX XX XX|
|US only|"Other +1"|^\\+1(\d{10})$|3|sbc5.contoso.biz<br/>sbc6.contoso.biz|Route for called numbers +1 XXX XXX XX XX (except +1 425 XXX XX XX or +1 206 XXX XX XX)|
|||||||


### Example 1: Configuration steps

The following example shows how to:

- Create a single PSTN Usage 
- Configure three voice routes
- Create a voice routing policy
- Assign the policy to user Spencer Low

**Step 1:** Create the PSTN Usage "US and Canada"

In a Skype for Business Remote PowerShell session, type:

```PowerShell
Set-CsOnlinePstnUsage -Identity Global -Usage @{Add="US and Canada"}
```

Validate that the usage was created by entering: 
```PowerShell
Get-CSOnlinePSTNUsage
``` 
Which returns a list of names that may be truncated:
```console
Identity	: Global
Usage    	: {testusage, US and Canada, International, karlUsage. . .}
```
The example below shows the result of  running the PowerShell command `(Get-CSOnlinePSTNUsage).usage` to display full names (not truncated):

<pre>
 testusage
 US and Canada
 International
 karlUsage
 New test env
 Tallinn Lab Sonus
 karlUsage2
 Unrestricted
 Two trunks
</pre>

**Step 2:** In a PowerShell session in Skype for Business Online, create three routes: Redmond 1, Redmond 2, and Other +1, as shown in the previous table

To create the "Redmond 1" route, enter:

```PowerShell
New-CsOnlineVoiceRoute -Identity "Redmond 1" -NumberPattern "^\+1(425|206)
(\d{7})$" -OnlinePstnGatewayList sbc1.contoso.biz, sbc2.contoso.biz -Priority 1 -OnlinePstnUsages "US and Canada"
```

Which returns:
<pre>
Identity                : Redmond 1
Priority                : 1
Description             :
NumberPattern           : ^\+1(425|206) (\d{7})$
OnlinePstnUsages        : {US and Canada}
OnlinePstnGatewayList   : {sbc1.contoso.biz, sbc2.contoso.biz}
Name                    : Redmond 1
</pre>
To create the Redmond 2 route, enter:

```PowerShell
New-CsOnlineVoiceRoute -Identity "Redmond 2" -NumberPattern "^\+1(425|206)
(\d{7})$" -OnlinePstnGatewayList sbc3.contoso.biz, sbc4.contoso.biz -Priority 2 -OnlinePstnUsages "US and Canada"
```

To create the Other +1 route, enter:

```PowerShell
New-CsOnlineVoiceRoute -Identity "Other +1" -NumberPattern "^\+1(\d{10})$"
-OnlinePstnGatewayList sbc5.contoso.biz, sbc6.contoso.biz -OnlinePstnUsages "US and Canada"
```

  > [!CAUTION]
  > Make sure that your regular expression in the NumberPattern attribute is a valid expression. You can test it using this website: [https://www.regexpal.com](https://www.regexpal.com)

In some cases, there is a need to route all calls to the same SBC; use -NumberPattern ".*"

Route all calls to same SBC.

```PowerShell
Set-CsOnlineVoiceRoute -id "Redmond 1" -NumberPattern ".*" -OnlinePstnGatewayList sbc1.contoso.biz
```

Validate that you’ve correctly configured the route by running the `Get-CSOnlineVoiceRoute` PowerShell command using options as shown:

```PowerShell
Get-CsOnlineVoiceRoute | Where-Object {($_.priority -eq 1) -or ($_.priority -eq 2) or ($_.priority -eq 4) -Identity "Redmond 1" -NumberPattern "^\+1(425|206) (\d{7})$" -OnlinePstnGatewayList sbc1.contoso.biz, sbc2.contoso.biz -Priority 1 -OnlinePstnUsages "US and Canada"
```
Which should return:
<pre>
Identity	    	: Redmond 1 
Priority       		: 1
Description	 	: 
NumberPattern 		: ^\+1(425|206) (\d{7})$
OnlinePstnUsages 	: {US and Canada}	 
OnlinePstnGatewayList	: {sbc1.contoso.biz, sbc2.contoso.biz}
Name		 	: Redmond 1
Identity		: Redmond 2 
Priority       		: 2
Description	 	: 
NumberPattern 		: ^\+1(425|206) (\d{7})$
OnlinePstnUsages 	: {US and Canada}	 
OnlinePstnGatewayList	: {sbc3.contoso.biz, sbc4.contoso.biz}
Name		 	: Redmond 2
    
Identity		: Other +1 
Priority       		: 4
Description	 	: 
NumberPattern 		: ^\+1(\d{10})$
OnlinePstnUsages 	: {US and Canada}	 
OnlinePstnGatewayList	: {sbc5.contoso.biz, sbc6.contoso.biz}
Name		 	: Other +1
</pre>

In the example, the route "Other +1" was automatically assigned priority 4. 

**Step 3:** Create a voice routing policy "US Only" and add to the policy the PSTN Usage "US and Canada."

In a PowerShell session in Skype for Business Online, type:

```PowerShell
New-CsOnlineVoiceRoutingPolicy "US Only" -OnlinePstnUsages "US and Canada"
```

The result is shown in this example:

<pre>
Identity            : Tag:US only
OnlinePstnUsages    : {US and Canada}
Description         :
RouteType           : BYOT
</pre>

**Step 4:** By using PowerShell, grant the voice routing policy to the user Spencer Low:

In a PowerShell session in Skype for Business Online, type:

```PowerShell
Grant-CsOnlineVoiceRoutingPolicy -Identity "Spencer Low" -PolicyName "US Only"
```

Validate the policy assignment by entering this command:

```PowerShell
Get-CsOnlineUser "Spencer Low" | select OnlineVoiceRoutingPolicy
```

The command returns the following:
<pre>
OnlineVoiceRoutingPolicy
---------------------
US Only
</pre>

## Example 2: Voice routing with multiple PSTN Usages

The voice routing policy created in Example 1 only allows calls to phone numbers in the US and Canada--unless the Microsoft Calling Plan license is also assigned to the user.

In the example that follows, you can create the voice routing policy "No Restrictions." The policy reuses the PSTN Usage "US and Canada" created in Example 1, as well as the new PSTN Usage "International."  This policy routes all other calls to the SBCs sbc2.contoso.biz and sbc5.contoso.biz. 

The examples that are shown assign the US Only policy to user Spencer Low, and the No Restrictions policy to the user John Woods so that routing occurs as follows:

- Spencer Low – US Only policy.  Calls are allowed only to US and Canadian numbers. When calling to the Redmond number range, the specific set of SBCs must be used. Non-US numbers will not be routed unless the Calling Plan license is assigned to the user.

- John Woods – International policy.  Calls are allowed to any number. When calling to the Redmond number range, the specific set of SBCs must be used. Non-US numbers will be routed using sbc2.contoso.biz and sbc5.contoso.biz.

![Shows voice routing policy assigned to user Spencer Low](media/ConfigDirectRouting-VoiceRoutingPolicyAssignedtoSpencerLow.png)

For all other calls, if a user has both licenses (Microsoft Phone System and Microsoft Calling Plan), automatic route is used. If nothing matches the number patterns in the administrator-created online voice routes, then the call is routed using Microsoft Calling Plan.  If the user has only Microsoft Phone System, the call is dropped because no matching rules are available.

![Shows voice routing policy assigned to user John Woods](media/ConfigDirectRouting-VoiceRoutingPolicyAssignedtoJohnWoods.png)

The following table summarizes routing policy "No Restrictions" usage designations and voice routes. 

|**PSTN usage**|**Voice route**|**Number pattern**|**Priority**|**SBC**|**Description**|
|:-----|:-----|:-----|:-----|:-----|:-----|
|US Only|"Redmond 1"|^\\+1(425\|206)(\d{7})$|1|sbc1.contoso.biz<br/>sbc2.contoso.biz|Active route for callee numbers +1 425 XXX XX XX or +1 206 XXX XX XX|
|US Only|"Redmond 2"|^\\+1(425\|206)(\d{7})$|2|sbc3.contoso.biz<br/>sbc4.contoso.biz|Backup route for callee numbers +1 425 XXX XX XX or +1 206 XXX XX XX|
|US Only|"Other +1"|^\\+1(\d{10})$|3|sbc5.contoso.biz<br/>sbc6>.contoso.biz|Route for callee numbers +1 XXX XXX XX XX (except +1 425 XXX XX XX or +1 206 XXX XX XX)|
|International|International|\d+|4|sbc2.contoso.biz<br/>sbc5.contoso.biz|Route for any number pattern |


  > [!NOTE]
  > - The order of PSTN Usages in Voice Routing Policies is critical. The usages are applied in order, and if a match is found in the first usage, then other usages are never evaluated. The PSTN Usage "International" must be placed after the PSTN Usage "US Only." To change the order of the PSTN Usages, run the `Set-CSOnlineVoiceRoutingPolicy` command. <br/>For example, to change the order from "US and Canada" first and "International" second to the reverse order run:<br/> `Set-CsOnlineVoiceRoutingPolicy -id tag:"no Restrictions" -OnlinePstnUsages @{Replace="International", "US and Canada"}`
 > - The priority for "Other +1" and "International" Voice routes are assigned automatically. They don’t matter as long as they have lower priorities than "Redmond 1" and "Redmond 2."


### Example 2: Configuration steps

The following example shows how to:

- Create a new PSTN Usage called International
- Create a new voice route called International
- Create a voice routing policy called No Restrictions
- Assign the policy to user John Woods


**Step 1**: Create the PSTN Usage "International." 

In a remote PowerShell session in Skype for Business Online, enter:

```PowerShell
Set-CsOnlinePstnUsage -Identity Global -Usage @{Add="International"}
```

**Step 2**:  Create the new voice route "International."

```PowerShell
New-CsOnlineVoiceRoute -Identity "International" -NumberPattern ".*" -OnlinePstnGatewayList sbc2.contoso.biz, sbc5.contoso.biz -OnlinePstnUsages "International"
```
Which returns:

<pre>
Identity                  : International
Priority                  : 5
Description               :
NumberPattern             : .*
OnlinePstnUsages          : {International}
OnlinePstnGatewayList     : {sbc2.contoso.biz, sbc5.contoso.biz}
Name                      : International
</pre>

**Step 3**: Create a Voice Routing Policy "No Restrictions". 

The PSTN Usage "Redmond 1" and "Redmond" are reused in this voice routing policy to preserve special handling for calls to number "+1 425 XXX XX XX" and "+1 206 XXX XX XX" as local or on-premises calls.

  ```PowerShell
  New-CsOnlineVoiceRoutingPolicy "No Restrictions" -OnlinePstnUsages "US and Canada", "International"
  ```

Take note of the order of PSTN Usages:

  a. If a call made to number "+1 425 XXX XX XX" with the usages configured as in the following example, the call follows the route set in "US and Canada" usage and the special routing logic is applied. That is, the call is routed using sbc1.contoso.biz and sbc2.contoso.biz first, and then sbc3.contoso.biz and sbc4.contoso.biz as the backup routes.

  b. If "International" PSTN usage is before "US and Canada," calls to +1 425 XXX XX XX are routed to sbc2.contoso.biz and sbc5.contoso.biz as part of the routing logic. Enter the command:

  ```PowerShell
  New-CsOnlineVoiceRoutingPolicy "No Restrictions" -OnlinePstnUsages "US and Canada", "International"
  ```

Which returns:

	<pre>
	Identity		      : International 
	OnlinePstnUsages : {US and Canada, International}	 
	Description		 :  
	RouteType	 	      : BYOT
	</pre>

**Step 4**: Assign the voice routing policy to the user "John Woods" using the following command.

```PowerShell
Grant-CsOnlineVoiceRoutingPolicy -Identity "John Woods" -PolicyName "No Restrictions”
```

Then verify the assignment using the command: 

```PowerShell
Get-CsOnlineUser "John Woods" | Select OnlineVoiceRoutingPolicy
```

Which returns:

<pre>
OnlineVoiceRoutingPolicy
------------------------
No Restrictions
</pre>

The result is that the voice policy applied to John Woods’ calls is unrestricted, and will follow the logic of call routing available for US, Canada, and International calling.



## See also

[Plan Direct Routing](direct-routing-plan.md)

[Configure Direct Routing](direct-routing-configure.md)
