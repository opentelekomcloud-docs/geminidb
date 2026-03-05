:original_name: nosql_09_0040.html

.. _nosql_09_0040:

Key Operations Recorded by CTS
==============================

With CTS, you can record GeminiDB key operations for later query, audit, and backtracking.

:ref:`Table 1 <nosql_09_0040__en-us_topic_0249811401_en-us_topic_0108439405_table7128270172415>` lists the key operations that can be recorded by CTS.

.. _nosql_09_0040__en-us_topic_0249811401_en-us_topic_0108439405_table7128270172415:

.. table:: **Table 1** GeminiDB Influx key operations

   +----------------------------------------+----------------+-----------------------------------+
   | Operation                              | Resource       | Trace Name                        |
   +========================================+================+===================================+
   | Creating a DB instance                 | instance       | NoSQLCreateInstance               |
   +----------------------------------------+----------------+-----------------------------------+
   | Deleting a DB instance                 | instance       | NoSQLDeleteInstance               |
   +----------------------------------------+----------------+-----------------------------------+
   | Adding nodes                           | instance       | NoSQLEnlargeInstance              |
   +----------------------------------------+----------------+-----------------------------------+
   | Restarting a DB instance               | instance       | NoSQLRestartInstance              |
   +----------------------------------------+----------------+-----------------------------------+
   | Restoring data to new DB instances     | instance       | NoSQLRestoreNewInstance           |
   +----------------------------------------+----------------+-----------------------------------+
   | Scaling up storage space               | instance       | NoSQLExtendInstanceVolume         |
   +----------------------------------------+----------------+-----------------------------------+
   | Resetting a password                   | instance       | NoSQLResetPassword                |
   +----------------------------------------+----------------+-----------------------------------+
   | Changing DB instance names             | instance       | NoSQLRenameInstance               |
   +----------------------------------------+----------------+-----------------------------------+
   | Changing a DB instance class           | instance       | NoSQLResizeInstance               |
   +----------------------------------------+----------------+-----------------------------------+
   | Binding an EIP                         | instance       | NoSQLBindEIP                      |
   +----------------------------------------+----------------+-----------------------------------+
   | Unbinding an EIP                       | instance       | NoSQLUnBindEIP                    |
   +----------------------------------------+----------------+-----------------------------------+
   | Creating a backup                      | backup         | NoSQLCreateBackup                 |
   +----------------------------------------+----------------+-----------------------------------+
   | Deleting a backup                      | backup         | NoSQLDeleteBackup                 |
   +----------------------------------------+----------------+-----------------------------------+
   | Setting a backup policy                | backup         | NoSQLSetBackupPolicy              |
   +----------------------------------------+----------------+-----------------------------------+
   | Adding an instance tag                 | tag            | NoSQLAddTags                      |
   +----------------------------------------+----------------+-----------------------------------+
   | Modifying an instance tag              | tag            | NoSQLModifyInstanceTag            |
   +----------------------------------------+----------------+-----------------------------------+
   | Deleting an instance tag               | tag            | NoSQLDeleteInstanceTag            |
   +----------------------------------------+----------------+-----------------------------------+
   | Creating a parameter template          | parameterGroup | NoSQLCreateConfigurations         |
   +----------------------------------------+----------------+-----------------------------------+
   | Modifying a parameter template         | parameterGroup | NoSQLUpdateConfigurations         |
   +----------------------------------------+----------------+-----------------------------------+
   | Modifying instance parameters          | parameterGroup | NoSQLUpdateInstanceConfigurations |
   +----------------------------------------+----------------+-----------------------------------+
   | Replicating a parameter template       | parameterGroup | NoSQLCopyConfigurations           |
   +----------------------------------------+----------------+-----------------------------------+
   | Resetting a parameter template         | parameterGroup | NoSQLResetConfigurations          |
   +----------------------------------------+----------------+-----------------------------------+
   | Applying a parameter template          | parameterGroup | NoSQLApplyConfigurations          |
   +----------------------------------------+----------------+-----------------------------------+
   | Deleting a parameter template          | parameterGroup | NoSQLDeleteConfigurations         |
   +----------------------------------------+----------------+-----------------------------------+
   | Deleting nodes that failed to be added | instance       | NoSQLDeleteEnlargeFailNode        |
   +----------------------------------------+----------------+-----------------------------------+
   | Enabling SSL                           | instance       | NoSQLSwitchSSL                    |
   +----------------------------------------+----------------+-----------------------------------+
   | Changing a security group              | instance       | NoSQLModifySecurityGroup          |
   +----------------------------------------+----------------+-----------------------------------+
   | Modifying the recycling policy         | instance       | NoSQLModifyRecyclePolicy          |
   +----------------------------------------+----------------+-----------------------------------+
   | Exporting a parameter template         | instance       | NoSQLSaveConfigurations           |
   +----------------------------------------+----------------+-----------------------------------+
