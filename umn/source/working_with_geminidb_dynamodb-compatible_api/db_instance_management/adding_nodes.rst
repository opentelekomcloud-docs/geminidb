:original_name: nosql_dynamodb_0072.html

.. _nosql_dynamodb_0072:

Adding Nodes
============

Scenarios
---------

This section describes how to add nodes to your DB instance to match the increasing data volume. You can also delete nodes if the volume decreases. For details, see :ref:`Deleting Nodes <nosql_03_0004>`.

Precautions
-----------

-  Adding nodes may lead to the decrease of operations per second (OPS). You are advised to perform this operation during off-peak hours.
-  You can only add nodes when the instance status is **Available** or **Checking restoration**.
-  A DB instance cannot be deleted when one or more nodes are being added.

Procedure
---------

#. :ref:`Log in to the GeminiDB console. <nosql_login>`

#. **Method 1**

   On the **Instances** page, click the target instance name.

   In the **Node Information** area on the **Basic Information** page, click **Add Node**.

   **Method 2**

   On the **Instances** page, locate the target instance and choose **More** > **Add Node** in the **Operation** column.

#. On the **Add Node** page, specify **New Nodes** and click **Next**.

   .. note::

      -  New nodes have the same specifications as the instance by default and cannot be changed.
      -  New nodes and the instance can be in different subnets of the same VPC.

#. On the displayed page, confirm the node configuration details.

   -  If you need to modify your settings, click **Previous** to go back to the page where you specify details.
   -  If you do not need to modify your settings, click **Submit** to add the nodes.

#. View the result of adding nodes.

   -  The status of the DB instance in the instance list is **Adding node**.
   -  After the nodes are added, the DB instance status becomes **Available**.
   -  Click the DB instance name. In the **Node Information** area on the **Basic Information** page, view the information about the new nodes.
