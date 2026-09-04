:original_name: nosql_dynamodb_0078.html

.. _nosql_dynamodb_0078:

Automatically Scaling Up Storage Space
======================================

You can enable storage autoscaling for GeminiDB DynamoDB-Compatible instances. When storage usage reaches your specified limit, autoscaling is triggered.

Storage autoscaling can only be configured after an instance is created.

This section describes how to configure storage autoscaling after an instance is created.

.. note::

   -  If you enable storage autoscaling using an account, no additional configuration is required.
   -  If you enable this function as an IAM user for the first time, the IAM user must be granted the permission to create agencies.

Permission Configuration
------------------------

If you are using an IAM user, configure the following permissions before enabling autoscaling:

#. GeminiDB FullAccess

#. .. _nosql_dynamodb_0078__nosql_increase_storage1_li7342161519187:

   IAM fine-grained permission

   For details, see `Creating a Custom Policy <https://docs.otc.t-systems.com/identity-access-management/umn/user_guide/permissions/creating_a_custom_policy.html>`__.

   Custom policy in JSON format:

   .. code-block::

      {
           "Version":"1.1",
           "Statement":[
               {
                   "Effect":"Allow",
                   "Action":[
                       "iam:permissions:listRolesForAgencyOnProject",
                       "iam:permissions:grantRoleToGroupOnProject",
                       "iam:agencies:createAgency",
                       "iam:agencies:listAgencies",
                       "iam:roles:listRoles",
                       "iam:roles:createRole"
                   ]
               }
           ]
      }

#. .. _nosql_dynamodb_0078__nosql_increase_storage1_li31075139411:

   `Creating a User Group and Assigning Permissions <https://docs.otc.t-systems.com/identity-access-management/umn/user_guide/user_groups_and_authorization/creating_a_user_group_and_assigning_permissions.html#en-us-topic-0046611269>`__

   You can create a user group on the IAM console and assign it custom permissions created in :ref:`2 <nosql_dynamodb_0078__nosql_increase_storage1_li7342161519187>` and system role **Security Administrator**.

#. `Adding Users to or Removing Users from a User Group <https://docs.otc.t-systems.com/identity-access-management/umn/user_guide/user_groups_and_authorization/adding_users_to_or_removing_users_from_a_user_group.html>`__

   Log in to the IAM console as a domain or an IAM user. Locate the IAM user that the target instance belongs to and add it to the user group created in :ref:`3 <nosql_dynamodb_0078__nosql_increase_storage1_li31075139411>`. The IAM user will inherit permissions of the user group.

Usage Notes
-----------

-  The instance is in the **Available** status.
-  Once autoscaling is enabled, an agency will be created and fees will be automatically deducted.

Configuring Storage Autoscaling for a Single Instance
-----------------------------------------------------

#. :ref:`Log in to the GeminiDB console. <nosql_login>`
#. On the **Instances** page, click the target instance name. The **Basic Information** page is displayed.
#. In the **Storage Space** area, click **Auto Scale**.
#. Toggle on **Auto Scale** and specify the parameters below.

   .. table:: **Table 1** Description

      +---------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                             | Description                                                                                                                                                                                                                                                        |
      +=======================================+====================================================================================================================================================================================================================================================================+
      | Auto Scale                            | If you toggle on this switch, storage autoscaling is enabled.                                                                                                                                                                                                      |
      +---------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Trigger If Available Storage Drops To | Storage autoscaling is triggered when the percentage of available storage falls to or below this threshold, or when available storage is 10 GB or less.                                                                                                            |
      +---------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Increase By                           | Percentage of current storage to be automatically added. The value can be **10**, **15**, or **20**. If the increased storage is not a multiple of 10 GB, the system rounds it up to the nearest multiple of 10. The minimum increment in each scale-up is 100 GB. |
      +---------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Storage Limit                         | Maximum storage capacity (GB) allowed for autoscaling.                                                                                                                                                                                                             |
      |                                       |                                                                                                                                                                                                                                                                    |
      |                                       | The value must be greater than or equal to the storage you configured when creating the instance, and cannot exceed the maximum storage capacity supported by the current instance specifications.                                                                 |
      +---------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

Configuring Storage Autoscaling for Multiple Instances
------------------------------------------------------

#. :ref:`Log in to the GeminiDB console. <nosql_login>`

#. On the **Instances** page, select the target instances and click **Auto Scale**.

#. In the displayed dialog box, set the parameters described in :ref:`Table 2 <nosql_dynamodb_0078__table674245613718>`.

   .. _nosql_dynamodb_0078__table674245613718:

   .. table:: **Table 2** Parameters

      +---------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                             | Description                                                                                                                                                                                                                                                        |
      +=======================================+====================================================================================================================================================================================================================================================================+
      | Auto Scale                            | If you toggle on this switch, storage autoscaling is enabled.                                                                                                                                                                                                      |
      +---------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Trigger If Available Storage Drops To | Storage autoscaling is triggered when the percentage of available storage falls to or below this threshold, or when available storage is 10 GB or less.                                                                                                            |
      +---------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Increase By                           | Percentage of current storage to be automatically added. The value can be **10**, **15**, or **20**. If the increased storage is not a multiple of 10 GB, the system rounds it up to the nearest multiple of 10. The minimum increment in each scale-up is 100 GB. |
      +---------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Storage Limit                         | The value cannot be specified when you configure storage autoscaling for multiple instances. By default, storage will scale up to the maximum allowed by your instance specifications.                                                                             |
      +---------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.
