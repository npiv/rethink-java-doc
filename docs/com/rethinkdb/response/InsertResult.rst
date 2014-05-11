.. java:import:: com.rethinkdb.mapper DBObjectMapper

.. java:import:: com.rethinkdb.model DBObject

.. java:import:: com.rethinkdb.proto Q2L

.. java:import:: java.util List

InsertResult
============

.. java:package:: com.rethinkdb.response
   :noindex:

.. java:type:: public class InsertResult implements DBResult

Methods
-------
getDeleted
^^^^^^^^^^

.. java:method:: public int getDeleted()
   :outertype: InsertResult

getErrors
^^^^^^^^^

.. java:method:: public int getErrors()
   :outertype: InsertResult

getFirst_error
^^^^^^^^^^^^^^

.. java:method:: public String getFirst_error()
   :outertype: InsertResult

getGenerated_keys
^^^^^^^^^^^^^^^^^

.. java:method:: public List<String> getGenerated_keys()
   :outertype: InsertResult

getInserted
^^^^^^^^^^^

.. java:method:: public int getInserted()
   :outertype: InsertResult

getNew_val
^^^^^^^^^^

.. java:method:: public DBObject getNew_val()
   :outertype: InsertResult

getOld_val
^^^^^^^^^^

.. java:method:: public DBObject getOld_val()
   :outertype: InsertResult

getReplaced
^^^^^^^^^^^

.. java:method:: public int getReplaced()
   :outertype: InsertResult

getSkipped
^^^^^^^^^^

.. java:method:: public int getSkipped()
   :outertype: InsertResult

getUnchanged
^^^^^^^^^^^^

.. java:method:: public int getUnchanged()
   :outertype: InsertResult

toString
^^^^^^^^

.. java:method:: @Override public String toString()
   :outertype: InsertResult

