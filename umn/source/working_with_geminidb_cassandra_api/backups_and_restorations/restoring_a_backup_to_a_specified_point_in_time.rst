:original_name: nosql_02_0116.html

.. _nosql_02_0116:

Restoring a Backup to a Specified Point in Time
===============================================

Scenarios
---------

Existing automated backups can be restored to a specified point in time on a GeminiDB Cassandra instance.

The most recent full backup will be downloaded from OBS for restoration. After the restoration is complete, incremental backups will be replayed to the specified point in time. The time required depends on the amount of data to be restored.

Usage Notes
-----------

-  This feature is available only to new GeminiDB Cassandra instances.
-  After the automated backup policy is enabled, the system performs an incremental backup based on the preset interval. The incremental backup data is stored in OBS.

-  Data can be restored to a specified time point only after the automated backup policy is enabled.
-  During instance restoration, backups are downloaded from the OBS bucket to the data directory of the restored instance.

Procedure
---------

#. :ref:`Log in to the GeminiDB console. <nosql_login>`

#. On the **Instances** page, click the target GeminiDB Cassandra instance.

#. In the navigation pane on the left, click **Backups & Restorations**.

#. On the **Backups & Restorations** page, click **Restore to Point In Time**.


   .. figure:: /_static/images/en-us_image_0000002200454268.png
      :alt: **Figure 1** Restoring data to a specified point in time

      **Figure 1** Restoring data to a specified point in time

#. Select the restoration date and the time point to which the data is restored and then click **OK**.


   .. figure:: /_static/images/en-us_image_0000002200454892.png
      :alt: **Figure 2** Restore to Point in Time

      **Figure 2** Restore to Point in Time

#. On the displayed **Create New Instance** page, create a DB instance of the same specifications as the DB instance to be restored. The new DB instance is independent from the original one.

   -  You are recommended to deploy the restored DB instance in a different AZ to ensure that your applications will not be adversely affected by the failure in any single AZ.
   -  The compatible API, DB instance type, DB instance version, and CPU type are the same as those of the original and cannot be changed.
   -  Other settings are the same as those of the original instance by default and can be modified. For details, see :ref:`Creating a GeminiDB Cassandra Instance <nosql_06_0003>`.
