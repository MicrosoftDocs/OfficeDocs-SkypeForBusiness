---
title: "Migrate response groups"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "After your users are moved to Skype for Business Server 2019 pools, you can migrate your response groups. Migrating response groups includes copying agent groups, queues, workflows, audio files, and moving Response Group contact objects from the legacy deployment to the Skype for Business Server 2019 pool. After you migrate your legacy response groups, calls to the response groups are handled by the Response Group application in the Skype for Business Server 2019 pool. Calls to response groups are no longer handled by the legacy pool."
---

# Migrate response groups

After your users are moved to Skype for Business Server 2019 pools, you can migrate your response groups. Migrating response groups includes copying agent groups, queues, workflows, audio files, and moving Response Group contact objects from the legacy deployment to the Skype for Business Server 2019 pool. After you migrate your legacy response groups, calls to the response groups are handled by the Response Group application in the Skype for Business Server 2019 pool. Calls to response groups are no longer handled by the legacy pool.
  
> [!NOTE]
> Although you can migrate response groups before you move all users to the Skype for Business Server 2019 pool, we recommend that you move all users first. In particular, users who are response group agents will not have full functionality of new features until they are moved to the Skype for Business Server 2019 pool. 
  
Before you migrate response groups, you must have deployed a Skype for Business Server 2019 pool that includes the Response Group application. The Response Group application is installed and activated by default when you deploy Enterprise Voice. You can ensure that the Response Group application is installed by running the **Get-CsService -ApplicationServer** cmdlet. 
  
> [!NOTE]
> You can create new Skype for Business Server 2019 response groups in the Skype for Business Server 2019 pool before you migrate your legacy response groups. 
  
To migrate response groups from a legacy pool to the Skype for Business Server 2019, you run the **Move-CsRgsConfiguration** cmdlet. 
  
> [!IMPORTANT]
> The Response Group migration cmdlet moves the Response Group configuration for the entire pool. You cannot select specific groups, queues, or workflows to migrate. 
  
After you migrate the response groups, you need to use Skype for Business Server Control Panel or Skype for Business Server Management Shell cmdlets to verify that all agent groups, queues, and workflows moved successfully. 
  
When you migrate response groups, the legacy response groups are not removed. When you manage response groups after migration by using either Skype for Business Server Control Panel or Skype for Business Server Management Shell, you can see both the legacy response groups and the Skype for Business Server 2019 response groups. You should apply updates only to the Skype for Business Server 2019 response groups. The legacy response groups are retained only for rollback purposes. 
  
> [!CAUTION]
> After the migration has been completed and the new response groups have been created, the Skype for Business Server Control Panel and the Skype for Business Server Management Shell will display the legacy and Skype for Business Server 2019 versions of each response group. Do not use Skype for Business Server Control Panel or Skype for Business Server Management Shell to remove the legacy response groups. If you do remove one, the corresponding response group that was created during migration will stop working. The legacy response groups will be removed when you decommission the legacy pool. 
  
> [!IMPORTANT]
> We recommend that you do not remove any data from your previous deployment until you decommission the pool. In addition, we strongly recommend that you export response groups immediately after you migrate. If a legacy response group should get removed, you can then restore your response groups from the backup to get Skype for Business Server 2019 response groups running again. 
  
Skype for Business Server 2019 introduces a new Response Group feature called **Workflow Type**. **Workflow Type** can be **Managed** or **Unmanaged**. All response groups are migrated with **Workflow Type** set to **Unmanaged** and with an empty Manager list. 
  
When you run the **Move-CsRgsConfiguration** cmdlet, the agent groups, queues, workflows, and audio files remain in the legacy pool for rollback purposes. If you do need to roll back to the legacy pool, however, you need to run the **Move-CsApplicationEndpoint** cmdlet to move contact objects back to the legacy pool. 
  
The following procedure for migrating Response Group configurations assumes that you have a one-to-one relationship between your legacy pools and the Skype for Business Server 2019 pools. If you plan to consolidate or split up pools during your migration and deployment, you need to plan which legacy pool maps to which Skype for Business Server 2019 pool.
  
## To migrate Response Group configurations

1. Log on to the computer with an account that is a member of the RTCUniversalServerAdmins group or has equivalent administrator rights and permissions.
    
2. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Skype for Business Server 2019**, and then click **Skype for Business Server Management Shell**.
    
3. Run:
    
   ```
   Move-CsRgsConfiguration -Source <source pool FQDN> -Destination <destination pool FQDN>
   ```

    For example:
    
   ```
   Move-CsRgsConfiguration -Source skype-old.contoso.net -Destination skype-new.contoso.net
   ```

4. After you migrate response groups and agents to the Skype for Business Server 2019 pool, the URL that agents use to sign in and sign out is a Skype for Business Server 2019 URL and is available from the **Tools** menu. Remind agents to update any references, such as bookmarks, to the new URL. 
    
## To verify Response Group migration by using Skype for Business Server Control Panel

1. Log on to the computer with an account that is a member of RTCUniversalReadOnlyAdmins group or is minimally a member of the CsViewOnlyAdministrator role.
    
2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. For details about the different methods you can use to start Skype for Business Server Control Panel, see [Open Skype for Business Server 2019 administrative tools](https://technet.microsoft.com/en-us/library/gg195741(v=ocs.15).aspx). 
    <!-- The above link points to un-rebranded 2013 content we will need to discuss rebrand or bring forward -->
3. In the left navigation pane, click **Response Groups**.
    
4. On the **Workflow** tab, verify that all the workflows in your legacy environment are included in the list. 
    
5. Click the **Queue** tab, and verify that all the queues in your legacy environment are included in the list. 
    
6. Click the **Group** tab, and verify that all the agent groups in your legacy environment are included in the list. 
    
## To verify Response Group migration by using Skype for Business Server Management Shell

1. Log on to the computer with an account that is a member of RTCUniversalReadOnlyAdmins group or is minimally a member of the CsViewOnlyAdministrator role.
    
2. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Skype for Business Server 2019**, and then click **Skype for Business Server Management Shell**.
    
    For details about the following cmdlets, run:
    
   ```
   Get-Help <cmdlet name> -Detailed
   ```

3. Run:
    
   ```
   Get-CsRgsAgentGroup
   ```

4. Verify that all the agent groups in your legacy environment are included in the list.
    
5. Run:
    
   ```
   Get-CsRgsQueue
   ```

6. Verify that all the queues in your legacy environment are included in the list.
    
7. Run:
    
   ```
   Get-CsRgsWorkflow
   ```

8. Verify that all the workflows in your legacy environment are included in the list.
    

