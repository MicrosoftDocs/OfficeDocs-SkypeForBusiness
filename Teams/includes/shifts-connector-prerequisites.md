Before you get started, make sure you have the following prerequisites:

- Blue Yonder version 2020.3, 2021.1, or 2021.2. </br>If you have 2020.3 or 2021.1, we recommend applying the 2020.3.0.4 or 2021.1.0.3 patch. The patch has a fix required for users to update their availability in Shifts.
- Blue Yonder service account name and password and service URLs. </br>If you don’t have this information, contact your Blue Yonder delivery partner or technical account manager. The account is created at the root enterprise level by a Blue Yonder enterprise administrator. It must have API Access, Client Admin, and Store Manager access. The account and password are required to create a connection.
- Federated SSO authentication is enabled in your Blue Yonder environment. Contact your Blue Yonder delivery partner or technical account manager to make sure federated SSO is enabled. They'll need the following information:

    - federatedSSOValidationService: `https://amer.wfmconnector.teams.microsoft.com/api/v1/fedauth/{tenantId}/6A51B888-FF44-4FEA-82E1-839401E9CD74/authorize` where {tenantId} is your tenantId
     - proxyHeader: X-MS-AuthToken

- At least one team is set up in Teams.
- Microsoft 365 service account is added as a team owner to all teams you want to map.</br> This service account is an account that you create. Create it in Azure Active Directory (Azure AD) and assign it a Microsoft 365 license. Then, add the account as a team owner to all teams that you want to map. The Shifts connector uses this account when syncing Shifts changes from Blue Yonder.

    We recommend that you create a service account specifically for this purpose and not use your user account.