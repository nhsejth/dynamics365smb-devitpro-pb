---
title: Migrate to Business Central online from on-premises
description: Learn how to migrate to the cloud from Business Central on-premises using an assisted setup guide in Business Central online.

author: jenolson
ms.service: dynamics365-business-central
ms.topic: conceptual
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.reviewer: edupont
ms. search.keywords: cloud, edge,
ms.date: 11/23/2021
ms.author: edupont

---

# Migrate to Business Central Online from Business Central On-premises

Your [!INCLUDE [prod_short](../developer/includes/prod_short.md)] on-premises solution can have an identical twin in a [!INCLUDE [prod_short](../developer/includes/prod_short.md)] online tenant. Use this twin to migrate to the cloud. The migration can be started quite easily from the assisted setup wizard in your on-premises solution.  

> [!NOTE]
> [!INCLUDE [bc-cloud-versions](../includes/bc-cloud-versions.md)] Alternatively, you can upgrade to the current version and then migrate to the cloud. For more information, see [Supported Upgrade Paths to Business Central Releases](../upgrade/upgrade-paths.md).

To verify that you are running on a version that supports this migration, in the [!INCLUDE [prodadmincenter](../developer/includes/prodadmincenter.md)], open the environment that you intend to migrate your data to, and then choose the **Apps** action. Make sure that these apps have the latest updates installed:

* Intelligent Cloud Base
* Business Central Intelligent Cloud

If you are migrating from an earlier supported version, you must also make sure that the following apps are updated:

* Business Central Cloud Migration – Previous Release
* Business Central Cloud Migration – Previous Release [code for your country-specific version]

For more information, see [Managing Apps](tenant-admin-center-manage-apps.md).  

## Manage the migration

[!INCLUDE [2021_releasewave2](../includes/2021_releasewave2.md)]

Once you have set up the connection between your [!INCLUDE [prod_short](../includes/prod_short.md)] on-premises deployment and [!INCLUDE [prod_short](../includes/prod_short.md)] online, you can manage your cloud data migration from the **Cloud Migration Management** page in [!INCLUDE[prod_short](../developer/includes/prod_short.md)] online.  

> [!NOTE]
> To manage migrations and run the migration tool, you must have the SUPER permission set in [!INCLUDE [prod_short](../includes/prod_short.md)] and be an administrator of the Microsoft 365 tenant.

The migration process starts when you run the **Set up Cloud Migration** assisted setup guide in [!INCLUDE [prod_short](../includes/prod_short.md)] online. In versions older than version 19, 2021 release wave 2, the process ran in a single step with few options for troubleshooting the migration.  

> [!TIP]
> We recommend that you take a backup of the target environment so that you can easily restore the environment to a specific state and time, should you want to.

The migration from [!INCLUDE[prod_short](../developer/includes/prod_short.md)] on-premises is in two separate steps:

* Data replication

  This step starts when you run the **Set up Cloud Migration** assisted setup guide in [!INCLUDE [prod_short](../includes/prod_short.md)] online. At the end of the process, you have a copy of the on-premises data in the relevant environment in [!INCLUDE [prod_short](../includes/prod_short.md)] online so that you can verify if the migration went well or not. The migration task has the status *Upgrade Pending* in the **Cloud Migration Management** page, and you can re-run the migration multiple times if you want to.  

  For example, you've run the assisted setup guide from a test company in a sandbox environment because you worry that a number of extensions might be problematic. Once the data has been replicated to the sandbox environment, you can use the troubleshooting tools in the [!INCLUDE [prodadmincenter](../developer/includes/prodadmincenter.md)], for example.
* Data upgrade

  This step starts when you choose the **Run Data Upgrade Now** action in the **Cloud Migration Management** page in [!INCLUDE [prod_short](../includes/prod_short.md)] online for the specific environment.  

  > [!WARNING]
  > Depending on your specific solution, you may have to work with the upgrade tools for some time. Make sure that no one is using either the existing on-premises solution or the new online environment until the data upgrade is complete.

  Once you have chosen this action, both the **Run Migration Now** and the **Run Data Upgrade Now** action can no longer be used for this company in the environment. If the upgrade has failed, you must start over. You can start the cloud migration in another environment, or you can restore the current environment from a backup from a point in time before the data upgrade. Alternatively, delete all companies in the current environment and start the migration again.

  If you want to migrate more companies, disable the migration, and start the setup again.  

> [!IMPORTANT]
> Do not run the cloud migration in an environment that is currently used in production. Either the data replication or the data upgrade can result in the loss of data that is database-specific, such as media content, since the data in that table will be replaced with the data from the table in the on-premises database. Any records that exist only in the online database will be lost.

### Testing the migration

To help you test the migration, you can run the data replication step in the target production environment, and then create a sandbox environment based on this production environment. That way, you run the data upgrade step in the sandbox environment for safe testing before you run the data upgrade step in the production environment.  

> [!IMPORTANT]
> If you create a sandbox environment that is a copy of the production environment, do not run the replication in the sandbox. Always run the data replication in the environment that you plan to use for production, and then create a new sandbox copy.

## Migrating data from extensions

When your on-premises solution is connected to the cloud, it is highly recommended that you test the impact of any extension in a sandbox environment before you install the extensions in your [!INCLUDE[prod_short](../developer/includes/prod_short.md)] production environment to help avoid any data failures or unintended consequences.  

> [!TIP]
> Starting with 2021 release wave 2 (version 19), the migration from [!INCLUDE[prod_short](../developer/includes/prod_short.md)] on-premises is in two separate steps, which gives you better options to test the migration in a sandbox environment before you migrate to the final production environment. For more information, see the [Manage the migration](#manage-the-migration) section.

In order to support data migration, tables and table extensions must specify if data from that table must be migrated or not. By default, the **ReplicateData** property is set to *Yes* so that, by default, any extension that is installed in the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] online environment will have all its tables migrated.  

In certain circumstances, you may want to not migrate all data. Here are a few examples:

* The extension is installed in the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] online environment but not in the [!INCLUDE [prod_short](../developer/includes/prod_short.md)] on-premises solution

    In this case, [!INCLUDE[prod_short](../developer/includes/prod_short.md)] will attempt to migrate the data but show a warning. Since the extension is not installed on-premises, any table related to that extension table will not migrate, and warning notifications will appear in the cloud migration status page.

    If you own the extension, we recommend that you set the **ReplicateData** property to *No* on the extension tables. If you do not, and if you want data to migrate, install the extension in both [!INCLUDE[prod_short](../developer/includes/prod_short.md)] online and your on-premises solution. If you do not want data to migrate, uninstall the extension from the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] online environment.  

* The extension references a base table

    This can cause your base table to appear empty when you view data in your [!INCLUDE[prod_short](../developer/includes/prod_short.md)] online tenant. If that happens, uninstall the extension from your [!INCLUDE[prod_short](../developer/includes/prod_short.md)] online tenant, and then run the cloud migration process again.

> [!TIP]
> Use the **Cloud Migration Management** page to verify that data migrated correctly. [!INCLUDE [bc-cloud-migrate-tableext](../includes/bc-cloud-migrate-tableext.md)]

For more information, see [FAQ about Migrating to Business Central Online from On-Premises Solutions](faq-migrate-data.md) and [Troubleshooting Cloud Migration](migration-troubleshooting.md).  

### Data that is not migrated

During the data migration process, [!INCLUDE[prod_short](../developer/includes/prod_short.md)] does not migrate most system tables, users, and permissions.  

> [!NOTE]
> Currently, record links are not migrated because the links are associated with a user ID, and we do not migrate users from the on-premises environment to the online tenant. You can choose to [upvote this feature suggestion](https://experience.dynamics.com/ideas/idea/?ideaid=b515c246-801d-ea11-b265-0003ff68f605).

## Upgrading to a new version of [!INCLUDE [prod_short](../developer/includes/prod_short.md)]

If you upgrade to a new version of [!INCLUDE [prod_short](../developer/includes/prod_short.md)] on-premises, including a cumulative update, then you must update the extensions as well. Depending on your on-premises solution, your [!INCLUDE [prod_short](../developer/includes/prod_short.md)] online environment contains different extensions for the cloud migration. For more information, see [Business Central Cloud Migration Extensions](/dynamics365/business-central/ui-extensions-data-replication?toc=/dynamics365/business-central/dev-itpro/toc.json).  

> [!IMPORTANT]
> In [!INCLUDE [prod_short](../developer/includes/prod_short.md)] online, install, publish, or upgrade the **Intelligent Cloud Base** extension first, and then the product-specific extension or extensions.

Also, at the end of the upgrade, you must make sure that the `applicationVersion` field in the `ndo$tenantdatabaseproperty` table is set to the right version. If the field is blank, or if it is set to an older version than the migration tool supports, the migration cannot run. For more information, see [Post-upgrade tasks](../upgrade/upgrade-unmodified-application-v14-v17.md#post-upgrade-tasks).  

## See also

[Best Practices for Cloud Migration](migrate-data.md#best-practices)  
[Migration On-premises Data to Business Central online](migrate-data.md)  
[Migrate to the Cloud from On-Premises](./migration-tool.md)  
[Managing your Online Environment](./migration-management.md)  
[ReplicateData Property](../developer/properties/devenv-replicatedata-property.md)  
[Intelligent Insights with Business Central Online](/dynamics365/business-central/about-intelligent-cloud)  
[Migrate Legacy Help to the [!INCLUDE[prod_long](../developer/includes/prod_long.md)] Format](../upgrade/migrate-help.md)  
[Upgrading from Dynamics NAV to Business Central Online](../upgrade/Upgrade-Considerations.md#online)  
[Important Information and Considerations for Before Upgrading to [!INCLUDE[prod_long](../developer/includes/prod_long.md)] Spring 2019](../upgrade/Upgrade-Considerations.md)