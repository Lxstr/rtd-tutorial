Configuration
###########################


The following configuration values exist for Flask-Session.  Flask-Session loads these values from your Flask application config, so you should configure
your app first before you pass it to Flask-Session.  Note that these values cannot be modified after the ``init_app`` was applied so make sure to not modify them at runtime.

We are not supplying something like `SESSION_REDIS_HOST` and `SESSION_REDIS_PORT`, if you want to use the `RedisSessionInterface`, you should configure `SESSION_REDIS` to your own `redis.Redis` instance. This gives you more flexibility, like maybe you want to use the same `redis.Redis` instance for cache purpose too, then you do not need to keep two `redis.Redis` instance in the same process.

The following configuration values are builtin configuration values within Flask itself that are related to session.  **They are all understood by
Flask-Session, for example, you should use PERMANENT_SESSION_LIFETIME to control your session lifetime.**

Configuration Values
************

| Name | Description |
|--|--|
|`SESSION_COOKIE_NAME`          | the name of the session cookie         |
|`SESSION_COOKIE_DOMAIN`        | the domain for the session cookie.  If this is not set, the cookie will be valid for all subdomains of `SERVER_NAME`. |
|`SESSION_COOKIE_PATH`          | the path for the session cookie.  If this is not set the cookie will be valid for all of `APPLICATION_ROOT` or if that is not set for `'/'`. |
|`SESSION_COOKIE_HTTPONLY`      | controls if the cookie should be set with the httponly flag.  Defaults to `True`. |
|`SESSION_COOKIE_SECURE`        | controls if the cookie should be set with the secure flag.  Defaults to `False`. |
|`PERMANENT_SESSION_LIFETIME`   | the lifetime of a permanent session as :class:`datetime.timedelta` object. Starting with Flask 0.8 this can also be an integer representing seconds. |

Configuration Keys
************


Basically you only need to configure `SESSION_TYPE`.

By default, all non-null sessions in Flask-Session are permanent.

| Name | Description |
|--|--|
| `SESSION_TYPE`            |  Specifies which type of session interface to use.  Built-in session types:<br>- **null**: NullSessionInterface (default) <br> - **redis**: RedisSessionInterface <br> - **memcached**: MemcachedSessionInterface <br> - **filesystem**: FileSystemSessionInterface <br> - **mongodb**: MongoDBSessionInterface <br> - **sqlalchemy**: SqlAlchemySessionInterface <br> - **elasticsearch**: ElasticsearchSessionInterface <br> - **datastore**: GoogleCloudDatastoreSessionInterface <br> - **firestore**: GoogleFireStoreSessionInterface <br> - **peewee**: PeeweeSessionInterface <br> - **dynamodb**: DynamoDBSessionInterface |
| `SESSION_PERMANENT`       |  Whether use permanent session or not, default to be `True` |
| `SESSION_USE_SIGNER`      |  Whether sign the session cookie sid or not, if set to `True`, you have to set :attr:`flask.Flask.secret_key`, default to be `False` |
| `SESSION_KEY_PREFIX`      |  A prefix that is added before all session keys. This makes it possible to use the same backend storage server for different apps, default "session:" |
