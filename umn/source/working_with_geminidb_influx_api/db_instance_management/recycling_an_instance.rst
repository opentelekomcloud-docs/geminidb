:original_name: nosql_03_0216.html

.. _nosql_03_0216:

Recycling an Instance
=====================

After a GeminiDB Influx instance is deleted, its backups are automatically moved to the recycle bin. To restore data, you can :ref:`rebuild the instance <nosql_03_0216__en-us_topic_0272078401_section927612820223>` from the recycle bin.

Usage Notes
-----------

-  If an instance is abnormal, its backups will not be moved to the recycle bin after the instance is deleted.
-  The recycle bin is enabled by default and cannot be disabled. The default retention period of backups in the recycle bin is seven days. This function is free of charge.
-  Operations after an instance is deleted

   -  If the instance has automated full backups, the system keeps the most recent automated full backup of the previous day. If there is no automated full backup generated on that day, it retains the latest available one and moves it to the recycle bin.
   -  If there are less than 100 backups in the recycle bin, the system will create a full backup and move it to the recycle bin.
   -  You can select one of the backups to rebuild the instance.

Modifying the Recycling Policy
------------------------------

.. important::

   Changes to the recycle bin's backup retention period apply only to backups deleted after the modification. Existing backups will follow their original retention policy.

#. :ref:`Log in to the GeminiDB console. <nosql_login>`
#. On the **Recycle Bin** page, click **Modify Recycling Policy**. In the displayed dialog box, set the backup retention period (range: 1 to 7 days) for the recycle bin. Then, click **OK**.

.. _nosql_03_0216__en-us_topic_0272078401_section927612820223:

Rebuilding a DB Instance
------------------------

Within the retention period, you can rebuild an instance from its backup.

#. :ref:`Log in to the GeminiDB console. <nosql_login>`
#. On the **Recycle Bin** page, locate the backup to be rebuilt and click **Rebuild** in the **Operation** column.
#. On the displayed page, set required parameters and submit the rebuilding task.
