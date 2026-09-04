:original_name: nosql_api_0033.html

.. _nosql_api_0033:

Querying the Recycling Policy
=============================

Function
--------

This API is used to query the recycling policy.

URI
---

GET https://{Endpoint}/v3/{project_id}/instances/recycle-policy

.. table:: **Table 1** Path parameters

   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                  |
   +============+===========+========+==============================================================================================================+
   | project_id | Yes       | String | Project ID of a user in a region. To obtain this value, see :ref:`Obtaining a Project ID <nosql_projectid>`. |
   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------+

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

.. table:: **Table 3** Response body parameters

   +----------------+--------+------------------------------------------------------------------------------------------+
   | Parameter      | Type   | Description                                                                              |
   +================+========+==========================================================================================+
   | recycle_policy | object | Recycling policy. For details, see :ref:`Table 4 <nosql_api_0033__table83891652131118>`. |
   +----------------+--------+------------------------------------------------------------------------------------------+

.. _nosql_api_0033__table83891652131118:

.. table:: **Table 4** RecyclePolicy

   +--------------------------+---------+-------------------------------------------------------------------------------------------------------+
   | Parameter                | Type    | Description                                                                                           |
   +==========================+=========+=======================================================================================================+
   | retention_period_in_days | Integer | Policy retention duration (1 to 7 days). The value is a positive integer. The default value is **7**. |
   +--------------------------+---------+-------------------------------------------------------------------------------------------------------+

Example Requests
----------------

-  URI example

   .. code-block:: text

      GET https://{Endpoint}/v3/054e292c9880d4992f02c0196d3ea468/instances/recycle-policy

-  Example request body

   None

Example Responses
-----------------

**Status code: 200**

Success

.. code-block::

   {
     "recycle_policy": {
       "retention_period_in_days": 7
     }
   }

Status Codes
------------

See :ref:`Status Codes <nosql_status_code>`.

Error Codes
-----------

See :ref:`Error Codes <nosql_error_code>`.
