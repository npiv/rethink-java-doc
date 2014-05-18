###################
String Manipulation
###################

*****
match
*****
Matches against a regular expression. If there is a match, returns an object with the fields:

* str: The matched string
* start: The matched string"s start
* end: The matched string"s end
* groups: The capture groups defined with parentheses

If no match is found, returns None.

Example: Get all users whose name starts with "A".

.. code-block:: java

	r.table("users").filter(doc->
		doc.field("name").match("^A")
	).run(conn);

*****
split
*****
Splits a string into substrings. Splits on whitespace when called with no arguments. When called with a separator, splits on that separator. When called with a separator and a maximum number of splits, splits on that separator at most max_splits times. (Can be called with None as the separator if you want to split on whitespace while still specifying max_splits.)

Mimics the behavior of Python"s string.split in edge cases, except for splitting on the empty string, which instead produces an array of single-character strings.

Example: Split on whitespace.

.. code-block:: java

	r.expr("foo  bar bax").split().run(conn);


******
upcase
******
Upcases a string.

Example:

.. code-block:: java

	r.expr("Sentence about LaTeX.").upcase().run(conn)


********
downcase
********
Downcases a string.

Example:

.. code-block:: java

	r.expr("Sentence about LaTeX.").downcase().run(conn)
