.. java:import:: com.rethinkdb.ast RTOperationConverter

.. java:import:: com.rethinkdb.model DBObject

.. java:import:: com.rethinkdb.proto ProtoUtil

.. java:import:: com.rethinkdb.proto Q2L

.. java:import:: com.rethinkdb.proto RAssocPairBuilder

.. java:import:: com.rethinkdb.proto RTermBuilder

.. java:import:: com.rethinkdb.response DBResultFactory

.. java:import:: java.util.concurrent.atomic AtomicInteger

RethinkDBConnection
===================

.. java:package:: com.rethinkdb
   :noindex:

.. java:type:: public class RethinkDBConnection

Constructors
------------
RethinkDBConnection
^^^^^^^^^^^^^^^^^^^

.. java:constructor:: public RethinkDBConnection()
   :outertype: RethinkDBConnection

RethinkDBConnection
^^^^^^^^^^^^^^^^^^^

.. java:constructor:: public RethinkDBConnection(String hostname)
   :outertype: RethinkDBConnection

RethinkDBConnection
^^^^^^^^^^^^^^^^^^^

.. java:constructor:: public RethinkDBConnection(String hostname, int port)
   :outertype: RethinkDBConnection

RethinkDBConnection
^^^^^^^^^^^^^^^^^^^

.. java:constructor:: public RethinkDBConnection(String hostname, int port, String authKey)
   :outertype: RethinkDBConnection

RethinkDBConnection
^^^^^^^^^^^^^^^^^^^

.. java:constructor:: public RethinkDBConnection(String hostname, int port, String authKey, int timeout)
   :outertype: RethinkDBConnection

Methods
-------
close
^^^^^

.. java:method:: public void close()
   :outertype: RethinkDBConnection

reconnect
^^^^^^^^^

.. java:method:: public void reconnect()
   :outertype: RethinkDBConnection

run
^^^

.. java:method:: public DBObject run(Q2L.Query.Builder query)
   :outertype: RethinkDBConnection

run
^^^

.. java:method:: public DBObject run(Q2L.Term term)
   :outertype: RethinkDBConnection

use
^^^

.. java:method:: public void use(String dbName)
   :outertype: RethinkDBConnection

