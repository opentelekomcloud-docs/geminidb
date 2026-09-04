:original_name: nosql_dynamodb_0089.html

.. _nosql_dynamodb_0089:

Restoring Data to a New Instance
================================

Scenarios
---------

GeminiDB DynamoDB-Compatible API allows you to use an existing backup to restore data to a new instance.

Procedure
---------

#. :ref:`Log in to the GeminiDB console. <nosql_login>`

#. Restore a backup.

   **Method 1**

   a. On the **Instances** page, click the target instance.
   b. On the **Backups & Restorations** page, locate the target backup and click **Restore**.

   **Method 2**

   On the **Backups** page, locate the target backup and click **Restore**.

#. In the displayed dialog box, confirm the current instance details and restoration method and click **OK**.

   -  The API type and DB engine version of the new instance default to those of the original instance and cannot be changed.
   -  The system automatically calculates the minimum storage required to restore data to the new instance based on the size of the selected backup file. The storage capacity can be adjusted as required, and must be an integer multiple of 10 GB.
   -  A new administrator password must be set for the instance.

   -  To modify other parameters, refer to the instructions for creating instances of the required DB engine in *Getting Started*.

#. View the restoration results.

   A new DB instance is created using the backup data. The status of the DB instance changes from **Creating** to **Available**.

   After the restoration, the system will perform a full backup.

   The new DB instance is independent of the original one.
