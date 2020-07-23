Block Access to SharePoint for specific users

1.  Open SharePoint Admin Center -
    [<span class="underline">https://admin.microsoft.com/sharepoint?page=accessControl\&modern=true</span>](https://admin.microsoft.com/sharepoint?page=accessControl&modern=true)

> Open: “Policies” - “Access Policies” – “Unmanaged Devices” Set: “Block
> Access” and click “Save”
> 
> ![](media/image1.jpg)

2.  Navigate to Azure Active Directory – Conditional Access Policies
    [<span class="underline">https://portal.azure.com/\#blade/Microsoft\_AAD\_IAM/ConditionalAccessBlade/Policies</span>](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies)

> You should see a new policy has been created by SharePoint similar to
> this example

![](media/image2.jpg)

3.  Update the policy to target only specific users/group

> ![](media/image3.jpg)

4.  Make sure that only SharePoint Online is selected as targeted Cloud
    App

> ![](media/image4.jpg)

5.  Update “Conditions” to include desktop clients as well

![](media/image5.jpg)

6.  Make sure that Grant Access is enabled

![](media/image6.jpg)

7.  Make sure “Use app enforced restrictions” is enabled

![](media/image7.jpg)

8.  Enable your policy and click “Save”

To test your policy, you need to **sign out** from any client like Teams
desktop app or onedrive sync client and sign in again to see policy
working.
