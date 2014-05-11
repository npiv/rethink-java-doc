.. java:import:: com.rethinkdb.model DBObject

.. java:import:: com.rethinkdb.response DBResultFactory

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

setDbOptionIfNeeded
^^^^^^^^^^^^^^^^^^^

.. java:method:: public void setDbOptionIfNeeded(Q2L.Query.Builder q, String db)
   :outertype: RethinkDBConnection

use
^^^

.. java:method:: public void use(String dbName)
   :outertype: RethinkDBConnection

