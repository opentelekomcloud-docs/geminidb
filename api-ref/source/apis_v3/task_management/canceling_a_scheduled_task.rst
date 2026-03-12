:original_name: nosql_10_0103.html

.. _nosql_10_0103:

Canceling a Scheduled Task
==========================

Function
--------

This function is used to cancel a scheduled task based on the task ID.

Constraints
-----------

This API supports the following types of instances:

-  GeminiDB Influx
-  GeminiDB Cassandra

URI
---

DELETE https://{Endpoint}/v3/{project_id}/scheduled-jobs/{job_id}

.. table:: **Table 1** URI parameters

   +------------+-----------+--------+---------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                 |
   +============+===========+========+=============================================================================================+
   | project_id | Yes       | String | Project ID of a user in a region                                                            |
   +------------+-----------+--------+---------------------------------------------------------------------------------------------+
   | job_id     | Yes       | String | Task ID. The value is the same as the **job_id** field returned in the scheduled task list. |
   +------------+-----------+--------+---------------------------------------------------------------------------------------------+

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

Response Parameters
-------------------

**Status code: 204**

None

Example Requests
----------------

Cancel a scheduled task.

.. code-block:: text

   DELETE https://{Endpoint}/v3/0549b4a43100d4f32f51c01c2fe4acdb/scheduled-jobs/56d3c1138dcf4f1da73b0170700c78d0

Example Responses
-----------------

None

Status Codes
------------

See :ref:`Status Codes <nosql_status_code>`.

Error Codes
-----------

See :ref:`Error Codes <nosql_error_code>`.
