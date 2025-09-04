:original_name: nosql_api_0032.html

.. _nosql_api_0032:

Creating a Manual Backup
========================

Function
--------

This API is used to create a manual backup.

Constraints
-----------

This API supports the following instance type:

-  GeminiDB Cassandra

URI
---

POST https://{Endpoint}/v3/{project_id}/instances/{instance_id}/backups

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

.. table:: **Table 2** Request header parameter

   +--------------+-----------+--------+---------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                         |
   +==============+===========+========+=====================================================================+
   | Content-Type | Yes       | String | MIME type of the request body. **application/json** is recommended. |
   +--------------+-----------+--------+---------------------------------------------------------------------+
   | X-Auth-Token | Yes       | String | User token.                                                         |
   +--------------+-----------+--------+---------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                        |
   +=================+=================+=================+====================================================================================================================================================================+
   | name            | Yes             | String          | Manual backup name.                                                                                                                                                |
   |                 |                 |                 |                                                                                                                                                                    |
   |                 |                 |                 | The name can include 4 to 64 characters and must start with a letter. It is case-sensitive and can contain only letters, digits, hyphens (-), and underscores (_). |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description     | Yes             | String          | Manual backup description.                                                                                                                                         |
   |                 |                 |                 |                                                                                                                                                                    |
   |                 |                 |                 | The description can include a maximum of 256 characters and cannot contain the following special characters: >!<"&'=                                               |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 202**

.. table:: **Table 4** Response body parameters

   ========= ====== ===========
   Parameter Type   Description
   ========= ====== ===========
   job_id    String Task ID.
   backup_id String Backup ID.
   ========= ====== ===========

Example Request
---------------

-  URI example

   .. code-block:: text

      POST https://{Endpoint}/v3/054e292c9880d4992f02c0196d3ea468/instances/a4d8ea2584e047439a667703c0684119in06/backups

-  Creating a manual backup

   .. code-block::

      {
        "name" : "backup-4f57",
        "description" : "manual backup"
      }

Example Response
----------------

**Status code: 202**

Success

.. code-block::

   {
     "job_id" : "8061ceaf-b319-4315-9338-7f3de8e26f05",
     "backup_id" : "646d88d0b03f4fd2ae944ae2a33bcb6ain06"
   }

Status Codes
------------

See :ref:`Status Codes <nosql_status_code>`.

Error Codes
-----------

See :ref:`Error Codes <nosql_error_code>`.
