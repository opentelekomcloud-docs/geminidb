:original_name: nosql_05_0113.html

.. _nosql_05_0113:

Deleting the Node that Fails to Be Added
========================================

Function
--------

This API is used to delete the node that fails to be added to an instance.

Constraints
-----------

This API supports the following types of instances:

-  GeminiDB Cassandra

URI
---

DELETE https://{Endpoint}/v3/{project_id}/instances/{instance_id}/enlarge-failed-nodes

.. table:: **Table 1** URI parameters

   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                                                                                                                                                                         |
   +=============+===========+========+=====================================================================================================================================================================================================================================================+
   | project_id  | Yes       | String | Project ID of a tenant in a region. To obtain this value, see :ref:`Obtaining a Project ID <nosql_projectid>`.                                                                                                                                      |
   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Instance ID, which can be obtained by calling the API described in :ref:`Querying Instances and Details <nosql_05_0016>`. If there are no instances available, call the API described in :ref:`Creating an Instance <nosql_05_0014>` to create one. |
   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

   ========= ========= ====== ===========
   Parameter Mandatory Type   Description
   ========= ========= ====== ===========
   node_id   Yes       String Node ID.
   ========= ========= ====== ===========

Response Parameters
-------------------

**Status code: 202**

.. table:: **Table 4** Response body parameters

   ========= ====== ===========
   Parameter Type   Description
   ========= ====== ===========
   job_id    String Task ID.
   ========= ====== ===========

Example Requests
----------------

-  URI example

   .. code-block:: text

      DELETE https://{Endpoint}/v3/619d3e78f61b4be68bc5aa0b59edcf7b/instances/c865f921f3dd45198f209a607533a779in06/enlarge-failed-nodes

-  Example request body

   .. code-block::

      {
        "node_id" : "b60f00f19cd044fc8d7b52908978f629no06"
      }

Example Responses
-----------------

**Status code: 202**

Accepted

.. code-block::

   {
     "job_id" : "89638f5e-0780-497c-b3c0-4d0968383e19"
   }

Status Codes
------------

See :ref:`Status Codes <nosql_status_code>`.

Error Codes
-----------

See :ref:`Error Codes <nosql_error_code>`.
