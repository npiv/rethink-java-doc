.. java:import:: com.rethinkdb RethinkDBConnection

.. java:import:: com.rethinkdb.ast RTTreeKeeper

.. java:import:: com.rethinkdb.fluent RTTopLevelQuery

.. java:import:: com.rethinkdb.model DBObject

.. java:import:: com.rethinkdb.response DBResponseMapper

.. java:import:: com.rethinkdb.response.model DDLResult

.. java:import:: com.rethinkdb.response.model DMLResult

.. java:import:: java.util List

RTTopLevelQuery_Types.T_DDLResult
=================================

.. java:package:: com.rethinkdb.fluent.types
   :noindex:

.. java:type:: public static class T_DDLResult extends RTTopLevelQuery
   :outertype: RTTopLevelQuery_Types

Constructors
------------
T_DDLResult
^^^^^^^^^^^

.. java:constructor:: public T_DDLResult(RTTreeKeeper treeKeeper)
   :outertype: RTTopLevelQuery_Types.T_DDLResult

Methods
-------
run
^^^

.. java:method:: @Override public DDLResult run(RethinkDBConnection connection)
   :outertype: RTTopLevelQuery_Types.T_DDLResult

