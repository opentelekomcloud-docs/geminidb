:original_name: nosql_05_0115.html

.. _nosql_05_0115:

Querying the Autoscaling Policy of Storage Space
================================================

Function
--------

This API is used to query the autoscaling policy of storage space.

Constraints
-----------

This API supports the following types of instances:

-  GeminiDB Cassandra

URI
---

GET https://{Endpoint}/v3/{project_id}/instances/{instance_id}/disk-auto-expansion

.. table:: **Table 1** Path parameters

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

   ============ ========= ====== ===========
   Parameter    Mandatory Type   Description
   ============ ========= ====== ===========
   X-Auth-Token Yes       String User token.
   ============ ========= ====== ===========

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-----------------------+-----------------------+-----------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                           |
   +=======================+=======================+=======================================================================+
   | policy                | object                | Autoscaling policy for storage space.                                 |
   |                       |                       |                                                                       |
   |                       |                       | No information is returned if the autoscaling policy is disabled.     |
   |                       |                       |                                                                       |
   |                       |                       | For details, see :ref:`Table 4 <nosql_05_0115__table17759131171816>`. |
   +-----------------------+-----------------------+-----------------------------------------------------------------------+

.. _nosql_05_0115__table17759131171816:

.. table:: **Table 4** AutoEnlargePolicy

   +-----------+---------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type    | Description                                                                                                                                                                                                                                                                                                                |
   +===========+=========+============================================================================================================================================================================================================================================================================================================================+
   | threshold | Integer | Threshold for triggering autoscaling.                                                                                                                                                                                                                                                                                      |
   +-----------+---------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | step      | Integer | Percentage increase (step%). When autoscaling is triggered, the database system automatically scales up the current storage space of your instance by step%. If the increased storage space is not a multiple of 10 GB, the system rounds it up to the nearest multiple of 10 GB. The default minimum increment is 100 GB. |
   +-----------+---------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | size      | Integer | Storage limit in GB that autoscaling can increase storage space to.                                                                                                                                                                                                                                                        |
   +-----------+---------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Requests
----------------

-  URI example

   .. code-block:: text

      GET https://{Endpoint}/v3/619d3e78f61b4be68bc5aa0b59edcf7b/instances/93e4b3eda14349b1b870f72829bc3b9bin06/disk-auto-expansion

-  Example request body

   None

Example Responses
-----------------

**Status code: 200**

Success

.. code-block::

   {
     "policy" : {
       "threshold" : 90,
       "step" : 10,
       "size" : 600
     }
   }

Status Codes
------------

For details, see :ref:`Status Codes <nosql_status_code>`.

Error Codes
-----------

For details, see :ref:`Error Codes <nosql_error_code>`.
