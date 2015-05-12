Installation
============

Get the code
------------

Installation is easy using ``pip`` and the only requirement is a recent version of Django.

.. code-block:: bash

    $ pip install django-activity-stream

or get it from source

.. code-block:: bash

    $ pip install git+https://github.com/justquick/django-activity-stream.git#egg=actstream


Basic app configuration
-----------------------

Then to add the Django Activity Stream to your project add the app ``actstream`` to your ``INSTALLED_APPS`` and urlconf.

.. code-block:: python

    INSTALLED_APPS = (
        'django.contrib.auth',
        ...
        'actstream'
    )

.. warning:: In Django versions older than 1.7, the app must be placed somewhere after all the apps that are going to be generating activities (eg ``django.contrib.auth``). The safest thing to do is to have it as the last app in ``INSTALLED_APPS``.

Add the activity urls to your urlconf

.. code-block:: python

    urlpatterns = patterns('',
        ...
        ('^activity/', include('actstream.urls')),
        ...
    )

The activity urls are not required for basic usage but provide activity :ref:`feeds` and handle following, unfollowing and querying of followers.

3rd Party Extras
----------------

If you have `South <http://south.aeracode.org/>`_ installed you have to migrate actstream tables

.. code-block:: bash

    $ django-admin.py migrate actstream

If you want to use custom data on your actions, then make sure you have `django-jsonfield <https://github.com/bradjasper/django-jsonfield/>`_ installed

.. code-block:: bash

    $ pip install django-jsonfield

You can learn more at :ref:`custom-data`


Supported Environments
----------------------

The following Python/Django versions and database configurations have been tested to work with the latest version of django-activity-stream.

* PostgreSQL 9.1, 9.2 and 9.3
    * **Psy** = `psycopg2 2.5.4 <http://initd.org/psycopg/docs/>`_
    * **PCffi** = `psycopg2cffi 2.5.2 <https://github.com/chtd/psycopg2cffi>`_
* MySQL 5.5 and 5.6
    * **My** = `MySQL-python 1.2.5 <https://github.com/farcepest/MySQLdb1>`_
    * **PyMy** = `PyMySQL 0.6.2 <https://github.com/PyMySQL/PyMySQL/>`_
* **S** = `Sqlite 3.7 <https://docs.python.org/2/library/sqlite3.html>`_

+--------------+------------+------------+------------+------------+------------+------------+---------+
|              | Py 2.6     | Py 2.7     | Py 3.2     | Py 3.3     | Py 3.4     | PyPy 2     | PyPy 3  |
+==============+============+============+============+============+============+============+=========+
| Django 1.4   |  Psy/My/S  |  Psy/My/S  |            |            |            | PCffi/My/S |         |
+--------------+------------+------------+------------+------------+------------+------------+---------+
| Django 1.5   |  Psy/My/S  |  Psy/My/S  | Psy/PyMy/S | Psy/PyMy/S | Psy/PyMy/S | PCffi/My/S |  My/S   |
+--------------+------------+------------+------------+------------+------------+------------+---------+
| Django 1.6   |  Psy/My/S  |  Psy/My/S  | Psy/PyMy/S | Psy/PyMy/S | Psy/PyMy/S | PCffi/My/S |  My/S   |
+--------------+------------+------------+------------+------------+------------+------------+---------+
| Django 1.7   |  Psy/My/S  |  Psy/My/S  | Psy/PyMy/S | Psy/PyMy/S | Psy/PyMy/S | PCffi/My/S |  My/S   |
+--------------+------------+------------+------------+------------+------------+------------+---------+
