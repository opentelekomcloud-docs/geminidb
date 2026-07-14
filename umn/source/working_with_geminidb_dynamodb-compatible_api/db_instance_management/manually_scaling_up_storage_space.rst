:original_name: nosql_dynamodb_0077.html

.. _nosql_dynamodb_0077:

Manually Scaling Up Storage Space
=================================

Scenarios
---------

This section describes how to scale up the storage space of a DB instance to suit your service requirements.

During the scale-up process, the DB instance will not restart, and your services will not be interrupted.

Precautions
-----------

Storage space can only be scaled up, not down.

Procedure
---------

#. :ref:`Log in to the GeminiDB console. <nosql_login>`

#. On the **Instances** page, locate the target instance and click **Scale Storage Space** in the **Operation** column.

   Alternatively, click the instance name. In the **Storage Space** area on the **Basic Information** page, click **Scale**.

#. On the displayed page, specify the new storage capacity and click **Next**.

   For cloud native storage, storage must be scaled up in increments of 10 GB, with a minimum increment of 10 GB.

#. On the displayed page, confirm the storage space.

   -  If you need to modify your settings, click **Previous** to go back to the page where you specify details.
   -  If you do not need to modify your settings, click **Submit** to scale up the storage space.

#. Check the scale-up result.

   -  The status of the DB instance in the instance list is **Scaling up**.
   -  After the scale up is completed, the DB instance status becomes **Available**.
   -  In the **Storage Space** area on the **Basic Information** page, check whether the scale up was successful.
