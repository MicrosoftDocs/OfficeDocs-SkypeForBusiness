---
title: 'Lync Server 2013: Deploy Shared Line Appearance'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Deploy Shared Line Appearance
ms:assetid: 6666dfef-9ecf-4834-af6a-2d5da227dfa3
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Mt712152(v=OCS.15)
ms:contentKeyID: 72522137
ms.date: 06/13/2016
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Deploy Shared Line Appearance in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2016-06-13_

Read this topic to learn how to deploy Shared Line Appearance (SLA) in Lync Server 2013, Cumulative Update April 2016. SLA is a feature for handling multiple calls on a specific number called a shared number.

For more information about this feature, see [Plan for Shared Line Appearance in Lync Server 2013](lync-server-2013-plan-for-shared-line-appearance.md).

Shared Line Appearance (SLA) is a new feature in Lync Server 2013, Cumulative Update April 2016. To enable this feature, you must have first deployed this cumulative update.

<div>

## Install Shared Line Appearance

1.  After Lync Server 2013, Cumulative Update April 2016 is deployed, the SLA application is not enabled by default. To enable the application, follow the steps below:
    
    1.  Register SLA as a server application by running the following command for each pool:
        
            New-CsServerApplication -Identity
                            'Service:Registrar:%FQDN%/SharedLineAppearance' -Uri
                            http://www.microsoft.com/LCS/SharedLineAppearance -Critical $false -Enabled
                            $true -Priority (Get-CsServerApplication -Identity
                            'Service:Registrar:%FQDN%/UserServices').Priority 
        
        where %FQDN% is the fully qualified domain name of the pool.
    
    2.  Run the following command to update the RBAC roles for the SLA cmdlets:
        
            Update-CsAdminRole 
    
    3.  Restart all the Front End Servers (RTCSRV service) in all the pools where SLA was installed and enabled:
        
        ``` 
         Stop-CsWindowsService RTCSRV Start-CsWindowsService RTCSRV
                        
        ```

</div>

<div>

## Create an SLA group and add users to it

1.  Create the SLA group by using the [Set-CsSlaConfiguration](https://docs.microsoft.com/powershell/module/skype/set-csslaconfiguration) cmdlet:
    
        Set-CsSlaConfiguration -Identity <IdentityOfGroup>
                  -MaxNumberOfCalls <Number> -BusyOption
                  <BusyOnBusy|Voicemail|Forward> [-Target
                  <TargetUserOrPhoneNumber>]
    
    The Set-CsSlaConfiguration cmdlet marks the Enterprise Voice account SLAGroup1 as an SLA entity, and the number of SLAGroup1 becomes the number for the SLA group. All calls to SLAGroup1 will ring the entire SLA group.
    
    The following example creates an SLA group for an existing Enterprise Voice user, SLAGroup1, and uses the number assigned for SLAGroup1 as the SLA mainline number.
    
    The command sets the maximum number of concurrent calls for the new SLA group to 3, and for calls in excess of that to hear a busy signal:
    
        Set-CsSlaConfiguration -Identity SLAGroup1 -MaxNumberOfCalls 3
                  -BusyOption BusyOnBusy
    
    You can use Set-CsSlaConfiguration to create a new SLA group or modify an existing one.
    
    <div>
    

    > [!NOTE]  
    > Note that what you specify for <CODE>-Identity</CODE> must be a valid existing Enterprise Voice-enabled user account.

    
    </div>

2.  Add delegates to the group by using the [Add-CsSlaDelegates](https://docs.microsoft.com/powershell/module/skype/add-cssladelegates) cmdlet:
    
        Add-CsSlaDelegates -Identity <IdentityOfGroup> -Delegate
                  <NameOfDelegate@domain>
    
    The following example adds a user to the SLA group. Each user added to the group must be a valid Enterprise Voice-enabled user:
    
        Add-CsSlaDelegates -Identity SLAGroup1 -Delegate
                  sip:SLA_Delegate1@contoso.com
    
    Repeat the cmdlet for each user you want to add to the group. Users can only belong to a single SLA group.

</div>

<div>

## Configure the SLA group Busy Option

1.  Configure the SLA group Busy Option by using the [Set-CsSlaConfiguration](https://docs.microsoft.com/powershell/module/skype/set-csslaconfiguration) cmdlet:
    
        Set-CsSlaConfiguration -Identity <IdentityOfGroup>
                  -BusyOption <Option> [-Target <TargetUserOrPhoneNumber>]
    
    The following example sets calls that exceed the maximum number of concurrent calls to be forwarded to the telephone number 202-555-1234. The target could be a user in your organization instead of a phone number; in that case, the syntax for the person to receive the forwarded calls is the same as when you specify a delegate: `sip:<NameofDelegate@domain>`. The other possible parameter for `BusyOption` is `Voicemail`:
    
        Set-CsSlaConfiguration -Identity SLAGroup1 -BusyOption Forward
                  -Target tel:+2025551234]

</div>

<div>

## Configure the SLA group Missed Call Option

1.  Configure the SLA group Missed Call Option by using the [Set-CsSlaConfiguration](https://docs.microsoft.com/powershell/module/skype/set-csslaconfiguration) cmdlet:
    
        Set-CsSlaConfiguration -Identity <IdentityOfGroup> 
                  -MissedCallOption <Option> -MissedCallForwardTarget
                  <TargetUserOrPhoneNumber> -BusyOption <Option> -MaxNumberofCalls <#> -Target [Target]
    
    The following example specifies that missed calls are to be forwarded to the user named `sla_forward_number`. The valid options for the `-MissedCallOption` parameter are `Forward`, `BusySignal`, or `Disconnect`. If you choose `Forward`, you must also include the `-MissedCallForwardTarget` parameter, with a user or phone number as the target:
    
        Set-CsSlaConfiguration -Identity SLAGroup1 -MissedCallOption
                  Forward -MissedCallForwardTarget sip:sla_forward_number@contoso.com 
            -BusyOption Forward -MaxNumberOfCalls 2 -Target sip:sla_forward_number@contoso.com 

</div>

<div>

## Remove a delegate from a group

1.  Remove a delegate from a group by using the [Remove-CsSlaDelegates](https://docs.microsoft.com/powershell/module/skype/remove-cssladelegates) cmdlet:
    
        Remove-CsSlaDelegates -Identity <IdentityOfGroup> -Delegate
                  <NameOfDelegate@domain>
    
    For example:
    
        Remove-CsSlaDelegates -Identity SLAGroup1 -Delegate
                  sip:SLA_Delegate3@contoso.com

</div>

<div>

## Delete an SLA group

1.  Delete an SLA group by using the [Remove-CsSlaConfiguration](https://docs.microsoft.com/powershell/module/skype/remove-csslaconfiguration?view=skype-ps) cmdlet:
    
    ``` 
    Remove-CsSlaConfiguration -Identity <IdentityOfGroup>
              
    ```
    
    For example:
    
        Remove-CsSlaConfiguration -Identity SLAGroup1 

</div>

</div>

<span> </span>

</div>

</div>

</div>

