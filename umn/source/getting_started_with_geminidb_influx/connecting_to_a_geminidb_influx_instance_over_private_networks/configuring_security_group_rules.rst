:original_name: nosql_02_0052.html

.. _nosql_02_0052:

Configuring Security Group Rules
================================

Scenarios
---------

The default security group rule allows all outgoing data packets. ECSs and GeminiDB instances in the same security group can access each other. After a security group is created, you can define different access rules. After a GeminiDB instance is added to the security group, it is protected by the access rules.

The following describes how to set security groups.

Precautions
-----------

-  If the ECS and DB instance are in the same security group, they can communicate with each other by default. No security group rule needs to be configured.
-  If the ECS and DB instance are in different security groups, you need to configure security group rules for the ECS and DB instance separately.

   -  To allow access to the GeminiDB Influx instance, you need to configure an inbound rule for the security group where the instance resides.
   -  By default, the security group allows all outbound data packets, so you do not need to configure a security rule for the ECS. If not all access from the ECS is allowed, you need to configure an outbound rule for the ECS.

-  By default, you can create up to 500 security group rules. However, too many rules increase network latency for initial access, so it is recommended that you add no more than 50 rules for each security group.
-  Currently, a GeminiDB Influx instance can be associated with only one security group.
-  :ref:`Table 1 <nosql_02_0052__table78461843145>` lists security group rules.

.. _nosql_02_0052__table78461843145:

.. table:: **Table 1** Security group rules

   +--------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Scenario                                         | Description                                                                                                                                                                                                                        |
   +==================================================+====================================================================================================================================================================================================================================+
   | Connecting to an instance over a private network | Configure security group rules as follows:                                                                                                                                                                                         |
   |                                                  |                                                                                                                                                                                                                                    |
   |                                                  | -  If the ECS and GeminiDB Influx instance are in the same security group, they can communicate with each other by default. No security group rule needs to be configured.                                                         |
   |                                                  | -  If they are in different security groups, configure security group rules for them, separately.                                                                                                                                  |
   |                                                  |                                                                                                                                                                                                                                    |
   |                                                  |    -  Configure inbound rules for the security group associated with the GeminiDB Influx instance. For details, see :ref:`Procedure <nosql_02_0052__en-us_topic_0249811530_section9281154719202>`.                                 |
   |                                                  |    -  By default, the security group allows all outbound data packets, so you do not need to configure a security rule for the ECS. If not all access from the ECS is allowed, you need to configure an outbound rule for the ECS. |
   +--------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _nosql_02_0052__en-us_topic_0249811530_section9281154719202:

Procedure
---------

#. Log in to the console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Networking**, click **Virtual Private Cloud**.
#. In the navigation pane on the left, choose **Access Control** > **Security Groups**.
#. On the **Security Groups** page, click the security group name.
#. On the **Inbound Rules** tab, click **Add Rule**. In the displayed **Add Inbound Rule** dialog box, set required parameters to add inbound rules. On the **Outbound Rules** tab, click **Add Rule**. In the displayed **Add Outbound Rule** dialog box, set required parameters to add outbound rules.
#. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000002417434596.png
