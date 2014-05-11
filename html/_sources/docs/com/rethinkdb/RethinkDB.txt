.. java:import:: com.rethinkdb.fluent RTFluentQuery

RethinkDB
=========

.. java:package:: com.rethinkdb
   :noindex:

.. java:type:: public class RethinkDB extends RTFluentQuery

   The starting point for all interaction with RethinkDB. This singleton corresponds to r in the documentation and is used to open a connection or generate a query. i.e:

   .. parsed-literal::

      RethinkDB.r.connect("hostname", 28015);

   Or

   .. parsed-literal::

      RethinkDB.r.dbCreate("test")

Fields
------
r
^

.. java:field:: public static RethinkDB r
   :outertype: RethinkDB

   The Singleton to use to begin interacting with RethinkDB Driver

Methods
-------
connect
^^^^^^^

.. java:method:: public RethinkDBConnection connect()
   :outertype: RethinkDB

   Connect with default hostname and default port and default timeout

   :return: connection

connect
^^^^^^^

.. java:method:: public RethinkDBConnection connect(String hostname)
   :outertype: RethinkDB

   connect with given hostname and default port and default timeout

   :param hostname: hostname
   :return: connection

connect
^^^^^^^

.. java:method:: public RethinkDBConnection connect(String hostname, int port)
   :outertype: RethinkDB

   connect with given hostname and port and default timeout

   :param hostname: hostname
   :param port: port
   :return: connection

connect
^^^^^^^

.. java:method:: public RethinkDBConnection connect(String hostname, int port, String authKey)
   :outertype: RethinkDB

   connect with given hostname, port and authentication key and default timeout

   :param hostname: hostname
   :param port: port
   :param authKey: authentication key
   :return: connection

connect
^^^^^^^

.. java:method:: public RethinkDBConnection connect(String hostname, int port, String authKey, int timeout)
   :outertype: RethinkDB

   connect with given hostname, port, authentication key and timeout

   :param hostname: hostname
   :param port: port
   :param authKey: authentication key
   :param timeout: the maximum time to wait attempting to connect
   :return: connection

