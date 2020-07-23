---
title: Block access to SharePoint for specific users
author: cichur
ms.author: v-cichur
manager: serdars
ms.reviewer: Nigolc
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
- M365-collaboration
- Teams_ITAdmin_Help
f1.keywords:
- NOCSH
appliesto: 
- Microsoft Teams
localization_priority: Normal
search.appverid: MET150
description: Learn about how to block access to SharePoint for specific users
---

# Block access to SharePoint for specific users

1. Open SharePoint [Admin Center](https://admin.microsoft.com/sharepoint?page=accessControl&modern=true).

2. Expand **Policies** > **Access Policies**.

3. In the **Unmanaged Devices** section,  select **Block Access** and click **Save**.

   ![The image shows the Unmanaged devices section for Policies](media/no-sharepoint-access1.png)

4. Open the [Azure Active Directory](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies) portal and navigate to **Conditional Access Policies** section.

    You'll see a new policy has been created by SharePoint that's similar to this example:

    ![The screenshot shows a new policy that's named Use app-enforced Restrictions for browser access](media/no-sharepoint-access2.png)

5. Update the policy to target only specific users/group.

    ![The images shows the Sharepoint admin center with the Select user section highlighted.](media/no-sharepoint-access2b.png)

6. Verify that only SharePoint Online is selected as targeted Cloud App

    ![The images shows the Sharepoint online is selected as the targeted app.](media/no-sharepoint-access3.png)

7. Update **Conditions** to include desktop clients, as well.

    ![The image shows desktop and mobile apps highlighted.](media/no-sharepoint-access4.png)

8. Make sure that **Grant access** is enabled

    ![The image shows that grant access is enabled.](media/no-sharepoint-access5.png)

9. Make sure **Use app enforced restrictions** is enabled.

10. Enable your policy and click **Save**.

    ![The image shows that use app enforced restrictions is enabled.](media/no-sharepoint-access6.png)

To test your policy, you need to sign out from any client such as the Teams desktop app or the OneDrive sync client and sign in again to see policy
working.
