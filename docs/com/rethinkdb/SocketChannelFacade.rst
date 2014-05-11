.. java:import:: com.google.protobuf InvalidProtocolBufferException

.. java:import:: com.rethinkdb.proto Q2L

.. java:import:: java.io IOException

.. java:import:: java.net InetSocketAddress

.. java:import:: java.nio ByteBuffer

.. java:import:: java.nio ByteOrder

.. java:import:: java.nio.channels SocketChannel

SocketChannelFacade
===================

.. java:package:: com.rethinkdb
   :noindex:

.. java:type:: public class SocketChannelFacade

Methods
-------
close
^^^^^

.. java:method:: public void close()
   :outertype: SocketChannelFacade

connect
^^^^^^^

.. java:method:: public void connect(String hostname, int port)
   :outertype: SocketChannelFacade

read
^^^^

.. java:method:: public Q2L.Response read()
   :outertype: SocketChannelFacade

readLEInt
^^^^^^^^^

.. java:method:: public int readLEInt()
   :outertype: SocketChannelFacade

readString
^^^^^^^^^^

.. java:method:: public String readString()
   :outertype: SocketChannelFacade

write
^^^^^

.. java:method:: public void write(byte[] bytes)
   :outertype: SocketChannelFacade

writeLEInt
^^^^^^^^^^

.. java:method:: public void writeLEInt(int i)
   :outertype: SocketChannelFacade

writeStringWithLength
^^^^^^^^^^^^^^^^^^^^^

.. java:method:: public void writeStringWithLength(String s)
   :outertype: SocketChannelFacade

