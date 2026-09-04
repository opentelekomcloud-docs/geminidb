:original_name: nosql_03_0213.html

.. _nosql_03_0213:

Adding Nodes
============

Scenarios
---------

This section describes how to add nodes to a DB instance to suit your service requirements. A node cannot be deleted after being added.

Usage Notes
-----------

-  Adding nodes may lead to the decrease of OPS. You are advised to perform this operation during off-peak hours.
-  You can only add nodes when the instance status is **Available** or **Checking restoration**.
-  A DB instance cannot be deleted when one or more nodes are being added.

Method 1
--------

#. :ref:`Log in to the GeminiDB console <nosql_login>`.
#. On the **Instances** page, click the target instance.
#. In the **Node Information** area on the **Basic Information** page, click **Add Node**.
#. Specify **Add Nodes** and click **Next**.

   -  By default, the specifications of new nodes are the same as the instance specifications and cannot be modified.
   -  A GeminiDB Influx instance supports a maximum of nine nodes.

#. On the displayed page, confirm node configurations.

   -  To modify the configuration, click **Previous** to go back to the page where you specify details.
   -  If you do not need to modify your settings, click **Submit** to add the nodes.

#. View the result of adding nodes.

   -  The status of the DB instance in the instance list is **Adding node**.
   -  After the nodes are added, the DB instance status becomes **Available**.
   -  Click the DB instance name. In the **Node Information** area on the **Basic Information** page, view the information about the new nodes.

Method 2
--------

#. :ref:`Log in to the GeminiDB console <nosql_login>`.
#. On the **Instances** page, locate the target instance and choose **More** > **Add Node** in the **Operation** column.
#. Specify **Add Nodes** and click **Next**.

   -  By default, the specifications of new nodes are the same as the instance specifications and cannot be modified.

#. On the displayed page, confirm node configurations.

   -  To modify the configuration, click **Previous** to go back to the page where you specify details.
   -  If you do not need to modify your settings, click **Submit** to add the nodes.

#. View the result of adding nodes.

   -  The status of the DB instance in the instance list is **Adding node**.
   -  After the nodes are added, the DB instance status becomes **Available**.
   -  Click the DB instance name. In the **Node Information** area on the **Basic Information** page, view the information about the new nodes.
