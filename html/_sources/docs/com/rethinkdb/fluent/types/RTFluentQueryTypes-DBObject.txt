.. java:import:: com.rethinkdb RethinkDBConnection

.. java:import:: com.rethinkdb.ast RTTreeKeeper

.. java:import:: com.rethinkdb.fluent RTFluentQuery

.. java:import:: com.rethinkdb.fluent RTTopLevelQuery

.. java:import:: com.rethinkdb.model DBObject

.. java:import:: com.rethinkdb.response DBResponseMapper

.. java:import:: com.rethinkdb.response.model DDLResult

.. java:import:: com.rethinkdb.response.model DMLResult

.. java:import:: java.util List

RTFluentQueryTypes.DBObject
===========================

.. java:package:: com.rethinkdb.fluent.types
   :noindex:

.. java:type:: public static class DBObject extends RTFluentQuery
   :outertype: RTFluentQueryTypes

Constructors
------------
DBObject
^^^^^^^^

.. java:constructor:: public DBObject(RTTreeKeeper treeKeeper)
   :outertype: RTFluentQueryTypes.DBObject

Methods
-------
run
^^^

.. java:method:: @Override public com.rethinkdb.model.DBObject run(RethinkDBConnection connection)
   :outertype: RTFluentQueryTypes.DBObject

