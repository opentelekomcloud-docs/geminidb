:original_name: nosql_api_0035.html

.. _nosql_api_0035:

Querying Instances in the Recycle Bin
=====================================

Function
--------

This API is used to query all instances in the recycle bin.

URI
---

GET https://{Endpoint}/v3/{project_id}/recycle-instances

.. table:: **Table 1** URI parameter

   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                    |
   +============+===========+========+================================================================================================================+
   | project_id | Yes       | String | Project ID of a tenant in a region. To obtain this value, see :ref:`Obtaining a Project ID <nosql_projectid>`. |
   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                      |
   +=================+=================+=================+==================================================================================================================================================================================+
   | offset          | No              | Integer         | Index offset.                                                                                                                                                                    |
   |                 |                 |                 |                                                                                                                                                                                  |
   |                 |                 |                 | -  If **offset** is set to *N*, the query starts from the *N*\ +1 piece of data. The default value is **0**, which indicates that the query starts from the first piece of data. |
   |                 |                 |                 | -  The value must be a non-negative number.                                                                                                                                      |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit           | No              | Integer         | Maximum records to be queried.                                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                                                  |
   |                 |                 |                 | -  The value ranges from **1** to **100**.                                                                                                                                       |
   |                 |                 |                 | -  If this parameter is not transferred, the first 100 records are queried by default.                                                                                           |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   ============ ========= ====== ===========
   Parameter    Mandatory Type   Description
   ============ ========= ====== ===========
   X-Auth-Token Yes       String User token
   ============ ========= ====== ===========

Response Parameters
-------------------

Status code: 200

.. table:: **Table 4** Response body parameters

   +-------------+------------------+----------------------------------------------------------------------------------------------+
   | Parameter   | Type             | Description                                                                                  |
   +=============+==================+==============================================================================================+
   | total_count | Integer          | Total number of records.                                                                     |
   +-------------+------------------+----------------------------------------------------------------------------------------------+
   | instances   | Array of objects | Instance information. For details, see :ref:`Table 5 <nosql_api_0035__table78091930141817>`. |
   +-------------+------------------+----------------------------------------------------------------------------------------------+

.. _nosql_api_0035__table78091930141817:

.. table:: **Table 5** RecycleInstance

   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                   |
   +=======================+=======================+===============================================================================================+
   | id                    | String                | Instance ID.                                                                                  |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------+
   | name                  | String                | Instance name.                                                                                |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------+
   | mode                  | String                | Instance type. The value can be:                                                              |
   |                       |                       |                                                                                               |
   |                       |                       | -  **Cluster**: GeminiDB Cassandra cluster instance                                           |
   |                       |                       | -  **CloudNativeCluster**: GeminiDB Influx cluster (performance-enhanced) instance            |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------+
   | data_store            | object                | Database information For details, see :ref:`Table 6 <nosql_api_0035__table584019300183>`.     |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------+
   | charge_type           | String                | Billing mode.                                                                                 |
   |                       |                       |                                                                                               |
   |                       |                       | -  **prePaid**: indicates that the billing mode is yearly/monthly.                            |
   |                       |                       | -  **postPaid**: indicates that the billing mode is pay-per-use.                              |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------+
   | enterprise_project_id | String                | Enterprise project ID. The value **0** indicates that the default enterprise project is used. |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------+
   | backup_id             | String                | Backup ID.                                                                                    |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------+
   | created_at            | String                | Instance creation time.                                                                       |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------+
   | deleted_at            | String                | Instance deletion time.                                                                       |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------+
   | retained_until        | String                | Retention end time.                                                                           |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------+

.. _nosql_api_0035__table584019300183:

.. table:: **Table 6** RecycleDatastore

   +-----------------------+-----------------------+-----------------------------------------------+
   | Parameter             | Type                  | Description                                   |
   +=======================+=======================+===============================================+
   | type                  | String                | Database type.                                |
   |                       |                       |                                               |
   |                       |                       | -  **cassandra**: GeminiDB Cassandra instance |
   |                       |                       | -  **influxdb**: GeminiDB Influx instance     |
   +-----------------------+-----------------------+-----------------------------------------------+
   | version               | String                | Database version.                             |
   +-----------------------+-----------------------+-----------------------------------------------+

Example Requests
----------------

-  URI example

   .. code-block:: text

      GET https://{Endpoint}/v3/619d3e78f61b4be68bc5aa0b59edcf7b/instances/recycle-instances?offset=0&limit=100

-  Example request body

   None

Example Responses
-----------------

Status code: 200

Successful request

.. code-block::

   {
     "total_count" : 1,
     "instances" : [ {
       "id" : "07fc12a8e0e94df7a3fcf53d0b5e1605in06",
       "name" : "test",
       "mode" : "Cluster",
       "data_store" : {
         "type" : "cassandra",
         "version" : "3.11"
       },
       "charge_type" : "postPaid",
       "enterprise_project_id" : "0",
       "backup_id" : "bf9ee62a7f7044c583c6765c916c36edbr02",
       "created_at" : "2022-01-01T10:00:00",
       "deleted_at" : "2022-02-01T11:00:00",
       "retained_until" : "2022-02-02T11:00:00"
     } ]
   }

Status Codes
------------

See :ref:`Status Codes <nosql_status_code>`.

Error Codes
-----------

See :ref:`Error Codes <nosql_error_code>`.
