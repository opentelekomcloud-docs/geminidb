:original_name: nosql_06_0003.html

.. _nosql_06_0003:

Creating a Parameter Template
=============================

Function
--------

This API is used to create a parameter template and configure the name, description, DB engine version, and parameter values in the parameter template.

Constraints
-----------

This API can be used for GeminiDB Cassandra and GeminiDB Influx instances.

The new parameter template cannot have the same name as any existing parameter template.

For configuration item **values**, you can enter system-defined parameters that allow for modification.

URI
---

POST https://{Endpoint}/v3/{project_id}/configurations

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

   +-------------+-----------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type                                                                                             | Description                                                                                                                                                                          |
   +=============+===========+==================================================================================================+======================================================================================================================================================================================+
   | name        | Yes       | String                                                                                           | Parameter template name. It can include a maximum of 64 characters and can contain only uppercase letters, lowercase letters, digits, hyphens (-), underscores (_), and periods (.). |
   +-------------+-----------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description | No        | String                                                                                           | Parameter template description. It can contain a maximum of 256 characters except the following special characters: >!<"&'= The value is left blank by default.                      |
   +-------------+-----------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | values      | No        | Map<String,String>                                                                               | Parameter values defined by users based on a default parameter template. Keep the parameter values unchanged by default.                                                             |
   +-------------+-----------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | datastore   | Yes       | :ref:`ConfigurationDatastoreOption <nosql_06_0003__request_configurationdatastoreoption>` object | Database object.                                                                                                                                                                     |
   +-------------+-----------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _nosql_06_0003__request_configurationdatastoreoption:

.. table:: **Table 4** ConfigurationDatastoreOption

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                           |
   +=================+=================+=================+=======================================================================================================================================================================================================================================+
   | type            | Yes             | String          | Database type. The value can be:                                                                                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                                                                       |
   |                 |                 |                 | -  **cassandra**: GeminiDB Cassandra instance                                                                                                                                                                                         |
   |                 |                 |                 | -  **influxdb**: GeminiDB Influx instance                                                                                                                                                                                             |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | version         | Yes             | String          | Database version. The value can be:                                                                                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                                                                                                       |
   |                 |                 |                 | -  **3.11**: GeminiDB Cassandra instance 3.11                                                                                                                                                                                         |
   |                 |                 |                 | -  **1.7**: GeminiDB Influx instance 1.7                                                                                                                                                                                              |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | mode            | No              | String          | Instance type.                                                                                                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                                                                                       |
   |                 |                 |                 | This parameter is mandatory when you create a parameter template for a GeminiDB Influx instance. The value is **CloudNativeCluster**, indicating a GeminiDB Influx cluster (performance-enhanced) instance with cloud native storage. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

Status code: 200

.. table:: **Table 5** Response body parameters

   +---------------+---------------------------------------------------------------------------------+---------------------------------+
   | Parameter     | Type                                                                            | Description                     |
   +===============+=================================================================================+=================================+
   | configuration | :ref:`ConfigurationResult <nosql_06_0003__response_configurationresult>` object | Parameter template information. |
   +---------------+---------------------------------------------------------------------------------+---------------------------------+

.. _nosql_06_0003__response_configurationresult:

.. table:: **Table 6** ConfigurationResult

   +------------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | Parameter              | Type                  | Description                                                                                                |
   +========================+=======================+============================================================================================================+
   | id                     | String                | Parameter template ID.                                                                                     |
   +------------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | name                   | String                | Parameter template name.                                                                                   |
   +------------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | datastore_version_name | String                | Database version name.                                                                                     |
   +------------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | datastore_name         | String                | Database name.                                                                                             |
   +------------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | description            | String                | Parameter template description                                                                             |
   +------------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | mode                   | String                | Instance type.                                                                                             |
   |                        |                       |                                                                                                            |
   |                        |                       | **CloudNativeCluster**: GeminiDB Influx cluster (performance-enhanced) instance with cloud native storage  |
   +------------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | created                | String                | Creation time in the yyyy-MM-ddTHH:mm:ssZ format.                                                          |
   |                        |                       |                                                                                                            |
   |                        |                       | **T** is the separator between calendar and hourly notation of time. **Z** indicates the time zone offset. |
   +------------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | updated                | String                | Update time in the yyyy-MM-ddTHH:mm:ssZ format.                                                            |
   |                        |                       |                                                                                                            |
   |                        |                       | **T** is the separator between calendar and hourly notation of time. **Z** indicates the time zone offset. |
   +------------------------+-----------------------+------------------------------------------------------------------------------------------------------------+

Example Requests
----------------

-  URI example

   .. code-block:: text

      POST https://{Endpoint}/v3/375d8d8fad1f43039e23d3b6c0f60a19/configurations

-  Creating a parameter template for GeminiDB Cassandra instances

   .. code-block::

      {
        "name" : "configuration_test",
        "description" : "configuration_test",
        "values" : {
          "max_connections" : "10",
          "autocommit" : "OFF"
        },
        "datastore" : {
          "type" : "cassandra",
          "version" : "3.11"
        }
      }

-  Creating a parameter template for GeminiDB Influx instances

   .. code-block::

      {
        "name" : "configuration_test2",
        "description" : "configuration_test2",
        "datastore" : {
          "type" : "influxdb",
          "mode":"CloudNativeCluster",
          "version" : "1.8"
        }
      }

Example Responses
-----------------

**Status code**: **200**

Success

-  Example response for a GeminiDB Cassandra instance:

   .. code-block::

      {
          "configuration": {
              "id": "a2685db51a074b2893150f7d78731758pr06",
              "name": "configuration_test23",
              "description": "configuration_test",
              "datastore_version_name": "3.11",
              "datastore_name": "cassandra",
              "mode": null,
              "created": "2026-02-12T03:29:01+0000",
              "updated": "2026-02-12T03:29:01+0000"
          }
      }

-  Example response for a GeminiDB Influx instance:

   .. code-block::

      {
          "configuration": {
              "id": "e1b984b199d64c97a3c9a2e7d098da2apr13",
              "name": "configuration_test",
              "description": "configuration_test",
              "datastore_version_name": "1.8",
              "datastore_name": "influxdb",
              "mode": "CloudNativeCluster",
              "created": "2026-02-12T03:15:33+0000",
              "updated": "2026-02-12T03:15:33+0000"
          }
      }

Status Codes
------------

See :ref:`Status Codes <nosql_status_code>`.

Error Codes
-----------

See :ref:`Error Codes <nosql_error_code>`.
