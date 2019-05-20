---
title: "Migrate dial-in access numbers"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "Migrating dial-in access numbers to Skype for Business Server 2019 requires running the Move-CsApplicationEndpoint cmdlet to migrate the contact objects. During the legacy install and Skype for Business Server 2019 coexistence period, dial-in access numbers that you created in Skype for Business Server 2019 behave similarly to the dial-in access numbers that you create in the legacy install, as described in this section."
---

# Migrate dial-in access numbers

Migrating dial-in access numbers to Skype for Business Server 2019 requires running the **Move-CsApplicationEndpoint** cmdlet to migrate the contact objects. During the legacy install and Skype for Business Server 2019 coexistence period, dial-in access numbers that you created in Skype for Business Server 2019 behave similarly to the dial-in access numbers that you create in the legacy install, as described in this section. 

Dial-in access numbers that you created in the legacy install but moved to Skype for Business Server 2019, or that you created in Skype for Business Server 2019 before, during, or after migration, have the following characteristics:

- Do not appear on Office Communications Server 2007 R2 meeting invitations and the dial-in access number page.

- Appear on the legacy install meeting invitations and the dial-in access number page.

- Appear on Skype for Business Server 2019 meeting invitations and the dial-in access number page.

- Cannot be viewed or modified in the Office Communications Server 2007 R2 administrative tool.

- Can be viewed and modified in the legacy install Control Panel and in the legacy install Management Shell.

- Can be viewed and modified in the Skype for Business Server 2019 Control Panel and in Skype for Business Server 2019 Management Shell.

- Can be re-sequenced within the region by using the Set-CsDialinConferencingAccessNumber cmdlet with the Priority parameter.

You must finish migrating dial-in access numbers that point to the legacy install pool before you decommission the legacy install pool. If you do not complete dial-in access number migration as described in the following procedure, incoming calls to the access numbers will fail.

> [!IMPORTANT]
> You must perform this procedure prior to decommissioning the legacy install pool. 

> [!NOTE]
> We recommend that you move dial-in access numbers when network usage is low, in case there is a short period of service outage. 

## To identify and move dial-in access numbers

1. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Skype for Business Server 2019**, and then click **Skype for Business Server Management Shell**.

2. To move each dial-in access number to a pool hosted on Skype for Business Server 2019, from the command line run: 

   ```
   Move-CsApplicationEndpoint -Identity <SIP URI of the access number to be moved> -Target <FQDN of the pool to which the access number is moving>
   ```

3. Open Skype for Business Server Control Panel.

4. In the left navigation bar, click **Conferencing**.

5. Click the **Dial-in Access Number** tab. 

6. Verify that no dial-in access numbers remain for the legacy install pool from which you are migrating.

    > [!NOTE]
    > When all dial-in access numbers point to the Skype for Business Server 2019 pool, you can then decommission the legacy install pool. 

## Verify the dial-in access number migration using Skype for Business Server Control Panel

1. From a user account that is assigned to the **CsUserAdministrator** role or the **CsAdministrator** role, log on to any computer in your internal deployment. 

2. Open Skype for Business Server Control Panel.

3. In the left navigation bar, click **Conferencing**.

4. Click the **Dial-in Access Number** tab. 

5. Verify that all the dial-in access numbers are migrated to the pool hosted on Skype for Business Server 2019.

## Verify the dial-in access number migration using Skype for Business Server Management Shell

1. Open Skype for Business Server Management Shell.

2. To return all the dial-in conferencing access numbers migrated, from the command line run:

   ```
   Get-CsDialInConferencingAccessNumber -Filter {Pool -eq "<FQDN of the pool to which the access number is moved>"}
   ```

3. Verify that all the dial-in access numbers are migrated to the pool hosted on Skype for Business Server 2019.


