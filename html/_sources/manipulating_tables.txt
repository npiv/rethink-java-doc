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
* durability: if set to "soft", this enables soft durability on this table: writes will be 
* acknowledged by the server immediately and flushed to disk in the background. Default is "hard" (acknowledgement of writes happens after data has been written to disk);
* datacenter: the name of the datacenter this table should be assigned to.

Example: Create a table named "dc_universe" with the default settings.

.. code-block:: java
    
     DDLResult result = r.tableCreate("dc_universe").run(connection);

Possible Signatures: 

.. code-block:: java

	 public TableCreate tableCreate(String tableName)
	 public TableCreate tableCreate(String tableName, String primaryKey, Durability durability, String datacenter)

---------
tableDrop
---------
Drop a table. The table and all its data will be deleted.

If succesful, the operation returns a :java:ref:`DDLResult` {"dropped": 1}. If the specified table doesn"t exist a :java:ref:`RethinkDBException` is thrown.

Example: Drop a table named "dc_universe".

.. code-block:: java
	
	DDLResult result = r.tableDrop("dv_universe").run(connection);

---------
tableList
---------

List all table names in a database. The result is a list of strings.

Example: List all tables of the "test" database.

.. code-block:: java

	List<String> result = r.tableList().run(connection);


-----------
indexCreate
-----------
Create a new secondary index on this table.

Example: To efficiently query our heros by code name we have to create a secondary index. 

.. code-block:: java
    
	DDLResult res = r.table("dc").indexCreate("code_name").run(conn);

Example: You can also create a secondary index based on an arbitrary function on the document.

.. code-block:: java
    
	DDLResult res = r.table("dc").indexCreate("power_rating",
		hero -> hero.field("combat_power").add(hero.field("compassion_power").mul(2));
	).run(conn)

---------
indexDrop
---------
Delete a previously created secondary index of this table.

Example: Drop a secondary index named "code_name".

.. code-block:: java
    
     DDLResult res = r.table("dc").indexDrop("code_name").run(conn);    

---------
indexList
---------
List all the secondary indexes of this table.

Example: List the available secondary indexes for this table.

.. code-block:: java
    
     List<String> res = r.table("dc").indexList().run(conn);          


-----------
indexStatus
-----------
Get the status of the specified indexes on this table, or the status of all indexes on this table if no indexes are specified.

Example: Get the status of all the indexes on test:

.. code-block:: java
    
     List<IndexStatusResult> res = r.table("dc").indexStatus().run(conn);          

Example: Get the status of the timestamp index:

.. code-block:: java
    
     List<IndexStatusResult> res = r.table("dc").indexStatus("timestamp").run(conn);          


-----------
indexWait
-----------
Wait for the specified indexes on this table to be ready, or for all indexes on this table to be ready if no indexes are specified.

Example: Wait for all indexes on the table test to be ready:

.. code-block:: java
    
     List<IndexStatusResult> res = r.table("dc").indexWait().run(conn);          

Example: Wait for the index timestamp to be ready:

.. code-block:: java
    
     List<IndexStatusResult> res = r.table("dc").indexWait("timestamp").run(conn);          
