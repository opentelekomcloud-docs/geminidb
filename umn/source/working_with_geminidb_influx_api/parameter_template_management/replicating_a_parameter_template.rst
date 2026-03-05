:original_name: nosql_07_0006.html

.. _nosql_07_0006:

Replicating a Parameter Template
================================

Scenarios
---------

Replicating a parameter template makes it easy to bring most of your custom parameters and values into a new one. You can also export the parameter template to generate a new parameter template for future use.

Default parameter templates cannot be replicated. You can create parameter templates based on the default ones.

Procedure
---------

#. :ref:`Log in to the GeminiDB console. <nosql_login>`

#. In the navigation pane on the left, choose **Parameter Templates**.

#. On the **Parameter Templates** page, click the **Custom Templates** tab. Locate the parameter template that you want to replicate and click **Replicate** in the **Operation** column.

   Alternatively, click the instance name on the **Instances** page. On the **Parameters** page, click **Export** to generate a new parameter template for future use.

#. In the displayed dialog box, enter the parameter template name and description and click **OK**.

   -  **New Parameter Template**: The template name can be up to 64 characters long. It can contain only uppercase letters, lowercase letters, digits, hyphens (-), underscores (_), and periods (.).
   -  **Description**: The description contains a maximum of 256 characters and cannot include line breaks or the following special characters: >!<"&'=

   After the replication, a new template is generated in the list on the **Custom Templates** tab.
