:original_name: nosql_05_0015.html

.. _nosql_05_0015:

Deleting an Instance
====================

Function
--------

This API is used to delete an instance. Only pay-per-use instances can be deleted. Yearly/Monthly instances need to be unsubscribed from if they are no longer needed.

Constraints
-----------

This API can be used for GeminiDB Cassandra instances.

URI
---

DELETE https://{Endpoint}/v3/{project_id}/instances/{instance_id}

.. table:: **Table 1** URI parameters

   +-------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                                    |
   +=============+===========+========+================================================================================================================+
   | project_id  | Yes       | String | Project ID of a tenant in a region. To obtain this value, see :ref:`Obtaining a Project ID <nosql_projectid>`. |
   +-------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Instance ID.                                                                                                   |
   +-------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameter

   ============ ========= ====== ===========
   Parameter    Mandatory Type   Description
   ============ ========= ====== ===========
   X-Auth-Token Yes       String User token.
   ============ ========= ====== ===========

Response Parameters
-------------------

**Status code: 202**

.. table:: **Table 3** Response body parameters

   ========= ====== ===========
   Parameter Type   Description
   ========= ====== ===========
   job_id    String Task ID.
   ========= ====== ===========

Example Request
---------------

URI example

.. code-block:: text

   DELETE https://{Endpoint}/v3/375d8d8fad1f43039e23d3b6c0f60a19/instances/9136fd2a9fcd405ea4674276ce36dae8in02

Example Response
----------------

**Status code: 202**

Accepted

.. code-block::

   {
     "job_id" : "04efe8e2-9255-44ae-a98b-d87cae411890"
   }

Status Codes
------------

See :ref:`Status Codes <nosql_status_code>`.

Error Codes
-----------

See :ref:`Error Codes <nosql_error_code>`.
