:original_name: nosql_03_0216.html

.. _nosql_03_0216:

Recycling an Instance
=====================

Usage Notes
-----------

-  If an instance is abnormal, it will not be moved to the recycle bin after being deleted.
-  The recycle bin is enabled by default and cannot be disabled. Instances in the recycle bin can be retained for 7 days by default. This function is free of charge.
-  Operations after an instance is deleted

   -  If there are fewer than 100 backups (including automated full backups) in the recycle bin, the system retains the automated full backup from one day prior if available; otherwise, the latest one is retained. The system will also generate a new full backup. You can select one of the backups to rebuild the instance.

   -  If there are 100 or more backups (including automated full backups) in the recycle bin, the system retains the automated full backup from one day prior if available; otherwise, the latest one is retained. You can select this backup to rebuild the instance.

Modifying the Recycling Policy
------------------------------

.. important::

   You can modify the retention period, and the changes only apply to the DB instances deleted after the changes, so exercise caution when performing this operation.

#. :ref:`Log in to the GeminiDB console. <nosql_login>`
#. On the **Recycle Bin** page, click **Modify Recycling Policy**. In the displayed dialog box, set the retention period (range: 1 to 7 days) for the deleted instances. Then, click **OK**.

Rebuilding a DB Instance
------------------------

Within the retention period, you can rebuild an instance from its backup.

#. :ref:`Log in to the GeminiDB console. <nosql_login>`
#. On the **Recycle Bin** page, locate the target instance and click **Rebuild** in the **Operation** column.
#. On the displayed page, set required parameters and submit the rebuilding task.
