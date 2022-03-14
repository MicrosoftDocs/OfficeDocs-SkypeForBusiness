1. Sign in to the Microsoft 365 admin center.

2. Provide the admin credentials for your Microsoft 365 tenant.

3. Go to **Resources** in the left panel, and then select **Rooms & equipment**. If these options aren't available in the left panel, you may need to select **Show all** first.

4. Select **Add a resource mailbox** to create a new room account. Enter a display name and email address for the account, select **Add**, and then select **Close**.

5. By default, resource accounts are configured with the following settings:

- Allow repeat meetings
- Automatically decline meetings outside of the following limits
  - Booking window (days): 180
  - Maximum duration (hours): 24
- Auto accept meeting requests

If you want to change them, select **Set scheduling options** before you select **Close**. If you want to change them later, go to **Resources** > **Rooms & equipment**, select the resource account. Then  under **Booking options**, select **Edit**.

6. Go to **Users** > **Active users**, and select the room you created to open the properties panel.

7. Next, assign a password to the resource account. In the panel, select **Reset password**.
 
8. Requiring users to change the password on a shared device will cause sign in problems. Uncheck **Require this user to change their password when they first sign in**, and select **Reset**.

9. In the **Licenses and Apps** section, set **Select location** to the country or region where the device will be installed. Then select the license you want to assign, such as Meeting Room, and select **Save changes**. The license may vary depending on your organization.

To change the settings of the resource mailbox, see [Configure mailbox properties](#configure-mailbox-properties) or use the Exchange admin center.

You may also need to apply bandwidth policies or meeting policies to this account. See [Next steps](#next-steps) for more information.
