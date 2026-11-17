:original_name: nosql_03_0201.html

.. _nosql_03_0201:

Recycle Bin
===========

You can move backups of deleted GeminiDB Cassandra instances to the recycle bin, so you can restore them if necessary.

Usage Notes
-----------

-  If an instance is abnormal, its backups will not be moved to the recycle bin after the instance is deleted.
-  The recycle bin is enabled by default and cannot be disabled. The default retention period of backups in the recycle bin is seven days. This function is free of charge.
-  Operations after an instance is deleted

   -  If there are fewer than 100 backups (including automated full backups) in the recycle bin, the system retains the automated full backup from one day prior if available; otherwise, the latest one is retained. The system will also generate a new full backup. You can select one of the backups to rebuild the instance.

   -  If there are 100 or more backups (including automated full backups) in the recycle bin, the system retains the automated full backup from one day prior if available; otherwise, the latest one is retained. You can select this backup to rebuild the instance.

Modifying the Recycling Policy
------------------------------

.. important::

   A new recycling policy only applies to backups that were moved to the recycle bin after the new policy was put into effect. For backups that were moved to the recycle bin before the modification, the original recycling policy takes effect.

#. :ref:`Log in to the GeminiDB console <nosql_login>`.
#. On the **Recycle Bin** page, click **Modify Recycling Policy**. In the displayed dialog box, set the retention period (range: 1 to 7 days) for the deleted instance backups. Then, click **OK**.

Rebuilding a DB instance
------------------------

Within the retention period, you can rebuild an instance from its backup.

#. :ref:`Log in to the GeminiDB console. <nosql_login>`
#. On the **Recycle Bin** page, locate the backup to be rebuilt and click **Rebuild** in the **Operation** column.
#. On the displayed page, set required parameters and submit the rebuilding task.
