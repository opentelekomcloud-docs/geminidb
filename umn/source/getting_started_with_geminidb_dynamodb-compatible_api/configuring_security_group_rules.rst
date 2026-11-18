:original_name: nosql_dynamodb_0040.html

.. _nosql_dynamodb_0040:

Configuring Security Group Rules
================================

Scenarios
---------

The default security group rule allows all outgoing data packets. ECSs and GeminiDB instances in the same security group can access each other. After a security group is created, you can define different access rules. After a GeminiDB instance is added to the security group, it is protected by the access rules.

The following describes how to set security groups.

Precautions
-----------

-  If the ECS and DB instance are in the same security group, they can communicate with each other by default. No security group rule needs to be configured.

-  If the ECS and DB instance are in different security groups, you need to configure security group rules for them separately.

   -  GeminiDB DynamoDB-Compatible instance: Add **inbound** rules to the DB instance's security group on the GeminiDB console.
   -  ECS: If the ECS uses the default security group that permits all outgoing traffic, no additional security group rule is needed for the ECS. However, if it uses a non-default security group that restricts outbound traffic, you must configure **outbound** rules for that security group.

-  By default, you can create up to 500 security group rules. However, too many rules increase network latency for initial access, so it is recommended that you add no more than 50 rules for each security group.
-  Currently, each GeminiDB DynamoDB-Compatible instance can have only one security group.
-  :ref:`Table 1 <nosql_dynamodb_0040__table78461843145>` lists the security group rules required for connecting to an instance.

.. _nosql_dynamodb_0040__table78461843145:

.. table:: **Table 1** Security group rules

   +--------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Scenario                                         | Security Group Rules                                                                                                                                                                                                                                                                               |
   +==================================================+====================================================================================================================================================================================================================================================================================================+
   | Connecting to an instance over a private network | When connecting to a GeminiDB DynamoDB-Compatible instance over a private network, configure security group rules in either of the following ways:                                                                                                                                                 |
   |                                                  |                                                                                                                                                                                                                                                                                                    |
   |                                                  | -  If the ECS and DB instance are in the same security group, they can communicate with each other by default. No security group rule needs to be set.                                                                                                                                             |
   |                                                  | -  If they are in different security groups, configure security group rules for them separately.                                                                                                                                                                                                   |
   |                                                  |                                                                                                                                                                                                                                                                                                    |
   |                                                  |    -  GeminiDB DynamoDB-Compatible instance: Add **inbound** rules to the DB instance's security group on the GeminiDB console. For details, see :ref:`Procedure <nosql_dynamodb_0040__section22661510275>`.                                                                                       |
   |                                                  |    -  ECS: If the ECS uses the default security group that permits all outgoing traffic, no additional security group rule is needed for the ECS. However, if it uses a non-default security group that restricts outbound traffic, you must configure **outbound** rules for that security group. |
   +--------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _nosql_dynamodb_0040__section22661510275:

Procedure
---------

#. Log in to the console.
#. Click |image1| in the upper left corner and select a region and a project.
#. In the **Service List**, choose **Networking** > **Virtual Private Cloud**.
#. In the navigation pane on the left, choose **Access Control** > **Security Groups**.
#. On the **Security Groups** page, click the security group name.
#. On the **Inbound Rules** tab page, click **Add Rule**. In the displayed **Add Inbound Rule** dialog box, set required parameters to add inbound rules. On the **Outbound Rules** tab, click **Add Rule**. In the displayed **Add Outbound Rule** dialog box, set required parameters to add outbound rules.
#. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000002561988037.png
