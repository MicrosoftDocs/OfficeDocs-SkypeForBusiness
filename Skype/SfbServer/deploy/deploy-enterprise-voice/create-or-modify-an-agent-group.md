---
title: "Create or modify an agent group in Skype for Business"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- IT_Skype16
- Strat_SB_Admin
ms.custom: 
ms.assetid: f1461fff-51c1-4f4b-9311-8cba02c333fc
description: "Create or modify an agent group in Response Group, in Skype for Business Server Enterprise Voice."
---

# Create or modify an agent group in Skype for Business
 
Create or modify an agent group in Response Group, in Skype for Business Server Enterprise Voice.
  
When you create an agent group, you select the agents that are assigned to the group and specify additional group settings, such as the routing method and whether an agent can sign in to and out of the group. 
  
An agent who must sign in and out of the group, which is different from signing in or out of Skype for Business, is called a formal agent. Formal agents must be signed in to the group before they can receive calls routed to the group. This can be useful for agents who answer calls from the group on a part-time basis. Formal agents sign in and out of their groups by clicking a menu item in Skype for Business to open the Windows Internet Explorer Internet browser and display a webpage console.
  
An agent who does not sign in or out of the group is called an informal agent. Informal agents are automatically signed in to the group when they sign in to Skype for Business, and they cannot sign out of the group.
  
Only on-premises users can be agents. If an agent is moved from on-premises to online, Response Group calls will not be routed to that agent.
  
Use one of the following procedures to create or modify an agent group.
  
> [!IMPORTANT]
> When you assign users as response group agents, inform them that, if they have Privacy mode enabled, they need to search for "RGS Presence Watcher" contacts and add them to their Contacts list. Agents who have Privacy mode enabled, but who do not have "RGS Presence Watcher" in their Contacts list, cannot receive calls to the response group. Agents who do not have Privacy mode enabled are not affected. 
  
### To use Skype for Business Server Control Panel to create or modify an agent group

1. Log on as a member of the RTCUniversalServerAdmins group, or as a member of one of the predefined administrative roles that support Response Group.
    
    > [!NOTE]
    > If you are one of the delegated Response Group Managers for a managed workflow, you can create groups and use them in the workflows that you manage. 
  
2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel.  
    
3. In the left navigation bar, click **Response Groups**, and then click **Group**.
    
4. On the **Group** page, do one of the following:
    
   - To create a new agent group, click **New**. In the **Select a Service** search field, type all or part of the name of the **ApplicationServer** service where you want to add the group. In the resulting list of services, click the service that you want, and then click **OK**.
    
   - To modify an existing agent group, type all or part of the name of the agent group in the search field. In the resulting list, click the group that you want, click **Edit**, and then click **Show details**.
    
5. In **Name**, type an identifying name for the agent group.
    
6. In **Description**, type a description for the group.
    
7. In the **Participation policy**, select one of the following to set up the sign-in behavior for the group:
    
   - Select **Informal** to specify that agents in the group do not need to sign in and out of the group. Agents are automatically signed in to the group when they sign in to Skype for Business.
    
   - Select **Formal** to specify that agents in the group must sign in and out of the group. When you select this option, agents click a menu item in Skype for Business to open Internet Explorer and display a webpage console for signing in and out of the group.
    
8. In **Alert time (seconds)**, specify the number of seconds to ring an agent before offering the call to the next available agent (the default is 20 seconds).
    
    > [!IMPORTANT]
    > The agent alert time setting cannot exceed 180 seconds. If the agent alert time exceeds 180 seconds, the client application rejects the call because the SIP transaction timer reaches its maximum wait time. 
  
9. In **Routing method**, select the method for routing calls to agents in the group as follows:
    
   - To offer a new call first to the agent who has been idle the longest (has had a presence of **Available** or **Inactive** in Skype for Business the longest), click **Longest idle**. 
    
   - To offer a new call to all available agents at the same time, click **Parallel**. The call is sent to the first agent who accepts it.
    
   - To offer a new call to each agent in turn, click **Round robin**. 
    
   - To always offer a new call to the agents in the order in which they are listed in the **Agent** list, click **Serial**. 
    
   - To offer a new call to all agents who are signed into Skype for Business and the Response Group application at the same time, regardless of their current presence, click **Attendant**. Users who are configured as agents can see all the calls that are waiting and answer waiting calls in any order. The call is sent to the first agent who accepts it, after which the other agents no longer see the call.
    
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
    
    > [!IMPORTANT]
    > If you use an email distribution list, hidden memberships or hidden lists might become visible to the Response Group administrator or users. 
  
    Hidden memberships or hidden lists can become visible as follows:
    
     - If a distribution list was configured so that the membership is hidden and the Response Group administrator assigns the distribution list to the agent list, users can call the group to find out who the members are. 
    
     - If a distribution list was configured so that it is hidden in the Exchange Global Address List, the Response Group administrator might be able to see the distribution list and assign it to the agent list if the Response Group process has the appropriate user rights and permissions, even if the administrator does not have the appropriate user rights and permissions.
    
11. Click **Commit**.
    
### To use Skype for Business Server Management Shell to create or modify an agent group

1. Log on as a member of the RTCUniversalServerAdmins group, or as a member of one of the predefined administrative roles that support Response Group.
    
2. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business 2015**, and then click **Skype for Business Server Management Shell**.
    
3. Use **New-CsRgsAgentGroup** to create a new agent group. Use **Set-CsRgsAgentGroup** to modify an existing agent group. At the command line, run:
    
   ```
   New-CsRgsAgentGroup -Name "<agent group name>" -Parent $serviceId [-Description "<agent group description>"] -[AgentAlertTime <# seconds until call is routed to next agent>] [-ParticipationPolicy <Formal | Informal>] [-RoutingMethod <method for routing calls>] [-AgentsByUri("<first agent's SIP address>","<second agent's SIP address>")];
   ```

    For example:
    
   ```
   New-CsRgsAgentGroup -Name "Help Desk" -Parent "service:ApplicationServer:atl-cs-001.contoso.com"  -Description "Contoso Help Desk" -AgentAlertTime 20 -ParticipationPolicy Formal -RoutingMethod RoundRobin -AgentsByUri("sip:mindy@contoso.com","sip:bob@contoso.com")
   ```

    > [!IMPORTANT]
    > The agent alert time setting cannot exceed 180 seconds. If the agent alert time is greater than 180 seconds, the client application rejects the call because the SIP transaction timer reaches its maximum wait time. 
  
4. Confirm that the agent group is created. Run:
    
   ```
   Get-CsRgsAgentGroup -Name "Help Desk"
   ```

## See also

[Get-CsService](https://docs.microsoft.com/powershell/module/skype/get-csservice?view=skype-ps)
  
[New-CsRgsAgentGroup](https://docs.microsoft.com/powershell/module/skype/new-csrgsagentgroup?view=skype-ps)
  
[Set-CsRgsAgentGroup](https://docs.microsoft.com/powershell/module/skype/set-csrgsagentgroup?view=skype-ps)
  
[Get-CsRgsAgentGroup](https://docs.microsoft.com/powershell/module/skype/get-csrgsagentgroup?view=skype-ps)
