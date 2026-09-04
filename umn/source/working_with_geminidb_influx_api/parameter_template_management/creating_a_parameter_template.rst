:original_name: nosql_07_0002.html

.. _nosql_07_0002:

Creating a Parameter Template
=============================

You can use database parameter templates to manage DB engine configurations. A database parameter template acts as a container for engine configuration values that can be applied to one or more DB instances.

Each user can create up to 100 parameter templates. The parameter template quota is shared by all DB instances in a project.

Procedure
---------

#. :ref:`Log in to the GeminiDB console. <nosql_login>`
#. In the navigation pane, choose **Parameter Templates**.
#. On the **Parameter Templates** page, click **Create Parameter Template**.
#. Select a compatible DB engine version, name the parameter template, add the parameter template description, and click **OK** to create a parameter group template.

   -  **Compatible API**: Select the API type that is compatible with your DB engine parameter template.
   -  **DB Engine Version**: Select a DB engine version, for example, 1.7.
   -  **Parameter Template Name**: The template name can be up to 64 characters long. It can contain only uppercase letters, lowercase letters, digits, hyphens (-), underscores (_), and periods (.).
   -  **Description**: The description contains a maximum of 256 characters and cannot include line breaks or the following special characters: >!<"&'=

#. On the **Parameter Templates** page, view the created parameter template.
