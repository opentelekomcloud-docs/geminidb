:original_name: nosql_10_0101.html

.. _nosql_10_0101:

Querying the Maintenance Period of an Instance
==============================================

Function
--------

This function is used to query the maintenance period of an instance.

Constraints
-----------

This API supports the following types of instances:

-  GeminiDB Influx
-  GeminiDB Cassandra

URI
---

GET https://{Endpoint}/v3/{project_id}/instances/{instance_id}/ops-window

.. table:: **Table 1** Path parameters

   =========== ========= ====== ================================
   Parameter   Mandatory Type   Description
   =========== ========= ====== ================================
   project_id  Yes       String Project ID of a user in a region
   instance_id Yes       String Instance ID
   =========== ========= ====== ================================

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   ============ ========= ====== ===========
   Parameter    Mandatory Type   Description
   ============ ========= ====== ===========
   X-Auth-Token Yes       String User token
   ============ ========= ====== ===========

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response header parameter

   ================== ====== ======================================
   Parameter          Type   Description
   ================== ====== ======================================
   maintenance_window String Maintenance time window of an instance
   ================== ====== ======================================

Example Requests
----------------

Query the maintenance period of an instance.

.. code-block:: text

   GET
   https://{Endpoint}/v3/619d3e78f61b4be68bc5aa0b59edcf7b/instances/e73893ef73754465a8bd2e0857bbf13ein02/ops-window

Example Responses
-----------------

**Status code: 200**

Success

.. code-block::

   {
     "maintenance_window" : "02:00-06:00"
   }

Status Codes
------------

See :ref:`Status Codes <nosql_status_code>`.

Error Codes
-----------

See :ref:`Error Codes <nosql_error_code>`.
