---
title: Upgrade MariaDB 10.0 to 10.2 for Adobe Commerce on cloud
description: MariaDB 10.0 and 10.1 are end-of-life (EOL). [Support ended 31 Mar 2019 and 17 Oct 2020 respectively](https://endoflife.date/mariadb). This article explains how to upgrade MariaDB from 10.0 to 10.2 or 10.2 to 10.3 or to 10.4, in order to use Adobe Commerce on cloud infrastructure.
exl-id: bf66798b-f05c-482f-a2b4-b9bef92b0bab
feature: Best Practices, Cloud
---
# Upgrade MariaDB 10.0 to 10.2 for Adobe Commerce on cloud

MariaDB 10.0 and 10.1 are end-of-life (EOL). [Support ended 31 Mar 2019 and 17 Oct 2020 respectively](https://endoflife.date/mariadb). This article explains how to upgrade MariaDB from 10.0 to 10.2 or 10.2 to 10.3 or to 10.4, in order to use Adobe Commerce on cloud infrastructure.

>[!NOTE]
>
>MariaDB 10.0 is end-of-life (EOL) and is not supported in current Adobe Commerce versions. It is best practice to move off any EOL version within 30 days of its EOL.

## Affected product and versions

* MariaDB 10.2 is recommended for Adobe Commerce on cloud infrastructure 2.3.x.
* MariaDB 10.4 is recommended for 2.4.x. MariaDB 10.3 is also compatible with Adobe Commerce on cloud infrastructure 2.4.x.

## Upgrade steps

To upgrade from MariaDB 10.0 to 10.2 or 10.2 to 10.3 or to 10.4, complete the following steps:

1. Create a [DB backup using ECE-Tools DB backup commands](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots). This must be done before steps 2 and 3 in case something goes wrong while updating tables/rows.
1. [Check and convert all compact tables to dynamic tables](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/commerce-235-upgrade-prerequisites-mariadb.html). This is required to avoid potential data loss during the database upgrade.
1. Check for MYISAM tables. You need to [convert all MyISAM tables to InnoD](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html).
1. After you have prepared the database tables and rows (the previous two steps), create a [DB backup using ECE-Tools DB backup commands](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots).
1. [Open a support ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) to schedule the upgrade from MariaDB 10.0 to 10.2 or 10.2 to 10.3 or 10.4. In the ticket detail the date and time when you want the DB upgraded. The support team needs 48 hours' notice and the merchants dev team needs to be available. Once the time and date are agreed for the upgrade, do the following:
    1. Put your site into maintenance mode, and stop any DB activities, e.g., crons.
    1. Create a [DB backup using ECE-Tools DB backup commands](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots).
    1. Let support know you have completed the backup. Do this via your support ticket. To get steps for viewing and tracking your tickets, refer to [Adobe Commerce Help Center User Guide: Track your Tickets](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) in our support knowledge base.
    1. The Adobe Commerce support team will begin the MariaDB upgrade process. If all the above steps have been taken, and the database is average size, this can be done in about an hour. Larger DBs will take longer. You will be informed via your ticket once the upgrade is complete.
1. Disable maintenance mode. Refer to [Enable or disable maintenance mode](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) in our developer documentation.

## Related Reading

To learn more about requirements for Adobe Commerce 2.4.x, refer to [Adobe Commerce 2.4 system requirements > Database](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirements#database) in our developer documentation.
