:original_name: nosql_dynamodb_0083.html

.. _nosql_dynamodb_0083:

Managing Automated Backups
==========================

GeminiDB DynamoDB-Compatible API supports automated backups to ensure data reliability. If a database or table is deleted maliciously or accidentally, backups can help recover your data.

.. _nosql_dynamodb_0083__section456243921816:

Automated Backup Policy
-----------------------

Automated backups are generated according to a backup policy and saved as packages in OBS buckets to ensure data confidentiality and durability. You are advised to regularly back up your database, in case it becomes faulty or damaged. Backing up data affects read and write performance, so set the automated backup time window to off-peak hours.

An automated backup policy is enabled by default when you create an instance. The default settings are as follows:

-  **Retention Period**: Automated backups are kept for seven days by default. You can set it to 1 day to 35 days.

   .. note::

      -  If the retention period is shorter than seven days, the system automatically backs up data daily.
      -  The system checks existing automated backups and deletes any backups that exceed your specified retention period.
      -  **Time Window**: Set it to a one-hour period the backup will be scheduled, such as 01:00-02:00 or 12:00-13:00. The backup time is in GMT format. The backup time window changes with the time zone if the DST or standard time is switched.

-  **Backup Cycle**: All options are selected by default.

   -  **All**: Each day of the week is selected. The system automatically backs up data every day.
   -  You can select one or more days in a week. The system automatically backs up data on the specified days.

   .. note::

      A full backup starts within one hour of the time you specify. The backup duration depends on the volume of data. A larger volume of data requires a longer backup time.

-  After an instance is created, you can modify the automated backup policy. The system will automatically back up data based on this policy.
-  If **Automated Backup** is disabled, any automated backups in progress stop immediately.

Modifying an Automated Backup Policy
------------------------------------

#. :ref:`Log in to the GeminiDB console. <nosql_login>`

#. On the **Instances** page, click the target instance. The **Basic Information** page is displayed.

#. On the **Backups & Restorations** page, click **Modify Backup Policy**. In the displayed dialog box, set the backup policy. Then, click **Yes** to save the configuration.

   For details about how to set a backup policy, see :ref:`Automated Backup Policy <nosql_dynamodb_0083__section456243921816>`.

#. Check or manage the generated backups on the **Backups** or **Backups & Restorations** page.

Disabling Automated Backup Policy
---------------------------------

#. :ref:`Log in to the GeminiDB console. <nosql_login>`

#. On the **Instances** page, click the target instance. The **Basic Information** page is displayed.

#. On the **Backups & Restorations** page, click **Modify Backup Policy**.

#. In the displayed dialog box, click |image1| to disable the backup policy and click **Yes**.

   When disabling the automated backup policy, you can decide whether to delete the automated backups by selecting **Delete automated backups**.

   -  If you select it, all backup files within the retention period will be deleted. No automated backups are displayed in the backup list until you enable the automated backup policy again.
   -  If you do not select it, all backup files within the retention period will be retained, but you can still manually delete them later if needed. For details, see section :ref:`Deleting an Automated Backup <nosql_dynamodb_0083__section106721241354>`.

   If the automated backup policy is disabled, any automated backups in progress stop immediately.

.. _nosql_dynamodb_0083__section106721241354:

Deleting an Automated Backup
----------------------------

If the automated backup policy is disabled, you can delete stored automated backups to free up storage space.

If the automated backup policy is enabled, the system will delete automated backups as they expire. You cannot delete them.

.. important::

   The deletion operation is irreversible, so exercise caution when performing this operation.

-  **Method 1**

   #. On the **Instances** page, click the target instance. The **Basic Information** page is displayed.
   #. On the **Backups & Restorations** page, locate the backup you wish to delete and click **Delete**.
   #. In the **Delete Backup** dialog box, confirm the backup information and click **Yes**.

-  **Method 2**

   #. On the **Backups** page, locate the target backup and click **Delete**.
   #. In the **Delete Backup** dialog box, confirm the backup information and click **Yes**.

.. |image1| image:: /_static/images/en-us_image_0000002417434784.png
