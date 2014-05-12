.. java:import:: com.rethinkdb.ast RTData

.. java:import:: com.rethinkdb.ast RTOperation

.. java:import:: com.rethinkdb.ast RTTreeKeeper

.. java:import:: com.rethinkdb.fluent.option Durability

.. java:import:: com.rethinkdb.fluent.types RTFluentQueryTypes

.. java:import:: com.rethinkdb.fluent.types RTTopLevelQueryTypes

.. java:import:: com.rethinkdb.model DBLambda

.. java:import:: com.rethinkdb.model DBObject

.. java:import:: com.rethinkdb.proto Q2L

.. java:import:: java.util ArrayList

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

.. java:constructor:: public RTFluentQuery(RTTreeKeeper treeKeeper)
   :outertype: RTFluentQuery

Methods
-------
add
^^^

.. java:method:: public RTFluentQuery add(double op)
   :outertype: RTFluentQuery

add
^^^

.. java:method:: public RTFluentQuery add(String op)
   :outertype: RTFluentQuery

all
^^^

.. java:method:: public RTFluentQuery all(Object... o)
   :outertype: RTFluentQuery

and
^^^

.. java:method:: public RTFluentQuery and(double op)
   :outertype: RTFluentQuery

and
^^^

.. java:method:: public RTFluentQuery and(Object... o)
   :outertype: RTFluentQuery

any
^^^

.. java:method:: public RTFluentQuery any(Object... o)
   :outertype: RTFluentQuery

db
^^

.. java:method:: public RTDBQuery db(String dbName)
   :outertype: RTFluentQuery

   Select the database to operate on

   :param dbName: database name

dbCreate
^^^^^^^^

.. java:method:: public RTTopLevelQueryTypes.DDLResult dbCreate(String dbName)
   :outertype: RTFluentQuery

   create database

   :param dbName: database name

dbDrop
^^^^^^

.. java:method:: public RTTopLevelQueryTypes.DDLResult dbDrop(String dbName)
   :outertype: RTFluentQuery

   drop database

   :param dbName: database name

dbList
^^^^^^

.. java:method:: public RTTopLevelQueryTypes.StringListResult dbList()
   :outertype: RTFluentQuery

   list databases

delete
^^^^^^

.. java:method:: public RTTopLevelQueryTypes.DMLResult delete()
   :outertype: RTFluentQuery

   Delete documents in a selection

delete
^^^^^^

.. java:method:: public RTTopLevelQueryTypes.DMLResult delete(Durability durability, Boolean returnVals)
   :outertype: RTFluentQuery

   Delete documents in a selection

   :param durability: Hard or Soft (leave null for default)
   :param returnVals: if set to true the deleted document will be returned.

divide
^^^^^^

.. java:method:: public RTFluentQuery divide(double op)
   :outertype: RTFluentQuery

downcase
^^^^^^^^

.. java:method:: public RTFluentQuery downcase()
   :outertype: RTFluentQuery

eq
^^

.. java:method:: public RTFluentQuery eq(Object... o)
   :outertype: RTFluentQuery

field
^^^^^

.. java:method:: public RTFluentQuery field(String fieldName)
   :outertype: RTFluentQuery

   Get the field name

   :param fieldName: field name

filter
^^^^^^

.. java:method:: public RTFluentQueryTypes.ObjectListResult filter(RTFluentQuery lambda)
   :outertype: RTFluentQuery

   Get all the documents for which the given predicate is true.

   :param lambda: predicate

filter
^^^^^^

.. java:method:: public RTFluentQueryTypes.ObjectListResult filter(DBObject example)
   :outertype: RTFluentQuery

   Get all the documents which match the given example

   :param example: example

ge
^^

.. java:method:: public RTFluentQuery ge(Object... o)
   :outertype: RTFluentQuery

get
^^^

.. java:method:: public RTFluentQueryTypes.DBObject get(String key)
   :outertype: RTFluentQuery

   Get a document by Primary Key

   :param key: key

get
^^^

.. java:method:: public RTFluentQueryTypes.DBObject get(Number key)
   :outertype: RTFluentQuery

   Get a document by Primary Key

   :param key: key

getAll
^^^^^^

.. java:method:: public RTFluentQueryTypes.ObjectListResult getAll(String index, String... additionalIndexes)
   :outertype: RTFluentQuery

   Get all documents where the given value matches the value of the requested index(es).

   :param index: at least one index mandatory
   :param additionalIndexes: optional additional indexes

getAll
^^^^^^

.. java:method:: public RTFluentQueryTypes.ObjectListResult getAll(String indexName, String index, String... additionalIndexes)
   :outertype: RTFluentQuery

   Get all documents where the given value matches the value of the requested index(es).

   :param indexName: the name of the index if not default (id)
   :param index: at least one index mandatory
   :param additionalIndexes: optional additional indexes

getAll
^^^^^^

.. java:method:: public RTFluentQueryTypes.ObjectListResult getAll(Number index, Number... additionalIndexes)
   :outertype: RTFluentQuery

   Get all documents where the given value matches the value of the requested index(es).

   :param index: at least one index mandatory
   :param additionalIndexes: optional additional indexes

getAll
^^^^^^

.. java:method:: public RTFluentQueryTypes.ObjectListResult getAll(String indexName, Number index, Number... additionalIndexes)
   :outertype: RTFluentQuery

   Get all documents where the given value matches the value of the requested index(es).

   :param indexName: the name of the index if not default (id)
   :param index: at least one index mandatory
   :param additionalIndexes: optional additional indexes

gt
^^

.. java:method:: public RTFluentQuery gt(Object... o)
   :outertype: RTFluentQuery

insert
^^^^^^

.. java:method:: public RTTopLevelQueryTypes.DMLResult insert(com.rethinkdb.model.DBObject... objects)
   :outertype: RTFluentQuery

   insert DBObjects

   :param objects: objects to insert

insert
^^^^^^

.. java:method:: public RTTopLevelQueryTypes.DMLResult insert(List<com.rethinkdb.model.DBObject> objects)
   :outertype: RTFluentQuery

   insert DBObjects

   :param objects: objects to insert

insert
^^^^^^

.. java:method:: public RTTopLevelQueryTypes.DMLResult insert(com.rethinkdb.model.DBObject dbObject, Durability durability, boolean returnVals, boolean upsert)
   :outertype: RTFluentQuery

   Insert one DBObject into the database

   :param dbObject: dbObject
   :param durability: Hard or Soft (leave null for default)
   :param returnVals: if set to true and in case of a single insert/upsert, the inserted/updated document will be returned.
   :param upsert: when set to true, performs a replace if a document with the same primary key exists.

insert
^^^^^^

.. java:method:: public RTTopLevelQueryTypes.DMLResult insert(List<com.rethinkdb.model.DBObject> dbObjects, Durability durability, boolean returnVals, boolean upsert)
   :outertype: RTFluentQuery

   Insert a list of DBObjects into the database

   :param dbObjects: dbObjects
   :param durability: Hard or Soft (leave null for default)
   :param returnVals: if set to true and in case of a single insert/upsert, the inserted/updated document will be returned.
   :param upsert: when set to true, performs a replace if a document with the same primary key exists.

lambda
^^^^^^

.. java:method:: public RTFluentQuery lambda(DBLambda lambda)
   :outertype: RTFluentQuery

   Opens a lambda. In java 1.6, 1.7 Should be invoked as r.lambda(new DBLambda() { ... })  From java 1.8 can be invoked as r.lambda(x-> ...);

le
^^

.. java:method:: public RTFluentQuery le(Object... o)
   :outertype: RTFluentQuery

lt
^^

.. java:method:: public RTFluentQuery lt(Object... o)
   :outertype: RTFluentQuery

map
^^^

.. java:method:: public RTFluentQueryTypes.GenericListResult map(RTFluentQuery lambda)
   :outertype: RTFluentQuery

   Transform each element of the sequence by applying the given mapping function. Returns a generic List

   :param lambda: the transformation to apply

mapToDouble
^^^^^^^^^^^

.. java:method:: public RTFluentQueryTypes.DoubleListResult mapToDouble(RTFluentQuery lambda)
   :outertype: RTFluentQuery

   Transform each element of the sequence by applying the given mapping function. Returns a List of Doubles

   :param lambda: the transformation to apply

mapToString
^^^^^^^^^^^

.. java:method:: public RTFluentQueryTypes.StringListResult mapToString(RTFluentQuery lambda)
   :outertype: RTFluentQuery

   Transform each element of the sequence by applying the given mapping function. Returns a List of Strings

   :param lambda: the transformation to apply

modulus
^^^^^^^

.. java:method:: public RTFluentQuery modulus(double op)
   :outertype: RTFluentQuery

multiply
^^^^^^^^

.. java:method:: public RTFluentQuery multiply(double op)
   :outertype: RTFluentQuery

ne
^^

.. java:method:: public RTFluentQuery ne(Object... o)
   :outertype: RTFluentQuery

not
^^^

.. java:method:: public RTFluentQuery not(Object... o)
   :outertype: RTFluentQuery

or
^^

.. java:method:: public RTFluentQuery or(Object... o)
   :outertype: RTFluentQuery

pluck
^^^^^

.. java:method:: public RTFluentQueryTypes.ObjectListResult pluck(List<String> fields)
   :outertype: RTFluentQuery

   Plucks out one or more attributes

   :param fields: fields to pluck

pluckNested
^^^^^^^^^^^

.. java:method:: public RTFluentQueryTypes.ObjectListResult pluckNested(List<DBObject> dbObjects)
   :outertype: RTFluentQuery

   Plucks out one or more attributes from nested objects

   :param dbObjects: dbObjects describing fields to pluck.

replace
^^^^^^^

.. java:method:: public RTTopLevelQueryTypes.DMLResult replace(DBObject dbObject)
   :outertype: RTFluentQuery

   Replace documents in a selection

   :param dbObject: the changes to make

replace
^^^^^^^

.. java:method:: public RTTopLevelQueryTypes.DMLResult replace(RTFluentQuery lambda)
   :outertype: RTFluentQuery

   Replace documents in a selection

   :param lambda: the changes to make

split
^^^^^

.. java:method:: public RTFluentQuery split()
   :outertype: RTFluentQuery

split
^^^^^

.. java:method:: public RTFluentQuery split(String separator)
   :outertype: RTFluentQuery

split
^^^^^

.. java:method:: public RTFluentQuery split(String separator, int maxTimes)
   :outertype: RTFluentQuery

subtract
^^^^^^^^

.. java:method:: public RTFluentQuery subtract(double op)
   :outertype: RTFluentQuery

sync
^^^^

.. java:method:: public RTFluentQuery sync()
   :outertype: RTFluentQuery

   sync ensures that writes on a given table are written to permanent storage. Queries that specify soft durability (durability='soft') do not give such guarantees, so sync can be used to ensure the state of these queries. A call to sync does not return until all previous writes to the table are persisted.

table
^^^^^

.. java:method:: public RTFluentQueryTypes.ObjectListResult table(String tableName)
   :outertype: RTFluentQuery

   Select the table to operate on

   :param tableName: table name

upcase
^^^^^^

.. java:method:: public RTFluentQuery upcase()
   :outertype: RTFluentQuery

update
^^^^^^

.. java:method:: public RTTopLevelQueryTypes.DMLResult update(com.rethinkdb.model.DBObject object)
   :outertype: RTFluentQuery

   Update JSON documents in a table.

   :param object: a DBObject of the changes to make

without
^^^^^^^

.. java:method:: public RTFluentQueryTypes.ObjectListResult without(String field, String... additionalFields)
   :outertype: RTFluentQuery

   The opposite of pluck. Takes an object or a sequence of objects, and returns them with the specified paths removed.

without
^^^^^^^

.. java:method:: public RTFluentQueryTypes.ObjectListResult without(List<String> fields)
   :outertype: RTFluentQuery

   The opposite of pluck. Takes an object or a sequence of objects, and returns them with the specified paths removed.

