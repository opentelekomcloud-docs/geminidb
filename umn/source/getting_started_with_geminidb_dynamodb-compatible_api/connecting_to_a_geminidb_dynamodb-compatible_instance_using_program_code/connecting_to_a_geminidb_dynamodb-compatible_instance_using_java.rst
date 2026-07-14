:original_name: nosql_dynamodb_0045.html

.. _nosql_dynamodb_0045:

Connecting to a GeminiDB DynamoDB-Compatible Instance Using Java
================================================================

This section describes how to connect to a GeminiDB DynamoDB-Compatible instance using Java.

Precautions
-----------

-  The target instance and ECS must be in the same VPC and subnet.
-  The ECS must be within the allowed access range of the security group associated with the target instance.

   -  If the target instance is associated with the default security group, no additional security group rules need to be configured for either the instance or the ECS.
   -  If the target instance is associated with a non-default security group, check whether the rules of this security group allow the ECS to access the instance. For details, see :ref:`Configuring Security Group Rules <nosql_dynamodb_0040>`.

Prerequisites
-------------

-  A GeminiDB DynamoDB-Compatible instance has been created.
-  JDK has been installed on the ECS.

Querying the Load Balancer Address of the GeminiDB DynamoDB-Compatible Instance
-------------------------------------------------------------------------------

#. :ref:`Log in to the GeminiDB console. <nosql_login>`

#. .. _nosql_dynamodb_0045__li672164718386:

   On the **Instances** page, click the target instance name. On the displayed **Basic Information** page, find the load balancer address.

Connecting to the Instance Using Java
-------------------------------------

Replace the IP address in the following code example with the load balancer address queried in :ref:`2 <nosql_dynamodb_0045__li672164718386>`.

Java code example:

.. code-block::

   public class ClientExample {
       public static AWSCredentialsProvider myCredentials = new AWSStaticCredentialsProvider(new BasicAWSCredentials("rwuser", "your_pwd"));
       public static void main(String[] args) {
           AmazonDynamoDB client = AmazonDynamoDBClientBuilder.standard()
               .withEndpointConfiguration(new AwsClientBuilder.EndpointConfiguration("http://ip", "eu-de"))
               .withCredentials(myCredentials)
               .build();
           DynamoDB dynamoDB = new DynamoDB(client);
           TableCollection res = dynamoDB.listTables();
           System.out.println(res);
       }
   }
