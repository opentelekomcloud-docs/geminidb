:original_name: nosql_05_0109.html

.. _nosql_05_0109:

Configuring an Autoscaling Policy for Storage Space
===================================================

Function
--------

This API is used to configure an autoscaling policy for storage space.

Constraints
-----------

-  This API supports GeminiDB Cassandra instances.
-  This API supports both pay-per-use and yearly/monthly instances.
-  If the instance status is not normal, autoscaling of storage space cannot be configured.

URI
---

PUT https://{Endpoint}/v3/{project_id}/instances/disk-auto-expansion

.. table:: **Table 1** Path parameters

   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                    |
   +============+===========+========+================================================================================================================+
   | project_id | Yes       | String | Project ID of a tenant in a region. To obtain this value, see :ref:`Obtaining a Project ID <nosql_projectid>`. |
   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   ============ ========= ====== ===========
   Parameter    Mandatory Type   Description
   ============ ========= ====== ===========
   X-Auth-Token Yes       String User token.
   ============ ========= ====== ===========

.. table:: **Table 3** Request body parameters

   +-----------------+-----------------+------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                                                                         | Description                                                                                            |
   +=================+=================+==============================================================================+========================================================================================================+
   | instance_ids    | Yes             | Array of strings                                                             | IDs of the instances where autoscaling is enabled for storage space. Up to 50 instances are supported. |
   +-----------------+-----------------+------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------+
   | switch_option   | No              | String                                                                       | Whether autoscaling is enabled. The value can be:                                                      |
   |                 |                 |                                                                              |                                                                                                        |
   |                 |                 |                                                                              | -  **on**, indicating that autoscaling is enabled for storage space.                                   |
   |                 |                 |                                                                              | -  **off**, indicating that autoscaling is disabled for storage space.                                 |
   |                 |                 |                                                                              |                                                                                                        |
   |                 |                 |                                                                              | The default value is **on**.                                                                           |
   +-----------------+-----------------+------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------+
   | policy          | No              | Array of :ref:`diskAutoExpansionPolicy <nosql_05_0109__table11976121915105>` | Autoscaling policies for storage space.                                                                |
   +-----------------+-----------------+------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------+

.. _nosql_05_0109__table11976121915105:

.. table:: **Table 4** diskAutoExpansionPolicy

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                                                                                                                  |
   +=================+=================+=================+==============================================================================================================================================================================================================================================================================================================================+
   | threshold       | No              | Integer         | Threshold for triggering autoscaling.                                                                                                                                                                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 | -  GeminiDB Cassandra instances                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 |    -  The value can be **80**, **85**, or **90**.                                                                                                                                                                                                                                                                            |
   |                 |                 |                 |    -  The default threshold is **90**, indicating that autoscaling is enabled when the used storage space exceeds 90% of total storage space or the available storage space is less than 10 GB.                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 | -  GeminiDB Redis instances                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 |    -  The value can be **60**, **65**, **70**, **75**, **80**, **85**, and **90**.                                                                                                                                                                                                                                           |
   |                 |                 |                 |    -  The default threshold is **80**, indicating that autoscaling is enabled when the used storage space exceeds 80% of total storage space.                                                                                                                                                                                |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | step            | No              | Integer         | Autoscaling step (s%).                                                                                                                                                                                                                                                                                                       |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 | -  GeminiDB Cassandra instances                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 |    -  The value can be **10**, **15**, or **20**, and the default value is **10**.                                                                                                                                                                                                                                           |
   |                 |                 |                 |    -  After autoscaling is enabled, storage space will increase by s% automatically.                                                                                                                                                                                                                                         |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 | -  GeminiDB Redis instances                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 |    -  The value can be **10**, **15**, or **20**, and the default value is **20**.                                                                                                                                                                                                                                           |
   |                 |                 |                 |    -  When the storage usage is greater than 98%: If the total storage is less than 600 GB, the storage usage after autoscaling (used storage space/total storage space) will be less than 85%. If the total storage is greater than or equal to 600 GB, the system automatically scales up the storage space by over 90 GB. |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 | .. note::                                                                                                                                                                                                                                                                                                                    |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 |    -  GeminiDB Cassandra instances                                                                                                                                                                                                                                                                                           |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 |       -  If the autoscaling step is not a multiple of 10, round it up.                                                                                                                                                                                                                                                       |
   |                 |                 |                 |       -  The value after the decimal point is rounded. The minimum step is 100 GB by default.                                                                                                                                                                                                                                |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 |    -  GeminiDB Redis instances                                                                                                                                                                                                                                                                                               |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 |       -  The value after the decimal point is rounded. The minimum step is 1 GB by default.                                                                                                                                                                                                                                  |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | size            | No              | Integer         | Storage limit in GB that autoscaling can increase storage space to.                                                                                                                                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 | -  GeminiDB Cassandra instances                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 |    -  Maximum amount that the system can automatically scale up an instance's storage space to must be greater than or equal to 100 GB of the current DB instance storage space. The value must be no less than the total storage of the instance and cannot exceed its maximum storage.                                     |
   |                 |                 |                 |    -  Batch autoscaling does not allow you to specify an upper storage limit. The upper limit is the maximum storage defined by your instance specifications by default.                                                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 | -  GeminiDB Redis instances                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 |    -  Autoscaling does not allow you to specify an upper storage limit. The upper limit is the maximum storage defined by your instance specifications by default.                                                                                                                                                           |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 204**

No response parameters

Example Requests
----------------

-  Enabling the autoscaling policy of storage space

   -  URI example

      .. code-block:: text

         POST https://{Endpoint}/v3/619d3e78f61b4be68bc5aa0b59edcf7b/instances/disk-auto-expansion

   -  Enabling autoscaling for storage space (Set **threshold** to **90**, **step** to **10**, and **size** to **600**.)

      .. code-block::

         {
           "instance_ids" : [ "93e4b3eda14349b1b870f72829bc3b9bin06" ],
           "policy" : {
             "threshold" : 90,
             "step" : 10,
             "size" : 600
           }
         }

-  Disabling the autoscaling policy of storage space

   -  URI example

      .. code-block:: text

         POST https://{Endpoint}/v3/619d3e78f61b4be68bc5aa0b59edcf7b/instances/disk-auto-expansion

   -  Disabling the autoscaling policy of storage space

      .. code-block::

         {
           "instance_ids" : [ "93e4b3eda14349b1b870f72829bc3b9bin06" ],
           "switch_option":"off"
         }

Example Responses
-----------------

**Status code: 204**

No Content

.. code-block::

   { }

Status Codes
------------

For details, see :ref:`Status Codes <nosql_status_code>`.

Error Codes
-----------

For details, see :ref:`Error Codes <nosql_error_code>`.
