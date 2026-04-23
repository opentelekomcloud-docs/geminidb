:original_name: BatchUpgradeDbVersion.html

.. _BatchUpgradeDbVersion:

Patching Databases In Batches
=============================

Function
--------

This API is used to patch databases in batches.

Constraints
-----------

-  This API supports the following types of instances:

   -  GeminiDB Cassandra
   -  GeminiDB Influx

-  Upgrade is triggered immediately, so patch databases during off-peak hours.

URI
---

POST https://{Endpoint}/v3/{project_id}/instances/db-upgrade

.. table:: **Table 1** URI parameters

   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                    |
   +============+===========+========+================================================================================================================+
   | project_id | Yes       | String | Project ID of a tenant in a region. To obtain this value, see :ref:`Obtaining a Project ID <nosql_projectid>`. |
   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +--------------+-----------+--------+---------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                         |
   +==============+===========+========+=====================================================================+
   | Content-Type | Yes       | String | MIME type of the request body. **application/json** is recommended. |
   +--------------+-----------+--------+---------------------------------------------------------------------+
   | X-Auth-Token | Yes       | String | User token                                                          |
   +--------------+-----------+--------+---------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   +--------------+-----------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type             | Description                                                                                                                                   |
   +==============+===========+==================+===============================================================================================================================================+
   | instance_ids | Yes       | Array of strings | IDs of instances where databases need to be patched. Up to 10 IDs of an instance of the same GeminiDB engine type can be specified at a time. |
   +--------------+-----------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

Status code: 202

.. table:: **Table 4** Response body parameters

   +-----------------+---------------------------------------------------------------------+----------------------+
   | Parameter       | Type                                                                | Description          |
   +=================+=====================================================================+======================+
   | upgrade_results | :ref:`Array of objects <batchupgradedbversion__table1235216577419>` | Batch upgrade result |
   +-----------------+---------------------------------------------------------------------+----------------------+

.. _batchupgradedbversion__table1235216577419:

.. table:: **Table 5** UpgradeResult

   +---------------+--------+----------------------------------------------------------------------------------+
   | Parameter     | Type   | Description                                                                      |
   +===============+========+==================================================================================+
   | job_id        | String | Task ID returned only when a patch installation task is successfully submitted   |
   +---------------+--------+----------------------------------------------------------------------------------+
   | instance_id   | String | Instance ID                                                                      |
   +---------------+--------+----------------------------------------------------------------------------------+
   | error_code    | String | Error code returned only when a patch installation task fails to be submitted    |
   +---------------+--------+----------------------------------------------------------------------------------+
   | error_message | String | Failure cause returned only when a patch installation task fails to be submitted |
   +---------------+--------+----------------------------------------------------------------------------------+

Status code: 400

.. table:: **Table 6** Response body parameters

   ========== ====== =============
   Parameter  Type   Description
   ========== ====== =============
   error_code String Error code
   error_msg  String Error message
   ========== ====== =============

Status code: 500

.. table:: **Table 7** Response body parameters

   ========== ====== =============
   Parameter  Type   Description
   ========== ====== =============
   error_code String Error code
   error_msg  String Error message
   ========== ====== =============

Example Requests
----------------

URI example

.. code-block:: text

   POST https://{Endpoint}/v3/619d3e78f61b4be68bc5aa0b59edcf7b/instances/db-upgrade

Example Requests

Patching databases in batches

.. code-block::

   {
      "instance_ids" : [ "046287aae57843b1a7bc61b7a8812f41in13", "3d1e04f49efa473a8c7eaf07ed7ff870in13" ]
    }

Example Responses
-----------------

Status code: 202

Accepted

.. code-block::

   {
     "upgrade_results" : [ {
       "instance_id" : "046287aae57843b1a7bc61b7a8812f41in13",
       "job_id" : "e4616470-733d-41de-a9b0-a260709293d3"
     }, {
       "instance_id" : "3d1e04f49efa473a8c7eaf07ed7ff870in13",
       "error_code" : "DBS.200011",
       "error_message" : "The status of DB instance does not allow the operation."
     } ]
   }

Status Codes
------------

See :ref:`Status Codes <nosql_status_code>`.

Error Codes
-----------

See :ref:`Error Codes <nosql_error_code>`.
