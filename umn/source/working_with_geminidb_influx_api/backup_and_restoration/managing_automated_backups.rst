:original_name: nosql_09_0047.html

.. _nosql_09_0047:

Managing Automated Backups
==========================

GeminiDB Influx API creates automated backups to ensure data reliability. If a database or table is deleted, maliciously or accidentally, backups can help recover your data.

.. _nosql_09_0047__section7348925133816:

Configuring an Automated Backup Policy
--------------------------------------

Automated backups are generated according to a backup policy and saved as packages in OBS buckets to ensure data confidentiality and durability. You are advised to regularly back up your database, in case it becomes faulty or damaged. However, backing up data might affect the database read and write performance so it is recommended that you enable automated backups during off-peak hours.

When you create a DB instance, an automated backup policy is enabled by default.

-  **Retention Period**: Automated backup files are saved for seven days by default. The backup retention period can range from 1 to 35 days. Automated full backups are automatically deleted when their retention period expires.

   -  Extending the retention period enhances data durability.
   -  If you shorten the retention period, the new backup policy will apply to existing backups. Any automated backups exceeding the new retention period will be deleted immediately. Manual backups will not be deleted automatically.

   .. note::

      -  If the retention period is less than seven days, the system automatically backs up data every day.
      -  The system checks existing automated backup files and deletes the files that exceed the backup retention period you set.

-  **Backup Cycle**: By default, each day of the week is selected.

   -  **All**: Each day of the week is selected. The system automatically backs up data every day.
   -  Select a cycle: You can select one or more days in a week. The system automatically backs up data at the specified time.

   .. note::

      A full backup starts within one hour of the time you specify. The amount of time required for the backup depends on the amount of data to be backed up. The more data has to be backed up, the longer it will take.

-  **Automatic deletion policy for full backups:**

   To ensure data integrity, the automatic deletion policy always retains at least one full backup so that data within the retention period can be restored.

   For example, if **Backup Cycle** was set to **Monday** and **Wednesday** and **Retention Period** was set to **7** days, the deletion behavior is as follows:

   -  The full backup created this Monday will be automatically deleted on next Monday. The reason is as follows:

      On next Monday, the full backup created this Monday exceeds the retention period. Because this Wednesday's full backup is still retained, the requirement to retain at least one full backup is satisfied, and this Monday's full backup will be automatically deleted on that day according to the automatic deletion policy.

   -  The full backup created this Wednesday will be automatically deleted on next Wednesday. The reason is as follows:

      The full backup created this Wednesday exceeds the retention period on next Wednesday, while that created on next Monday exceeds the retention period on the Monday after next. According to the automatic deletion policy for full backups, at least one full backup must be retained. Therefore, this Wednesday's full backup is automatically deleted on next Wednesday.

      .. note::

         **Time Window**: Set it to a one-hour period during which the backup will be scheduled within 24 hours, such as **01:00-02:00** or **12:00-13:00**. The backup time is displayed in GMT. If the selected time zone switches between daylight saving time (DST) and standard time, the corresponding local backup time window changes accordingly. The backup time window indicates when the backup starts, not the duration of the entire backup task. The backup duration depends on the data volume of your instance.

-  After a DB instance is created, you can modify the automated backup policy as needed. You can change the time window after the DB instance is created. The system backs up data based on the automated backup policy you have set.

-  If **Automated Backup** is disabled, any automated backups in progress stop immediately.

Modifying the Automated Backup Policy
-------------------------------------

#. :ref:`Log in to the GeminiDB console. <nosql_login>`

#. On the **Instances** page, click the target instance name to go to the **Basic Information** page.

#. Choose **Backups & Restorations** in the navigation pane, and click **Modify Backup Policy**. In the displayed dialog box, set the backup policy. Then, click **OK** to save the configuration.

   For details about how to set a backup policy, see :ref:`Configuring an Automated Backup Policy <nosql_09_0047__section7348925133816>`.

#. Check or manage the generated backups on the **Backups** or **Backups & Restorations** page.

Disabling the Automated Backup Policy
-------------------------------------

#. :ref:`Log in to the GeminiDB console. <nosql_login>`

#. On the **Instances** page, click the target instance name to go to the **Basic Information** page.

#. Choose **Backups & Restorations** in the navigation pane, and click **Modify Backup Policy**.

#. In the displayed dialog box, click |image1| to disable **Automated Backup** and click **OK**.

   When disabling the automated backup policy, you can decide whether to delete the automated backups by selecting **Delete automated backups**.

   -  If you select it, all backup files within the retention period will be deleted. No automated backups are displayed in the backup list until you enable the automated backup policy again.
   -  If you do not select it, all backup files within the retention period will be retained, but you can still manually delete them later if needed. For details, see section :ref:`Deleting an Automated Backup <nosql_09_0047__section106721241354>`.

   If **Automated Backup** is disabled, any automated backups in progress stop immediately.

.. _nosql_09_0047__section106721241354:

Deleting an Automated Backup
----------------------------

After the automated backup policy is disabled, you can manually delete the saved automated backups to release storage.

After the automated backup policy is enabled, the system checks and automatically deletes expired automated backups. You cannot delete automated backups.

.. important::

   The deletion operation is irreversible, so exercise caution when performing this operation.

-  **Method 1**

   #. On the **Instances** page, click the target instance. The **Basic Information** page is displayed.
   #. On the **Backups & Restorations** page, locate the backup you wish to delete and click **Delete**.
   #. In the **Delete Backup** dialog box, confirm the backup information and click **Yes**.

-  **Method 2**

   #. On the **Backups** page, locate the target backup and click **Delete**.
   #. In the **Delete Backup** dialog box, confirm the backup information and click **Yes**.

.. |image1| image:: /_static/images/en-us_image_0000002450993413.png
