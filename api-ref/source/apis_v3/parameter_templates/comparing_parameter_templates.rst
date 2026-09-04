:original_name: nosql_06_0110.html

.. _nosql_06_0110:

Comparing Parameter Templates
=============================

Function
--------

This API is used to compare two parameter templates.

Constraints
-----------

This API supports the following types of instances:

-  GeminiDB Cassandra
-  GeminiDB Influx

This API only compares parameter templates with one of the same node type and DB engine to learn about configurations of the current template.

URI
---

POST https://{Endpoint}/v3/{project_id}/configurations/comparison

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

   +-------------------------+-----------+--------+----------------------------------------------------------+
   | Parameter               | Mandatory | Type   | Description                                              |
   +=========================+===========+========+==========================================================+
   | source_configuration_id | Yes       | String | ID of the source parameter template to be compared.      |
   +-------------------------+-----------+--------+----------------------------------------------------------+
   | target_configuration_id | Yes       | String | ID of the destination parameter template for comparison. |
   +-------------------------+-----------+--------+----------------------------------------------------------+

Response Parameters
-------------------

Status code: 202

.. table:: **Table 4** Response body parameters

   +-------------+--------------------------------------------------------------------+---------------------------------+
   | Parameter   | Type                                                               | Description                     |
   +=============+====================================================================+=================================+
   | differences | Array of :ref:`Table 5 <nosql_06_0110__table172261018261>` objects | Differences between parameters. |
   +-------------+--------------------------------------------------------------------+---------------------------------+

.. _nosql_06_0110__table172261018261:

.. table:: **Table 5** DiffDetails

   +----------------+--------+--------------------------------------------------------+
   | Parameter      | Type   | Description                                            |
   +================+========+========================================================+
   | parameter_name | String | Parameter name.                                        |
   +----------------+--------+--------------------------------------------------------+
   | source_value   | String | Parameter value in the source parameter template.      |
   +----------------+--------+--------------------------------------------------------+
   | target_value   | String | Parameter value in the destination parameter template. |
   +----------------+--------+--------------------------------------------------------+

Example Requests
----------------

-  URI example

   .. code-block:: text

      POST https://{Endpoint}/v3/375d8d8fad1f43039e23d3b6c0f60a19/configurations/comparison

-  Comparing a source parameter template with the target parameter template

   .. code-block::

      {
        "source_configuration_id" : "0764fdcd949b411ba76c2b762b80c212pr06",
        "target_configuration_id" : "fa42c57bb62844e490052f2ff9d5a264pr06"
      }

Example Responses
-----------------

Status code: 202

Accepted

.. code-block::

   {
     "differences" : [ {
       "parameter_name" : "batch_size_fail_threshold_in_kb",
       "source_value" : "1000",
       "target_value" : "5000"
     } ]
   }

Status Codes
------------

See :ref:`Status Codes <nosql_status_code>`.

Error Codes
-----------

See :ref:`Error Codes <nosql_error_code>`.
