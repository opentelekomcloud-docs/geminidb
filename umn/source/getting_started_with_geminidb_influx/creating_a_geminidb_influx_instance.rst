:original_name: nosql_02_0051.html

.. _nosql_02_0051:

Creating a GeminiDB Influx Instance
===================================

This section describes how to create a GeminiDB Influx instance on the GeminiDB console.

Procedure
---------

#. :ref:`Log in to the GeminiDB console <nosql_login>`.
#. On the **Instances** page, click **Create DB Instance**.
#. On the displayed page, select your DB instance specifications, and click **Create Now**.

   .. table:: **Table 1** Basic information

      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                                       |
      +===================================+===================================================================================================================================================================================================================================================================================================================================+
      | Region                            | The region where the tenant is located. It can be changed in the upper left corner.                                                                                                                                                                                                                                               |
      |                                   |                                                                                                                                                                                                                                                                                                                                   |
      |                                   | .. important::                                                                                                                                                                                                                                                                                                                    |
      |                                   |                                                                                                                                                                                                                                                                                                                                   |
      |                                   |    NOTICE:                                                                                                                                                                                                                                                                                                                        |
      |                                   |    Select the region nearest where you will be accessing the DB from so latency can be kept to a minimum and response time will be faster. Also, products deployed in different regions cannot communicate with each other through a private network and you cannot change the region of an instance after creating the instance. |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | DB Instance Name                  | The new name can be the same as an existing instance name. It must start with a letter and consist of 4 to 64 characters. Only letters, digits, hyphens (-), and underscores (_) are allowed.                                                                                                                                     |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Compatible API                    | InfluxDB                                                                                                                                                                                                                                                                                                                          |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Storage Type                      | -  **Cloud native**: more flexible, new-gen version with support for more AZs                                                                                                                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                                                                                                                                                   |
      |                                   |    .. note::                                                                                                                                                                                                                                                                                                                      |
      |                                   |                                                                                                                                                                                                                                                                                                                                   |
      |                                   |       Cloud native storage is only available to cluster (performance-enhanced) instances.                                                                                                                                                                                                                                         |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | DB Instance Type                  | Performance-enhanced cluster instances can be created.                                                                                                                                                                                                                                                                            |
      |                                   |                                                                                                                                                                                                                                                                                                                                   |
      |                                   | -  Cluster: One cluster consists of at least three nodes. A cluster is easy to scale out to meet increasing data growth needs.                                                                                                                                                                                                    |
      |                                   |                                                                                                                                                                                                                                                                                                                                   |
      |                                   | -  Compared with cluster instances, instances in a performance-enhanced cluster support a larger scale and higher read/write performance.                                                                                                                                                                                         |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | DB Engine Version                 | 1.7                                                                                                                                                                                                                                                                                                                               |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | AZ                                | An AZ is a part of a region with its own independent power supplies and networks. AZs are physically isolated but can communicate through an internal network connection.                                                                                                                                                         |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. table:: **Table 2** Specifications and storage

      +-------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter               | Description                                                                                                                                    |
      +=========================+================================================================================================================================================+
      | Instance Specifications | Performance specifications vary depending on the connections and maximum IOPS.                                                                 |
      +-------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
      | Nodes                   | The number of nodes ranges from 2 to 9. After an instance is created, you can add nodes. For details, see :ref:`Adding Nodes <nosql_03_0213>`. |
      +-------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
      | Storage Space           | The storage is an integer, and the minimum storage is 100 GB. You can add at least 10 GB each time.                                            |
      +-------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+

   .. table:: **Table 3** Network

      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                |
      +===================================+============================================================================================================================================================================================+
      | VPC                               | The virtual network where your DB instances are located. A VPC isolates networks for different services. You can select an existing VPC or create a VPC.                                   |
      |                                   |                                                                                                                                                                                            |
      |                                   | If there are no VPCs available, the system allocates resources to you by default.                                                                                                          |
      |                                   |                                                                                                                                                                                            |
      |                                   | For details on how to create a subnet, see the "Creating a VPC" section in the *Virtual Private Cloud User Guide*.                                                                         |
      |                                   |                                                                                                                                                                                            |
      |                                   | .. note::                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                            |
      |                                   |    After the GeminiDB Influx instance is created, the VPC where the instance resides cannot be changed.                                                                                    |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Subnet                            | A subnet provides dedicated network resources that are logically isolated from other networks for network security.                                                                        |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Security Group                    | A security group controls access between GeminiDB Influx instances and other services. When you select a security group, you must ensure that it allows the client to access DB instances. |
      |                                   |                                                                                                                                                                                            |
      |                                   | If no security group is available, the system creates one for you.                                                                                                                         |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | SSL                               | Secure Sockets Layer (SSL) encrypts connections between clients and servers, preventing data from being tampered with or stolen during transmission.                                       |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. table:: **Table 4** Database configuration

      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                 |
      +===================================+=============================================================================================================================================================================+
      | Administrator                     | The default administrator account is **rwuser**.                                                                                                                            |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Administrator Password            | Set a password for the administrator. The password:                                                                                                                         |
      |                                   |                                                                                                                                                                             |
      |                                   | -  Must be 8 to 32 characters long.                                                                                                                                         |
      |                                   | -  Must contain uppercase letters, lowercase letters, digits, and any of the following special characters: ``~!@#%^*-_=+?``                                                 |
      |                                   | -  For security reasons, you must select a strong password. The system will verify the password strength.                                                                   |
      |                                   |                                                                                                                                                                             |
      |                                   | Keep this password secure. If you lose it, the system cannot retrieve it.                                                                                                   |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Confirm Password                  | Enter the administrator password again.                                                                                                                                     |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter Template                | A parameter template contains engine configuration values that can be applied to one or more instances.                                                                     |
      |                                   |                                                                                                                                                                             |
      |                                   | After a DB instance is created, you can modify parameters to better meet your service requirements. For details, see :ref:`Modifying a Parameter Template <nosql_07_0003>`. |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Enterprise Project                | This parameter is provided for enterprise users.                                                                                                                            |
      |                                   |                                                                                                                                                                             |
      |                                   | An enterprise project groups cloud resources, so you can manage resources and members by project. The default project is **default**.                                       |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. table:: **Table 5** Tags

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                       |
      +===================================+===================================================================================================================================================+
      | Tags                              | The setting is optional. Adding tags helps you better identify and manage your DB instances. You can add a maximum of 20 tags for each instance.  |
      |                                   |                                                                                                                                                   |
      |                                   | A tag is composed of a key-value pair.                                                                                                            |
      |                                   |                                                                                                                                                   |
      |                                   | -  A tag key is mandatory if the instance will be tagged.                                                                                         |
      |                                   |                                                                                                                                                   |
      |                                   |    Each tag key is unique for each instance. The key can contain 1 to 36 characters, including digits, letters, underscores (_), and hyphens (-). |
      |                                   |                                                                                                                                                   |
      |                                   | -  A tag value is optional if the instance will be tagged.                                                                                        |
      |                                   |                                                                                                                                                   |
      |                                   |    The value can contain up to 43 characters, including digits, letters, underscores (_), periods (.), and hyphens (-).                           |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+

#. On the displayed page, confirm the DB instance details.

   -  If you need to modify the specifications, click **Previous** to return to the previous page.
   -  If you do not need to modify the specifications, click **Submit** to start creating the instance.

#. On the **Instances** page, view and manage your DB instances.

   -  Creating a DB instance takes about 5 to 9 minutes. During the process, the instance status displayed in the DB instance list is **Creating**.

   -  After the creation is complete, the status changes to **Available**.

      You can click |image1| in the upper right corner of the page to refresh the DB instance statuses.

   -  During creation, an automated backup policy is enabled by default. A full backup is automatically triggered after a DB instance is created.

   -  After a DB instance is created, the default database port is **8635** and cannot be changed.

.. |image1| image:: /_static/images/en-us_image_0000002417594324.png
