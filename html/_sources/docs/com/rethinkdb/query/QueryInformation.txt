.. java:import:: com.rethinkdb.proto Q2L

.. java:import:: java.util ArrayList

.. java:import:: java.util Arrays

.. java:import:: java.util List

QueryInformation
================

.. java:package:: com.rethinkdb.query
   :noindex:

.. java:type::  class QueryInformation

   Used within the query package to store and build a ProtoBuf query. This class is never exposed as an external api and is only used to facilitate the RethinkQueryBuilder within the query package.

Methods
-------
getArgs
^^^^^^^

.. java:method:: protected List<Q2L.Term> getArgs()
   :outertype: QueryInformation

getOptsArgs
^^^^^^^^^^^

.. java:method:: protected List<Q2L.Term.AssocPair> getOptsArgs()
   :outertype: QueryInformation

getQueryType
^^^^^^^^^^^^

.. java:method:: protected Q2L.Query.QueryType getQueryType()
   :outertype: QueryInformation

getTermType
^^^^^^^^^^^

.. java:method:: protected Q2L.Term.TermType getTermType()
   :outertype: QueryInformation

ofQueryType
^^^^^^^^^^^

.. java:method:: public QueryInformation ofQueryType(Q2L.Query.QueryType type)
   :outertype: QueryInformation

   Set the query type

   :param type: query type
   :return: self

ofTermType
^^^^^^^^^^

.. java:method:: public QueryInformation ofTermType(Q2L.Term.TermType termType)
   :outertype: QueryInformation

   Set the termType of the first inner Term of the query. This corresponds to the action, INSERT, DB_LIST etc..

   :param termType: term type
   :return: self

withArg
^^^^^^^

.. java:method:: public QueryInformation withArg(Q2L.Term arg)
   :outertype: QueryInformation

withArgs
^^^^^^^^

.. java:method:: public QueryInformation withArgs(Q2L.Term... args)
   :outertype: QueryInformation

   The args of the first inner Term of the query. These correspond to the parameters of the term type

   :param args: Term args
   :return: self

withOptArg
^^^^^^^^^^

.. java:method:: public QueryInformation withOptArg(String name, Q2L.Term value)
   :outertype: QueryInformation

   Add an optional args of the first inner Term of the query.

   :param name: arg name
   :param value: arg value
   :return: self

