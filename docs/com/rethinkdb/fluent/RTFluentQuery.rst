.. java:import:: com.rethinkdb.ast RTData

.. java:import:: com.rethinkdb.ast RTOperation

.. java:import:: com.rethinkdb.ast RTTreeKeeper

.. java:import:: com.rethinkdb.fluent.types RTFluentQuery_DBObjectList

.. java:import:: com.rethinkdb.fluent.types RTTopLevelQuery_StringList

.. java:import:: com.rethinkdb.model DBObject

.. java:import:: com.rethinkdb.proto Q2L

.. java:import:: com.rethinkdb.fluent.option Durability

.. java:import:: com.rethinkdb.response DMLResult

.. java:import:: java.util Arrays

.. java:import:: java.util List

.. java:import:: java.util.concurrent.atomic AtomicInteger

RTFluentQuery
=============

.. java:package:: com.rethinkdb.fluent
   :noindex:

.. java:type:: public class RTFluentQuery<T> extends RTTopLevelQuery<T>

Constructors
------------
RTFluentQuery
^^^^^^^^^^^^^

.. java:constructor:: public RTFluentQuery()
   :outertype: RTFluentQuery

RTFluentQuery
^^^^^^^^^^^^^

.. java:constructor:: public RTFluentQuery(RTTreeKeeper treeKeeper, Class<T> sampleClass)
   :outertype: RTFluentQuery

Methods
-------
db
^^

.. java:method:: public RTDBQuery db(String dbName)
   :outertype: RTFluentQuery

   Select the database to operate on

   :param dbName: database name

dbCreate
^^^^^^^^

.. java:method:: public RTTopLevelQuery<DMLResult> dbCreate(String dbName)
   :outertype: RTFluentQuery

   create database

   :param dbName: database name

dbDrop
^^^^^^

.. java:method:: public RTTopLevelQuery<DMLResult> dbDrop(String dbName)
   :outertype: RTFluentQuery

   drop database

   :param dbName: database name

dbList
^^^^^^

.. java:method:: public RTTopLevelQuery_StringList dbList()
   :outertype: RTFluentQuery

   list databases

get
^^^

.. java:method:: public RTFluentQuery<DBObject> get(String key)
   :outertype: RTFluentQuery

   Get a document by Primary Key

   :param key: key

get
^^^

.. java:method:: public RTFluentQuery<DBObject> get(Number key)
   :outertype: RTFluentQuery

   Get a document by Primary Key

   :param key: key

getAll
^^^^^^

.. java:method:: public RTFluentQuery<List> getAll(String index, String... additionalIndexes)
   :outertype: RTFluentQuery

   Get all documents where the given value matches the value of the requested index(es).

   :param index: at least one index mandatory
   :param additionalIndexes: optional additional indexes

getAll
^^^^^^

.. java:method:: public RTFluentQuery<List> getAll(String indexName, String index, String... additionalIndexes)
   :outertype: RTFluentQuery

   Get all documents where the given value matches the value of the requested index(es).

   :param indexName: the name of the index if not default (id)
   :param index: at least one index mandatory
   :param additionalIndexes: optional additional indexes

getAll
^^^^^^

.. java:method:: public RTFluentQuery<List> getAll(Number index, Number... additionalIndexes)
   :outertype: RTFluentQuery

   Get all documents where the given value matches the value of the requested index(es).

   :param index: at least one index mandatory
   :param additionalIndexes: optional additional indexes

getAll
^^^^^^

.. java:method:: public RTFluentQuery<List> getAll(String indexName, Number index, Number... additionalIndexes)
   :outertype: RTFluentQuery

   Get all documents where the given value matches the value of the requested index(es).

   :param indexName: the name of the index if not default (id)
   :param index: at least one index mandatory
   :param additionalIndexes: optional additional indexes

insert
^^^^^^

.. java:method:: public RTTopLevelQuery<DMLResult> insert(DBObject... objects)
   :outertype: RTFluentQuery

   insert DBObjects

   :param objects: objects to insert

insert
^^^^^^

.. java:method:: public RTTopLevelQuery<DMLResult> insert(List<DBObject> objects)
   :outertype: RTFluentQuery

   insert DBObjects

   :param objects: objects to insert

insert
^^^^^^

.. java:method:: public RTTopLevelQuery<DMLResult> insert(DBObject dbObject, Durability durability, boolean returnVals, boolean upsert)
   :outertype: RTFluentQuery

   Insert one DBObject into the database

   :param dbObject: dbObject
   :param durability: Hard or Soft (leave null for default)
   :param returnVals: if set to true and in case of a single insert/upsert, the inserted/updated document will be returned.
   :param upsert: when set to true, performs a replace if a document with the same primary key exists.

insert
^^^^^^

.. java:method:: public RTTopLevelQuery<DMLResult> insert(List<DBObject> dbObjects, Durability durability, boolean returnVals, boolean upsert)
   :outertype: RTFluentQuery

   Insert a list of DBObjects into the database

   :param dbObjects: dbObjects
   :param durability: Hard or Soft (leave null for default)
   :param returnVals: if set to true and in case of a single insert/upsert, the inserted/updated document will be returned.
   :param upsert: when set to true, performs a replace if a document with the same primary key exists.

table
^^^^^

.. java:method:: public RTFluentQuery_DBObjectList table(String tableName)
   :outertype: RTFluentQuery

   Select the table to operate on

   :param tableName: table name

update
^^^^^^

.. java:method:: public RTFluentQuery<DMLResult> update(DBObject object)
   :outertype: RTFluentQuery

