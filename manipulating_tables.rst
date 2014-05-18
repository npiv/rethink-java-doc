###################
Manipulating Tables
###################

-----------
tableCreate
-----------
Create a table. A RethinkDB table is a collection of JSON documents.

If successful, the operation returns a :java:ref:`DDLResult` {created=1}. If a table with the same name already exists, the operation throws :java:ref:`RethinkDBException`.

.. note: 
	you can only use alphanumeric characters and underscores for the table name.

When creating a table you can specify the following options:

* primaryKey: the name of the primary key. The default primary key is id;
* durability: if set to 'soft', this enables soft durability on this table: writes will be 
* acknowledged by the server immediately and flushed to disk in the background. Default is 'hard' (acknowledgement of writes happens after data has been written to disk);
* datacenter: the name of the datacenter this table should be assigned to.

Example: Create a table named 'dc_universe' with the default settings.

.. code-block:: java
    
     DDLResult result = r.tableCreate("dc_universe").run(connection);

Possible Signatures: :java:ref:`RTDBQuery.tableCreate`

---------
tableDrop
---------
Drop a table. The table and all its data will be deleted.

If succesful, the operation returns a :java:ref:`DDLResult` {"dropped": 1}. If the specified table doesn't exist a :java:ref:`RethinkDBException` is thrown.

Example: Drop a table named 'dc_universe'.

.. code-block:: java
	
	DDLResult result = r.tableDrop("dv_universe").run(connection);

---------
tableList
---------

List all table names in a database. The result is a list of strings.

Example: List all tables of the 'test' database.

.. code-block:: java

	List<String> result = r.tableList().run(connection);

