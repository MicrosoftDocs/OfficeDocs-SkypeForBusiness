In Microsoft Teams, a resource account is required for each auto attendant or call queue. Resource accounts may also be assigned service telephone numbers. This is how you assign phone numbers to auto attendants and call queues allowing callers from outside Teams to reach the auto attendant or call queue.

This article covers how to create resource accounts and ready them for use with auto attendants and call queues.

Before you start the procedures in this article, ensure you've done the following:

- [Obtain Microsoft Teams Phone Resource Account licenses](#obtain-microsoft-teams-phone-resource-account-licenses)
- [Obtain service numbers](#obtain-service-numbers)

> [!NOTE]
> Resource accounts used for auto attendants and call queues are disabled for sign in and must remain so. Chat and presence are not available for these accounts.

### Obtain Microsoft Teams Phone Resource Account licenses

Each resource account requires a license in order to work with auto attendants and call queues. You can use a free *Microsoft Teams Phone Resource Account* license. To obtain these licenses, see [Microsoft Teams Phone Resource Account licenses](../teams-add-on-licensing/virtual-user.md).

We cover how to [assign the license to a resource account later in this article](#assign-a-license).

If you purchased **Teams Phone Standard** or **Teams Phone with Calling Plan** bundle licenses, *Teams Phone Resource Account* licenses are already in your account.

To see if you already have Resource Account licenses, log into Microsoft 365 using an account with Global admin permissions. Then, go to [Billing > Your products](https://admin.microsoft.com/Adminportal/Home#/subscriptions). If you have Resource Account licenses, they'll appear as **Microsoft Teams Phone Resource Account**.

1. Open the Microsoft 365 admin center and log in with a user that is a Global admin. This is usually the account you used to sign up for Microsoft 365.
2. In the left navigation pane, go to [**Billing** > **Purchase services**](https://admin.microsoft.com/Adminportal/Home#/catalog) > **Add-ons** > **See all Add-ons products**.
3. Scroll to the end to find the **Microsoft Teams Phone Resource Account** license. Select **Details**, then **Buy**.
4. On the license purchase page, select the number of Resource Account licenses you want. You need one Resource Account license for each auto attendant and call queue you plan to set up. We recommend selecting at least five licenses so you can easily set up more auto attendants and call queues in the future without having to purchase more licenses right away.
5. Uncheck **Automatically assign to all of your users with no licenses**.
6. Select **Check out now**.
7. Confirm your order, select **Next**, and then **Place order**.

There is a zero cost, but you still need to follow these steps to acquire the license.

### Obtain service numbers

Service numbers are optional for auto attendants and call queues, however you will need at least one service number in order for callers to reach your auto attendant and call queue configuration. For any auto attendant or call queue that you want to be reachable directly by a service number, you must have a resource account with an associated service number.

Resource accounts can use either toll or toll-free service numbers. You can request new numbers or port existing numbers from another carrier.

To get new service numbers, see [Getting service phone numbers](../getting-service-phone-numbers.md).

To port a number from another carrier, see [Transfer phone numbers to Teams](../phone-number-calling-plans/transfer-phone-numbers-to-teams.md).

## Create a resource account

You can create a resource account in the Teams admin center.

1. In the Teams admin center, expand **Voice**, and then select **Resource accounts**.
2. Select **Add**.
3. In the **Add resource account** pane, fill out **Display name**, **Username**, and the **Resource account type**. The resource account type can be either **Auto attendant** or **Call queue**, depending how you intend to use this resource account.
4. Select **Save**.

## Assign a license

For each resource account, you must assign a *Microsoft Teams Phone Resource Account* license or *Teams Phone Standard* license.

1. In the Microsoft 365 admin center, expand **Users**, then select **Active users**.
2. Select the resource account to which you want to assign a license. The resource account's user pane will appear.
3. On the **Licenses and Apps** tab, under **Licenses**, select **Microsoft Teams Phone Resource Account**.
4. Select **Save changes**.

## Assign a service number

If you're planning to use the resource account with an auto attendant or call queue that requires a service number, assign a number to the resource account.

1. In the Teams admin center, on the **Resource accounts** page, select the resource account to which you want to assign a service number, and then select **Assign/unassign**.
2. In the **Phone number type** dropdown, choose the type of number that you want to use.
3. In the **Assigned phone number** box, search for the number you want to use and select **Add**. Be sure to include the country code (for example, +1 250 555 0012).
4. Select **Save**.

To assign a direct routing or hybrid number to a resource account you need to use PowerShell:

`Set-CsPhoneNumberAssignment -Identity aa-contoso_main@contoso64.net -PhoneNumber +19295550150 -PhoneNumberType DirectRouting`