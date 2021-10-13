# Clients

## Test

 Returns information about which clients are supported in your Skype for Business Server environment. Client version policies enable you to specify which clients will be able to log on to your Skype for Business Server system.

Let us consider various  scenarios and how do they map to Skype for Business cmdlets.

<br>

---
> **Scenario 1 :** Lists all the client version policies

![Client Version Policy](../media/ClientVersionPolicy-1.png)

***Cmdlet***

[Get-CsClientVersionPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/get-csclientversionpolicy?view=skype-ps)

***Example***

```powershell
 Get-CsClientVersionPolicy
```

---

> **Scenario 2 :** Create a new client version policy

![Client Version Policy](../media/ClientVersionPolicy-2.png)

***Cmdlet***

[New-CsClientVersionPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/new-csclientversionpolicy?view=skype-ps)  

***Example***

```powershell
 New-CsClientVersionPolicy -Identity site:Redmond
```

---

> **Scenario 3 :** Get details of a selected client version policy

![Client Version Policy](../media/ClientVersionPolicy-3.png)

***Cmdlet***

[Get-CsClientVersionPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/get-csclientversionpolicy?view=skype-ps)

***Example***

```powershell
 Get-CsClientVersionPolicy -Identity site:Redmond
```

---

> **Scenario 4 :** Delete selected client version policies

![Client Version Policy](../media/ClientVersionPolicy-4.png)

***Cmdlet***

[Remove-CsClientVersionPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/remove-csclientversionpolicy?view=skype-ps)

***Example***

```powershell
 Remove-CsClientVersionPolicy -Identity site:Redmond
```

> **Scenario 5 :** Update client version policy

![Client Version Policy](../media/ClientVersionPolicy-5678.png)

- **annotation 5**

    ***Cmdlet***

    [Get-CsClientVersionPolicyRule](https://docs.microsoft.com/en-us/powershell/module/skype/get-csclientversionpolicyrule?view=skype-ps)

    ***Example***

    ```powershell
    Get-CsClientVersionPolicyRule -Filter "Global/*"
    ```

- **annotation 6**

    ***Cmdlet***

    [Get-CsClientVersionPolicyRule](https://docs.microsoft.com/en-us/powershell/module/skype/get-csclientversionpolicyrule?view=skype-ps)

    ***Example***

    ```powershell
    Get-CsClientVersionPolicyRule -Identity "Global/2336c611-a243-4c5d-994b-eea8a524d0e4"
    ```

- **annotation 7**

    ***Cmdlet***

    [New-CsClientVersionPolicyRule](https://docs.microsoft.com/en-us/powershell/module/skype/new-csclientversionpolicyrule?view=skype-ps)

    ***Example***

    ```powershell
    $x = \[guid\]::NewGuid()

    New-CsClientVersionPolicyRule -Parent "site:Redmond" -RuleId $x -MajorVersion 4 -UserAgent InHouse
    ```

- **annotation 8**

    ***Cmdlet***

    [Set-CsClientVersionPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/set-csclientversionpolicy?view=skype-ps)

    ***Example***

    ```powershell
    Set-CsClientVersionPolicy -Identity site:Redmond -Rules $Null

    $x = Get-CsClientVersionPolicy -Identity site:Dublin | Select-Object -ExpandProperty Rules

    Set-CsClientVersionPolicy -Identity site:Redmond -Rules $x
    ```
