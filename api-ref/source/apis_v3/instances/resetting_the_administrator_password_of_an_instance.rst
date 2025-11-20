:original_name: nosql_05_0101.html

.. _nosql_05_0101:

Resetting the Administrator Password of an Instance
===================================================

Function
--------

This API is used to reset the administrator password of an instance.

Constraints
-----------

This API can be used for GeminiDB Cassandra instances.

Abnormal instances do not support this operation.

Only the password of user **rwuser** can be reset.

URI
---

PUT https://{Endpoint}/v3/{project_id}/instances/{instance_id}/password

.. table:: **Table 1** URI parameters

   +-------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                                    |
   +=============+===========+========+================================================================================================================+
   | project_id  | Yes       | String | Project ID of a tenant in a region. To obtain this value, see :ref:`Obtaining a Project ID <nosql_projectid>`. |
   +-------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Instance ID.                                                                                                   |
   +-------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+

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

.. table:: **Table 3** Request body parameter

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                              |
   +=================+=================+=================+==========================================================================================================================================================================================+
   | password        | Yes             | String          | Database password.                                                                                                                                                                       |
   |                 |                 |                 |                                                                                                                                                                                          |
   |                 |                 |                 | The password can include 8 to 32 characters and contain uppercase letters, lowercase letters, digits, and a combination of any two of the following special characters: ``~!@#%^*-_=+?`` |
   |                 |                 |                 |                                                                                                                                                                                          |
   |                 |                 |                 | Enter a strong password against security risks such as brute force cracking.                                                                                                             |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

Status code: 204

None

Example Request
---------------

-  URI example

   .. code-block:: text

      PUT https://{Endpoint}/v3/375d8d8fad1f43039e23d3b6c0f60a19/instances/9136fd2a9fcd405ea4674276ce36dae8in06/password

-  Resetting the administrator password of an instance to **\*****\***

   .. code-block::

      {
        "password" : "******"
      }

Example Response
----------------

**Status code: 204**

No Content

Status Codes
------------

See :ref:`Status Codes <nosql_status_code>`.

Error Codes
-----------

See :ref:`Error Codes <nosql_error_code>`.
