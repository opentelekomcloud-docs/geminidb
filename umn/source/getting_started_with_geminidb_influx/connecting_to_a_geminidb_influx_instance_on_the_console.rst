:original_name: nosql_09_0092.html

.. _nosql_09_0092:

Connecting to a GeminiDB Influx Instance on the Console
=======================================================

You can connect to a GeminiDB Influx instance on the console.

Prerequisites
-------------

There is an available GeminiDB Influx instance.

Usage Notes
-----------

-  SELECT query commands are supported.
-  INSERT commands for writing data are supported.
-  Commands for database operations (including creating, deleting, and displaying databases) are supported.
-  Commands for user operations (including creating, deleting, displaying, and authorizing users, and changing user passwords) are supported.
-  Commands of retention policies (including creating, deleting, displaying, and modifying retention policies) are supported.
-  CONTINUOUS QUERY commands (including CREATE CONTINUOUS QUERY, DROP CONTINUOUS QUERY, and SHOW CONTINUOUS QUERY) are supported.

Procedure
---------

#. :ref:`Log in to the GeminiDB console <nosql_login>`.

#. In the instance list, locate a target instance and click **Log In** in the **Operation** column.

   Alternatively, click the instance name to go to the **Basic Information** page. Click **Log In** in the upper right corner of the page.

#. Enter the password for logging in to the instance.

   If you need to log in again after the password is reset, click **Re-login** in the upper right corner and use the new password.

#. Manage relevant databases.

   -  Save commands to the execution record.

      This function is enabled by default to save the recently executed commands for your later query.

      Then you can click the **Executed Commands** tab on the lower page to view historical commands.

      .. note::

         Commands with passwords are not displayed on the **Executed Commands** tab page.

      If this function is disabled, the commands executed subsequently are not displayed any longer. You can click |image1| next to **Save Executed SQL Statements** in the upper right corner to disable this function.

   -  Execute a command.

      You can enter a command in the command window and click **Execute** or **F8**.

      After a command is executed, you can view the execution result on the **Results** page.

   -  Save a command.

      You can save a command to all instances or the current instance. Then you can view details in **My Commands**.

      .. note::

         Commands with passwords cannot be saved to **My Commands**.

   -  View my commands.

      Common commands are displayed the **My Commands** page.

      You can set a filter to narrow the scope of commands. If you select **All**, all commands saved in the current account are displayed.

      Alternatively, you can enter a command title or statement in the search box to search for the corresponding command.

      On the **My Commands** page, you can also create, edit, and delete a command or copy it to the command window.

   -  Clear commands.

      You can also press **F10** to clear the command in the command window.

.. |image1| image:: /_static/images/en-us_image_0000002548274029.png
