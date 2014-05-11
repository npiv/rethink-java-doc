.. java:import:: com.rethinkdb.ast RTOperation

.. java:import:: com.rethinkdb.ast RTTreeKeeper

.. java:import:: com.rethinkdb.fluent.types RTFluentQuery_DBObjectList

.. java:import:: com.rethinkdb.fluent.types RTTopLevelQuery_StringList

.. java:import:: com.rethinkdb.proto Q2L

.. java:import:: com.rethinkdb.fluent.option Durability

.. java:import:: com.rethinkdb.response DDLResult

.. java:import:: java.util List

RTDBQuery
=========

.. java:package:: com.rethinkdb.fluent
   :noindex:

.. java:type:: public class RTDBQuery<T> extends RTTopLevelQuery<T>

Constructors
------------
RTDBQuery
^^^^^^^^^

.. java:constructor:: public RTDBQuery(RTTreeKeeper treeKeeper, Class<T> sampleClass)
   :outertype: RTDBQuery

Methods
-------
table
^^^^^

.. java:method:: public RTFluentQuery_DBObjectList table(String tableName)
   :outertype: RTDBQuery

   Select the table to operate on

   :param tableName: table name

tableCreate
^^^^^^^^^^^

.. java:method:: public RTTopLevelQuery<DDLResult> tableCreate(String tableName)
   :outertype: RTDBQuery

   Create table with tableName, primaryKey, Durability on a specific dataCenter.

tableCreate
^^^^^^^^^^^

.. java:method:: public RTTopLevelQuery<DDLResult> tableCreate(String tableName, String primaryKey, Durability durability, String datacenter)
   :outertype: RTDBQuery

   Create table with tableName, primaryKey, Durability on a specific dataCenter.

   :param tableName: tableName (mandatory)
   :param primaryKey: primary key (leave null for default)
   :param durability: durability (leave null for default)
   :param datacenter: datacenter (leave null for default)

tableDrop
^^^^^^^^^

.. java:method:: public RTTopLevelQuery<DDLResult> tableDrop(String tableName)
   :outertype: RTDBQuery

   drop table

   :param tableName: table name

tableList
^^^^^^^^^

.. java:method:: public RTTopLevelQuery_StringList tableList()
   :outertype: RTDBQuery

   list tables

