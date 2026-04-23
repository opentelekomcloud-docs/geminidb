:original_name: nosql_api_0034.html

.. _nosql_api_0034:

Modifying the Recycling Policy
==============================

Function
--------

This API is used to change a retention period for deleted instances. The new retention period is available to only those instances deleted after the change, but not to the instances already moved to the recycle bin before the change.

Constraints
-----------

The retention period for deleted instances can be 1 to 7 days.

URI
---

PUT https://{Endpoint}/v3/{project_id}/instances/recycle-policy

.. table:: **Table 1** URI parameter

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

   +----------------+-----------+--------+-----------------------------------------------------------------------------------------+
   | Parameter      | Mandatory | Type   | Description                                                                             |
   +================+===========+========+=========================================================================================+
   | recycle_policy | Yes       | object | Recycling policy. For details, see :ref:`Table 4 <nosql_api_0034__table4684131531510>`. |
   +----------------+-----------+--------+-----------------------------------------------------------------------------------------+

.. _nosql_api_0034__table4684131531510:

.. table:: **Table 4** RecyclePolicy

   +--------------------------+-----------+---------+-------------------------------------------------------------------------------------------------------+
   | Parameter                | Mandatory | Type    | Description                                                                                           |
   +==========================+===========+=========+=======================================================================================================+
   | retention_period_in_days | No        | Integer | Policy retention duration (1 to 7 days). The value is a positive integer. The default value is **7**. |
   +--------------------------+-----------+---------+-------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

No response parameters

Example Requests
----------------

-  URI example

   .. code-block:: text

      PUT https://{Endpoint}/v3/619d3e78f61b4be68bc5aa0b59edcf7b/instances/recycle-policy

-  Setting the retention period of instances in the recycle bin to 3 days

   .. code-block::

      {
        "recycle_policy": {
          "retention_period_in_days": 3
        }
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
