:original_name: nosql_07_0003.html

.. _nosql_07_0003:

Modifying a Parameter Template
==============================

You can modify parameters in a custom parameter template to bring out the best performance of the service.

Note that parameter values in default parameter templates cannot be changed.

.. note::

   Though parameter values in a default template cannot be changed, you can view details about a default parameter template. If a custom parameter template is set incorrectly, the database startup may fail. You can re-configure the custom parameter template according to the configurations of the default parameter template.

Modifying Parameters in a Custom Parameter Template
---------------------------------------------------

#. :ref:`Log in to the GeminiDB console. <nosql_login>`

#. In the navigation pane, choose **Parameter Templates**.

#. On the **Custom Templates** tab, click the target parameter template.

#. Change parameter values as required.

   -  To save the modifications, click **Save**.
   -  To cancel the modifications, click **Cancel**.
   -  To preview the modifications, click **Preview**.

#. After parameters are modified, click **Change History** to view parameter modification details.

   For how to view parameter modification details, see :ref:`Viewing Parameter Change History <nosql_07_0012>`.

   .. important::

      -  The modifications take effect only after you apply the parameter template to DB instances. For details, see :ref:`Applying a Parameter Template <nosql_07_0008>`.
      -  The change history page displays only the modifications of the last seven days.

Modifying Parameters of a Specified DB Instance
-----------------------------------------------

#. :ref:`Log in to the GeminiDB console. <nosql_login>`

#. In the navigation pane, choose **Instances**. Click the target instance. The **Basic Information** page is displayed.

#. In the navigation pane on the left, choose **Parameters**. On the displayed page, modify parameters as required.

   -  To save the modifications, click **Save**.
   -  To cancel the modifications, click **Cancel**.
   -  To preview the modifications, click **Preview**.

#. After parameters are modified, click **Change History** to view parameter modification details.

   For how to view parameter modification details, see :ref:`Viewing Parameter Change History <nosql_07_0012>`.

   .. important::

      After the parameter template is modified, choose whether to reboot the instance based on the information in the **Effective upon Reboot** column.

      -  If the value is **Yes** and the instance status on the **Instances** page is **Pending restart**, restart the instance to apply the changes.
      -  If the value is **No**, the modifications take effect immediately.
