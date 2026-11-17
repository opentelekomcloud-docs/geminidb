:original_name: nosql_12_0014.html

.. _nosql_12_0014:

Configuring a Storage Autoscaling Policy
========================================

Function
--------

This API is used to configure a storage autoscaling policy.

Constraints
-----------

-  This API can be used for GeminiDB Cassandra and GeminiDB Redis instances.
-  This API supports both pay-per-use and yearly/monthly instances.
-  By default, the system automatically bills new storage for yearly/monthly instances.
-  Autoscaling is available only when your account balance is sufficient.
-  If the instance status is not normal, autoscaling of storage space cannot be configured.
-  This API supports partial updates. The parameters that are not transferred in the request remain unchanged.

URI
---

PUT /v4/{project_id}/instances/disk-auto-expansion

.. table:: **Table 1** URI parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                    |
   +=================+=================+=================+================================================================================================================+
   | project_id      | Yes             | String          | **Definition**                                                                                                 |
   |                 |                 |                 |                                                                                                                |
   |                 |                 |                 | Project ID of a tenant in a region. To obtain this value, see :ref:`Obtaining a Project ID <nosql_projectid>`. |
   |                 |                 |                 |                                                                                                                |
   |                 |                 |                 | **Constraints**                                                                                                |
   |                 |                 |                 |                                                                                                                |
   |                 |                 |                 | N/A                                                                                                            |
   |                 |                 |                 |                                                                                                                |
   |                 |                 |                 | **Range**                                                                                                      |
   |                 |                 |                 |                                                                                                                |
   |                 |                 |                 | N/A                                                                                                            |
   |                 |                 |                 |                                                                                                                |
   |                 |                 |                 | **Default Value**                                                                                              |
   |                 |                 |                 |                                                                                                                |
   |                 |                 |                 | N/A                                                                                                            |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +-----------------+-----------------+-----------------+-------------------+
   | Parameter       | Mandatory       | Type            | Description       |
   +=================+=================+=================+===================+
   | x-auth-token    | Yes             | String          | **Definition**    |
   |                 |                 |                 |                   |
   |                 |                 |                 | User token.       |
   |                 |                 |                 |                   |
   |                 |                 |                 | **Constraints**   |
   |                 |                 |                 |                   |
   |                 |                 |                 | N/A               |
   |                 |                 |                 |                   |
   |                 |                 |                 | **Range**         |
   |                 |                 |                 |                   |
   |                 |                 |                 | N/A               |
   |                 |                 |                 |                   |
   |                 |                 |                 | **Default Value** |
   |                 |                 |                 |                   |
   |                 |                 |                 | N/A               |
   +-----------------+-----------------+-----------------+-------------------+

.. table:: **Table 3** Request body parameters

   +-----------------+-----------------+----------------------------------------------------------------------------+------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                                                                       | Description                                                |
   +=================+=================+============================================================================+============================================================+
   | instance_ids    | Yes             | Array of strings                                                           | **Definition**                                             |
   |                 |                 |                                                                            |                                                            |
   |                 |                 |                                                                            | IDs of the instances where storage autoscaling is enabled. |
   |                 |                 |                                                                            |                                                            |
   |                 |                 |                                                                            | **Constraints**                                            |
   |                 |                 |                                                                            |                                                            |
   |                 |                 |                                                                            | A maximum of 50 instances are supported.                   |
   |                 |                 |                                                                            |                                                            |
   |                 |                 |                                                                            | **Range**                                                  |
   |                 |                 |                                                                            |                                                            |
   |                 |                 |                                                                            | N/A                                                        |
   |                 |                 |                                                                            |                                                            |
   |                 |                 |                                                                            | **Default Value**                                          |
   |                 |                 |                                                                            |                                                            |
   |                 |                 |                                                                            | N/A                                                        |
   +-----------------+-----------------+----------------------------------------------------------------------------+------------------------------------------------------------+
   | switch_option   | No              | String                                                                     | **Definition**                                             |
   |                 |                 |                                                                            |                                                            |
   |                 |                 |                                                                            | Whether autoscaling is enabled.                            |
   |                 |                 |                                                                            |                                                            |
   |                 |                 |                                                                            | **Constraints**                                            |
   |                 |                 |                                                                            |                                                            |
   |                 |                 |                                                                            | N/A                                                        |
   |                 |                 |                                                                            |                                                            |
   |                 |                 |                                                                            | **Range**                                                  |
   |                 |                 |                                                                            |                                                            |
   |                 |                 |                                                                            | -  **on**: Storage autoscaling is enabled.                 |
   |                 |                 |                                                                            | -  **off**: Storage autoscaling is disabled.               |
   |                 |                 |                                                                            |                                                            |
   |                 |                 |                                                                            | **Default Value**                                          |
   |                 |                 |                                                                            |                                                            |
   |                 |                 |                                                                            | **on**                                                     |
   +-----------------+-----------------+----------------------------------------------------------------------------+------------------------------------------------------------+
   | policy          | No              | :ref:`DiskAutoExpansionPolicy <nosql_12_0014__table12356203211549>` object | **Definition**                                             |
   |                 |                 |                                                                            |                                                            |
   |                 |                 |                                                                            | Storage autoscaling policy.                                |
   |                 |                 |                                                                            |                                                            |
   |                 |                 |                                                                            | **Constraints**                                            |
   |                 |                 |                                                                            |                                                            |
   |                 |                 |                                                                            | N/A                                                        |
   |                 |                 |                                                                            |                                                            |
   |                 |                 |                                                                            | **Range**                                                  |
   |                 |                 |                                                                            |                                                            |
   |                 |                 |                                                                            | N/A                                                        |
   |                 |                 |                                                                            |                                                            |
   |                 |                 |                                                                            | **Default Value**                                          |
   |                 |                 |                                                                            |                                                            |
   |                 |                 |                                                                            | N/A                                                        |
   +-----------------+-----------------+----------------------------------------------------------------------------+------------------------------------------------------------+

.. _nosql_12_0014__table12356203211549:

.. table:: **Table 4** DiskAutoExpansionPolicy

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                                                                                                                                                                  |
   +=================+=================+=================+==============================================================================================================================================================================================================================================================================================================================================================================+
   | threshold       | No              | Integer         | **Definition**                                                                                                                                                                                                                                                                                                                                                               |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 | Threshold for triggering autoscaling.                                                                                                                                                                                                                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 | **Constraints**                                                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 | N/A                                                                                                                                                                                                                                                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 | **Range**                                                                                                                                                                                                                                                                                                                                                                    |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 | -  The value of a GeminiDB Cassandra instance can be **80**, **85**, or **90**.                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 | -  The value of a GeminiDB Redis instance can be **60**, **65**, **70**, **75**, **80**, **85**, or **90**.                                                                                                                                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 | **Default Value**                                                                                                                                                                                                                                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 | -  The default threshold of a GeminiDB Cassandra instance is **90**, which indicates autoscaling is enabled when the used storage exceeds 90% of total storage or the available storage is less than 10 GB.                                                                                                                                                                  |
   |                 |                 |                 | -  The default threshold of a GeminiDB Redis instance is **80**, which indicates that autoscaling is enabled when the used storage exceeds 80% of total storage.                                                                                                                                                                                                             |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | step            | No              | Integer         | **Definition**                                                                                                                                                                                                                                                                                                                                                               |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 | Scaling step when the storage is scaled by percentage.                                                                                                                                                                                                                                                                                                                       |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 | **Constraints**                                                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 | -  GeminiDB Cassandra                                                                                                                                                                                                                                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 |    -  If the autoscaling step is not a multiple of 10, round it up.                                                                                                                                                                                                                                                                                                          |
   |                 |                 |                 |    -  The value after the decimal point is rounded. The minimum step is 100 GB by default.                                                                                                                                                                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 | -  GeminiDB Redis                                                                                                                                                                                                                                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 |    -  The value after the decimal point is rounded. The minimum step is 1 GB by default.                                                                                                                                                                                                                                                                                     |
   |                 |                 |                 |    -  If your account balance is insufficient, storage autoscaling for yearly/monthly instances will fail.                                                                                                                                                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 | **Range**                                                                                                                                                                                                                                                                                                                                                                    |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 | -  GeminiDB Cassandra                                                                                                                                                                                                                                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 |    -  The value can be **10**, **15**, or **20**, and the default value is **10**.                                                                                                                                                                                                                                                                                           |
   |                 |                 |                 |    -  After autoscaling is enabled, storage will automatically increase by the percentage specified for this parameter.                                                                                                                                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 | -  GeminiDB Redis                                                                                                                                                                                                                                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 |    -  The value can be **10**, **15**, or **20**, and the default value is **20**.                                                                                                                                                                                                                                                                                           |
   |                 |                 |                 |    -  When the storage usage is greater than 98%: If the total storage is less than 600 GB, the system automatically scales up storage to ensure that the storage usage (used storage space/total storage space) after autoscaling will be less than 85%. If the total storage is greater than or equal to 600 GB, the system automatically scales up storage by over 90 GB. |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 | **Default Value**                                                                                                                                                                                                                                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 | -  GeminiDB Cassandra                                                                                                                                                                                                                                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 |    -  **10**                                                                                                                                                                                                                                                                                                                                                                 |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 | -  GeminiDB Redis                                                                                                                                                                                                                                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 |    -  **20**                                                                                                                                                                                                                                                                                                                                                                 |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | size            | No              | Integer         | **Definition**                                                                                                                                                                                                                                                                                                                                                               |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 | Maximum storage that can be reached through autoscaling, in GB.                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 | **Constraints**                                                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 | -  GeminiDB Cassandra                                                                                                                                                                                                                                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 |    -  The maximum storage must be greater than or equal to the current storage plus 100 GB, but cannot exceed what your instance specifications allow.                                                                                                                                                                                                                       |
   |                 |                 |                 |    -  The value of this parameter cannot be specified when you configure storage autoscaling for multiple instances. By default, storage will scale up to the maximum allowed by your instance specifications.                                                                                                                                                               |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 | -  GeminiDB Redis                                                                                                                                                                                                                                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 |    -  The maximum storage must be greater than or equal to the current storage plus 1 GB, but cannot exceed what your instance specifications allow.                                                                                                                                                                                                                         |
   |                 |                 |                 |    -  The value of this parameter cannot be specified when you configure storage autoscaling for multiple instances. By default, storage will scale up to the maximum allowed by your instance specifications.                                                                                                                                                               |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 | **Range**                                                                                                                                                                                                                                                                                                                                                                    |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 | N/A                                                                                                                                                                                                                                                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 | **Default Value**                                                                                                                                                                                                                                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 | N/A                                                                                                                                                                                                                                                                                                                                                                          |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 5** Response body parameters

   +-----------------------+--------------------------------------------------------------------+--------------------------------------------------------------------------+
   | Parameter             | Type                                                               | Description                                                              |
   +=======================+====================================================================+==========================================================================+
   | results               | Array of :ref:`Table 6 <nosql_12_0014__table122669393412>` objects | **Definition**                                                           |
   |                       |                                                                    |                                                                          |
   |                       |                                                                    | Results of configuring the storage autoscaling policy for the instances. |
   |                       |                                                                    |                                                                          |
   |                       |                                                                    | **Range**                                                                |
   |                       |                                                                    |                                                                          |
   |                       |                                                                    | N/A                                                                      |
   +-----------------------+--------------------------------------------------------------------+--------------------------------------------------------------------------+

.. _nosql_12_0014__table122669393412:

.. table:: **Table 6** DiskAutoExpansionResultV4

   +-----------------------+-----------------------+--------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                              |
   +=======================+=======================+==========================================================================+
   | instance_id           | String                | **Definition**                                                           |
   |                       |                       |                                                                          |
   |                       |                       | Instance ID.                                                             |
   |                       |                       |                                                                          |
   |                       |                       | **Range**                                                                |
   |                       |                       |                                                                          |
   |                       |                       | N/A                                                                      |
   +-----------------------+-----------------------+--------------------------------------------------------------------------+
   | status                | String                | **Definition**                                                           |
   |                       |                       |                                                                          |
   |                       |                       | Operation status.                                                        |
   |                       |                       |                                                                          |
   |                       |                       | **Range**                                                                |
   |                       |                       |                                                                          |
   |                       |                       | -  **success**: The operation is successful.                             |
   |                       |                       | -  **failed**: The operation failed.                                     |
   +-----------------------+-----------------------+--------------------------------------------------------------------------+
   | error_message         | String                | **Definition**                                                           |
   |                       |                       |                                                                          |
   |                       |                       | Error message. This parameter is returned only when the operation fails. |
   |                       |                       |                                                                          |
   |                       |                       | **Range**                                                                |
   |                       |                       |                                                                          |
   |                       |                       | N/A                                                                      |
   +-----------------------+-----------------------+--------------------------------------------------------------------------+

**Status code: 207**

.. table:: **Table 7** Response body parameter

   +-----------------------+--------------------------------------------------------------------+--------------------------------------------------------------------------+
   | Parameter             | Type                                                               | Description                                                              |
   +=======================+====================================================================+==========================================================================+
   | results               | Array of :ref:`Table 8 <nosql_12_0014__table847203711353>` objects | **Definition**                                                           |
   |                       |                                                                    |                                                                          |
   |                       |                                                                    | Results of configuring the storage autoscaling policy for the instances. |
   |                       |                                                                    |                                                                          |
   |                       |                                                                    | **Range**                                                                |
   |                       |                                                                    |                                                                          |
   |                       |                                                                    | N/A                                                                      |
   +-----------------------+--------------------------------------------------------------------+--------------------------------------------------------------------------+

.. _nosql_12_0014__table847203711353:

.. table:: **Table 8** DiskAutoExpansionResultV4

   +-----------------------+-----------------------+--------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                              |
   +=======================+=======================+==========================================================================+
   | instance_id           | String                | **Definition**                                                           |
   |                       |                       |                                                                          |
   |                       |                       | Instance ID.                                                             |
   |                       |                       |                                                                          |
   |                       |                       | **Range**                                                                |
   |                       |                       |                                                                          |
   |                       |                       | N/A                                                                      |
   +-----------------------+-----------------------+--------------------------------------------------------------------------+
   | status                | String                | **Definition**                                                           |
   |                       |                       |                                                                          |
   |                       |                       | Operation status.                                                        |
   |                       |                       |                                                                          |
   |                       |                       | **Range**                                                                |
   |                       |                       |                                                                          |
   |                       |                       | -  **success**: The operation is successful.                             |
   |                       |                       | -  **failed**: The operation failed.                                     |
   +-----------------------+-----------------------+--------------------------------------------------------------------------+
   | error_message         | String                | **Definition**                                                           |
   |                       |                       |                                                                          |
   |                       |                       | Error message. This parameter is returned only when the operation fails. |
   |                       |                       |                                                                          |
   |                       |                       | **Range**                                                                |
   |                       |                       |                                                                          |
   |                       |                       | N/A                                                                      |
   +-----------------------+-----------------------+--------------------------------------------------------------------------+

**Status code: 400**

.. table:: **Table 9** Response body parameter

   +-----------------------+-----------------------------------------------------------------------+--------------------------------------------------------------------------+
   | Parameter             | Type                                                                  | Description                                                              |
   +=======================+=======================================================================+==========================================================================+
   | results               | Array of :ref:`Table 10 <nosql_12_0014__table16511537163510>` objects | **Definition**                                                           |
   |                       |                                                                       |                                                                          |
   |                       |                                                                       | Results of configuring the storage autoscaling policy for the instances. |
   |                       |                                                                       |                                                                          |
   |                       |                                                                       | **Range**                                                                |
   |                       |                                                                       |                                                                          |
   |                       |                                                                       | N/A                                                                      |
   +-----------------------+-----------------------------------------------------------------------+--------------------------------------------------------------------------+

.. _nosql_12_0014__table16511537163510:

.. table:: **Table 10** DiskAutoExpansionResultV4

   +-----------------------+-----------------------+--------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                              |
   +=======================+=======================+==========================================================================+
   | instance_id           | String                | **Definition**                                                           |
   |                       |                       |                                                                          |
   |                       |                       | Instance ID.                                                             |
   |                       |                       |                                                                          |
   |                       |                       | **Range**                                                                |
   |                       |                       |                                                                          |
   |                       |                       | N/A                                                                      |
   +-----------------------+-----------------------+--------------------------------------------------------------------------+
   | status                | String                | **Definition**                                                           |
   |                       |                       |                                                                          |
   |                       |                       | Operation status.                                                        |
   |                       |                       |                                                                          |
   |                       |                       | **Range**                                                                |
   |                       |                       |                                                                          |
   |                       |                       | -  **success**: The operation is successful.                             |
   |                       |                       | -  **failed**: The operation failed.                                     |
   +-----------------------+-----------------------+--------------------------------------------------------------------------+
   | error_message         | String                | **Definition**                                                           |
   |                       |                       |                                                                          |
   |                       |                       | Error message. This parameter is returned only when the operation fails. |
   |                       |                       |                                                                          |
   |                       |                       | **Range**                                                                |
   |                       |                       |                                                                          |
   |                       |                       | N/A                                                                      |
   +-----------------------+-----------------------+--------------------------------------------------------------------------+

Example Request
---------------

-  Enabling autoscaling

   .. code-block:: text

      PUT https://{endpoint}/v4/619d3e78f61b4be68bc5aa0b59edcf7b/instances/disk-auto-expansion

       {
         "instance_ids" : [ "93e4b3eda14349b1b870f72829bc3b9bin06","1234567890abcdef1234567890abcdefin06"],
         "policy" : {
           "threshold" : 90,
           "step" : 10,
           "size" : 600
         }
       }

-  Disabling autoscaling

   .. code-block:: text

      PUT https://{endpoint}/v4/619d3e78f61b4be68bc5aa0b59edcf7b/instances/disk-auto-expansion

       {
         "instance_ids" : [ "93e4b3eda14349b1b870f72829bc3b9bin06","1234567890abcdef1234567890abcdefin06" ],
         "switch_option" : "off"
       }

Example Response
----------------

-  **Status code: 200**

   OK

   Example response when the operation is successful on all instances:

   .. code-block::

      {
        "results" : [ {
          "instance_id" : "93e4b3eda14349b1b870f72829bc3b9bin06",
          "status" : "success"
        }, {
          "instance_id" : "1234567890abcdef1234567890abcdefin06",
          "status" : "success"
        } ]
      }

-  **Status code: 207**

   Multi-Status

   Example response when the operation is successful on part of the instances:

   .. code-block::

      {
        "results" : [ {
          "instance_id" : "93e4b3eda14349b1b870f72829bc3b9bin06",
          "status" : "success"
        }, {
          "instance_id" : "1234567890abcdef1234567890abcdefin06",
          "status" : "failed",
          "error_message" : "Instance error"
        } ]
      }

-  **Status code: 400**

   Bad Request

   Example response when the operation fails on all instances:

   .. code-block::

      {
        "results" : [ {
          "instance_id" : "93e4b3eda14349b1b870f72829bc3b9bin06",
          "status" : "failed",
          "error_message" : "Instance error"
        }, {
          "instance_id" : "1234567890abcdef1234567890abcdefin06",
          "status" : "failed",
          "error_message" : "Instance error"
        } ]
      }

Status Codes
------------

See :ref:`Status Codes <nosql_status_code>`.

Error Codes
-----------

See :ref:`Error Codes <nosql_error_code>`.
