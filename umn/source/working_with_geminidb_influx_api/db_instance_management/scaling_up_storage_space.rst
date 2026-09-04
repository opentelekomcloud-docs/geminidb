:original_name: nosql_09_0050.html

.. _nosql_09_0050:

Scaling Up Storage Space
========================

Scenarios
---------

This section describes how to scale up the storage space of a DB instance to suit your service requirements.

During the scale-up process, the DB instance will not restart, and your services will not be interrupted.

Usage Notes
-----------

Storage space can only be scaled up. It cannot be scaled down.

Method 1
--------

#. :ref:`Log in to the GeminiDB console <nosql_login>`.

#. On the **Instances** page, click the target instance.

#. In the **Storage Space** area on the **Basic Information** page, click **Scale**.

#. On the displayed page, specify the new storage capacity and click **Next**.

   Select at least 10 GB each time, and the value must be an integer.

#. On the displayed page, confirm the storage space.

   -  If you need to modify your settings, click **Previous** to go back to the page where you specify details.
   -  If you do not need to modify your settings, click **Submit** to scale up the storage space.

#. Check the scale-up result.

   -  The status of the DB instance in the instance list is **Scaling up**.
   -  After the scale up is completed, the DB instance status becomes **Available**.
   -  In the **Storage Space** area on the **Basic Information** page, check whether the scale up was successful.

Method 2
--------

#. :ref:`Log in to the GeminiDB console <nosql_login>`.

#. On the **Instances** page, locate the target instance and choose **More** > **Scale Storage Space** in the **Operation** column.

#. On the displayed page, specify the new storage capacity and click **Next**.

   Select at least 10 GB each time, and the value must be an integer.

#. On the displayed page, confirm the storage space.

   -  If you need to modify your settings, click **Previous** to go back to the page where you specify details.
   -  If you do not need to modify your settings, click **Submit** to scale up the storage space.

#. Check the scale-up result.

   -  The status of the DB instance in the instance list is **Scaling up**.
   -  After the scale up is completed, the DB instance status becomes **Available**.
   -  In the **Storage Space** area on the **Basic Information** page, check whether the scale up was successful.
