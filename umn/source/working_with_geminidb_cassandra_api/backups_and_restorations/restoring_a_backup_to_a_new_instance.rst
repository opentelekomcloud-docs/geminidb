:original_name: nosql_03_0009.html

.. _nosql_03_0009:

Restoring a Backup to a New Instance
====================================

Scenarios
---------

You can restore an existing backup to a new GeminiDB Cassandra instance.

Procedure
---------

#. :ref:`Log in to the GeminiDB console. <nosql_login>`

#. Restore a backup.

   **Method 1**

   a. On the **Instance Management** page, click the target DB instance.
   b. On the **Backups & Restorations** page, locate the target backup and click **Restore**.

   **Method 2**

   On the **Backup Management** page, locate the target backup and click **Restore**.

#. In the displayed dialog box, confirm the current instance details and restoration method and click **OK**.

   -  The default API type and DB engine version are the same as those of the original instance and cannot be changed.
   -  The system automatically calculates the minimum storage space required for restoring the new instance based on the size of the selected backup file. The storage space must be an integer multiple of 1.
   -  You need to set a new administrator password.

   -  To modify other parameters, see the description of creating DB instances of other DB engines in the *Getting Started*.

#. View the restoration results.

   A new DB instance is created using the backup data. The status of the DB instance changes from **Creating** to **Available**.

   After the restoration, the system will perform a full backup.

   The new DB instance is independent from the original one.
