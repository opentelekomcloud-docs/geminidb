:original_name: topic_300000015.html

.. _topic_300000015:

Querying Tags of a Specified Project
====================================

Function
--------

This API is used to query tags of a specified project.

URI
---

GET https://{Endpoint}/v3/{project_id}/tags

.. table:: **Table 1** URI parameters

   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                    |
   +============+===========+========+================================================================================================================+
   | project_id | Yes       | String | Project ID of a tenant in a region. To obtain this value, see :ref:`Obtaining a Project ID <nosql_projectid>`. |
   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query parameters

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                               |
   +=================+=================+=================+===========================================================================================================+
   | offset          | No              | Integer         | Index offset.                                                                                             |
   |                 |                 |                 |                                                                                                           |
   |                 |                 |                 | -  The query starts from the next piece of data indexed by this parameter. The value is **0** by default. |
   |                 |                 |                 | -  The value must be a non-negative number.                                                               |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------+
   | limit           | No              | Integer         | Maximum records to be queried.                                                                            |
   |                 |                 |                 |                                                                                                           |
   |                 |                 |                 | -  The value ranges from **1** to **100**.                                                                |
   |                 |                 |                 | -  If this parameter is not transferred, the first 100 records are queried by default.                    |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------+

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

   +-------------+------------------------------------------------------------------+--------------------------+
   | Parameter   | Type                                                             | Description              |
   +=============+==================================================================+==========================+
   | tags        | Array of :ref:`Tag <topic_300000015__table219011824212>` objects | All tags.                |
   +-------------+------------------------------------------------------------------+--------------------------+
   | total_count | Integer                                                          | Total number of records. |
   +-------------+------------------------------------------------------------------+--------------------------+

.. _topic_300000015__table219011824212:

.. table:: **Table 5** Tag

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                              |
   +=======================+=======================+==========================================================================================================================================+
   | type                  | String                | Tag type. The value can be:                                                                                                              |
   |                       |                       |                                                                                                                                          |
   |                       |                       | -  **user**                                                                                                                              |
   |                       |                       | -  **system**                                                                                                                            |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | key                   | String                | Tag key. The tag key must be specified and can include a maximum of 36 Unicode characters.                                               |
   |                       |                       |                                                                                                                                          |
   |                       |                       | The key is case-sensitive and can contain digits, uppercase letters, lowercase letters, underscores (_), and hyphens (-).                |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | values                | Array of strings      | Tag values. The value can include a maximum of 43 Unicode characters and can also be an empty string.                                    |
   |                       |                       |                                                                                                                                          |
   |                       |                       | The value is case-sensitive and can contain digits, uppercase letters, lowercase letters, underscores (_), periods (.), and hyphens (-). |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+

Example Requests
----------------

URI example

.. code-block:: text

   GET https://{Endpoint}/v3/0549b4a43100d4f32f51c01c2fe4acdb/tags?offset=1&limit=10

Example Responses
-----------------

**Status code: 200**

Success

.. code-block::

   {
     "tags" : [ {
       "key" : "key1",
       "values" : [ "value1", "value2" ],
       "type" : "user"
     }, {
       "key" : "key2",
       "values" : [ "value1", "value2" ],
       "type" : "system"
     } ],
     "total_count" : 2
   }

Status Codes
------------

See :ref:`Status Codes <nosql_status_code>`.

Error Codes
-----------

See :ref:`Error Codes <nosql_error_code>`.
