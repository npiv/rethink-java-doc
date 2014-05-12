.. java:import:: com.rethinkdb RethinkDBConnection

.. java:import:: com.rethinkdb.ast RTTreeKeeper

.. java:import:: com.rethinkdb.fluent RTFluentQuery

.. java:import:: com.rethinkdb.fluent RTTopLevelQuery

.. java:import:: com.rethinkdb.model DBObject

.. java:import:: com.rethinkdb.response DBResponseMapper

.. java:import:: com.rethinkdb.response.model DDLResult

.. java:import:: com.rethinkdb.response.model DMLResult

.. java:import:: java.util List

RTFluentLevelQuery_Types.T_StringListResult
===========================================

.. java:package:: com.rethinkdb.fluent.types
   :noindex:

.. java:type:: public static class T_StringListResult extends RTFluentQuery
   :outertype: RTFluentLevelQuery_Types

Constructors
------------
T_StringListResult
^^^^^^^^^^^^^^^^^^

.. java:constructor:: public T_StringListResult(RTTreeKeeper treeKeeper)
   :outertype: RTFluentLevelQuery_Types.T_StringListResult

Methods
-------
run
^^^

.. java:method:: @Override @SuppressWarnings public List<String> run(RethinkDBConnection connection)
   :outertype: RTFluentLevelQuery_Types.T_StringListResult

