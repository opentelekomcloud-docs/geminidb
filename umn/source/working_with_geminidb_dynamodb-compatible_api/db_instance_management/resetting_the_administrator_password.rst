:original_name: nosql_dynamodb_0067.html

.. _nosql_dynamodb_0067:

Resetting the Administrator Password
====================================

Scenarios
---------

For security purposes, reset your administrator password regularly.

Precautions
-----------

-  You can reset the administrator password if the instance is in the **Available**, **Backing up**, **Checking restoration**, or **Scaling up** state, or if certain nodes are not running properly.
-  The new password will take effect immediately after a successful reset.

.. caution::

   Change your password during off-peak hours to avoid service interruptions.

Method 1
--------

#. :ref:`Log in to the GeminiDB console. <nosql_login>`

#. On the **Instances** page, locate the DB instance you wish to reset the password for and choose **More** > **Reset Password** in the **Operation** column.

#. Enter and confirm the new administrator password and click **OK**.

   The password must be 8 to 32 characters in length and contain uppercase letters, lowercase letters, digits, and any of the following special characters: ``~!@#%^*-_=+?``

Method 2
--------

#. :ref:`Log in to the GeminiDB console. <nosql_login>`

#. On the **Instances** page, click the DB instance you wish to reset the password for. The **Basic Information** page is displayed.

#. In the **DB Information** area, click **Reset Password** in the **Administrator** field.

#. Enter and confirm the new administrator password and click **OK**.

   The password must be 8 to 32 characters in length and contain uppercase letters, lowercase letters, digits, and any of the following special characters: ``~!@#%^*-_=+?``
