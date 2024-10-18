---
title: Set up dynamic filters for SIP Gateway
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: chasing
ms.date: 08/20/2024
ms.topic: article
audience: admin
appliesto: 
  - Microsoft Teams
ms.service: msteams
ms.subservice: itpro-devices
ms.collection: 
  - teams-rooms-devices
  - Teams_ITAdmin_Devices
  - Tier1
f1.keywords: 
  - NOCSH                           
search.appverid: MET150
ms.localizationpriority: medium
description: Learn how to create and set up dynamic filters and exclusions for SIP gateway to control access to your organization's resources.
---

# Set up dynamic filters for SIP Gateway

This article explains how to exclude SIP Gateway from Conditional Access Policy, which is a feature that allows you to control access to your organization's resources based on certain conditions. You can exclude SIP Gateway from conditional access if you use it for voice and don't want to enforce extra security requirements on those users. In this article, you'll find the steps to create an exclusion group and assign it to the policy along with the prerequisites.

The SIP Gateway resources mentioned in this article can’t be directly excluded from Conditional Access policies. Hence, we describe the dynamic app filter approach to exclude SIP Gateway apps. Also, simply excluding SIP Gateway apps won't address the gap as SIP Gateway apps don't own any scopes on their own and depend on Teams app for the required scopes.

## Prerequisites

To add or deactivate custom security attributes definitions, you must have:

- [Attribute Assignment Administrator](/entra/identity/role-based-access-control/permissions-reference#attribute-assignment-administrator)
- [Attribute Definition Administrator](/entra/identity/role-based-access-control/permissions-reference#attribute-definition-reader)
- Microsoft Graph module, when using [Microsoft Graph PowerShell](/powershell/microsoftgraph/installation)

> [!IMPORTANT]
> By default, Global Administrator and other administrator roles do not have permissions to read, define, or assign custom security attributes.

## Step 1: Add an attribute set

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com/) as a [Attribute Definition Administrator](/entra/identity/role-based-access-control/permissions-reference).
2. Browse to **Protection** > **Custom security attributes**.
3. Select **Add attribute set** to add a new attribute set.

   > [!NOTE]
   > If **Add attribute set** is disabled, ensure that you're assigned the Attribute Definition Administrator role. For more information, see [Troubleshoot custom security attributes](/entra/fundamentals/custom-security-attributes-troubleshoot).

4. Enter a name, description, and maximum number of attributes.

   > [!TIP]
   > An attribute set name can be 32 characters with no spaces or special characters. Once you've specified a name, you can't rename it. For more information, see [Limits and constraints](/entra/fundamentals/custom-security-attributes-overview).
  
5. When finished, select **Add**.
6. The new attribute set appears in the list of attribute sets.

## Step 2: Add a custom security attribute definition

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com/) as a [Attribute Definition Administrator](/entra/identity/role-based-access-control/permissions-reference).
2. Browse to **Protection** > **Custom security attributes**.
3. On the **Custom security attributes** page, choose an existing attribute set or select **Add attribute set** to add a new attribute set. All custom security attribute definitions must be part of an attribute set.
4. Select to open the selected attribute set.
5. Select **Add attribute** to add a new custom security attribute to the attribute set.
6. In the **Attribute name** box, enter a custom security attribute name.

   > [!TIP]
   > An attribute set name can be 32 characters with no spaces or special characters. Once you've specified a name, you can't rename it. For more information, see [Limits and constraints](/entra/fundamentals/custom-security-attributes-overview).

   :::image type="content" source="media/exclude-attribute-set.png" alt-text="Screenshot displaying the Exclude attribute set." lightbox="media/exclude-attribute-set.png":::

7. In the **Description** box, enter an optional description.

   > [!TIP]
   > A description can be 128 characters long. If necessary, you can later change the description.

8. From the **Data type** list, select the data type for the custom security attribute.
   - Data type: A description.
   - Boolean: A Boolean value that can be true or false.
   - Integer: A 32-bit integer.
   - String: A string that can be X characters long.

9. For **Allow multiple values to be assigned**, select **Yes** or **No**.
   - Select **Yes** to allow multiple values to be assigned to this custom security attribute.
   - Select **No** to only allow a single value to be assigned to this custom security attribute.

10. For **Only allow predefined values to be assigned**, select **Yes** or **No**.
    - Select **Yes**, if custom security attribute can be assigned values from a predefined values list.
    - Select **No** to allow this custom security attribute to be assigned user-defined values or potentially predefined values.

11. If **Only allow predefined values to be assigned** is selected Yes, then select **Add value** to add predefined values. An active value is available for assignment of objects. A value that isn't active is defined, but not yet available for assignment.
12. When finished, select **Save**.
13. The new custom security attribute appears in the list of custom security attributes.

## Step 3: Add SIP Gateway Service Principals to your tenant

**Using Azure Active Directory module:**

1. Open a new elevated PowerShell window.
2. Run `Install-Module AzureAD`.
3. Run `Import-Module AzureAD`.
4. Run `Connect-AzureRmAccount`.
5. Sign in with the admin account.
6. Run the following cmdlet:

   ```powershell
   Get-AzureADServicePrincipal -Filter "AppId eq '582b2e88-6cca-4418-83d2-2451801e1d26'"
   ```

   If you get no output, then run:

   ```powershell
   New-AzureADServicePrincipal -AppId "582b2e88-6cca-4418-83d2-2451801e1d26"
   ```

7. Run the following cmdlet:

   ```powershell
   Get-AzureADServicePrincipal -Filter "AppId eq '0ab9de21-b802-4d77-b279-1ad41ca233b4'"
   ```

   If you get no output, then run:

   ```powershell
   New-AzureADServicePrincipal -AppId "0ab9de21-b802-4d77-b279-1ad41ca233b4"
   ```

**Using MS Graph module:**

1. Run the following cmdlets:

   ```powershell
   ## SIP Gateway API:
   Get-MgServicePrincipal -Filter "AppId eq '0ab9de21-b802-4d77-b279-1ad41ca233b4'"
   New-MgServicePrincipal -AppId "0ab9de21-b802-4d77-b279-1ad41ca233b4"
   ```

   ```powershell
   ## SIP Gateway UserApp:
   Get-MgServicePrincipal -Filter "AppId eq '582b2e88-6cca-4418-83d2-2451801e1d26'"
   New-MgServicePrincipal -AppId "582b2e88-6cca-4418-83d2-2451801e1d26"
   ```

2. After running these cmdlets, you should get the following output to proceed:

   :::image type="content" source="media/powershell-output-expected.png" alt-text="Screenshot of the output that is expected after running cmdlets.":::

**Bulk device sign-in**

If you are using bulk-sigin for your devices, you will also have to add this extra service principal Teams SIP Gateway:

```powershell
##Using AzureAd Module:
Get-AzureADServicePrincipal -Filter "AppId eq '61c8fd69-c13e-4ee6-aaa6-24ff71c09bca
```

If you get no output, then run:

```powershell
New-AzureADServicePrincipal -AppId "61c8fd69-c13e-4ee6-aaa6-24ff71c09bca"
```

```powershell
## Using MS Graph Module:
Get-AzureADServicePrincipal -Filter "AppId eq '61c8fd69-c13e-4ee6-aaa6-24ff71c09bca
New-MgServicePrincipal -AppId "61c8fd69-c13e-4ee6-aaa6-24ff71c09bca" 
```

## Step 4: Assign custom security attribute to SIP Gateway

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com/) as at least a [Conditional Access Administrator](/entra/identity/role-based-access-control/permissions-reference).
2. Browse to **Identity** > **Applications** > **Enterprise applications**.
3. Clear all filters.
4. Search for SIP Gateway API (0ab9de21-b802-4d77-b279-1ad41ca233b4) and select it.
5. Under **Manage** > **Custom security attributes**, select **Add assignment**.
6. Under **Attribute set**, select the attribute set you created in [step 1](#step-1-add-an-attribute-set).
7. Under **Attribute name**, select the attribute name you created in [step 2](#step-2-add-a-custom-security-attribute-definition).
8. Under **Assigned values**, select **Add values**, select the value from the list (requireMFA in this example), then select **Done**.

   :::image type="content" source="media/require-mfa-selection.png" alt-text="Screenshot displaying to select requireMFA.":::

9. Select **Save**.
10. Follow the same steps for SIP Gateway UserApp (582b2e88-6cca-4418-83d2-2451801e1d26).
11. Follow the same steps for Teams SIP Gateway (61c8fd69-c13e-4ee6-aaa6-24ff71c09bca) in case you’re using bulk signin for your devices.

## Step 5: Exclude this attribute from your Conditional Access Policy

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com/) as at least a [Conditional Access Administrator](/entra/identity/role-based-access-control/permissions-reference).
2. Browse to **Protection** > **Conditional Access**.
3. Select the policy you want to change.
4. Under **Target resources**, select the following options to autofill this field:
   - From **Select what this policy applies to** list, choose **Cloud apps**.
   - On the **Include** tab, select **All** apps option.
   - Change tab to **Exclude** and under **Select excluded cloud apps**, search for **Microsoft Teams Services** and click on **Select**.

5. Select **Edit filter**.
6. On the **Edit filter** page, set **Configure** to **Yes**.
7. Select the attribute you created earlier (in this case 'exclAttrAllowMultiple').
8. Set **Operator** to **Contains**.
9. Set **Value** to the one assigned to SIP Gateway apps in [step 4](#step-4-assign-custom-security-attribute-to-sip-gateway) (in this case requireMFA).

   :::image type="content" source="media/edit-filter.png" alt-text="Screenshot displaying the edit filter pane." lightbox="media/edit-filter.png":::

10. Select **Done**.
11. Review and confirm your settings.

    :::image type="content" source="media/include-all-apps-settings.png" alt-text="Screenshot displaying the settings that need confirmation.":::

12. Select **Save** to enable your policy.

## Related articles

- [Configure SIP Gateway](sip-gateway-configure.md)
- [Plan for SIP Gateway](sip-gateway-plan.md)
