:original_name: nosql_dynamodb_0068.html

.. _nosql_dynamodb_0068:

Changing the vCPUs and Memory of an Instance
============================================

Scenarios
---------

This section describes how to change your instance's vCPUs or memory to suit your workload needs.

Precautions
-----------

-  You can upgrade or downgrade instance specifications.
-  Node specifications are changed using a rolling method. It takes about 5 to 10 minutes to update a single node, and the total duration depends on the number of nodes.
-  During a specification change, computing tasks on the node being updated are offloaded to other nodes. To mitigate the risk of instance overload, change node specifications during off-peak hours.
-  Avoid performing DDL operations during a specification change.

   .. note::

      Data definition language (DDL) is a subset of SQL used to define data structures and database objects. It primarily consists of three statements: CREATE, ALTER, and DROP. DDL is used to create, modify, and delete database objects, such as tables, indexes, views, functions, stored procedures, and triggers.

-  During a specification change, nodes are updated one by one. Brief read/write failures or increased latency may occur on each node during its update. To minimize the impact, perform this operation during off-peak hours.
-  If you force a specification change when the instance is not running properly, this may lead to a brief interruption (within seconds).

Method 1
--------

#. :ref:`Log in to the GeminiDB console <nosql_login>`.

#. On the **Instances** page, click the target instance name.

#. In the **DB Information** area on the **Basic Information** page, click **Change** next to the **Specifications** field.

#. On the displayed page, select the desired vCPUs and memory and click **Next**.

#. On the displayed page, confirm the specifications.

   -  If you need to modify your settings, click **Previous** to go back to the page where you specify details.
   -  If you do not need to modify your settings, click **Submit**.

#. Check the change results.

   Go to the **Basic Information** page and in the **Specifications** area you can see the new specifications.

Method 2
--------

#. :ref:`Log in to the GeminiDB console <nosql_login>`.

#. On the **Instances** page, locate the instance whose specifications you want to change and choose **Change Specifications** in the **Operation** column.

#. On the displayed page, select the desired vCPUs and memory and click **Next**.

#. On the displayed page, confirm the specifications.

   -  If you need to modify your settings, click **Previous** to go back to the page where you specify details.
   -  If you do not need to modify your settings, click **Submit**.

#. Check the change results.

   Go to the **Basic Information** page and in the **Specifications** area you can see the new specifications.
