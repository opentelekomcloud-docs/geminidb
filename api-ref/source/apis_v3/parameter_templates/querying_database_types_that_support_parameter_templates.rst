:original_name: nosql_06_0112.html

.. _nosql_06_0112:

Querying Database Types That Support Parameter Templates
========================================================

Function
--------

This API is used to query database types that support parameter templates.

URI
---

GET https://{Endpoint}/v3/{project_id}/configurations/datastores

.. table:: **Table 1** URI parameters

   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                    |
   +============+===========+========+================================================================================================================+
   | project_id | Yes       | String | Project ID of a tenant in a region. To obtain this value, see :ref:`Obtaining a Project ID <nosql_projectid>`. |
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

   +------------+----------------------------------------------------------------------+---------------------+
   | Parameter  | Type                                                                 | Description         |
   +============+======================================================================+=====================+
   | datastores | Array of :ref:`Table 4 <nosql_06_0112__table15853131613014>` objects | DB API information. |
   +------------+----------------------------------------------------------------------+---------------------+

.. _nosql_06_0112__table15853131613014:

.. table:: **Table 4** DataStoreList

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                  |
   +=======================+=======================+==============================================================================================================+
   | datastore_name        | String                | Database type                                                                                                |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------+
   | version               | String                | Database type version                                                                                        |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------+
   | mode                  | String                | Instance type. The value can be:                                                                             |
   |                       |                       |                                                                                                              |
   |                       |                       | -  **Cluster**: GeminiDB Cassandra cluster instance                                                          |
   |                       |                       | -  **CloudNativeCluster**: GeminiDB Influx cluster (performance-enhanced) instance with cloud native storage |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------+

Example Requests
----------------

-  URI example

   .. code-block:: text

      GET https://{Endpoint}/v3/375d8d8fad1f43039e23d3b6c0f60a19/configurations/datastores

-  Example request body

   None

Example Responses
-----------------

**Status code: 200**

Success

.. code-block::

   {
     "datastores" : [ {
       "datastore_name" : "influxdb",
       "mode": "CloudNativeCluster",
       "version" : "1.7"
     }, {
       "datastore_name" : "cassandra",
       "mode": "Cluster",
       "version" : "3.11"
     } ]
   }

Status Codes
------------

See :ref:`Status Codes <nosql_status_code>`.

Error Codes
-----------

See :ref:`Error Codes <nosql_error_code>`.
