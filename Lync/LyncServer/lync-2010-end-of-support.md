---
title: "Lync Server 2010 end of support roadmap"
ms.author: v-judegn
author: v-judegn
manager: lolaj
ms.date: 12/19/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.assetid: e150e7b9-c432-4c8d-a0ae-c11847129a7d
description: "Lync Server 2010 is nearing end of support. Use this planning roadmap as a guide to prepare to upgrade to Microsoft Teams or to Lync Server 2015."
---

# Lync Server 2010 end of support roadmap

*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*

On **October 13, 2020**, Lync Server 2010 will reach end of support. If you haven't already begun your migration from Lync Server 2010 to Microsoft Teams or to Lync Server 2015, now's the time to start your planning.

## What does end of support mean?

Lync Server, like almost all Microsoft products, has a support lifecycle during which we provide new features, bug fixes, security fixes, and so on. This
lifecycle typically lasts for 10 years from the date of the product's initial release, and the end of this lifecycle is known as the product's end of support.
When Lync Server 2010 reaches its end of support on October 13, 2020, Microsoft will no longer provide:

- Technical support for problems that may occur;
- Bug fixes for issues that are discovered and that may impact the stability and usability of the server;
- Security fixes for vulnerabilities that are discovered and that may make the server vulnerable to security breaches;
- Time zone updates.

Your installation of Lync Server 2010 will continue to run after this date. However, because of the changes listed above, we strongly recommend that you migrate from Lync Server 2010 as soon as possible.

For more information about Office 2010 servers nearing the end of support, see [Resources to help you upgrade from Office 2010 servers and clients](https://docs.microsoft.com/office365/enterprise/upgrade-from-office-2010-servers-and-products).

## What are my options?

With Lync Server 2010 reaching its end of support, this is a great time to explore your options and prepare a migration plan. You can:

- Migrate fully to Office 365. Migrate mailboxes using cutover, minimal hybrid, or full hybrid migration, then remove on-premises Lync servers and Active Directory.
- Migrate your Lync Server 2010 servers to Lync Server 2015 on your on-premises servers.

> [!IMPORTANT]
> If your organization chooses to migrate mailboxes to Office 365 but intends to keep DirSync or Azure AD Connect in place to continue managing user accounts from on-premises Active Directory, you need to keep at least one Lync server on-premises. If the last Lync server is removed, you won’t be able to make changes to Lync recipients in Lync Online. This is because the source of authority remains in your on-premises Active Directory and changes need to be made there. In this scenario, you have the following options:

- (**Recommended**) If you can migrate your mailboxes to Office 365 and upgrade your servers by October 13, 2020, use Lync Server 2010 to connect to Office 365 and migrate mailboxes. Next, migrate Lync Server 2010 to Lync Server 2015 and decommission any remaining Lync Server 2010 servers.
- If you can’t complete the mailbox migration and on-premises server upgrade by October 13, 2020, upgrade your on-premises Lync Server 2010 servers to Lync Server 2015 first, then use Lync Server 2015 to connect to Office 365 and migrate mailboxes.

> [!NOTE]
> While a little more complicated, you may also migrate mailboxes to Office 365 while migrating your on-premises Lync Server 2010 servers to Lync Server 2015.

Here are the three paths you can take to avoid the end of support for Lync Server 2010.

![Lync Server 2010 upgrade paths](./media/Lync-2010-end-of-support/Lync-2010-end-of-support-options.png)

The following sections explore each option in more detail.

## Migrate to Office 365

Migrating your email to Office 365 is your best and simplest option to help you retire your Lync Server 2010 deployment. With a migration to Office 365, you can
make a single hop from old technology to state-of-the-art features, like:

- Compliance capabilities such as Retention Policies, In-Place and Litigation Hold, in-place eDiscovery, and more;
- Microsoft Teams;
- Power BI;
- Focused Inbox;
- Delve Analytics;

Office 365 also gets new features and experiences first and you and your users can usually start using them right away. In addition to new features, you won't
have to worry about:

- Purchasing and maintaining hardware;
- Paying for heating and cooling of your servers;
- Keeping up to date on security, product, and time zone fixes;
- Maintaining storage and software to support compliance requirements;
- Upgrading to a new version of Lync - you're always on the latest version
    of Lync in Office 365.

### How should I migrate to Office 365?

Depending on your organization, you have a few options that'll help you get to Office 365. When choosing a migration option, you need to consider a few things
like the number of seats or mailboxes you need to move, how long you want the migration to last, and whether you need a seamless integration between your
on-premises installation and Office 365 during the migration. This table shows your migration options and the most important factors that'll determine which
method you'll use.

| **Migration option**     | **Organization size** | **Duration**        |
|--------------------------|-----------------------|---------------------|
| Cutover migration        | Fewer than 150 seats  | A week or less      |
| Minimal hybrid migration | Fewer than 150 seats  | A few weeks or less |
| Full hybrid migration    | More than 150 seats   | A few weeks or more |

The following sections give you an overview of these methods. Check out [Decide on a migration path](https://support.office.com/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27) to learn the details of each method.

### Cutover migration

A cutover migration is one where, at a pre-selected date and time, you'll migrate all your mailboxes, distribution groups, contacts, and so on, to Office
365; when you've finished, you'll shut down your on-premises Lync servers and start using Office 365 exclusively.

The cutover migration method is great for small organizations that don't have very many mailboxes, want to get to Office 365 quickly, and don't want to deal
with some of the complexities of the other methods. But it's also somewhat limited because it should be completed in a week or less and because it requires
users to reconfigure their Outlook profiles. While cutover migration can handle up to 2,000 mailboxes, we strongly recommend you migrate a maximum of 150
mailboxes with this method. If you try to migrate more than 150 mailboxes, you could run out of time to transfer all the mailboxes before your deadline, and
your IT support staff may get overwhelmed helping users reconfigure Outlook.

If you're thinking about doing a cutover migration, here are a few things to think consider:

- Office 365 will need to connect to your Lync Server 2010 servers using Outlook anywhere over TCP port 443;
- All on-premises mailboxes will be moved to Office 365;
- You'll need an on-premises administrator account that has access to read the contents of your users' mailboxes;
- The Lync Server 2010 accepted domains that you want to use in Office 365 need to be added as verified domains in the service;
- Between the time you start the migration and when you begin the completion phase, Office 365 will periodically synchronize the Office 365 and on-premises mailboxes. This lets you complete the migration without worrying about email being left behind in your on-premises mailboxes;
- Users will receive new temporary passwords for their Office 365 account that they'll need to change when they log in to their mailboxes for the first time;
- You'll need an Office 365 license that includes Lync Online for each user mailbox you migrate;
- Users will need to set up a new Outlook profile on each of their devices and download their email again. The amount of email that Outlook will download     can vary. For more information, take a look at [Change how much mail to keep offline](https://support.office.com/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&rs=en-US&ad=US&fromAR=1).

To learn more about cutover migration, take a look at:

- [What you need to know about a cutover email migration to Office 365](https://support.office.com/article/What-you-need-to-know-about-a-cutover-email-migration-to-Office-365-961978ef-f434-472d-a811-1801733869da)
- [Perform a cutover migration of email to Office 365](https://support.office.com/article/Perform-a-cutover-migration-of-email-to-Office-365-9496e93c-1e59-41a8-9bb3-6e8df0cd81b4)

### Minimal hybrid migration

A minimal hybrid, or express, migration is one where you have a few hundred mailboxes that you want to migrate to Office 365, can complete the migration
within a few weeks, and don't need any of the advanced hybrid migration features like shared Free/Busy calendar information.

Minimal hybrid migration is great for organizations that need to take more time to migrate their mailboxes to Office 365, but still plan to complete the
migration within a few weeks. You get some benefits of the more advanced full hybrid migration without many of the complexities. You can control how many, and
which, mailboxes are migrated at a given time; Office 365 mailboxes will be created with the username and passwords of their on-premises accounts; and,
unlike cutover migrations, your users won't need to recreate their Outlook profiles.

If you're thinking about doing minimal hybrid migration, here are a few things to consider:

- You'll need to perform a one-time directory synchronization between your on-premises Active Directory servers and Office 365;
- Users will be able to log in to their Office 365 mailbox using the same username and password they were using when their mailbox was migrated;
- You'll need an Office 365 license that includes Lync Online for each user mailbox you migrate;
- Users don't need to set up a new Outlook profile on most of their devices (some older Android phones might need a new profile) and won't need to re-download their email.

To learn more about minimal hybrid migration, take a look at [Use Minimal Hybrid to quickly migrate Lync mailboxes to Office 365](https://support.office.com/article/Use-Minimal-Hybrid-to-quickly-migrate-Lync-mailboxes-to-Office-365-fdecceed-0702-4af3-85be-f2a0013937ef)

### Full hybrid

A full hybrid migration is one where your organization has many hundreds, up to tens of thousands, of mailboxes and you want to move some or all of them to Office 365. Because these migrations are typically longer-term, hybrid migrations make it possible to:

- Show on-premises users the free/busy calendar information for users in Office 365, and vice versa;
- See a unified global address list that contains recipients in both on-premises and Office 365;
- View full Outlook recipient cards for all users, regardless of whether they're on-premises or in Office 365;
- Secure email communication between on-premises Lync servers and Office 365 using TLS and certificates;
- Treat messages sent between on-premises Lync servers and Office 365 as internal, enabling them to:
    - Be properly evaluated and processed by transport and compliance agents targeting internal messages;
    - Bypass anti-spam filters.

Full hybrid migrations are best for organizations that expect to stay in a hybrid configuration for many months or more. You'll get the features listed
earlier in this section, plus directory synchronization, better integrated compliance features, and the ability to move mailboxes to and from Office 365
using online mailbox moves. Office 365 becomes an extension of your on-premises organization.

If you're thinking about doing a full hybrid migration, here are a few things to consider:

- Full hybrid migrations aren't suited to all types of organizations. Due to the complexity of full hybrid migrations, organizations with less than a few hundred mailboxes don't typically see benefits that justify the effort and cost needed to set one up. If this sounds like your organization, we strongly recommend that you consider Cutover or Minimal hybrid migrations instead;
- You'll need to set up directory synchronization using Azure Active Directory Connect (AADConnect) between your on-premises Active Directory servers and Office 365;
- Users will be able to log in to their Office 365 mailbox using the same username and password they use when they log into the local network (requires Azure Active Directory Connect with password synchronization and/or Active Directory Federation Services);
- You'll need an Office 365 license that includes Lync Online for each user mailbox you migrate;
- Users don't need to set up a new Outlook profile on most of their devices (some older Android phones might need a new profile) and won't need to re-download their email.

> [!IMPORTANT]
> If your organization chooses to migrate mailboxes to Office 365 but intends to keep DirSync or Azure AD Connect in place to continue managing user accounts from on-premises Active Directory, you need to keep at least one Lync server on-premises. If the last Lync server is removed, you won’t be able to make changes to Lync recipients in Lync Online. This is because the source of authority remains in your on-premises Active Directory and changes need to be made there.

If a full hybrid migration sounds right for you, take a look at the following resources to help you with your migration:

- [Lync Deployment Assistant](https://aka.ms/exdeploy)
- [Lync Server Hybrid Deployments](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx)
- [Hybrid Configuration wizard](https://technet.microsoft.com/library/hh529921%28v=exchg.150%29.aspx)
- [Hybrid Configuration wizard FAQs](https://technet.microsoft.com/library/mt488940%28v=exchg.150%29.aspx)
- [Hybrid deployment prerequisites](https://technet.microsoft.com/library/hh534377%28v=exchg.150%29.aspx)

## Upgrade to a newer version of Lync Server On-Premises

While we strongly believe that you can achieve the best value and user experience by migrating fully to Office 365, we also understand that some
organizations need to keep some Lync Servers on-premises. This could be because of regulatory requirements, to guarantee data isn't stored in a
datacenter located in another country, or it might be because you have unique settings or requirements that can’t be met in the cloud, or it could simply be
that you need Lync to manage cloud mailboxes because you still use Active Directory on-premises. In any case for which you choose or need to keep Lync
on-premises, you should ensure your Lync Server 2010 environment is upgraded to at least Lync Server 2010 or Lync Server 2015 and Lync Server 2010 is removed before the End
of Support date.

For the best experience, we recommend that you upgrade your remaining on-premises environment to Lync Server 2015. You don’t need to install Lync
Server 2010 if you want to go straight from Lync Server 2010 to Lync Server 2015.

Lync Server 2015 includes all the features and advancements included with previous releases of Lync, and it most closely matches the experience available with
Office 365 (although some features are available only in Office 365). Check out just a few of the things you've been missing out on:

| **Lync release**                     | **Features**                                                                                                                                                                                                                                         |
|------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Lync Server 2010                            | Simplified architecture reducing the number of server roles to three (Mailbox, Client Access, Edge Transport)                                                                                                                                        |
|                                          | Data loss prevention policies (DLP) that help keep sensitive information from leaking                                                                                                                                                                |
|                                          | Significantly improved Outlook Web App Experience                                                                                                                                                                                                    |
| Lync Server 2015                            | *Features from Lync Server 2010 and…*                                                                                                                                                                                                                   |
|                                          | Further simplified server roles to just Mailbox and Edge Transport                                                                                                                                                                                   |
|                                          | Improved DLP along with integration with SharePoint                                                                                                                                                                                                  |
|                                          | Improved database resilience                                                                                                                                                                                                                         |
|                                          | Online document collaboration                                                                                                                                                                                                                        |

| **Consideration**                        | **More Info**                                                                                                                                                                                                                                        |
|------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| End of support dates                     | Like Lync Server 2010, each version of Lync has its own end of support date:                                                                                                                                                                        |
|                                          | **Lync Server 2010** - October 2020                                                                                                                                                                                                                       |
|                                          | The earlier the end of support date, the sooner you'll need to perform another migration. October 2020 is a lot closer than you think!                                                                                                                 |
| Migration path to Lync Server 2010 or 2015  | The migration path from Lync Server 2010 to a newer version is the same whether you choose Lync Server 2010 or Lync Server 2015:                                                                                                                              |
|                                          | Install Lync Server 2015 into your existing Lync Server 2010 organization Move services and other infrastructure to Lync Server 2015 Move mailboxes and public folders to Lync Server 2015 Decommission remaining Lync Server 2010 servers  |
| Version coexistence                      | When migrating to Lync Server 2010 or Lync Server 2015, you can install either version into an existing Lync Server 2010 organization. This enables you to install one or more Lync Server 2010 or Lync Server 2015 servers and perform your migration.             |
| Server hardware                          | Server hardware requirements have changed from Lync Server 2010. You'll need to make sure the hardware you're going to use is compatible. You can find out more about hardware requirements for each version here:                                      |
|                                          | [Lync Server 2015 System Requirements](https://technet.microsoft.com/library/aa996719%28v=exchg.160%29.aspx)                                                                                                                                      |
|                                          | [Lync Server 2010 System Requirements](https://technet.microsoft.com/library/aa996719%28v=exchg.150%29.aspx)                                                                                                                                      |
|                                          | You'll find that with the significant improvements in Lync performance, and the increased computing power and storage capacity in newer servers, you'll likely need fewer servers to support the same number of mailboxes.                       |
| Operating system version                 | The minimum supported operating system versions for each version are:                                                                                                                                                                                |
|                                          | **Lync Server 2015** Windows Server 2012                                                                                                                                                                                                                |
|                                          | **Lync Server 2010** Windows Server 2008 R2 SP1                                                                                                                                                                                                         |
|                                          | You can find more information about operating system support at [Lync Supportability Matrix](https://technet.microsoft.com/library/ff728623%28v=exchg.150%29.aspx).                                                                        |
| Active Directory forest functional level | The minimum supported Active Directory forest functional levels for each version are:                                                                                                                                                                |
|                                          | **Lync Server 2015** Windows Server 2008 R2 SP1                                                                                                                                                                                                         |
|                                          | **Lync Server 2010** Windows Server 2003                                                                                                                                                                                                                |
|                                          | You can find more information about forest functional level support at [Lync Supportability Matrix](https://technet.microsoft.com/library/ff728623%28v=exchg.150%29.aspx).                                                                 |
| Office client versions                   | The minimum supported Office client versions for each version are:                                                                                                                                                                                   |
|                                          | **Lync Server 2015** Office 2010 (with the latest updates)                                                                                                                                                                                              |
|                                          | **Lync Server 2010** Office 2007 SP3                                                                                                                                                                                                                    |
|                                          | You can find more information about Office client support at [Lync Supportability Matrix](https://technet.microsoft.com/library/ff728623%28v=exchg.150%29.aspx).                                                                           |

You can use the following resources to help you with your migration:

- [Lync Deployment Assistant](https://aka.ms/exdeploy)
- Active Directory schema changes for Lync [2015](https://technet.microsoft.com/library/bb738144%28v=exchg.160%29.aspx), [2010](https://technet.microsoft.com/library/bb738144%28v=exchg.150%29.aspx)
- System requirements for Lync [2015](https://technet.microsoft.com/library/aa996719%28v=exchg.160%29.aspx), [2010](https://technet.microsoft.com/library/aa996719%28v=exchg.150%29.aspx)
- Prerequisites for Lync [2015](https://technet.microsoft.com/library/bb691354%28v=exchg.160%29.aspx), [2010](https://technet.microsoft.com/library/bb691354%28v=exchg.150%29.aspx)

## Summary of options for Office 2010 client and servers and Windows 7

For a visual summary of the upgrade, migrate, and move-to-the-cloud options for Office 2010 clients and servers and Windows 7, see the [end of support poster](./media/upgrade-from-office-2010-servers-and-products/Office2010Windows7EndOfSupport.pdf).

![](./media/upgrade-from-office-2010-servers-and-products/office2010-windows7-end-of-support.png)

This one-page poster is a quick way to understand the various paths you can take to prevent Office 2010 client and server products and Windows 7 from reaching end of support, with preferred paths and option support in Microsoft 365 Enterprise highlighted.

You can also [download](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/enterprise/media/migration-microsoft-365-enterprise-workload/Office2010Windows7EndOfSupport.pdf) this poster and print it in letter, legal, or tabloid (11 x 17) formats.
      
## What if I need help?

If you're migrating to Office 365, you might be eligible to use our Microsoft FastTrack service. FastTrack provides best practices, tools, and resources to
make your migration to Office 365 as seamless as possible. Best of all, you'll have a real support engineer that will walk you through your migration, from
planning and design all the way to migrating your last mailbox. If you want to know more about FastTrack, take a look at [Microsoft FastTrack](https://fasttrack.microsoft.com/).

If you run into any problems during your migration to Office 365 and you aren't using FastTrack, or your migration to a newer version of Lync Server, we're
here to help. Here are some resources you can use:

- [Technical community](https://social.technet.microsoft.com/Forums/office/home?category=Lyncserver)
- [Customer support](https://support.microsoft.com/gp/support-options-for-business)

## Related topics

[Resources to help you upgrade from Office 2010 servers and clients](https://docs.microsoft.com/office365/enterprise/upgrade-from-office-2010-servers-and-products)

[Office Retirement Group (Microsoft Tech Community)](https://go.microsoft.com/fwlink/?linkid=842065)
