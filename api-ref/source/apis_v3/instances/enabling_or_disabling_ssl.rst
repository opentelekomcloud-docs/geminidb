:original_name: nosql_05_0107.html

.. _nosql_05_0107:

Enabling or Disabling SSL
=========================

Function
--------

This API is used to enable or disable SSL.

Constraints
-----------

-  This API supports the following types of instances:

   -  GeminiDB Cassandra
   -  GeminiDB Influx

-  The instance will be restarted after SSL is enabled or disabled on it. Exercise caution when you enable or disable SSL.

URI
---

POST https://{Endpoint}/v3/{project_id}/instances/{instance_id}/ssl-option

.. table:: **Table 1** URI parameters

   +-------------+-----------+--------+--------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                                  |
   +=============+===========+========+==============================================================================================================+
   | project_id  | Yes       | String | Project ID of a user in a region. To obtain this value, see :ref:`Obtaining a Project ID <nosql_projectid>`. |
   +-------------+-----------+--------+--------------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Instance ID.                                                                                                 |
   +-------------+-----------+--------+--------------------------------------------------------------------------------------------------------------+

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

   +-----------------+-----------------+-----------------+------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                |
   +=================+=================+=================+============================================================+
   | ssl_option      | Yes             | String          | Whether SSL is enabled.                                    |
   |                 |                 |                 |                                                            |
   |                 |                 |                 | -  **on**, indicating that SSL is enabled by default.      |
   |                 |                 |                 | -  **off**, indicating that SSL is not enabled by default. |
   +-----------------+-----------------+-----------------+------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 202**

.. table:: **Table 4** Response body parameters

   ========= ====== ===========
   Parameter Type   Description
   ========= ====== ===========
   job_id    String Task ID.
   ========= ====== ===========

Example Requests
----------------

-  Enabling SSL

   -  URI example

      .. code-block:: text

         POST https://{Endpoint}/v3/619d3e78f61b4be68bc5aa0b59edcf7b/instances/944bdc55da6c4b33b260b34185ac86bein13/ssl-option

   -  Enabling SSL

      .. code-block::

         {
           "ssl_option" : "on"
         }

-  Disabling SSL

   -  URI example

      .. code-block:: text

         POST https://{Endpoint}/v3/619d3e78f61b4be68bc5aa0b59edcf7b/instances/944bdc55da6c4b33b260b34185ac86bein13/ssl-option

   -  Disabling SSL

      .. code-block::

         {
           "ssl_option" : "off"
         }

Example Responses
-----------------

**Status code: 202**

Accepted

.. code-block::

   {
     "job_id" : "f85104b5-4a9c-4e0f-9505-fc5409d8f7ae"
   }

Status Codes
------------

See :ref:`Status Codes <nosql_status_code>`.

Error Codes
-----------

See :ref:`Error Codes <nosql_error_code>`.
