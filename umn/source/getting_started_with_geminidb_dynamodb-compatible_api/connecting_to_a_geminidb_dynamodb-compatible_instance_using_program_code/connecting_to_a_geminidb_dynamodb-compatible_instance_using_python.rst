:original_name: nosql_dynamodb_0046.html

.. _nosql_dynamodb_0046:

Connecting to a GeminiDB DynamoDB-Compatible Instance Using Python
==================================================================

This section describes how to connect to a GeminiDB DynamoDB-Compatible instance using Python.

Precautions
-----------

-  The target instance and ECS must be in the same VPC and subnet.
-  The ECS must be within the allowed access range of the security group associated with the target instance.

   -  If the target instance is associated with the default security group, no additional security group rules need to be configured for either the instance or the ECS.
   -  If the target instance is associated with a non-default security group, check whether the rules of this security group allow the ECS to access the instance. For details, see :ref:`Configuring Security Group Rules <nosql_dynamodb_0040>`.

Prerequisites
-------------

-  A GeminiDB DynamoDB-Compatible instance has been created.
-  Python has been installed on an ECS.

Querying the Load Balancer Address of the GeminiDB DynamoDB-Compatible Instance
-------------------------------------------------------------------------------

#. :ref:`Log in to the GeminiDB console. <nosql_login>`

#. .. _nosql_dynamodb_0046__li672164718386:

   On the **Instances** page, click the target instance. On the displayed **Basic Information** page, view the load balancer address.

Connecting to the Instance Using Python
---------------------------------------

Replace the IP address in the following code example with the load balancer address queried in :ref:`2 <nosql_dynamodb_0046__li672164718386>`.

Python code example:

.. code-block::

   #!/usr/bin/python
   import boto3


   url = 'http://ip'
   dynamodb = boto3.resource('dynamodb',
                             endpoint_url=url,
                             aws_access_key_id='rwuser',
                             aws_secret_access_key='your_pwd',
                             region_name="region-a")
