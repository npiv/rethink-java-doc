.. java:import:: com.rethinkdb RethinkDBConnection

.. java:import:: com.rethinkdb.ast RTTreeKeeper

.. java:import:: com.rethinkdb.fluent RTFluentQuery

.. java:import:: com.rethinkdb.fluent RTTopLevelQuery

.. java:import:: com.rethinkdb.model DBObject

.. java:import:: com.rethinkdb.response DBResponseMapper

.. java:import:: com.rethinkdb.response.model DDLResult

.. java:import:: com.rethinkdb.response.model DMLResult

.. java:import:: java.util List

RTFluentQueryTypes.StringListResult
===================================

.. java:package:: com.rethinkdb.fluent.types
   :noindex:

.. java:type:: public static class StringListResult extends RTFluentQuery
   :outertype: RTFluentQueryTypes

Constructors
------------
StringListResult
^^^^^^^^^^^^^^^^

.. java:constructor:: public StringListResult(RTTreeKeeper treeKeeper)
   :outertype: RTFluentQueryTypes.StringListResult

Methods
-------
run
^^^

.. java:method:: @Override @SuppressWarnings public List<String> run(RethinkDBConnection connection)
   :outertype: RTFluentQueryTypes.StringListResult

