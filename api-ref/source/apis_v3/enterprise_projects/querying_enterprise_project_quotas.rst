:original_name: topic_300000018.html

.. _topic_300000018:

Querying Enterprise Project Quotas
==================================

Function
--------

This API is used to query enterprise project quotas.

URI
---

GET https://{Endpoint}/v3/{project_id}/enterprise-projects/quotas

.. table:: **Table 1** Path parameters

   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                    |
   +============+===========+========+================================================================================================================+
   | project_id | Yes       | String | Project ID of a tenant in a region. To obtain this value, see :ref:`Obtaining a Project ID <nosql_projectid>`. |
   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query parameters

   +-------------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter               | Mandatory       | Type            | Description                                                                                                                         |
   +=========================+=================+=================+=====================================================================================================================================+
   | enterprise_project_name | No              | String          | Enterprise project name. Fuzzy search is supported. If this parameter is not specified, all enterprise project quotas are returned. |
   +-------------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------+
   | offset                  | No              | Integer         | Index offset.                                                                                                                       |
   |                         |                 |                 |                                                                                                                                     |
   |                         |                 |                 | -  The query starts from the next piece of data indexed by this parameter. The value is **0** by default.                           |
   |                         |                 |                 | -  The value must be a positive integer.                                                                                            |
   +-------------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------+
   | limit                   | No              | Integer         | Maximum records to be queried.                                                                                                      |
   |                         |                 |                 |                                                                                                                                     |
   |                         |                 |                 | -  The value ranges from **1** to **100**.                                                                                          |
   |                         |                 |                 | -  If this parameter is not transferred, the first 100 records are queried by default.                                              |
   +-------------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   ============ ========= ====== ===========
   Parameter    Mandatory Type   Description
   ============ ========= ====== ===========
   X-Auth-Token Yes       String User token
   ============ ========= ====== ===========

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-------------+---------+----------------------------------------------------------------------------------------------------+
   | Parameter   | Type    | Description                                                                                        |
   +=============+=========+====================================================================================================+
   | total_count | Integer | Total number of records                                                                            |
   +-------------+---------+----------------------------------------------------------------------------------------------------+
   | quotas      | objects | Enterprise project quotas. For details, see :ref:`Table 5 <topic_300000018__table18282101411527>`. |
   +-------------+---------+----------------------------------------------------------------------------------------------------+

.. _topic_300000018__table18282101411527:

.. table:: **Table 5** NoSqlQueryEpsQuotaInfo

   +-------------------------+--------+--------------------------------------------------------------------------------------------------------+
   | Parameter               | Type   | Description                                                                                            |
   +=========================+========+========================================================================================================+
   | enterprise_project_id   | String | Enterprise project ID                                                                                  |
   +-------------------------+--------+--------------------------------------------------------------------------------------------------------+
   | enterprise_project_name | String | Enterprise project name                                                                                |
   +-------------------------+--------+--------------------------------------------------------------------------------------------------------+
   | quota                   | object | Enterprise project quotas. For details, see :ref:`Table 6 <topic_300000018__table629161419521>`.       |
   +-------------------------+--------+--------------------------------------------------------------------------------------------------------+
   | used                    | object | Enterprise project quota used. For details, see :ref:`Table 7 <topic_300000018__table02981014125217>`. |
   +-------------------------+--------+--------------------------------------------------------------------------------------------------------+

.. _topic_300000018__table629161419521:

.. table:: **Table 6** NoSqlEpsQuotaTotal

   ========= ======= ==============
   Parameter Type    Description
   ========= ======= ==============
   instance  Integer Instance quota
   vcpus     Integer vCPU quota
   ram       Integer RAM quota
   ========= ======= ==============

.. _topic_300000018__table02981014125217:

.. table:: **Table 7** NoSqlEpsQuotaUsed

   ========= ======= ===================
   Parameter Type    Description
   ========= ======= ===================
   instance  Integer Used instance quota
   vcpus     Integer Used vCPU quota
   ram       Integer Used RAM quota
   ========= ======= ===================

Example Requests
----------------

-  URI example

   .. code-block:: text

      GET https://{Endpoint}/v3/0549b4a43100d4f32f51c01c2fe4acdb/enterprise-projects/quotas?enterprise_project_name=test&offset=1&limit=10

Example Responses
-----------------

**Status code: 200**

Success.

.. code-block::

   {
     "quotas" : [ {
       "enterprise_project_id" : "c0348bb1-d09d-4ee2-8edd-53e496fe6b52",
       "enterprise_project_name" : "test1",
       "quota" : {
         "instance" : 500,
         "vcpus" : 1000,
         "ram" : 2000
       },
       "used" : {
         "instance" : 15,
         "vcpus" : 88,
         "ram" : 256
       }
     }, {
       "enterprise_project_id" : "780a6b1f-58b8-4df6-a85e-326d052de704",
       "enterprise_project_name" : "test2",
       "quota" : {
         "instance" : 500,
         "vcpus" : 1000,
         "ram" : 2000
       },
       "used" : {
         "instance" : 36,
         "vcpus" : 64,
         "ram" : 192
       }
     } ],
     "total_count" : 2
   }

Status Codes
------------

See :ref:`Status Codes <nosql_status_code>`.

Error Codes
-----------

See :ref:`Error Codes <nosql_error_code>`.
