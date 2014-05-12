.. java:import:: com.rethinkdb RethinkDBConnection

.. java:import:: com.rethinkdb.ast RTTreeKeeper

.. java:import:: com.rethinkdb.fluent RTTopLevelQuery

.. java:import:: com.rethinkdb.model DBObject

.. java:import:: com.rethinkdb.response DBResponseMapper

.. java:import:: com.rethinkdb.response.model DDLResult

.. java:import:: com.rethinkdb.response.model DMLResult

.. java:import:: java.util List

RTTopLevelQueryTypes.DDLResult
==============================

.. java:package:: com.rethinkdb.fluent.types
   :noindex:

.. java:type:: public static class DDLResult extends RTTopLevelQuery
   :outertype: RTTopLevelQueryTypes

Constructors
------------
DDLResult
^^^^^^^^^

.. java:constructor:: public DDLResult(RTTreeKeeper treeKeeper)
   :outertype: RTTopLevelQueryTypes.DDLResult

Methods
-------
run
^^^

.. java:method:: @Override public com.rethinkdb.response.model.DDLResult run(RethinkDBConnection connection)
   :outertype: RTTopLevelQueryTypes.DDLResult

