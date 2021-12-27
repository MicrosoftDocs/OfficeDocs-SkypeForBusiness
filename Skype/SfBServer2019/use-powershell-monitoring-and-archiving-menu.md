---
title: "Use PowerShell for tasks on Monitoring and Archiving menu"
ms.reviewer: 
ms.author: ankum
author: ankum
manager: ravrao
ms.date: 11/03/2021
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.collection:
description: "Summary: Skype for Business Server Control panel to Cmdlet mapping for Monitoring and Archiving menu."
---
# Monitoring and Archiving

This article describes how similar results as that of the **Monitoring and Archiving** menu item in the legacy Control Panel can be achieved using cmdlets.

This article describes the following sub-menus :

- [Monitoring and Archiving](#monitoring-and-archiving)
  - [Call Detail Recording](#call-detail-recording)
  - [Quality of Experience Data](#quality-of-experience-data)
  - [Archiving Policy](#archiving-policy)
  - [Archiving Configuration](#archiving-configuration)

## Call Detail Recording

**CALL DETAIL RECORDING** sub-menu enables administrators to manage call detail recording (CDR) settings.CDR enables you to track usage of such things as peer-to-peer instant messaging sessions, Voice over Internet Protocol (VoIP) phone calls, and conferencing calls.

Let us consider the various tasks a user can do on **CALL DETAIL RECORDING**, and the Skype for Business cmdlets those tasks map to.

---

> **Scenario 1**: List all the CDR configurations

   ![List Cdr Configuration](./media/cdr-configurations-1.png)

***Cmdlet***

[Get-CsCdrConfiguration](/powershell/module/skype/get-cscdrconfiguration)

***Example***

```powershell
 Get-CsCdrConfiguration
```

---

> **Scenario 2**: Create a new CDR configuration

   ![Create Cdr Configuration](./media/cdr-configurations-2.png)

***Cmdlet***

[New-CsCdrConfiguration](/powershell/module/skype/new-cscdrconfiguration)  

***Example***

```powershell
 New-CsCdrConfiguration -Identity site:Redmond -EnableCDR $False
```

---

> **Scenario 3**: Get details of a chosen CDR configuration

   ![Get Cdr Configuration](./media/cdr-configurations-3.png)

***Cmdlet***

[Get-CsCdrConfiguration](/powershell/module/skype/get-cscdrconfiguration)

***Example***

```powershell
 Get-CsCdrConfiguration -Identity site:Redmond
```

---

> **Scenario 4**: Delete chosen CDR configurations

   ![Delete Cdr Configuration](./media/cdr-configurations-4.png)

***Cmdlet***

[Remove-CsCdrConfiguration](/powershell/module/skype/remove-cscdrconfiguration)

***Example***

```powershell
 Remove-CsCdrConfiguration -Identity site:Redmond
```

---

> **Scenario 5**: Update a CDR configuration

   ![Update Cdr Configuration](./media/cdr-configurations-5.png)

***Cmdlet***

[Set-CsCdrConfiguration](/powershell/module/skype/set-cscdrconfiguration)

***Example***

```powershell
 Set-CsCdrConfiguration -Identity site:Redmond -PurgeHourOfDay 23
```

---

## Quality of Experience Data

The **QUALITY OF EXPERIENCE DATA** sub-menu enables administrators to manage Quality of Experience (QoE) settings. throughout the organization; this includes managing group expansion, certificate settings, and allowed authentication methods. Because administrators can configure different settings at the global, site, and service scope (albeit for the only the Web Services service), one can customize Web Services capabilities for different users and different locations.

Let us consider the various tasks a user can do on **WEB SERVICE**, and the Skype for Business cmdlets those tasks map to.

---
> **Scenario 1**: List all the QoE configurations

   ![List QoE configuration](./media/qoe-configuration-1.png)

***Cmdlet***

[Get-CsQoEConfiguration](/powershell/module/skype/get-csqoeconfiguration)

***Example***

```powershell
 Get-CsQoEConfiguration
```

---

> **Scenario 2**: Create a new QoE configuration

   ![New QoE configuration](./media/qoe-configuration-2.png)

***Cmdlet***

[New-CsQoEConfiguration](/powershell/module/skype/new-csqoeconfiguration)  

***Example***

```powershell
 New-CsQoEConfiguration -Identity site:Redmond -EnableQoE $False
```

---

> **Scenario 3**: Get details of a chosen QoE configuration

   ![Get QoE configuration](./media/qoe-configuration-3.png)

***Cmdlet***

[Get-CsQoEConfiguration](/powershell/module/skype/get-csqoeconfiguration)

***Example***

```powershell
 Get-CsQoEConfiguration -Identity site:Redmond
```

---

> **Scenario 4**: Delete chosen QoE configurations

   ![Delete QoE configuration](./media/qoe-configuration-4.png)

***Cmdlet***

[Remove-CsQoEConfiguration](/powershell/module/skype/remove-csqoeconfiguration)

***Example***

```powershell
 Remove-CsQoEConfiguration -Identity site:Redmond
```

---

> **Scenario 5**: Update a QoE configuration

   ![Update QoE configuration](./media/qoe-configuration-5.png)

***Cmdlet***

[Set-CsQoEConfiguration](/powershell/module/skype/set-csqoeconfiguration)

***Example***

```powershell
 Set-CsQoEConfiguration -Identity site:Redmond -EnableQoE $False
```

---

## Archiving Policy

Administrators can use **ARCHIVING POLICY** to manage instant messaging (IM) session archiving policies.Archiving policies enable you to archive all IM and web conferencing sessions that take place between internal users and/or between internal users and external users

Let us consider the various tasks a user can do on **ARCHIVING POLICY**, and the Skype for Business cmdlets those tasks map to.

---

> **Scenario 1**: List all the archiving policies

   ![List Archiving Policy](./media/archiving-policy-1.png)

***Cmdlet***

[Get-CsArchivingPolicy](/powershell/module/skype/get-csarchivingpolicy)

***Example***

```powershell
 Get-CsArchivingPolicy
```

---

> **Scenario 2**: Create a new archiving policy

   ![Create Archiving Policy](./media/archiving-policy-2.png)

***Cmdlet***

[New-CsArchivingPolicy](/powershell/module/skype/new-csarchivingpolicy)  

***Example***

```powershell
 New-CsArchivingPolicy -Identity site:Redmond -ArchiveInternal $True
```

---

> **Scenario 3**: Get details of a chosen archiving policy

   ![Get Archiving Policy](./media/archiving-policy-3.png)

***Cmdlet***

[Get-CsArchivingPolicy](/powershell/module/skype/get-csarchivingpolicy)

***Example***

```powershell
 Get-CsArchivingPolicy -Identity site:Redmond
```

---

> **Scenario 4**: Delete chosen archiving policies

   ![Delete Archiving Policy](./media/archiving-policy-4.png)

***Cmdlet***

[Remove-CsArchivingPolicy](/powershell/module/skype/remove-csarchivingpolicy)

***Example***

```powershell
 Remove-CsArchivingPolicy -Identity site:Redmond
```

---

> **Scenario 5**: Update a archiving policy

   ![Update Archiving Policy](./media/archiving-policy-5.png)

***Cmdlet***

[Set-CsArchivingPolicy](/powershell/module/skype/set-csarchivingpolicy)

***Example***

```powershell
 Set-CsArchivingPolicy -Identity global -ArchiveInternal $True
```

---

## Archiving Configuration

Administrators can use **ARCHIVING CONFIGURATION** to configure how (or if) instant messaging (IM) sessions are archived in the organization.

Let us consider the various tasks a user can do on **ARCHIVING CONFIGURATION**, and the Skype for Business cmdlets those tasks map to.

---

> **Scenario 1**: List all the archiving configurations

   ![List Archiving Configuration](./media/archiving-configuration-1.png)

***Cmdlet***

[Get-CsArchivingConfiguration](/powershell/module/skype/get-csarchivingconfiguration)

***Example***

```powershell
 Get-CsArchivingConfiguration
```

---

> **Scenario 2**: Create a new archiving configuration

   ![Create Archiving Configuration](./media/archiving-configuration-2.png)

***Cmdlet***

[New-CsArchivingConfiguration](/powershell/module/skype/new-csarchivingconfiguration)  

***Example***

```powershell
 New-CsArchivingConfiguration -Identity site:Redmond -EnableArchiving "ImOnly"
```

---

> **Scenario 3**: Get details of a chosen archiving configuration

   ![Get Archiving Configuration](./media/archiving-configuration-3.png)

***Cmdlet***

[Get-CsArchivingConfiguration](/powershell/module/skype/get-csarchivingconfiguration)

***Example***

```powershell
 Get-CsArchivingConfiguration -Identity site:Redmond
```

---

> **Scenario 4**: Delete chosen archiving configurations

   ![Delete Archiving Configuration](./media/archiving-configuration-4.png)

***Cmdlet***

[Remove-CsArchivingConfiguration](/powershell/module/skype/remove-csarchivingconfiguration)

***Example***

```powershell
 Remove-CsArchivingConfiguration -Identity site:Redmond
```

---

> **Scenario 5**: Update a archiving configuration

   ![Update Archiving Configuration](./media/archiving-configuration-5.png)

***Cmdlet***

[Set-CsArchivingConfiguration](/powershell/module/skype/set-csarchivingconfiguration)

***Example***

```powershell
 Set-CsArchivingConfiguration -Identity site:Redmond -ArchiveDuplicateMessages $False -KeepArchivingDataForDays 30
```

---
