:original_name: nosql_09_0101.html

.. _nosql_09_0101:

Connecting to an Instance Using Java
====================================

This section describes how to connect to a GeminiDB Influx instance using the Java programming language.

Prerequisites
-------------

-  You have downloaded the client code from the `InfluxDB open-source project website <https://github.com/influxdata/influxdb1-client>`__.

Example Code
------------

.. code-block::

   package influxdb;

   import okhttp3.OkHttpClient;
   import org.influxdb.InfluxDB;
   import org.influxdb.InfluxDBFactory;
   import org.influxdb.dto.Point;
   import org.influxdb.dto.Query;
   import org.influxdb.dto.QueryResult;

   import java.util.concurrent.TimeUnit;

   public class demoNoSSL {
       public static void main(String[] args) {
           OkHttpClient.Builder client = new OkHttpClient.Builder()
                   .connectTimeout(10, TimeUnit.SECONDS)
                   .writeTimeout(10, TimeUnit.SECONDS)
                   .readTimeout(10, TimeUnit.SECONDS)
                   .retryOnConnectionFailure(true);

           final String serverURL = "http://xx.xx.xx.xx:xx", username = "xx", password = "xx";
           InfluxDB influxdb = InfluxDBFactory.connect(serverURL, username, password, client);

           // Create a database...
           String databaseName = "foo";

           influxdb.query(new Query("CREATE DATABASE " + databaseName, databaseName));
           influxdb.setDatabase(databaseName);

           // Write points to influxdb.
           influxdb.write(Point.measurement("bar")
                   .time(System.currentTimeMillis(), TimeUnit.MILLISECONDS)
                   .tag("location", "chengdu")
                   .addField("temperature", 22)
                   .build());

           // Query your data using InfluxQL.
           QueryResult queryResult = influxdb.query(new Query("SELECT * FROM bar", databaseName));

           // Close it if your application is terminating or you are not using it anymore.
           influxdb.close();
       }
   }
