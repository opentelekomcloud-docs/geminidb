:original_name: nosql_dynamodb_0074.html

.. _nosql_dynamodb_0074:

Deleting Nodes
==============

Scenarios
---------

You can delete nodes that are no longer used to release resources.

Precautions
-----------

Deleted nodes cannot be recovered. Exercise caution when performing this operation.

Procedure
---------

#. :ref:`Log in to the GeminiDB console. <nosql_login>`
#. On the **Instances** page, click the target instance name.
#. In the **Node Information** area on the **Basic Information** page, locate the node you want to delete and click **Delete** in the **Operation** column.
#. In the displayed dialog box, click **Yes**.

   -  When nodes are being deleted, the instance status is **Deleting node**.
   -  After nodes are deleted, the instance status changes to **Available**.
