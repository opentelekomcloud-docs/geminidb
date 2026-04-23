:original_name: QueryModifyHistory.html

.. _QueryModifyHistory:

Viewing Parameter Change History of an Instance
===============================================

Function
--------

This API is used to view change history of parameters of an instance.

Constraints
-----------

This API supports the following instance types:

-  GeminiDB Cassandra
-  GeminiDB Influx

This API can be used to query only the past seven days of parameter changes.

URI
---

GET https://{Endpoint}/v3/{project_id}/instances/{instance_id}/configuration-histories

.. table:: **Table 1** URI parameters

   +-------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                                    |
   +=============+===========+========+================================================================================================================+
   | project_id  | Yes       | String | Project ID of a tenant in a region. To obtain this value, see :ref:`Obtaining a Project ID <nosql_projectid>`. |
   +-------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Instance ID.                                                                                                   |
   +-------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query parameters

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                   |
   +=================+=================+=================+===============================================================================================================================================================================+
   | offset          | No              | Integer         | Index offset.                                                                                                                                                                 |
   |                 |                 |                 |                                                                                                                                                                               |
   |                 |                 |                 | If **offset** is set to *N*, the query starts from the *N*\ +1 piece of data. The default value is **0**, which indicates that the query starts from the first piece of data. |
   |                 |                 |                 |                                                                                                                                                                               |
   |                 |                 |                 | The value must be a non-negative number.                                                                                                                                      |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit           | No              | Integer         | Maximum records to be queried.                                                                                                                                                |
   |                 |                 |                 |                                                                                                                                                                               |
   |                 |                 |                 | -  The value ranges from **1** to **100**.                                                                                                                                    |
   |                 |                 |                 | -  If this parameter is not transferred, the first 100 records are queried by default.                                                                                        |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   ============ ========= ====== ===========
   Parameter    Mandatory Type   Description
   ============ ========= ====== ===========
   X-Auth-Token Yes       String User token.
   ============ ========= ====== ===========

Response Parameters
-------------------

Status code: 200

.. table:: **Table 4** Response body parameters

   +-----------------------+--------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                                                   | Description                                                                                                                                                                   |
   +=======================+========================================================================================================+===============================================================================================================================================================================+
   | total_count           | Integer                                                                                                | Total number of parameter change records                                                                                                                                      |
   |                       |                                                                                                        |                                                                                                                                                                               |
   |                       |                                                                                                        | By default, the total number of parameter change records is returned. If a parameter name is searched, the total number of records that meet the search criteria is returned. |
   +-----------------------+--------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | histories             | Array of :ref:`ConfigurationHistoryRsp <querymodifyhistory__response_configurationhistoryrsp>` objects | Change history of parameters of an instance.                                                                                                                                  |
   +-----------------------+--------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _querymodifyhistory__response_configurationhistoryrsp:

.. table:: **Table 5** ConfigurationHistoryRsp

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                |
   +=======================+=======================+============================================================================================================+
   | parameter_name        | String                | Parameter name.                                                                                            |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | old_value             | String                | Original parameter value.                                                                                  |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | new_value             | String                | New parameter value.                                                                                       |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | update_result         | String                | Update result. The value can be:                                                                           |
   |                       |                       |                                                                                                            |
   |                       |                       | -  **SUCCESS**: The operation succeeded.                                                                   |
   |                       |                       | -  **FAILED**: The operation failed.                                                                       |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | applied               | Boolean               | -  **true**: A change is applied.                                                                          |
   |                       |                       | -  **false**: A change is not applied.                                                                     |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | updated_at            | String                | Update time in the yyyy-MM-ddTHH:mm:ssZ format.                                                            |
   |                       |                       |                                                                                                            |
   |                       |                       | **T** is the separator between calendar and hourly notation of time. **Z** indicates the time zone offset. |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | applied_at            | String                | Update time in the yyyy-MM-ddTHH:mm:ssZ format.                                                            |
   |                       |                       |                                                                                                            |
   |                       |                       | **T** is the separator between calendar and hourly notation of time. **Z** indicates the time zone offset. |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------+

Example Requests
----------------

-  URI example

   .. code-block:: text

      GET https://{Endpoint}/v3/0549b4a43100d4f32f51c01c2fe4acdb/instances/c4e095105bc64797bc3be633ae7201eein10/configuration-histories?offset=0&limit=10

Example Responses
-----------------

Status code: 200

Success

.. code-block::

   {
       "total_count" : 1,
       "histories" : [ {
       "parameter_name" : "mongos.connPoolMaxShardedConnsPerHost",
       "old_value" : "600",
       "new_value" : "500",
       "update_result" : "FAILED",
       "applied" : true,
       "updated_at" : "2022-09-20T11:17:04+0000",
       "applied_at" : "2022-09-20T11:17:04+0000"
     } ]
   }

Status Codes
------------

See :ref:`Status Codes <nosql_status_code>`.

Error Codes
-----------

See :ref:`Error Codes <nosql_error_code>`.
