.. java:import:: com.rethinkdb RethinkDBConnection

.. java:import:: com.rethinkdb.ast RTTreeKeeper

.. java:import:: com.rethinkdb.fluent RTTopLevelQuery

.. java:import:: com.rethinkdb.model DBObject

.. java:import:: com.rethinkdb.response DBResponseMapper

.. java:import:: com.rethinkdb.response.model DDLResult

.. java:import:: com.rethinkdb.response.model DMLResult

.. java:import:: java.util List

RTTopLevelQuery_Types.T_DMLResult
=================================

.. java:package:: com.rethinkdb.fluent.types
   :noindex:

.. java:type:: public static class T_DMLResult extends RTTopLevelQuery
   :outertype: RTTopLevelQuery_Types

Constructors
------------
T_DMLResult
^^^^^^^^^^^

.. java:constructor:: public T_DMLResult(RTTreeKeeper treeKeeper)
   :outertype: RTTopLevelQuery_Types.T_DMLResult

Methods
-------
run
^^^

.. java:method:: @Override public DMLResult run(RethinkDBConnection connection)
   :outertype: RTTopLevelQuery_Types.T_DMLResult

