.. java:import:: com.rethinkdb.model DBObject

.. java:import:: java.util List

InsertResult
============

.. java:package:: com.rethinkdb.response
   :noindex:

.. java:type:: public class InsertResult

Methods
-------
getDeleted
^^^^^^^^^^

.. java:method:: public int getDeleted()
   :outertype: InsertResult

   always 0 for an insert operation

getErrors
^^^^^^^^^

.. java:method:: public int getErrors()
   :outertype: InsertResult

   the number of errors encountered while performing the insert.

getFirst_error
^^^^^^^^^^^^^^

.. java:method:: public String getFirst_error()
   :outertype: InsertResult

   if errors were encountered, contains the text of the first error.

getGenerated_keys
^^^^^^^^^^^^^^^^^

.. java:method:: public List<String> getGenerated_keys()
   :outertype: InsertResult

   a list of generated primary keys in case the primary keys for some documents were missing (capped to 100000).

getInserted
^^^^^^^^^^^

.. java:method:: public int getInserted()
   :outertype: InsertResult

   the number of documents that were succesfully inserted.

getNew_val
^^^^^^^^^^

.. java:method:: public DBObject getNew_val()
   :outertype: InsertResult

   if returnVals is set to true, contains the inserted/updated document.

   :return: new value

getOld_val
^^^^^^^^^^

.. java:method:: public DBObject getOld_val()
   :outertype: InsertResult

   if returnVals is set to true, contains null.

   :return: old value

getReplaced
^^^^^^^^^^^

.. java:method:: public int getReplaced()
   :outertype: InsertResult

   the number of documents that were updated when upsert is used.

getSkipped
^^^^^^^^^^

.. java:method:: public int getSkipped()
   :outertype: InsertResult

   always 0 for an insert operation

getUnchanged
^^^^^^^^^^^^

.. java:method:: public int getUnchanged()
   :outertype: InsertResult

   the number of documents that would have been modified, except that the new value was the same as the old value when doing an upsert.

toString
^^^^^^^^

.. java:method:: @Override public String toString()
   :outertype: InsertResult

