---
title: 'Lync Server 2013: Configuration management'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Configuration management
ms:assetid: 00ea1196-cb40-427f-99a4-5e8037cbf367
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn720316(v=OCS.15)
ms:contentKeyID: 63969570
ms.date: 05/16/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configuration management in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2015-05-15_

Configuration management is the process of recording and tracking hardware and software assets and system configuration information. It is generally used to track software licenses, maintain a standard hardware and software build for client computers and servers, and define naming standards for new computers. Configuration management generally covers the following categories:

  - **Hardware**   This category tracks the pieces of equipment that the IT organization owns, where equipment is located, and who uses equipment. This information enables an organization to plan and budget for upgrades, maintain standard hardware builds, report on the value of IT assets for accounting purposes, and help prevent theft.

  - **Software**   This category tracks software that is installed on each computer, the version numbers, and where the licenses are held. This information helps plan upgrades, to ensure that software is licensed, and detect the presence of unauthorized (and unlicensed) software.

  - **Standard Builds**   This category tracks the current standard build for the client computers and servers and whether the client computers and servers meet this standard. Defining and enforcing standard builds helps support staff because the staff is required to maintain only a limited number of versions of each piece of software.

  - **Cumulative Updates and Hotfixes**   This category tracks which service packs are tested and approved for use and which computers are up to date. This information is important to reduce the risk of computers being compromised and to detect users who have installed unapproved updates.

  - **System Configuration Information**   This category tracks the function of a system, the interaction between system elements, and the processes that depend on a system that is running smoothly. For example, third-party proxy server may be configured on a single server. The proxy server’s dependence on this server should be understood and contingency plans may be required if there is a failure. If the proxy server can be configured to also communicate with another front-end server, dependencies and contingency plans will probably change.

<div>

## Implementing configuration management

After you determine what items need managing, implement configuration management by collecting data and reporting data. The simplest approach for small organizations is to collect data manually (number and model of client computers, operating system, installed software) and save it in an Office Word or Office Excel document. For larger, more complex, and constantly changing systems, the discovery of assets and collection of detailed information must be automated. Decide what information is relevant to your organization and record it in a database.

The configuration management database is a useful tool for support staff and management in the following areas:

  - **Security Audits**   The database enables you to identify servers that are running Lync Server and client computer systems that must have hotfixes applied or that have missed the installation of a service pack or the latest antivirus updates.

  - **Software Installation**   Identifying client software versions and tracking them will aid administrators in planning version updates and new installs and also by helping with licensing documentation and compliance.

  - **Configuration Information**   If you maintain an up-to-date list of all settings that were changed from their default, then you'll be able to troubleshoot issues quickly and more effectively.

  - **Planning Upgrades**   If a capacity review reveals that additional storage space is required on your Lync database servers, it’s important to know whether each server has an internal RAID controller. If they do, then are they the same model? Do they have the same number of disks installed? The configuration management database will indicate the type of disk that can be installed, the number, and the upgrade path in each case.

</div>

<div>

## Tools used for configuration management

There are many tools to discover, audit, and report assets. Some of these tools are discussed in this section.

  - **Automated Scripts**   You can write simple scripts to report items such as the operating system, service pack level, and whether software exists on a specific set of computers. You can write these scripts to an organization’s exact requirements. However, the required number of scripts and their complexity can make scripts expensive to create and maintain.

  - **Automated Tools**   Depending on the size of your business and your organizational needs, you may want to consider using automated tools. Tools such as System Center Configuration Manager incorporate standard report templates (such as service pack level) and also enable you to create customized reports, for example, for a custom application. The System Center Configuration Manager can also be used to report on hardware and software configurations.

</div>

<div>

## Relationship with change management

Configuration management is closely related to change management. Configuration management identifies the need for change and identifies and records that a change has occurred. For example, the configuration management database can be used to identify servers that require a hotfix. Change management then defines the process for applying the hotfix.

Conversely, if a new cumulative update is rolled out, the change management process should supply this information to the configuration management system. The configuration management tools will probably need to be configured to identify the new software so that they can discover and track where and when the software is deployed.

</div>

</div>

<span> </span>

</div>

</div>

</div>

