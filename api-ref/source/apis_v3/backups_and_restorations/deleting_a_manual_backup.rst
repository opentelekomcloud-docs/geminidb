:original_name: DeleteBackup.html

.. _DeleteBackup:

Deleting a Manual Backup
========================

Function
--------

This API is used to delete a manual backup.

Constraints
-----------

This API supports the following instances:

-  GeminiDB Cassandra
-  GeminiDB Influx

URI
---

DELETE https://{Endpoint}/v3/{project_id}/backups/{backup_id}

.. table:: **Table 1** URI parameters

   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                  |
   +============+===========+========+==============================================================================================================+
   | project_id | Yes       | String | Project ID of a user in a region. To obtain this value, see :ref:`Obtaining a Project ID <nosql_projectid>`. |
   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------+
   | backup_id  | Yes       | String | Backup file ID.                                                                                              |
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

**Status code: 202**

.. table:: **Table 3** Response body parameters

   ========= ====== ===========
   Parameter Type   Description
   ========= ====== ===========
   job_id    String Task ID.
   ========= ====== ===========

Example Requests
----------------

-  URI example

   .. code-block:: text

      DELETE https://{Endpoint}/v3/054e292c9880d4992f02c0196d3ea468/backups/5b0ae36cb8a746b68685a8fb588d8a15br06

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
