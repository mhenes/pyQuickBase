
pyQuickBase: Python Interface to QuickBase API
==================================================

.. image:: https://badge.fury.io/py/pyquickbase.png
    :target: http://badge.fury.io/py/pyquickbase

pyQuickBase is an MIT licensed client library for the Intuit QuickBase API, using `Requests`_ for HTTP, and `lxml`_ is used for XML processing.

Warning - this library is no longer maintained!
-------

I no longer work with the QuickBase platform and can not guarantee that this library even works. If you are a Python developer and would like to take over maintaining it; please contact me by email at kevin.seelbach@gmail.com.


Version
-------

0.2.5
-----
- Added streaming to the request function.

0.2.4
-----
- Fixed _parse_records to check for <url> child in structured record fields (for file downloading).

0.2.3
-----
- Added a new `return_file` function to retrieve a QuickBase file as a Python file object.

0.2.2
-----
- Fixed a readme issue.

0.2.1
-----
-  Made the package pip installable.
-  Added support for uploading files with add\_record module.


Installation
------------

To install pyQuickBase, simply:

.. code-block:: bash

    $ pip install pyquickbase

API Features
------------

-  add\_record
-  add\_replace\_db\_page
-  delete\_record
-  do\_query
-  do\_query\_count
-  edit\_record
-  get\_db\_page
-  get\_schema
-  granted\_dbs
-  import\_from\_csv
-  list\_db\_pages

Other Modules
-------------

-  get\_file -- used in conjunction with a query and specified
   attachment field ID, can download one or many files from a table to
   local folder.

Requirements
------------
-  Python (2.6+)
-  `lxml`_
-  `Requests`_
-  chardet
-  cStringIO


Examples
--------

Initialize the client:

.. code-block:: pycon

    >>> import quickbase
    >>> client = quickbase.Client(username, password, database=database,
            apptoken=token, base_url=url)
    ...

List all records in a table:

.. code-block:: pycon

    >>> import datetime
    >>> response = client.do_query(query="'3'.XEX.''}", structured=True,
            columns='a', database=database)
    >>> for record in response:
            dt = datetime.datetime.fromtimestamp(int(r['1']) / 1000).strftime('%m-%d-%Y')
            print "Record ID# %s was created on %s" % (record['3'], dt)
    ...


License
-------

MIT, See license file.

Developed by `Kevin V Seelbach`_.  I am no longer working on the QuickBase platform (have not since late 2012) and can not guarantee support or that this implementation even works. 


Contribute
----------
#. Fork `the repository`_ on GitHub to start making your changes to the **master** branch (or branch off of it).
#. Write a test which shows that the bug was fixed or that the feature works as expected.



.. _`the repository`: http://github.com/kevinseelbach/pyQuickBase
.. _lxml: http://lxml.de/
.. _Requests: http://docs.python-requests.org/en/latest/
.. _`Kevin V Seelbach`: kevin.seelbach@gmail.com
