:original_name: nosql_increase_storage1.html

.. _nosql_increase_storage1:

Configuring Autoscaling
=======================

You can enable autoscaling for GeminiDB Cassandra instances. When storage usage reaches the limit, autoscaling is triggered.

You can enable autoscaling:

#. When creating an instance

   For details, see :ref:`Creating a GeminiDB Cassandra Instance <nosql_06_0003>`.

#. After creating an instance

For details, see operations in this section.

.. note::

   -  If you enable autoscaling as a domain user, no additional configuration is required.
   -  If you enable autoscaling as an IAM user first time, you need to temporarily assign the permission of creating an agency to the user.

Permission Configuration
------------------------

If you are using an IAM user, configure the following permissions before enabling autoscaling:

#. GeminiDB FullAccess

#. .. _nosql_increase_storage1__li7342161519187:

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

#. .. _nosql_increase_storage1__li31075139411:

   `Creating a User Group and Assigning Permissions <https://docs.otc.t-systems.com/identity-access-management/umn/user_guide/user_groups_and_authorization/creating_a_user_group_and_assigning_permissions.html#en-us-topic-0046611269>`__

   You can create a user group on the IAM console and assign it custom permissions created in :ref:`2 <nosql_increase_storage1__li7342161519187>` and system role **Security Administrator**.

#. `Adding Users to or Removing Users from a User Group <https://docs.otc.t-systems.com/identity-access-management/umn/user_guide/user_groups_and_authorization/adding_users_to_or_removing_users_from_a_user_group.html>`__

   Log in to the IAM console as a domain or an IAM user. Locate the IAM user that the target instance belongs to and add it to the user group created in :ref:`3 <nosql_increase_storage1__li31075139411>`. The IAM user will inherit permissions of the user group.

Usage Notes
-----------

-  The instance is in the **Available** status.
-  Once autoscaling is enabled, an agency will be created and fees will be automatically deducted.

Automatically Scaling Up Storage of a Single Instance
-----------------------------------------------------

#. :ref:`Log in to the GeminiDB console <nosql_login>`.

#. On the **Instances** page, click the target instance. The **Basic Information** page is displayed.

#. In the **Storage Space** area, click **Auto Scale**.


   .. figure:: /_static/images/en-us_image_0000002038307285.png
      :alt: **Figure 1** Auto Scale

      **Figure 1** Auto Scale

#. Toggle on **Auto Scale** and specify the parameters below.


   .. figure:: /_static/images/en-us_image_0000002038188189.png
      :alt: **Figure 2** Configuring autoscaling

      **Figure 2** Configuring autoscaling

   .. table:: **Table 1** Parameter description

      +---------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                             | Description                                                                                                                                                                                                  |
      +=======================================+==============================================================================================================================================================================================================+
      | Auto Scale                            | If you toggle on this switch, autoscaling is enabled.                                                                                                                                                        |
      +---------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Trigger If Available Storage Drops To | When the available storage usage drops to this value or the available storage space drops to 10 GB, autoscaling is triggered.                                                                                |
      +---------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Increase By                           | Percentage of the current storage to be automatically scaled. The value can be **10**, **15**, or **20**. If the value is not a multiple of 10, the value is rounded up. At least 100 GB is added each time. |
      +---------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Storage Limit                         | Limit of storage (GB) that can be automatically scaled to.                                                                                                                                                   |
      |                                       |                                                                                                                                                                                                              |
      |                                       | The value must be no less than the current storage of your instance and cannot exceed the maximum storage supported by your instance.                                                                        |
      +---------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

Automatically Scaling Up Storage of Multiple Instances In Batches
-----------------------------------------------------------------

#. :ref:`Log in to the GeminiDB console <nosql_login>`.

#. Select instances and click **Auto Scale**.


   .. figure:: /_static/images/en-us_image_0000002038307289.png
      :alt: **Figure 3** Auto Scale

      **Figure 3** Auto Scale

#. Select an instance, toggle on **Auto Scale**, and specify the parameters below.


   .. figure:: /_static/images/en-us_image_0000002038188193.png
      :alt: **Figure 4** Batch Auto Scale

      **Figure 4** Batch Auto Scale

   .. table:: **Table 2** Parameter description

      +---------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                             | Description                                                                                                                                   |
      +=======================================+===============================================================================================================================================+
      | Auto Scale                            | If you toggle on this switch, autoscaling is enabled.                                                                                         |
      +---------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
      | Trigger If Available Storage Drops To | When the available storage usage drops to this value or the available storage space drops to 10 GB, autoscaling is triggered.                 |
      +---------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
      | Increase By                           | Percentage of the current storage to be automatically scaled. The value can be **10**, **15**, or **20**. At least 100 GB is added each time. |
      +---------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
      | Storage Limit                         | This parameter cannot be customized. By default, the storage is scaled up the maximum of the selected instance.                               |
      +---------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.
