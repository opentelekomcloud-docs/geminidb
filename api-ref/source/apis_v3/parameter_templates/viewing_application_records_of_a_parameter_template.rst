:original_name: QueryApplyHistory.html

.. _QueryApplyHistory:

Viewing Application Records of a Parameter Template
===================================================

Function
--------

This API is used to view application records of a parameter template.

Constraints
-----------

This API supports the following instance types:

-  GeminiDB Cassandra
-  GeminiDB Influx

After an instance is deleted, application records of the parameter template that the instance uses are also deleted.

URI
---

GET https://{Endpoint}/v3/{project_id}/configurations/{config_id}/applied-histories

.. table:: **Table 1** URI parameters

   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                    |
   +============+===========+========+================================================================================================================+
   | project_id | Yes       | String | Project ID of a tenant in a region. To obtain this value, see :ref:`Obtaining a Project ID <nosql_projectid>`. |
   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+
   | config_id  | Yes       | String | Parameter template ID.                                                                                         |
   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+

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

   +-------------+---------------------------------------------------------------------------------------+----------------------------------------------+
   | Parameter   | Type                                                                                  | Description                                  |
   +=============+=======================================================================================+==============================================+
   | total_count | Integer                                                                               | Total number of records                      |
   +-------------+---------------------------------------------------------------------------------------+----------------------------------------------+
   | histories   | Array of :ref:`ApplyHistoryRsp <queryapplyhistory__response_applyhistoryrsp>` objects | Application records of a parameter template. |
   +-------------+---------------------------------------------------------------------------------------+----------------------------------------------+

.. _queryapplyhistory__response_applyhistoryrsp:

.. table:: **Table 5** ApplyHistoryRsp

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                |
   +=======================+=======================+============================================================================================================+
   | instance_id           | String                | Instance ID.                                                                                               |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | instance_name         | String                | Instance name.                                                                                             |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | applied_at            | String                | Effective time in the yyyy-MM-ddTHH:mm:ssZ format.                                                         |
   |                       |                       |                                                                                                            |
   |                       |                       | **T** is the separator between calendar and hourly notation of time. **Z** indicates the time zone offset. |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | apply_result          | String                | -  **SUCCESS**: indicates that the parameter template is applied to the corresponding instance.            |
   |                       |                       | -  **Applying**: indicates that the parameter template is being applied to the corresponding instance.     |
   |                       |                       | -  **FAILED**: indicates that the parameter template fails to be applied to the corresponding instance.    |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | failure_reason        | String                | Failure cause.                                                                                             |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------+

Example Requests
----------------

-  URI example

   .. code-block:: text

      GET https://{Endpoint}/v3/056f86e8d480d3cb2f43c00183f75e1f/configurations/e02e76567ae04662a2753492b77f965bpr06/applied-histories?offset=0&limit=10

Example Responses
-----------------

Status code: 200

Success

.. code-block::

   {
       "total_count" : 1,
       "histories" : [
       {
         "instance_id" : "a2d0cf32db3e4f2aa3a684240e10b457in06",
         "instance_name" : "test",
         "applied_at" : "2022-09-20T11:17:04+0000",
         "apply_result" : "SUCCESS",
         "failure_reason": ""
       }
     ]
   }

Status Codes
------------

See :ref:`Status Codes <nosql_status_code>`.

Error Codes
-----------

See :ref:`Error Codes <nosql_error_code>`.
