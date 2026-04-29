:original_name: nosql_03_0212.html

.. _nosql_03_0212:

Restarting a DB Instance
========================

Scenarios
---------

You may need to occasionally restart a DB instance to perform routine maintenance.

Precautions
-----------

-  If the instance status is **Available**, **Abnormal**, or **Checking restoration**, you can restart the instance.
-  Restarting a DB instance interrupts services, so exercise caution when performing this operation.
-  If you restart a DB instance, all nodes in the instance are also restarted.


Restarting a DB Instance
------------------------

#. :ref:`Log in to the GeminiDB console. <nosql_login>`

#. On the **Instances** page, locate the target instance and choose **More** > **Restart** in the **Operation** column.

   Alternatively, click the target DB instance, and on the displayed **Basic Information** page, click **Restart** in the upper right corner of the page.

#. In the displayed dialog box, click **Yes**.

   For GeminiDB Influx instances, you can restart several nodes at the same time or in sequence based on service requirements.
