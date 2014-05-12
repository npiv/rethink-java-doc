.. java:import:: com.rethinkdb RethinkDBConnection

.. java:import:: com.rethinkdb.ast RTTreeKeeper

.. java:import:: com.rethinkdb.fluent RTFluentQuery

.. java:import:: com.rethinkdb.fluent RTTopLevelQuery

.. java:import:: com.rethinkdb.model DBObject

.. java:import:: com.rethinkdb.response DBResponseMapper

.. java:import:: com.rethinkdb.response.model DDLResult

.. java:import:: com.rethinkdb.response.model DMLResult

.. java:import:: java.util List

RTFluentLevelQuery_Types.T_ObjectListResult
===========================================

.. java:package:: com.rethinkdb.fluent.types
   :noindex:

.. java:type:: public static class T_ObjectListResult extends RTFluentQuery
   :outertype: RTFluentLevelQuery_Types

Constructors
------------
T_ObjectListResult
^^^^^^^^^^^^^^^^^^

.. java:constructor:: public T_ObjectListResult(RTTreeKeeper treeKeeper)
   :outertype: RTFluentLevelQuery_Types.T_ObjectListResult

Methods
-------
run
^^^

.. java:method:: @Override @SuppressWarnings public List<DBObject> run(RethinkDBConnection connection)
   :outertype: RTFluentLevelQuery_Types.T_ObjectListResult

