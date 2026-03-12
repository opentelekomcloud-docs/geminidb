:original_name: nosql_06_0111.html

.. _nosql_06_0111:

Replicating a Parameter Template
================================

Function
--------

This API is used to replicate a parameter template.

Constraints
-----------

This API supports the following types of instances:

-  GeminiDB Cassandra
-  GeminiDB Influx

The parameter template generated after replication cannot have the same name as the default parameter template or an existing template.

Only custom parameter templates can be replicated.

URI
---

POST https://{Endpoint}/v3/{project_id}/configurations/{config_id}/copy

.. table:: **Table 1** URI parameters

   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                    |
   +============+===========+========+================================================================================================================+
   | project_id | Yes       | String | Project ID of a tenant in a region. To obtain this value, see :ref:`Obtaining a Project ID <nosql_projectid>`. |
   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+
   | config_id  | Yes       | String | Parameter template ID.                                                                                         |
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

   +-------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                                                                                                                                                   |
   +=============+===========+========+===============================================================================================================================================================================================================================+
   | name        | Yes       | String | Name of the parameter template generated after replication. The name can include a maximum of 64 characters and can contain only uppercase letters, lowercase letters, digits, hyphens (-), underscores (_), and periods (.). |
   +-------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description | No        | String | Parameter template description. The description can contain a maximum of 256 characters except the following special characters: >!<"&'= The value is left blank by default.                                                  |
   +-------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 202**

.. table:: **Table 4** Response body parameters

   ========= ====== ========================================
   Parameter Type   Description
   ========= ====== ========================================
   config_id String ID of the replicated parameter template.
   ========= ====== ========================================

Example Requests
----------------

-  URI example

   .. code-block:: text

      POST https://{Endpoint}/v3/375d8d8fad1f43039e23d3b6c0f60a19/configurations/e02e76567ae04662a2753492b77f965bpr06/copy

-  Replicating a Parameter Template

   .. code-block::

      {
        "name" : "paramsGroup-2434",
        "description" : "Replicating a parameter template"
      }

Example Responses
-----------------

**Status code: 202**

Accepted

.. code-block::

   {
     "config_id" : "7b4e07852bd54016906e89461b3182cdpr06"
   }

Status Codes
------------

See :ref:`Status Codes <nosql_status_code>`.

Error Codes
-----------

See :ref:`Error Codes <nosql_error_code>`.
