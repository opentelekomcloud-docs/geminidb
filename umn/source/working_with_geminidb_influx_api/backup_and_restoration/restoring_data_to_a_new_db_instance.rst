:original_name: nosql_09_0049.html

.. _nosql_09_0049:

Restoring Data to a New DB Instance
===================================

Scenarios
---------

GeminiDB Influx API allows you to restore the existing backup to a new DB instance.

Procedure
---------

#. :ref:`Log in to the GeminiDB console. <nosql_login>`

#. Restore a DB instance from the backup.

   **Method 1**

   a. On the **Instances** page, click the target instance.
   b. On the **Backups & Restorations** page, locate the target backup and click **Restore**.

   **Method 2**

   On the **Backups** page, locate the target backup and click **Restore**.

#. In the displayed dialog box, confirm the current instance details and restoration method and click **OK**.

   -  The default API type and DB engine version are the same as those of the original instance and cannot be changed.
   -  The system automatically calculates the minimum storage space required for restoring the new instance based on the size of the selected backup file. The storage space must be an integer multiple of 1.
   -  You need to set a new administrator password.

   -  You can modify other parameters. For details, see :ref:`Creating a GeminiDB Influx Instance <nosql_02_0051>`.

#. View the restoration results.

   A new DB instance is created using the backup data. The instance status changes from **Creating** to **Available**.

   A full backup is triggered after the new DB instance is created.

   The new DB instance is independent of the original one.
