:original_name: nosql_database_version.html

.. _nosql_database_version:

Querying Version Information
============================

Function
--------

This API is used to query version information of a specified type of instances.

Constraints
-----------

This API can be used for GeminiDB Cassandra instances.

URI
---

GET https://{Endpoint}/v3/{project_id}/datastores/{datastore_name}/versions

.. table:: **Table 1** URI parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                    |
   +=================+=================+=================+================================================================================================================+
   | project_id      | Yes             | String          | Project ID of a tenant in a region. To obtain this value, see :ref:`Obtaining a Project ID <nosql_projectid>`. |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------+
   | datastore_name  | Yes             | String          | Database type. The value can be:                                                                               |
   |                 |                 |                 |                                                                                                                |
   |                 |                 |                 | -  **cassandra**, indicating that the instances are of the GeminiDB Cassandra type.                            |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameter

   ============ ========= ====== ===========
   Parameter    Mandatory Type   Description
   ============ ========= ====== ===========
   X-Auth-Token Yes       String User token
   ============ ========= ====== ===========

Response Parameters
-------------------

Status code: 200

.. table:: **Table 3** Response body parameter

   +-----------------------+-----------------------+-----------------------------------------------+
   | Parameter             | Type                  | Description                                   |
   +=======================+=======================+===============================================+
   | versions              | Array of strings      | Database version. The supported versions are: |
   |                       |                       |                                               |
   |                       |                       | -  GeminiDB Cassandra instance 3.11           |
   +-----------------------+-----------------------+-----------------------------------------------+

Example Request
---------------

URI example

.. code-block:: text

   GET https://{Endpoint}/v3/375d8d8fad1f43039e23d3b6c0f60a19/datastores/cassandra/versions

Example Response
----------------

Status code: 200

Success

.. code-block::

   {
     "versions" : [ "3.11" ]
   }

Status Codes
------------

See :ref:`Status Codes <nosql_status_code>`.

Error Codes
-----------

See :ref:`Error Codes <nosql_error_code>`.
