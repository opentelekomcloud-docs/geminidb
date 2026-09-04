:original_name: nosql_cassandra_storage_001.html

.. _nosql_cassandra_storage_001:

Manually Scaling Down Storage Space
===================================

Scenarios
---------

As data volumes decrease, you can scale down storage to avoid underutilization of database nodes and unnecessary resource consumption.

Precautions
-----------

-  Before scaling down storage, ensure that the target storage capacity is greater than 125% of the used storage, rounded up to the nearest integer.
-  The minimum adjustment is 1 GB per operation, and the value must be an integer.
-  **Storage scaling does not require an instance restart and has no impact on existing data, services, or databases.**

Procedure
---------

#. :ref:`Log in to the GeminiDB console. <nosql_login>`

#. On the **Instances** page, locate the target instance and click **Scale Storage Space** in the **Operation** column.

   Alternatively, click the instance name. In the **Storage Space** area on the **Basic Information** page, click **Scale**.

#. On the displayed page, specify new storage and click **Next**.

#. On the displayed page, confirm the storage space.

   -  If you need to modify your settings, click **Previous** to go back to the page for you to specify details.
   -  If you do not need to modify your settings, click **Submit** to scale down the storage space.

#. Check the scale-down result.

   -  After the scale-down operation is complete, the instance status changes to **Available**.
   -  Click the instance name. In the **Storage Space** area on the **Basic Information** page, check the new storage space.
