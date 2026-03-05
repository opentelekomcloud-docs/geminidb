:original_name: nosql_09_0102.html

.. _nosql_09_0102:

Connecting to an Instance Using Python
======================================

This section describes how to connect to a GeminiDB Influx instance using Python.

Prerequisites
-------------

The Python client of InfluxDB has been installed.

Example Code
------------

.. code-block:: text

   from influxdb import InfluxDBClient

   client = InfluxDBClient(host=IP, port="****", username="****", password="****", ssl=False)
   client.get_list_database()

.. note::

   Replace **host**, **port**, **username**, and **password** with actual values.
