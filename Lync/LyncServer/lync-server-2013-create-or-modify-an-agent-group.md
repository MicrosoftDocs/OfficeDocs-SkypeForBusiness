---
title: 'Lync Server 2013: Create or modify an agent group'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Create or modify an agent group
ms:assetid: f1461fff-51c1-4f4b-9311-8cba02c333fc
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205370(v=OCS.15)
ms:contentKeyID: 48185784
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Create or modify an agent group in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-02-07_

Use one of the following procedures to create or modify an agent group.

<div>


> [!NOTE]  
> An Administrator—for example, CsVoiceAdministrator—must enable users for Enterprise Voice and Lync Server before the users can be assigned to agent groups. If you are one of the delegated Response Group Managers for a managed workflow, you can create agent groups and use the agent groups in the workflows that you manage.



</div>

<div>


> [!IMPORTANT]  
> When you assign users as response group agents, inform them that, if they have Privacy mode enabled, they need to search for "RGS Presence Watcher" contacts and add them to their Contacts list. Agents who have Privacy mode enabled, but who do not have "RGS Presence Watcher" in their Contacts list, cannot receive calls to the response group. Agents who do not have Privacy mode enabled are not affected.



</div>

<div>

## To use Lync Server Control Panel to create or modify an agent group

1.  Log on as a member of the RTCUniversalServerAdmins group, or as a member of one of the predefined administrative roles that support Response Group.
    
    <div>
    

    > [!NOTE]  
    > If you are one of the delegated Response Group Managers for a managed workflow, you can create groups and use them in the workflows that you manage.

    
    </div>

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Response Groups**, and then click **Group**.

4.  On the **Group** page, do one of the following:
    
      - To create a new agent group, click **New**. In the **Select a Service** search field, type all or part of the name of the **ApplicationServer** service where you want to add the group. In the resulting list of services, click the service that you want, and then click **OK**.
    
      - To modify an existing agent group, type all or part of the name of the agent group in the search field. In the resulting list, click the group that you want, click **Edit**, and then click **Show details**.

5.  In **Name**, type an identifying name for the agent group.

6.  In **Description**, type a description for the group.

7.  In the **Participation policy**, select one of the following to set up the sign-in behavior for the group:
    
      - Select **Informal** to specify that agents in the group do not need to sign in and out of the group. Agents are automatically signed in to the group when they sign in to Lync Server 2013.
    
      - Select **Formal** to specify that agents in the group must sign in and out of the group. When you select this option, agents click a menu item in Lync to open Internet Explorer and display a webpage console for signing in and out of the group.

8.  In **Alert time (seconds)**, specify the number of seconds to ring an agent before offering the call to the next available agent (the default is 20 seconds).
    
    <div>
    

    > [!IMPORTANT]  
    > The agent alert time setting cannot exceed 180 seconds. If the agent alert time exceeds 180 seconds, the client application rejects the call because the SIP transaction timer reaches its maximum wait time.

    
    </div>

9.  In **Routing method**, select the method for routing calls to agents in the group as follows:
    
      - To offer a new call first to the agent who has been idle the longest (has had a presence of **Available** or **Inactive** in Lync Server the longest), click **Longest idle**.
    
      - To offer a new call to all available agents at the same time, click **Parallel**. The call is sent to the first agent who accepts it.
    
      - To offer a new call to each agent in turn, click **Round robin**.
    
      - To always offer a new call to the agents in the order in which they are listed in the **Agent** list, click **Serial**.
    
      - To offer a new call to all agents who are signed into Lync Server 2013 and the Response Group application at the same time, regardless of their current presence, click **Attendant**. Lync 2010 Attendant users who are configured as agents can see all the calls that are waiting and answer waiting calls in any order. The call is sent to the first agent who accepts it, after which the other Lync 2010 Attendant users no longer see the call.

10. In **Agents**, specify how you want to create your agents list:
    
      - To use a custom list of agents, click **Define a custom group of agents**, and do one of the following:
        
          - To add a user to the agent group, click **Select**, and then in the **Select Agents** search field, type all or part of the name of the user that you want to add to this group, and then click **Find**. In the resulting list of agents, click the user, and then click **OK**.
        
          - To remove a user from the agent group, in the list of agents, click the user you want to remove, and then click **Remove**.
        
          - To change the order in which agents are offered calls in groups that use either round robin routing or serial routing, in the list of agents, click a user, and then click the up arrow or down arrow.
    
      - To use a Microsoft Exchange Server distribution list as your agent group, click **Use an existing email distribution list**, and then in **Distribution list address**, type the email address of the distribution list (for example, NetworkSupport@contoso.com).
        
        If you use an email distribution list, you are subject to the following constraints:
        
          - You cannot select multiple distribution lists for the agent group. Each group supports only a single distribution list.
        
          - If the distribution list contains one or more distribution lists, members of the nested distribution lists are not added to the agent list.
        
          - If serial or round robin routing is selected, the server offers an incoming call to the appropriate agent according to the routing method and according to the order in which agents are listed in the distribution list.
        
          - If the distribution list contains users for which Lync Server 2010 is enabled but Enterprise Voice is not enabled, they will be added to the agent group as dysfunctional agents. Make sure that all members of the distribution list have Enterprise Voice enabled for their user accounts.
        
        <div>
        

        > [!IMPORTANT]  
        > If you use an email distribution list, hidden memberships or hidden lists might become visible to the Response Group administrator or users.

        
        </div>
        
        Hidden memberships or hidden lists can become visible as follows:
        
          - If a distribution list was configured so that the membership is hidden and the Response Group administrator assigns the distribution list to the agent list, users can call the group to find out who the members are.
        
          - If a distribution list was configured so that it is hidden in the Exchange Global Address List, the Response Group administrator might be able to see the distribution list and assign it to the agent list if the Response Group process has the appropriate user rights and permissions, even if the administrator does not have the appropriate user rights and permissions.

11. Click **Commit**.

</div>

<div>

## To use Windows PowerShell to create or modify an agent group

1.  Log on as a member of the RTCUniversalServerAdmins group, or as a member of one of the predefined administrative roles that support Response Group.

2.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

3.  Use **New-CsRgsAgentGroup** to create a new agent group. Use **Set-CsRgsAgentGroup** to modify an existing agent group. At the command line, run:
    
        New-CsRgsAgentGroup -Name "<agent group name>" -Parent $serviceId [-Description "<agent group description>"] -[AgentAlertTime <# seconds until call is routed to next agent>] [-ParticipationPolicy <Formal | Informal>] [-RoutingMethod <method for routing calls>] [-AgentsByUri("<first agent's SIP address>","<second agent's SIP address>")];
    
    For example:
    
        New-CsRgsAgentGroup -Name "Help Desk" -Parent "service:ApplicationServer:atl-cs-001.contoso.com"  -Description "Contoso Help Desk" -AgentAlertTime 20 -ParticipationPolicy Formal -RoutingMethod RoundRobin -AgentsByUri("sip:mindy@contoso.com","sip:bob@contoso.com")
    
    <div>
    

    > [!IMPORTANT]  
    > The agent alert time setting cannot exceed 180 seconds. If the agent alert time is greater than 180 seconds, the client application rejects the call because the SIP transaction timer reaches its maximum wait time.

    
    </div>

4.  Confirm that the agent group is created. Run:
    
        Get-CsRgsAgentGroup -Name "Help Desk"

</div>

<div>

## See Also


[Delete an agent group in Lync Server 2013](lync-server-2013-delete-an-agent-group.md)  


[Managing Response Group agent groups in Lync Server 2013](lync-server-2013-managing-response-group-agent-groups.md)  
[Get-CsService](https://docs.microsoft.com/powershell/module/skype/Get-CsService)  
[New-CsRgsAgentGroup](https://docs.microsoft.com/powershell/module/skype/New-CsRgsAgentGroup)  
[Set-CsRgsAgentGroup](https://docs.microsoft.com/powershell/module/skype/Set-CsRgsAgentGroup)  
[Get-CsRgsAgentGroup](https://docs.microsoft.com/powershell/module/skype/Get-CsRgsAgentGroup)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

