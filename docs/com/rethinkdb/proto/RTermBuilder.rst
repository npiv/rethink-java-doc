.. java:import:: com.rethinkdb.model DBObject

RTermBuilder
============

.. java:package:: com.rethinkdb.proto
   :noindex:

.. java:type:: public class RTermBuilder

   Facilitate creation of ProtoBuf Term objects

Methods
-------
addArg
^^^^^^

.. java:method:: public RTermBuilder addArg(Term... args)
   :outertype: RTermBuilder

build
^^^^^

.. java:method:: public Term build()
   :outertype: RTermBuilder

createDatumTerm
^^^^^^^^^^^^^^^

.. java:method:: protected static Term createDatumTerm(Object value)
   :outertype: RTermBuilder

datumTerm
^^^^^^^^^

.. java:method:: public static Term datumTerm(String payload)
   :outertype: RTermBuilder

datumTerm
^^^^^^^^^

.. java:method:: public static Term datumTerm(Number payload)
   :outertype: RTermBuilder

datumTerm
^^^^^^^^^

.. java:method:: public static Term datumTerm(boolean payload)
   :outertype: RTermBuilder

datumTerm
^^^^^^^^^

.. java:method:: public static Term datumTerm(DBObject payload)
   :outertype: RTermBuilder

dbTerm
^^^^^^

.. java:method:: public static Term dbTerm(String dbName)
   :outertype: RTermBuilder

ofType
^^^^^^

.. java:method:: public RTermBuilder ofType(Term.TermType type)
   :outertype: RTermBuilder

tableTerm
^^^^^^^^^

.. java:method:: public static Term tableTerm(String tableName)
   :outertype: RTermBuilder

