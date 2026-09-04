:original_name: nosql_05_0114.html

.. _nosql_05_0114:

Querying IP Addresses Required for Creating an Instance or Adding Nodes
=======================================================================

Function
--------

This API is used to query IP addresses required for creating an instance or adding nodes to an instance.

Constraints
-----------

This API supports the following instances:

-  GeminiDB Cassandra
-  GeminiDB Influx

URI
---

GET https://{Endpoint}/v3/{project_id}/ip-num-requirement

.. table:: **Table 1** URI parameters

   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                    |
   +============+===========+========+================================================================================================================+
   | project_id | Yes       | String | Project ID of a tenant in a region. To obtain this value, see :ref:`Obtaining a Project ID <nosql_projectid>`. |
   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query parameters

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                                         |
   +=================+=================+=================+=====================================================================================================================================================================================================================================================+
   | node_num        | Yes             | Integer         | Nodes required for creating or scaling out an instance The maximum value is **200**.                                                                                                                                                                |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | engine_name     | No              | String          | DB engine type                                                                                                                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                                                                                     |
   |                 |                 |                 | -  **cassandra**: GeminiDB Cassandra DB type                                                                                                                                                                                                        |
   |                 |                 |                 | -  **influxdb**: GeminiDB Influx DB type                                                                                                                                                                                                            |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | instance_mode   | No              | String          | Instance type. The value is case-sensitive. If no instance ID is transferred, this parameter is mandatory. The value can be:                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                                                                                                     |
   |                 |                 |                 | -  **Cluster**: GeminiDB Cassandra cluster instance                                                                                                                                                                                                 |
   |                 |                 |                 | -  **CloudNativeCluster**: GeminiDB Influx cluster (performance-enhanced) instance with cloud native storage                                                                                                                                        |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | instance_id     | No              | String          | Instance ID, which can be obtained by calling the API described in :ref:`Querying Instances and Details <nosql_05_0016>`. If there are no instances available, call the API described in :ref:`Creating an Instance <nosql_05_0014>` to create one. |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

**Status code: 200**

.. table:: **Table 4** Response body parameters

   ========= ======= ============================
   Parameter Type    Description
   ========= ======= ============================
   count     Integer Number of IP addresses used.
   ========= ======= ============================

Example Requests
----------------

-  URI example

   .. code-block:: text

      GET https://{Endpoint}/v3/375d8d8fad1f43039e23d3b6c0f60a19/ip-num-requirement?node_num=3&engine_name=cassandra&instance_mode=Cluster

-  Example request body

   None

Example Responses
-----------------

**Status code: 200**

Success

.. code-block::

   {
     "count" : 3
   }

Status Codes
------------

See :ref:`Status Codes <nosql_status_code>`.

Error Codes
-----------

See :ref:`Error Codes <nosql_error_code>`.
