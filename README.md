
# Python Redis Server

This is a simple implementation of a Redis clone written in Python.
It is not meant to be a fully-featured Redis server, but rather a demonstration of how the Redis protocol works.

## Features

The following Redis commands are implemented:

- `PING`: Sends a `PONG` response to the client.
- `ECHO`: Echoes back the provided argument to the client.
- `SET`: Sets a key-value pair in the database. Optionally takes a `px` argument to set an expiry time in milliseconds.
- `GET`: Gets the value of a key from the database. If the key has an expiry time set and it has passed, the key-value pair is deleted and `-1` is returned to the client.

## Running the Server

To run the server, simply execute the following command (it requires Python 3):

```
./redis-clone
```

The server will listen on `localhost:6379` for incoming connections.

## Connecting to the Server

You can use any Redis client to connect to the server. For example, to connect to the server using `redis-cli`, run the following command:

```
redis-cli -h localhost -p 6379
```

You should then see a `127.0.0.1:6379>` prompt, where you can enter Redis commands as you would with a regular Redis server.

## Limitations

This Redis clone has several limitations compared to a real Redis server:

- Only a limited set of commands are implemented.
- The database is not persisted to disk, so all data is lost when the server is stopped.
- There is no support for multiple databases or authentication.

## Common Bug

When running your server locally, you might see an error like this:

```
Traceback (most recent call last):
  File "/.../python3.7/runpy.py", line 193, in _run_module_as_main
    "__main__", mod_spec)
  File "/.../python3.7/runpy.py", line 85, in _run_code
    exec(code, run_globals)
  File "/app/app/main.py", line 11, in <module>
    main()
  File "/app/app/main.py", line 6, in main
    s = socket.create_server(("localhost", 6379), reuse_port=True)
AttributeError: module 'socket' has no attribute 'create_server'
```

This is because `socket.create_server` was introduced in Python 3.8, and you
might be running an older version.

You can fix this by installing Python 3.8 locally and using that.

