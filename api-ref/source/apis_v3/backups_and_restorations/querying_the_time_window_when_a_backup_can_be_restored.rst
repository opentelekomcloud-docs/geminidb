:original_name: ListRestoreTime.html

.. _ListRestoreTime:

Querying the Time Window When a Backup Can Be Restored
======================================================

Function
--------

This API is used to query the time window when a backup can be restored.

Constraints
-----------

This API supports the following types of instances:

-  GeminiDB Cassandra

Make sure that full backup, incremental backup, and automated backup have been enabled. To enable incremental backup, contact customer service. This function can be used only when the next automated backup is performed.

This API can be used to query the time point that a backup can be restored to, so values of **start_time** and **end_time** are the same.

URI
---

GET https://{Endpoint}/v3/{project_id}/instances/{instance_id}/backups/restorable-time-periods

.. table:: **Table 1** URI parameters

   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                                                                                                                                                                         |
   +=============+===========+========+=====================================================================================================================================================================================================================================================+
   | project_id  | Yes       | String | Project ID of a user in a region. To obtain this value, see :ref:`Obtaining a Project ID <nosql_projectid>`.                                                                                                                                        |
   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Instance ID, which can be obtained by calling the API described in :ref:`Querying Instances and Details <nosql_05_0016>`. If there are no instances available, call the API described in :ref:`Creating an Instance <nosql_05_0014>` to create one. |
   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query parameters

   +------------+-----------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type    | Description                                                                                                                                                                          |
   +============+===========+=========+======================================================================================================================================================================================+
   | start_time | No        | String  | Start time point that the backup can be restored to. The time point is in the yyyy-mm-ddThh:mm:ssZ format. **T** indicates the start time, and **Z** indicates the time zone offset. |
   +------------+-----------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | end_time   | No        | String  | End time point that the backup can be restored to. The time point is in the yyyy-mm-ddThh:mm:ssZ format. **T** indicates the start time, and **Z** indicates the time zone offset.   |
   +------------+-----------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | offset     | No        | Integer | Offset. The records after this offset will be queried. The default value is **0**.                                                                                                   |
   +------------+-----------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit      | No        | Integer | Maximum number of records displayed on each page. The value ranges from **0** to **1000**. The default value is **1000**.                                                            |
   +------------+-----------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-------------------------+-----------------------------------------------------------------------------------+---------------------------------------------------+
   | Parameter               | Type                                                                              | Description                                       |
   +=========================+===================================================================================+===================================================+
   | total_count             | Integer                                                                           | Total time windows when a backup can be restored. |
   +-------------------------+-----------------------------------------------------------------------------------+---------------------------------------------------+
   | restorable_time_periods | Array of :ref:`restorableTime <listrestoretime__response_restorabletime>` objects | Time windows when a backup can be restored.       |
   +-------------------------+-----------------------------------------------------------------------------------+---------------------------------------------------+

.. _listrestoretime__response_restorabletime:

.. table:: **Table 5** restorableTime

   +------------+------+--------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Type | Description                                                                                                              |
   +============+======+==========================================================================================================================+
   | start_time | Long | Start time of the restoration time range in the UNIX timestamp format. The start time is the UTC time in milliseconds.   |
   +------------+------+--------------------------------------------------------------------------------------------------------------------------+
   | end_time   | Long | End time point of the restoration time range in the UNIX timestamp format. The end time is the UTC time in milliseconds. |
   +------------+------+--------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

-  URI example

   .. code-block:: text

      GET https://{Endpoint}/v3/054e292c9880d4992f02c0196d3ea468/instances/a4d8ea2584e047439a667703c0684119in06/backups/restorable-time-periods?start_time=2022-06-01T18:50:20+0800&end_time=2022-06-01T19:50:20+0800&offset=0&limit=1000

Example Response
----------------

**Status code: 200**

Success

.. code-block::

   {
     "total_count" : 1,
     "restorable_time_periods" : [ {
       "start_time" : 1607731200000,
       "end_time" : 1607731200000
     } ]
   }

Status Codes
------------

See :ref:`Status Codes <nosql_status_code>`.

Error Codes
-----------

See :ref:`Error Codes <nosql_error_code>`.
