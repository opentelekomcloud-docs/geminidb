:original_name: nosql_05_0110.html

.. _nosql_05_0110:

Checking Password Strength
==========================

Function
--------

This API is used to check whether the password is weak.

URI
---

POST https://{Endpoint}/v3/{project_id}/weak-password-verification

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

   ========= ========= ====== ==================
   Parameter Mandatory Type   Description
   ========= ========= ====== ==================
   password  Yes       String Database password.
   ========= ========= ====== ==================

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------------------+-----------------------+------------------------------------------+
   | Parameter             | Type                  | Description                              |
   +=======================+=======================+==========================================+
   | weak                  | Boolean               | Whether the password is a weak password. |
   |                       |                       |                                          |
   |                       |                       | -  **true**: It is a weak password.      |
   |                       |                       | -  **false**: It is not a weak password. |
   +-----------------------+-----------------------+------------------------------------------+

Example Requests
----------------

-  URI example

   .. code-block:: text

      POST https://{Endpoint}/v3/619d3e78f61b4be68bc5aa0b59edcf7b/weak-password-verification

-  Checking Password Strength

   .. code-block::

      {
        "password" : "xxxx"
      }

Example Responses
-----------------

**Status code: 200**

Success

.. code-block::

   {
     "weak" : false
   }

Status Codes
------------

See :ref:`Status Codes <nosql_status_code>`.

Error Codes
-----------

See :ref:`Error Codes <nosql_error_code>`.
