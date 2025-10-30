:original_name: nosql_05_0156.html

.. _nosql_05_0156:

Querying Changeable Specifications
==================================

Function
--------

This API is used to query instance specifications that can be changed.

Constraints
-----------

This API can be used for GeminiDB Cassandra instances.

URI
---

GET https://{Endpoint}/v3/{project_id}/instances/{instance_id}/available-flavors

.. table:: **Table 1** URI parameters

   +-------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                                    |
   +=============+===========+========+================================================================================================================+
   | project_id  | Yes       | String | Project ID of a tenant in a region. To obtain this value, see :ref:`Obtaining a Project ID <nosql_projectid>`. |
   +-------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Instance ID.                                                                                                   |
   +-------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query parameters

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                               |
   +=================+=================+=================+===========================================================================================================+
   | offset          | No              | Integer         | Index offset.                                                                                             |
   |                 |                 |                 |                                                                                                           |
   |                 |                 |                 | -  The query starts from the next piece of data indexed by this parameter. The value is **0** by default. |
   |                 |                 |                 | -  The value must be a positive integer.                                                                  |
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
   X-Auth-Token Yes       String User token.
   ============ ========= ====== ===========

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +------------------+------------------------------------------------------------------------+-------------------------------------------------------------------------------------+
   | Parameter        | Type                                                                   | Description                                                                         |
   +==================+========================================================================+=====================================================================================+
   | instance_id      | String                                                                 | Instance ID.                                                                        |
   +------------------+------------------------------------------------------------------------+-------------------------------------------------------------------------------------+
   | instance_name    | String                                                                 | Instance name.                                                                      |
   +------------------+------------------------------------------------------------------------+-------------------------------------------------------------------------------------+
   | current_flavor   | :ref:`ComputeFlavor <nosql_05_0156__table1629833693119>` object        | Instance specifications.                                                            |
   +------------------+------------------------------------------------------------------------+-------------------------------------------------------------------------------------+
   | optional_flavors | :ref:`OptionalFlavorsInfo <nosql_05_0156__table12981191752319>` object | Available specification options that the instance specifications can be changed to. |
   +------------------+------------------------------------------------------------------------+-------------------------------------------------------------------------------------+

.. _nosql_05_0156__table1629833693119:

.. table:: **Table 5** ComputeFlavor

   ============= ================== ===================
   Parameter     Type               Description
   ============= ================== ===================
   vcpus         String             Number of vCPUs.
   ram           String             Memory size in GB.
   spec_code     String             Specification code.
   az_status     Map<String,String> AZ status.
   region_status String             Region status.
   ============= ================== ===================

.. _nosql_05_0156__table12981191752319:

.. table:: **Table 6** OptionalFlavorsInfo

   +-------------+--------------------------------------------------------------------------+-------------------------------------------------------------------------------------+
   | Parameter   | Type                                                                     | Description                                                                         |
   +=============+==========================================================================+=====================================================================================+
   | list        | Array of :ref:`ComputeFlavor <nosql_05_0156__table1629833693119>` object | Available specification options that the instance specifications can be changed to. |
   +-------------+--------------------------------------------------------------------------+-------------------------------------------------------------------------------------+
   | total_count | Integer                                                                  | Total number of records.                                                            |
   +-------------+--------------------------------------------------------------------------+-------------------------------------------------------------------------------------+

Example Request
---------------

-  URI example

   .. code-block:: text

      GET https://{Endpoint}/v3/0549b4a43100d4f32f51c01c2fe4acdb/instances/094424666ef04f79a2dfbe9f5b8b31a5in06/available-flavors

-  Example request body

   None

Example Response
----------------

Status code: 200

Success

.. code-block::

   {
     "instance_id" : "094424666ef04f79a2dfbe9f5b8b31a5in06",
     "instance_name" : "geminidb_instance_noreuse_0_ZKv2FSkxgoc3F8bGzsaxNg",
     "current_flavor" : {
       "vcpus" : "4",
       "ram" : "16",
       "spec_code" : "geminidb.cassandra.xlarge.4",
       "az_status" : {
         "az2***" : "unknown",
         "az1***" : "normal",
         "az3***" : "unknown"
       },
       "region_status" : null
     },
     "optional_flavors" : {
       "list" : [ {
         "vcpus" : "2",
         "ram" : "8",
         "spec_code" : "geminidb.cassandra.large.4",
         "az_status" : {
           "az2***" : "unknown",
           "az1***" : "normal",
           "az4***" : "normal",
           "az3***" : "unknown"
         },
         "region_status" : "normal"
       }, {
         "vcpus" : "8",
         "ram" : "32",
         "spec_code" : "geminidb.cassandra.2xlarge.4",
         "az_status" : {
           "az2***" : "unknown",
           "az1***" : "normal",
           "az3***" : "unknown"
         },
         "region_status" : "normal"
       }, {
         "vcpus" : "16",
         "ram" : "64",
         "spec_code" : "geminidb.cassandra.4xlarge.4",
         "az_status" : {
           "az2***" : "unknown",
           "az1***" : "normal",
           "az3***" : "unknown"
         },
         "region_status" : "normal"
       }, {
         "vcpus" : "32",
         "ram" : "128",
         "spec_code" : "geminidb.cassandra.8xlarge.4",
         "az_status" : {
           "az2***" : "unknown",
           "az1***" : "normal",
           "az3***" : "unknown"
         },
         "region_status" : "normal"
       } ],
       "total_count": 4
     }
   }

Status Codes
------------

See :ref:`Status Codes <nosql_status_code>`.

Error Codes
-----------

See :ref:`Error Codes <nosql_error_code>`.
