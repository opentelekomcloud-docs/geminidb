:original_name: nosql_dynamodb_0166.html

.. _nosql_dynamodb_0166:

Managing Tags
=============

Tag Management Service (TMS) enables you to manage resources using tags on the console. TMS works with other cloud services to manage tags. TMS manages tags globally and other cloud services manage their own tags.

You can tag your GeminiDB DynamoDB-Compatible instances to easily identify and manage them. You can tag an instance while creating it or after the instance is created.

After an instance is tagged, you can search for the tag key or value to quickly query the instance details.

Precautions
-----------

-  You are advised to set predefined tags on the TMS console.

-  A tag consists of a key and value. You can add only one value for each key. For details about naming rules of tag keys and tag values, see :ref:`Table 1 <nosql_dynamodb_0166__table197401426182516>`.

-  A maximum of 20 tags can be added for each instance.

-  The tag name must comply with the naming rules described in :ref:`Table 1 <nosql_dynamodb_0166__table197401426182516>`.

   .. _nosql_dynamodb_0166__table197401426182516:

   .. table:: **Table 1** Naming rules

      +-----------------------+-----------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Requirement                                                                             | Example Value         |
      +=======================+=========================================================================================+=======================+
      | Tag key               | -  Cannot be left blank.                                                                | Organization          |
      |                       | -  Must be unique for each instance.                                                    |                       |
      |                       | -  Can contain a maximum of 36 characters.                                              |                       |
      |                       | -  Can only consist of digits, letters, underscores (_), hyphens (-), and at signs (@). |                       |
      +-----------------------+-----------------------------------------------------------------------------------------+-----------------------+
      | Tag value             | -  Can be left blank.                                                                   | nosql_01              |
      |                       | -  Can contain a maximum of 43 characters.                                              |                       |
      |                       | -  Can only consist of digits, letters, underscores (_), hyphens (-), and at signs (@). |                       |
      +-----------------------+-----------------------------------------------------------------------------------------+-----------------------+

Adding a Tag
------------

#. :ref:`Log in to the GeminiDB console <nosql_login>`.
#. On the **Instances** page, click the target instance. The **Basic Information** page is displayed.
#. In the navigation pane on the left, click **Tags**.
#. On the **Tags** page, click **Add Tag**. In the displayed dialog box, enter a tag key and value, and click **OK**.
#. View and manage tags on the **Tags** page.

Editing a Tag
-------------

#. :ref:`Log in to the GeminiDB console <nosql_login>`.

#. On the **Instances** page, click the target instance. The **Basic Information** page is displayed.

#. In the navigation pane on the left, click **Tags**.

#. On the **Tags** page, locate the tag to be edited and click **Edit** in the **Operation** column. In the displayed dialog box, change the tag value and click **OK**.

   Only the tag value can be edited when editing a tag.

#. View and manage tags on the **Tags** page.

Deleting a Tag
--------------

#. :ref:`Log in to the GeminiDB console <nosql_login>`.
#. On the **Instances** page, click the target instance. The **Basic Information** page is displayed.
#. In the navigation pane on the left, click **Tags**.
#. On the **Tags** page, locate the tag to be deleted and click **Delete** in the **Operation** column. In the displayed dialog box, click **Yes**.
#. After a tag has been deleted, it will not be displayed on the **Tags** page.

Searching an Instance by Tag
----------------------------

#. :ref:`Log in to the GeminiDB console <nosql_login>`.
#. On the **Instances** page, click **Search by Tag** in the upper right corner of the instance list.
#. Enter the key or value of the tag to be queried and click **Search** to query the instance associated with the tag.
