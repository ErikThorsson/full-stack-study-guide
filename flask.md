# Contexts
`from flask import request`

Can get info of current request from this global.
* Two different request have diff request.path

`from flask import url_for`
* ![](images/Screen Shot 2023-02-06 at 9.43.01 AM.png)
https://stackoverflow.com/questions/7478366/create-dynamic-urls-in-flask-with-url-for

# Local Context
local = Local() 
* Resolves to thread specific data for a request
* local.first_name = "foo"

# Request Context
Allows for internal redirects. Pushes request B on top of the 
stack and allows req A to return B's response. 

Request context is one item of "request context stack".
Similar to "app_context" and "app context stack"

Flask can have multiple apps.


# Multiprocessing

* gunicorn, gevent
* greenlets: lightweight coroutines for in-process sequential concurrent programming.
  * cooperative and sequential
  * greenlets can be used on their own, but they are frequently used with frameworks such as gevent to provide higher-level abstractions and asynchronous I/O.
  * thread(greenlet): get with `get_ident()`
  * https://greenlet.readthedocs.io/en/latest/
* Threads are truly parallel.
  * Threads (in theory) are preemptive and parallel [1], meaning that multiple threads can be processing work at the same time.
* gevent is an example of using greenlets to integrate with IO event loops (libev and libuv) to provide a complete asynchronous environment using familiar programming patterns.

https://github.com/iximiuz/flask-gevent-tutorial
