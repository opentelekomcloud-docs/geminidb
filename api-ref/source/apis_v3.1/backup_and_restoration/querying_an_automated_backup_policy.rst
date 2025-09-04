:original_name: nosql_api_0030.html

.. _nosql_api_0030:

Querying an Automated Backup Policy
===================================

Function
--------

This API is used to query an automated backup policy.

Constraints
-----------

This API can be used for GeminiDB Cassandra instances.

URI
---

GET https://{Endpoint}/v3.1/{project_id}/instances/{instance_id}/backups/policy

.. table:: **Table 1** URI parameters

   +-------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                                    |
   +=============+===========+========+================================================================================================================+
   | project_id  | Yes       | String | Project ID of a tenant in a region. To obtain this value, see :ref:`Obtaining a Project ID <nosql_projectid>`. |
   +-------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Instance ID.                                                                                                   |
   +-------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query parameters

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                   |
   +=================+=================+=================+===============================================================================================+
   | type            | No              | String          | Backup policy type. This parameter is available only to GeminiDB Cassandra. The value can be: |
   |                 |                 |                 |                                                                                               |
   |                 |                 |                 | -  **Instance**, indicating that an instance backup is queried.                               |
   |                 |                 |                 | -  **DatabaseTable**, indicating that a database or table backup is queried.                  |
   |                 |                 |                 | -  The default value is **Instance**.                                                         |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameter

   ============ ========= ====== ===========
   Parameter    Mandatory Type   Description
   ============ ========= ====== ===========
   X-Auth-Token Yes       String User token.
   ============ ========= ====== ===========

Response Parameters
-------------------

Status code: 200

.. table:: **Table 4** Response body parameter

   +---------------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter     | Type   | Description                                                                                                                                                       |
   +===============+========+===================================================================================================================================================================+
   | backup_policy | object | Backup policy objects, including backup retention period (days) and start time For details, see :ref:`Table 5 <nosql_api_0030__response_showbackuppolicyresult>`. |
   +---------------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _nosql_api_0030__response_showbackuppolicyresult:

.. table:: **Table 5** ShowBackupPolicyResult

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                              |
   +=======================+=======================+==========================================================================================================================+
   | keep_days             | Integer               | Backup retention days.                                                                                                   |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+
   | differential_period   | String                | Differential backup interval. Interval for automated differential backups.                                               |
   |                       |                       |                                                                                                                          |
   |                       |                       | Its value can be **30**, **60**, **180**, **360**, **720**, or **1440**.                                                 |
   |                       |                       |                                                                                                                          |
   |                       |                       | Unit: minute                                                                                                             |
   |                       |                       |                                                                                                                          |
   |                       |                       | Example value: **30**                                                                                                    |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+
   | incremental_period    | String                | Incremental backup interval, in minutes. Its value can be **5**, **10**, or **15**.                                      |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+
   | start_time            | String                | Backup time window. Automated backup will be triggered during the backup time window.                                    |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+
   | period                | String                | Backup period. After a backup period is specified, data will be automatically backed up on the selected days every week. |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

URI example

.. code-block:: text

   GET https://{Endpoint}/v3.1/375d8d8fad1f43039e23d3b6c0f60a19/instances/9136fd2a9fcd405ea4674276ce36dae8in02/backups/policy?type=Instance

Example Response
----------------

Status code: 200

Successful request

Response when an automated backup policy is enabled

.. code-block::

   {
     "backup_policy" : {
       "keep_days" : 7,
       "start_time" : "19:00-20:00",
       "period" : "1,2,4,5,6"
       "incremental_period": null,
       "differential_period": null
     }
   }

Response when an automated backup policy is disabled

.. code-block::

Status Codes
------------

See :ref:`Status Codes <nosql_status_code>`.

Error Codes
-----------

See :ref:`Error Codes <nosql_error_code>`.
