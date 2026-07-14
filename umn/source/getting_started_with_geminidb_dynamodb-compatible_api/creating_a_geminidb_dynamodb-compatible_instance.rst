:original_name: nosql_dynamodb_0039.html

.. _nosql_dynamodb_0039:

Creating a GeminiDB DynamoDB-Compatible Instance
================================================

This section describes how to create a GeminiDB DynamoDB-compatible instance on the GeminiDB console.

Procedure
---------

#. :ref:`Log in to the GeminiDB console. <nosql_login>`
#. On the **Instances** page, click **Create DB Instance**.
#. On the displayed page, specify instance information and click **Create Now**.

   .. table:: **Table 1** Basic information

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                   |
      +===================================+===============================================================================================================================================================================================================================================================================================================+
      | Region                            | The region where the tenant is located.                                                                                                                                                                                                                                                                       |
      |                                   |                                                                                                                                                                                                                                                                                                               |
      |                                   | .. note::                                                                                                                                                                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                                                                                                                               |
      |                                   |    To reduce network latency, deploy your DB instance in the region nearest to your workloads. Products in different regions cannot communicate with each other through a private network. After a DB instance is created, the region cannot be changed. Therefore, exercise caution when selecting a region. |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | DB Instance Name                  | The new name can be the same as an existing instance name. It must start with a letter and consist of 4 to 64 characters. Only letters, digits, hyphens (-), and underscores (_) are allowed.                                                                                                                 |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Compatible API                    | DynamoDB                                                                                                                                                                                                                                                                                                      |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Storage Type                      | **Cloud native**: more flexible, next-generation architecture with decoupled storage and compute and support for more AZs                                                                                                                                                                                     |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | DB Instance Type                  | Cluster                                                                                                                                                                                                                                                                                                       |
      |                                   |                                                                                                                                                                                                                                                                                                               |
      |                                   | One cluster consists of at least three nodes. A cluster can be easily scaled out to meet increasing data growth needs. It is recommended when high availability, large data volumes, and seamless scalability are required.                                                                                   |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | AZ                                | An availability zone (AZ) is a physical location where resources use independent power supplies and networks. A region contains one or more AZs that are physically isolated but interconnected through internal networks.                                                                                    |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. table:: **Table 2** Specifications and storage

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                    |
      +===================================+================================================================================================================================================================+
      | Instance Specifications           | The CPUs and memory of a DB instance.                                                                                                                          |
      |                                   |                                                                                                                                                                |
      |                                   | Different specifications support varying numbers of connections and maximum IOPS. Select appropriate specifications that match your workload needs.            |
      |                                   |                                                                                                                                                                |
      |                                   | After a DB instance is created, you can change its specifications. For details, see :ref:`Changing the vCPUs and Memory of an Instance <nosql_dynamodb_0068>`. |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Nodes                             | Specify the number of nodes as required. The value ranges from 2 to 12.                                                                                        |
      |                                   |                                                                                                                                                                |
      |                                   | After a DB instance is created, you can add nodes. For details, see :ref:`Adding Nodes <nosql_dynamodb_0072>`.                                                 |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Storage Space                     | Select a storage size of at least 10 GB. The value must be an integer and a multiple of 10 GB.                                                                 |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. table:: **Table 3** Network

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                              |
      +===================================+==========================================================================================================================================================================================+
      | VPC                               | The virtual network where your DB instances are located. A VPC isolates networks for different services. You can select an existing VPC or create a VPC.                                 |
      |                                   |                                                                                                                                                                                          |
      |                                   | If there are no VPCs available, the system automatically allocates resources to you.                                                                                                     |
      |                                   |                                                                                                                                                                                          |
      |                                   | For details about how to create a VPC, see section "Creating a VPC" in *Virtual Private Cloud User Guide*.                                                                               |
      |                                   |                                                                                                                                                                                          |
      |                                   | .. note::                                                                                                                                                                                |
      |                                   |                                                                                                                                                                                          |
      |                                   |    After a GeminiDB DynamoDB-Compatible instance is created, its VPC cannot be changed.                                                                                                  |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Subnet                            | A subnet provides dedicated network resources that are isolated from other networks, improving network security.                                                                         |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Security Group                    | A security group controls access to your GeminiDB DynamoDB-Compatible instance from other services. Ensure that the security group you select allows your client to access the instance. |
      |                                   |                                                                                                                                                                                          |
      |                                   | If there are no security groups available, the system automatically allocates resources to you.                                                                                          |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. table:: **Table 4** Database configuration

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                  |
      +===================================+==============================================================================================================================================+
      | Administrator                     | The default administrator account is **rwuser**.                                                                                             |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
      | Administrator Password            | Set a password for the administrator.                                                                                                        |
      |                                   |                                                                                                                                              |
      |                                   | -  The password must be 8 to 32 characters long.                                                                                             |
      |                                   | -  The password must contain uppercase letters, lowercase letters, digits, and any of the following special characters: ``~!@#%^*-_=+?``     |
      |                                   | -  Enter a strong password. The system will verify the password strength.                                                                    |
      |                                   |                                                                                                                                              |
      |                                   | Keep your password secure. The system cannot retrieve it if it is lost.                                                                      |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
      | Confirm Password                  | It must be the same as the administrator password.                                                                                           |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter Template                | A parameter template is a collection of engine configuration settings that can be applied to one or more DB instances of the same DB engine. |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
      | Enterprise Project                | This parameter is for enterprise users.                                                                                                      |
      |                                   |                                                                                                                                              |
      |                                   | Enterprise projects let you manage cloud resources and users by project. The default project is **default**.                                 |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+

   .. table:: **Table 5** Tags

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                          |
      +===================================+======================================================================================================================================================================+
      | Tags                              | The setting is optional. Adding tags to GeminiDB instances helps you better identify and manage the DB instances. Each instance can have up to 20 tags.              |
      |                                   |                                                                                                                                                                      |
      |                                   | A tag is composed of a key-value pair.                                                                                                                               |
      |                                   |                                                                                                                                                                      |
      |                                   | -  Key: It is mandatory if the DB instance will be tagged.                                                                                                           |
      |                                   |                                                                                                                                                                      |
      |                                   |    Each tag key is unique for each instance. A key can contain 1 to 36 characters. Only digits, letters, underscores (_), at signs (@), and hyphens (-) are allowed. |
      |                                   |                                                                                                                                                                      |
      |                                   | -  Value: It is optional if the DB instance will be tagged.                                                                                                          |
      |                                   |                                                                                                                                                                      |
      |                                   |    A value can contain up to 43 characters, including only digits, letters, underscores (_), at signs (@), and hyphens (-).                                          |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. On the displayed page, confirm the instance information.

   -  If you need to modify the settings, click **Previous**.
   -  If you do not need to modify the settings, click **Submit** to start creating the instance.

#. On the **Instances** page, you can view and manage this instance.

   -  Creating an instance takes about 5 to 9 minutes. During the process, the instance status is **Creating**.

   -  After the instance is created, its status becomes **Available**.

      You can click |image1| in the upper right corner of the page to refresh the instance status.

   -  During the creation, an automated backup policy is enabled for this instance by default. The system creates a full backup once the instance is created.

.. |image1| image:: /_static/images/en-us_image_0000002530115744.png
