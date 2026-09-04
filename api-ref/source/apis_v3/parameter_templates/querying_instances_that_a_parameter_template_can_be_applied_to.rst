:original_name: QueryApplicableInstances.html

.. _QueryApplicableInstances:

Querying Instances that a Parameter Template Can Be Applied To
==============================================================

Function
--------

This API is used to query instances that a parameter template can be applied to.

Constraints
-----------

This API supports the following instance types:

-  GeminiDB Cassandra
-  GeminiDB Influx

URI
---

GET https://{Endpoint}/v3/{project_id}/configurations/{config_id}/applicable-instances

.. table:: **Table 1** URI parameters

   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                    |
   +============+===========+========+================================================================================================================+
   | project_id | Yes       | String | Project ID of a tenant in a region. To obtain this value, see :ref:`Obtaining a Project ID <nosql_projectid>`. |
   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+
   | config_id  | Yes       | String | Parameter template ID.                                                                                         |
   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query parameters

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                   |
   +=================+=================+=================+===============================================================================================================================================================================+
   | offset          | No              | Integer         | Index offset.                                                                                                                                                                 |
   |                 |                 |                 |                                                                                                                                                                               |
   |                 |                 |                 | If **offset** is set to *N*, the query starts from the *N*\ +1 piece of data. The default value is **0**, which indicates that the query starts from the first piece of data. |
   |                 |                 |                 |                                                                                                                                                                               |
   |                 |                 |                 | The value must be a non-negative number.                                                                                                                                      |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit           | No              | Integer         | Maximum records to be queried.                                                                                                                                                |
   |                 |                 |                 |                                                                                                                                                                               |
   |                 |                 |                 | -  The value ranges from **1** to **100**.                                                                                                                                    |
   |                 |                 |                 | -  If this parameter is not transferred, the first 100 records are queried by default.                                                                                        |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   ============ ========= ====== ===========
   Parameter    Mandatory Type   Description
   ============ ========= ====== ===========
   X-Auth-Token Yes       String User token.
   ============ ========= ====== ===========

Response Parameters
-------------------

Status code: 200

.. table:: **Table 4** Response body parameters

   +-----------+----------------------------------------------------------------------------------------------------------+----------------------------------------------------------------+
   | Parameter | Type                                                                                                     | Description                                                    |
   +===========+==========================================================================================================+================================================================+
   | instances | Array of :ref:`ApplicableInstanceRsp <queryapplicableinstances__response_applicableinstancersp>` objects | All instances.                                                 |
   +-----------+----------------------------------------------------------------------------------------------------------+----------------------------------------------------------------+
   | count     | Integer                                                                                                  | Maximum number of instances that parameters can be applied to. |
   +-----------+----------------------------------------------------------------------------------------------------------+----------------------------------------------------------------+

.. _queryapplicableinstances__response_applicableinstancersp:

.. table:: **Table 5** ApplicableInstanceRsp

   ========= ====== ==============
   Parameter Type   Description
   ========= ====== ==============
   id        String Instance ID.
   name      String Instance name.
   ========= ====== ==============

Example Request
---------------

-  URI example

   .. code-block:: text

      GET https://{Endpoint}/v3/0549b4a43100d4f32f51c01c2fe4acdb/configurations/9e80bf6bbd7142f49761c07e9c32dd04pr06/applicable-instances?offset=0&limit=10

Example Response
----------------

Status code: 200

Successful response

.. code-block::

   {
     "instances" : [ {
       "id" : "f38e203908bd4fae82714e88f12600f6in06",
       "name" : "test"
     } ],
     "count" : 1000
   }

Status Codes
------------

See :ref:`Status Codes <nosql_status_code>`.

Error Codes
-----------

See :ref:`Error Codes <nosql_error_code>`.
