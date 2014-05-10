.. java:import:: com.rethinkdb RethinkDBConnection

.. java:import:: com.rethinkdb RethinkDBException

.. java:import:: com.rethinkdb.mapper DBObjectMapper

.. java:import:: com.rethinkdb.model DBObject

.. java:import:: com.rethinkdb.proto Q2L

.. java:import:: com.rethinkdb.response DBResult

.. java:import:: java.util.concurrent.atomic AtomicInteger

RethinkTerminatingQuery
=======================

.. java:package:: com.rethinkdb.query
   :noindex:

.. java:type:: public class RethinkTerminatingQuery<T extends DBResult>

   A query that has no further actions available upon it except run This object is created by RethinkQueryBuilder when the query is complete

Constructors
------------
RethinkTerminatingQuery
^^^^^^^^^^^^^^^^^^^^^^^

.. java:constructor:: public RethinkTerminatingQuery(Class<? extends DBResult> resultClazz, QueryInformation queryInformation)
   :outertype: RethinkTerminatingQuery

Methods
-------
run
^^^

.. java:method:: public T run(RethinkDBConnection connection)
   :outertype: RethinkTerminatingQuery

   run the query on the given connection

   :param connection: connection
   :return: DBResult

