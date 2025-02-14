:original_name: nosql_06_0008.html

.. _nosql_06_0008:

Obtaining Parameters of a Specified Parameter Template
======================================================

Function
--------

This API is used to obtain information about parameters of a specified parameter template.

Constraints
-----------

This API supports GeminiDB Cassandra instances.

URI
---

GET https://{Endpoint}/v3/{project_id}/configurations/{config_id}

.. table:: **Table 1** Path parameters

   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                    |
   +============+===========+========+================================================================================================================+
   | project_id | Yes       | String | Project ID of a tenant in a region. To obtain this value, see :ref:`Obtaining a Project ID <nosql_projectid>`. |
   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+
   | config_id  | Yes       | String | Parameter template ID.                                                                                         |
   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   ============ ========= ====== ===========
   Parameter    Mandatory Type   Description
   ============ ========= ====== ===========
   X-Auth-Token Yes       String User token.
   ============ ========= ====== ===========

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +--------------------------+-------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+
   | Parameter                | Type                                                                                                        | Description                                                                                                |
   +==========================+=============================================================================================================+============================================================================================================+
   | id                       | String                                                                                                      | Parameter template ID.                                                                                     |
   +--------------------------+-------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+
   | name                     | String                                                                                                      | Parameter template name.                                                                                   |
   +--------------------------+-------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+
   | description              | String                                                                                                      | Parameter template description.                                                                            |
   +--------------------------+-------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+
   | datastore_version_name   | String                                                                                                      | Database version name.                                                                                     |
   +--------------------------+-------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+
   | datastore_name           | String                                                                                                      | Database name.                                                                                             |
   +--------------------------+-------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+
   | created                  | String                                                                                                      | Creation time in the yyyy-MM-ddTHH:mm:ssZ format.                                                          |
   |                          |                                                                                                             |                                                                                                            |
   |                          |                                                                                                             | **T** is the separator between calendar and hourly notation of time. **Z** indicates the time zone offset. |
   +--------------------------+-------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+
   | updated                  | String                                                                                                      | Update time in the yyyy-MM-ddTHH:mm:ssZ format.                                                            |
   |                          |                                                                                                             |                                                                                                            |
   |                          |                                                                                                             | **T** is the separator between calendar and hourly notation of time. **Z** indicates the time zone offset. |
   +--------------------------+-------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+
   | configuration_parameters | Array of :ref:`ConfigurationParameterResult <nosql_06_0008__response_configurationparameterresult>` objects | Parameters defined by users based on a default parameter template.                                         |
   +--------------------------+-------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+

.. _nosql_06_0008__response_configurationparameterresult:

.. table:: **Table 4** ConfigurationParameterResult

   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                     |
   +=======================+=======================+=================================================================================================================================================+
   | name                  | String                | Parameter name.                                                                                                                                 |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | value                 | String                | Parameter value.                                                                                                                                |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | restart_required      | Boolean               | Whether the instance needs to be restarted. The value can be:                                                                                   |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  **false**, indicating that the instance does not need to be restarted.                                                                       |
   |                       |                       | -  **true**, indicating that the instance needs to be restarted.                                                                                |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | readonly              | Boolean               | Whether the parameter is read-only. The value can be:                                                                                           |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  **false**, indicating that the parameter is not read-only.                                                                                   |
   |                       |                       | -  **true**, indicating that the parameter is read-only.                                                                                        |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | value_range           | String                | Value range. For example, the value of the Integer type ranges from **0** to **1**, and the value of the Boolean type is **true** or **false**. |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | type                  | String                | Parameter type. The value can be **string**, **integer**, **boolean**, **list**, or **float**.                                                  |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | description           | String                | Parameter description.                                                                                                                          |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+

Example Requests
----------------

URI example

.. code-block:: text

   GET https://{Endpoint}/v3/375d8d8fad1f43039e23d3b6c0f60a19/configurations/e02e76567ae04662a2753492b77f965bpr06

Example Responses
-----------------

**Status code: 200**

Success

.. code-block::

   {
     "id" : "07fc12a8e0e94df7a3fcf53d0b5e1605pr06",
     "name" : "default-cassandra-3.11",
     "datastore_version_name" : "3.11",
     "datastore_name" : "cassandra",
     "description" : "Default parameter group for cassandra 3.11",
     "created" : "2020-03-21T04:40:51+0800",
     "updated" : "2020-03-21T04:40:51+0800",
     "configuration_parameters" : [ {
       "name" : "concurrent_reads",
       "value" : "64",
       "restart_required" : true,
       "readonly" : true,
       "value_range" : "4-512",
       "type" : "integer",
       "description" : "Number of concurrent read threads."
     } ]
   }

Status Codes
------------

For details, see :ref:`Status Codes <nosql_status_code>`.

Error Codes
-----------

For details, see :ref:`Error Codes <nosql_error_code>`.
