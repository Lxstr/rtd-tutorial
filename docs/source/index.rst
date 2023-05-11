Flask-Session |release|
###########################

A server-side implementation of the built-in cookie sessions for 
`Flask <https://flask.palletsprojects.com/>`__.


Installation
************

Install with the following command::

.. code-block:: python

   pip install flask-session
..



Quick Start
***********

Flask-Session is really easy to use.

Typically, all you have to do is to create your Flask application, load the configuration of choice and
then create the `Session` object by passing it the application.


.. code-block:: python

   from flask import Flask, session
   from flask_session import Session

   app = Flask(__name__)
   # SESSION_TYPE is the only mandatory configuration value, check Configuration section for more details
   SESSION_TYPE = 'redis'
   app.config.from_object(__name__)
   Session(app)

   @app.route('/set/')
   def set():
      session['key'] = 'value'
      return 'ok'

   @app.route('/get/')
   def get():
      return session.get('key', 'not set')
..

.. note::

   The `Session` instance is not used for direct access to the session, you should always use `flask.session` as shown above.

Now all of your key/value pairs are stored on the server-side database of your choice (according to the SESSION_TYPE variable). The client-side user will now have a cookie that only provides a id that the server matches against the database each time a request is sent with that cookie.


If using the application factory pattern, you may also set up your application using ``Session.init_app`` method:

.. code-block:: python

   sess = Session()
   sess.init_app(app)

..

Check out the :doc:`usage` section for further information, including
how to manage the :ref:`configuration`.


Documentation contents
######################

.. toctree::
   :maxdepth: 1

   configuration/values
   configuration/keys

.. toctree::
   :maxdepth: 2

   usage


Indices and tables
##################

* :ref:`genindex`
* :ref:`modindex`