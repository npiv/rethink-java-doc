.. java:import:: com.rethinkdb RethinkDBConnection

.. java:import:: com.rethinkdb RethinkDBConstants

.. java:import:: com.rethinkdb RethinkDBException

.. java:import:: com.rethinkdb.model DBObject

.. java:import:: com.rethinkdb.proto Q2L

.. java:import:: com.rethinkdb.proto RTermBuilder

.. java:import:: com.rethinkdb.query.option Durability

.. java:import:: com.rethinkdb.response DBResult

.. java:import:: com.rethinkdb.response DMLResult

.. java:import:: com.rethinkdb.response InsertResult

.. java:import:: com.rethinkdb.response StringListDBResult

.. java:import:: java.util ArrayList

.. java:import:: java.util Arrays

.. java:import:: java.util List

RethinkQueryBuilder
===================

.. java:package:: com.rethinkdb.query
   :noindex:

.. java:type:: public class RethinkQueryBuilder

   This class is the entry point for all the query, insert, dml actions that we can perform on a RethinkDB Instance.

Methods
-------
db
^^

.. java:method:: public RethinkQueryBuilder db(String dbName)
   :outertype: RethinkQueryBuilder

dbCreate
^^^^^^^^

.. java:method:: public RethinkTerminatingQuery<DMLResult> dbCreate(String dbName)
   :outertype: RethinkQueryBuilder

dbDrop
^^^^^^

.. java:method:: public RethinkTerminatingQuery<DMLResult> dbDrop(String dbName)
   :outertype: RethinkQueryBuilder

dbList
^^^^^^

.. java:method:: public RethinkTerminatingQuery<StringListDBResult> dbList()
   :outertype: RethinkQueryBuilder

getAll
^^^^^^

.. java:method:: public RethinkTerminatingQuery<InsertResult> getAll(String key, String... keys)
   :outertype: RethinkQueryBuilder

insert
^^^^^^

.. java:method:: public RethinkTerminatingQuery<InsertResult> insert(DBObject... objects)
   :outertype: RethinkQueryBuilder

insert
^^^^^^

.. java:method:: public RethinkTerminatingQuery<InsertResult> insert(List<DBObject> objects)
   :outertype: RethinkQueryBuilder

insert
^^^^^^

.. java:method:: public RethinkTerminatingQuery<InsertResult> insert(DBObject dbObject, Durability durability, boolean returnVals, boolean upsert)
   :outertype: RethinkQueryBuilder

insert
^^^^^^

.. java:method:: public RethinkTerminatingQuery<InsertResult> insert(List<DBObject> dbObjects, Durability durability, boolean returnVals, boolean upsert)
   :outertype: RethinkQueryBuilder

run
^^^

.. java:method:: public DBObject run(RethinkDBConnection connection)
   :outertype: RethinkQueryBuilder

table
^^^^^

.. java:method:: public RethinkQueryBuilder table(String tableName)
   :outertype: RethinkQueryBuilder

tableCreate
^^^^^^^^^^^

.. java:method:: public RethinkTerminatingQuery<DMLResult> tableCreate(String tableName)
   :outertype: RethinkQueryBuilder

tableCreate
^^^^^^^^^^^

.. java:method:: public RethinkTerminatingQuery<DMLResult> tableCreate(String tableName, String primaryKey, Durability durability, String datacenter)
   :outertype: RethinkQueryBuilder

   Create table with tableName, primaryKey, Durability on a specific dataCenter.

   :param tableName: tableName (mandatory)
   :param primaryKey: primary key (leave null for default)
   :param durability: durability (leave null for default)
   :param datacenter: datacenter (leave null for default)
   :return: query

tableDrop
^^^^^^^^^

.. java:method:: public RethinkTerminatingQuery<DMLResult> tableDrop(String tableName)
   :outertype: RethinkQueryBuilder

tableList
^^^^^^^^^

.. java:method:: public RethinkTerminatingQuery<StringListDBResult> tableList()
   :outertype: RethinkQueryBuilder

