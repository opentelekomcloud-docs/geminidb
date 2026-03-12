:original_name: nosql_05_0062.html

.. _nosql_05_0062:

Setting the Maintenance Period of an Instance
=============================================

Function
--------

This API is used to set the maintenance period of a specified instance.

Constraints
-----------

This API supports the following types of instances:

-  GeminiDB Influx
-  GeminiDB Cassandra

URI
---

PUT https://{Endpoint}/v3/{project_id}/instances/{instance_id}/maintenance-window

.. table:: **Table 1** URI parameters

   +-------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                                    |
   +=============+===========+========+================================================================================================================+
   | project_id  | Yes       | String | Project ID of a tenant in a region. To obtain this value, see :ref:`Obtaining a Project ID <nosql_projectid>`. |
   +-------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Instance ID                                                                                                    |
   +-------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+

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

   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                                                                                                                  |
   +============+===========+========+==============================================================================================================================================================================================================+
   | start_time | Yes       | String | Start time. The value must be a valid value in the "HH:MM" format. The current time is the UTC time and must be on the hour. By default, the interval between the end time and the start time is four hours. |
   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 204**

None

Example Requests
----------------

Set the maintenance window of an instance to 02:00-06:00.

.. code-block:: text

   PUT https://{Endpoint}/
   /v3/0549b4a43100d4f32f51c01c2fe4acdb/instances/b0965c9010f44ffca9af4ee00746aa8din12/maintenance-window

   {
     "start_time" : "02:00"
   }

Example Responses
-----------------

None

Status Codes
------------

See :ref:`Status Codes <nosql_status_code>`.

Error Codes
-----------

See :ref:`Error Codes <nosql_error_code>`.
