:original_name: topic_300000019.html

.. _topic_300000019:

Modifying Enterprise Project Quotas
===================================

Function
--------

This API is used to modify enterprise project quotas.

URI
---

PUT https://{Endpoint}/v3/{project_id}/enterprise-projects/quotas

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

   +-----------+-----------+---------+-----------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type    | Description                                                                                               |
   +===========+===========+=========+===========================================================================================================+
   | quotas    | Yes       | objects | Enterprise quotas to be modified. For details, see :ref:`Table 4 <topic_300000019__table16925173713216>`. |
   +-----------+-----------+---------+-----------------------------------------------------------------------------------------------------------+

.. _topic_300000019__table16925173713216:

.. table:: **Table 4** NoSqlRequestEpsQuota

   +-----------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory       | Type            | Description                                                                                             |
   +=======================+=================+=================+=========================================================================================================+
   | enterprise_project_id | Yes             | String          | Enterprise project ID                                                                                   |
   +-----------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------+
   | quota                 | Yes             | object          | Enterprise quotas to be modified. For details, see :ref:`Table 5 <topic_300000019__table697933717216>`. |
   |                       |                 |                 |                                                                                                         |
   |                       |                 |                 | .. note::                                                                                               |
   |                       |                 |                 |                                                                                                         |
   |                       |                 |                 |    At least one of parameters **instance**, **vcpus**, and **ram** must be transferred.                 |
   +-----------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------+

.. _topic_300000019__table697933717216:

.. table:: **Table 5** NoSqlEpsQuotaRequestInfo

   ========= ========= ======= ==============
   Parameter Mandatory Type    Description
   ========= ========= ======= ==============
   instance  No        Integer Instance quota
   vcpus     No        Integer vCPU quota
   ram       No        Integer RAM quota
   ========= ========= ======= ==============

Response Parameters
-------------------

**Status code: 204**

No response parameters

Example Requests
----------------

-  URI example

   .. code-block:: text

      PUT https://{Endpoint}/v3/054e292c9880d4992f02c0196d3ea468/enterprise-projects/quotas

-  Modifying quotas of an enterprise project (Set **instance** to **1000**, **vcpus** to **500**, and **ram** to **1024**.)

   .. code-block::

      {
        "quotas" : [ {
          "enterprise_project_id" : "4d05638e-d4c6-477c-9b51-9620fa257a11",
          "quota" : {
            "instance" : 1000,
            "vcpus" : 500,
            "ram" : 1024
          }
        }, {
            "enterprise_project_id" : "92450d0e-8c4b-48e1-9909-4d9d2f086ce4",
            "quota" : {
            "ram" : 512
          }
        } ]
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
