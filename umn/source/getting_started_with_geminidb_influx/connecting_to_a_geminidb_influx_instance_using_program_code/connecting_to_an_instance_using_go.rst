:original_name: nosql_09_0073.html

.. _nosql_09_0073:

Connecting to an Instance Using Go
==================================

This section describes how to connect to a GeminiDB Influx instance using the Go programming language.

Prerequisites
-------------

-  You have downloaded the client code from the `InfluxDB open-source project website <https://github.com/influxdata/influxdb1-client>`__.

Example Code
------------

.. code-block::

   package main

   import (
       "fmt"
       _ "github.com/influxdata/influxdb1-client" // this is important because of the bug in go mod
       client "github.com/influxdata/influxdb1-client/v2"
   )

   func main(){
       c, err := client.NewHTTPClient(client.HTTPConfig{
           Addr: "http://ip:port",
           Username: "******",
           Password: "******",
       })
       if err != nil {
           fmt.Println("Error creating InfluxDB Client: ", err.Error())
       }
       q := client.NewQuery("select * from cpu","db0","ns")
       if response, err := c.Query(q); err == nil && response.Error() == nil {
           fmt.Println("the result is: ",response.Results)
       }
   }
