In Microsoft Teams, a resource account is required for each auto attendant or call queue. Resource accounts may also be assigned telephone numbers. This is how you assign phone numbers to auto attendants and call queues allowing callers from outside Teams to reach the auto attendant or call queue.

This article covers how to create resource accounts and ready them for use with auto attendants and call queues.

Before you start the procedures in this article, ensure you've done the following steps:

- [Obtain Microsoft Teams Phone Resource Account licenses](#obtain-microsoft-teams-phone-resource-account-licenses)
- [Obtain phone numbers](#obtain-phone-numbers)
- [Assign permissions for managing a resource account](#assign-permissions-for-managing-a-resource-account)

> [!NOTE]
> Resource accounts used for auto attendants and call queues are disabled for sign in and must remain so. Chat and presence aren't available and won't work for these accounts. Even though presence still appears, it won't change.
>
> A **User Administrator** and a Teams administrator role is required to create and license resource accounts. For more information, see [Assign permissions for managing resource accounts](#assign-permissions-for-managing-a-resource-account) and [Using Microsoft Teams administrator roles to manage Teams](/microsoftteams/using-admin-roles).

### Obtain Microsoft Teams Phone Resource Account licenses

Each resource account requires a license in order to work with auto attendants and call queues, known as a **Microsoft Teams Phone Resource Account** license. Subscriptions with Teams Phone have access to a zero-cost allocation of **Microsoft Teams Phone Resource Account** licenses, and if more are needed, extra **Microsoft Teams Phone Resource Account** licenses can be purchased at a cost. For details on how to obtain these licenses, see [Microsoft Teams Phone Resource Account licenses](../teams-add-on-licensing/virtual-user.md).

We cover how to [assign the license to a resource account later in this article](#assign-a-license).

If you purchased **Teams Phone Standard**, **Teams Phone with Calling Plan**, or **Teams Shared Devices** licenses, you still need to complete the purchasing process for your allocation of **Teams Phone Resource Account** licenses, but your allotment of licenses will be zero cost at checkout.

To see if you already have **Teams Phone Resource Account** licenses in your tenant, sign into the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339) using an account with Global admin permissions. Then, go to [Billing > Your products](https://admin.microsoft.com/Adminportal/Home#/subscriptions). If you have **Teams Phone Resource Account** licenses, they'll appear as **Microsoft Teams Phone Resource Account**.

1. Open the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339) and sign in with a user that is a Global admin. This is usually the account you used to sign up for Microsoft 365.
1. In the left navigation pane, go to [**Billing** > **Purchase services**](https://admin.microsoft.com/Adminportal/Home#/catalog) > **Add-ons**.
1. Scroll to find the **Microsoft Teams Phone Resource Account** license.
1. Select the **Details** button.
1. Choose the number of licenses you want to purchase and a billing frequency.
    1. You need one license for each auto attendant and call queue you plan to set up. We recommend selecting at least five licenses so you can easily set up more auto attendants and call queues in the future without having to purchase more licenses right away.
1. Select the **Buy** button.
1. Fill in the purchasing details.
1. Confirm your order details, and then select the **Place order** button.

> [!IMPORTANT]
> Microsoft recommends that you use roles with the fewest permissions. This helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role. To learn more, see [About Admin roles in the Microsoft 365 admin center](/microsoft-365/admin/add-users/about-admin-roles).

There's zero cost for your allotment of licenses, but you still need to follow these steps to acquire the licenses.

### Obtain phone numbers

Phone numbers are optional for auto attendants and call queues. For any auto attendant or call queue that you want to be reachable directly by a phone number, you must have a resource account with an associated phone number.

Resource accounts can use either toll or toll-free phone numbers. You can request new numbers or port existing numbers from another carrier.

Acceptable phone numbers that can be applied to resource accounts include:

- **Calling Plans service numbers:** To acquire service numbers with Calling Plans, see [Getting service phone numbers](../getting-service-phone-numbers.md).
- **Direct Routing numbers:** To acquire Direct Routing numbers, see [Enable users for Direct Routing](/microsoftteams/direct-routing-enable-users#configure-the-phone-number-and-enable-enterprise-voice).
- **Operator Connect numbers:** To acquire Operator Connect numbers, see [Configure Operator Connect](/microsoftteams/operator-connect-configure#set-up-phone-numbers).

> [!NOTE]
> Resource accounts with Direct Routing phone numbers with or without extensions are supported. Currently, the Teams admin center only supports assigning Direct Routing phone numbers without extensions. To assign a Direct Routing phone number with an extension to a resource account, use the Teams PowerShell cmdlet [Set-CsPhoneNumberAssignment](/powershell/module/teams/set-csphonenumberassignment).

To port a number from another carrier, see [Transfer phone numbers to Teams](../phone-number-calling-plans/transfer-phone-numbers-to-teams.md).

## Assign permissions for managing a resource account

> [!NOTE]
> Currently, Teams administrators can create and manage resource accounts without requiring any user management permissions in Microsoft 365. As part of our commitment to deliver secure solutions that meet the highest standards, we are implementing changes to the management of resource accounts. Going forward, Teams administrators will need to have user management permissions in Microsoft 365 to create and manage resource accounts. This change will take effect in the 3rd quarter of 2024.

To create and manage a resource account, admins must have two roles - a **Teams administrator** role and the **User Administrator** role.

An admin needing to create resource accounts needs one of the following Teams administrator roles:

- Teams Telephony Administrator
- Teams Communications Administrator
- Teams Administrator

The User Administrator role is a built-in role in Microsoft 365 that grants permissions to create and manage user accounts. For more information, see [Assign admin roles in Microsoft 365](/microsoft-365/admin/add-users/assign-admin-roles).

If a user has a Teams administrator role without the User Administrator role, you must either assign the User Administrator role to provide the necessary permissions to create user accounts or create a custom role with the minimum required permission (microsoft.directory/users/create) to allow the creation of resource accounts. This custom role can be created with [Microsoft Graph API](/graph/overview). For information on creating a custom role in Microsoft Graph API, see [Assign custom admin roles using the Microsoft Graph API in Microsoft Entra ID](/entra/identity/role-based-access-control/custom-create) and [Create and assign a custom role in Microsoft Entra ID](/entra/identity/role-based-access-control/custom-create).

A Global Administrator also has the necessary Teams and User permissions to create and manage resource accounts, but we recommend using roles with the fewest permissions.

For more information about Teams administrator roles, see [Use Microsoft Teams administrator roles to manage Teams](/microsoftteams/using-admin-roles).

## Create a resource account

Before creating a resource account, you must [assign permissions for creating and managing a resource account](#assign-permissions-for-managing-a-resource-account).

You can create a resource account in the Teams admin center or with PowerShell.

### Teams admin center

1. Sign into the [Teams admin center](https://go.microsoft.com/fwlink/p/?linkid=2066851).
2. Expand **Voice**, and then select **Resource accounts**.
3. Select **Add**.
4. In the **Add resource account** pane, fill out **Display name**, **Username**, and the **Resource account type**. The resource account type can be either **Auto attendant** or **Call queue**, depending how you intend to use this resource account.
5. Select **Save**.

### PowerShell

You can create a resource account with the New-CsOnlineApplicationInstance PowerShell cmdlet. For more information, see [New-CsOnlineApplicationInstance](/powershell/module/teams/new-csonlineapplicationinstance).

## Assign a license

For each resource account, you must assign a **Microsoft Teams Phone Resource Account** license.

1. Sign into the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339).
2. Expand **Users**, then select **Active users**.
3. Select the resource account to which you want to assign a license. The resource account's user pane will appear.
4. On the **Licenses and Apps** tab, under **Licenses**, select **Microsoft Teams Phone Resource Account**.
5. Select **Save changes**.

> [!NOTE]
> If the resource account requires a phone number, check that the **Select location** dropdown list in the **Licenses and Apps** tab matches the intended country code.

## Assign a phone number

If you're planning to use the resource account with an auto attendant or call queue that requires a phone number, assign a number to the resource account.

1. Sign into the [Teams admin center](https://go.microsoft.com/fwlink/p/?linkid=2066851).
2. Expand **Voice**, and then select **Resource accounts** page.
3. Select the resource account to which you want to assign a phone number, and then select **Assign/unassign**.
4. In the **Phone number type** dropdown, choose the type of number that you want to use.
5. In the **Assigned phone number** box, search for the number you want to use and select **Add**. Be sure to include the country code (for example, +1 250 555 0012).
6. Select **Save**.
