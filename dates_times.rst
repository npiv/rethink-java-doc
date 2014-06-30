###############
Dates and Times
###############

***
now
***

Return a time object representing the current time in UTC. The command now() is computed once when the server receives the query, so multiple instances of r.now() will always return the same time inside a query.

Example: Add a new user with the time at which he subscribed.

.. code-block:: java

	r.table("users").insert(new MapObject()
		.with("name" "John")
	    .with("date", r.now())
	).run(conn)

****
time
****

Create a time object for a specific time.

examples:

.. code-block:: java

	r.time(2012, 1, 1) // date

	r.time(2014,2,3, 22,45,01) // with time

	r.time(2012, 1, 1, "Z") // date	with timezone


*********
epochTime
*********
Create a time object based on seconds since epoch. The first argument is a double and will be rounded to three decimal places (millisecond-precision).

Example: Update the birthdate of the user "John" to November 3rd, 1986.

.. code-block:: java

	r.epoch_time(531360000)


**********
inTimezone
**********
Return a new time object with a different timezone. While the time stays the same, the results returned by methods such as hours() will change since they take the timezone into account. The timezone argument has to be of the ISO 8601 format.

Example: Hour of the day in San Francisco (UTC/GMT -8, without daylight saving time).

.. code-block:: java

	r.now().inTimezone("-08:00").hours().run(conn)


********
timezone
********
Return the timezone of the time object.

Example: Return all the users in the "-07:00" timezone.

.. code-block:: java

	r.table("users").filter(user->
    	user.field("subscriptionDate").timezone().eq("-07:00")
	)


******
during
******
Return if a time is between two other times.

Example: Retrieve all the posts that were posted between December 1st, 2013 (inclusive) and December 10th, 2013 (exclusive).

.. code-block:: java

	r.table("posts").filter(row->
    	row.field("date").during(
    		r.time(2013, 12, 1, "Z"),  // left bound
    		r.time(2013, 12, 10, "Z",  // right bound
    		true,  // left inclusive
    		false) // right inclusive
    ))


****
date
****

return a new time object only based on the day, month and year (ie. the same day at 00:00).

Example: Retrieve all the users whose birthday is today

.. code-block:: java

	r.table("users").filter(user->
	    user.field("birthdate").date().eq(r.now().date())
	).run(conn)


***********
timeOfDay
***********

Return the number of seconds elapsed since the beginning of the day stored in the time object.

Example: Retrieve posts that were submitted before noon.

.. code-block:: java

	r.table("posts").filter(row->
	    row.field("date").timeOfDay().lt(12*60*60)
	).run(conn)

****
year
****

Return the year of a time object.

Example: Retrieve all the users born in 1986.

.. code-block:: java

	r.table("users").filter(user->
	    user.field("birthdate").year().eq(1986)
	).run(conn)

*****
month
*****

Return the month of a time object as a number between 1 and 12. For your convenience, the terms r.january, r.february etc. are defined and map to the appropriate integer.

Example: Retrieve all the users who were born in November.

.. code-block:: java

	r.table("users").filter(row->
	    row.field("birthdate").month().eq(11)
	)


****
day
****

Return the day of a time object as a number between 1 and 31.

Example: see month


***********
dayOfWeek
***********

Return the day of week of a time object as a number between 1 and 7 (following ISO 8601 standard). For your convenience, the terms r.monday, r.tuesday etc. are defined and map to the appropriate integer.

Example: see month



************
dayOfYear
************

Return the day of the year of a time object as a number between 1 and 366 (following ISO 8601 standard).

Example: see month



********
hours
********

Return the hour in a time object as a number between 0 and 23.

Example: see month


********
minutes
********

Return the minute in a time object as a number between 0 and 59.

Example: see month


********
seconds
********

Return the seconds in a time object as a number between 0 and 59.999 (double precision).

Example: see month


**********
toISO8601
**********

Convert a time object to its iso 8601 format.

Example: Return the current time in an ISO8601 format.

.. code-block:: java

	r.now().toISO8601()


*************	
toEpochTime
*************

Convert a time object to its epoch time.

Example: Return the current time in seconds since the Unix Epoch with millisecond-precision.

.. code-block:: java

	r.now().toEpochTime()