---
tags: python, clastic, web application, framework
title: Notes about Clastic.
---
# Notes about Clastic

Some notes, thoughts, and questions without any particular order.

## Route decorators

The cline application under the `examples` directory uses route decorators.
Other examples don't use them.
Considering that these might make route ordering difficult,
are they still valid, or are they deprecated/discouraged?


## Testing

Clastic's parameter injection makes it very easy
to unit test endpoint functions.
No need to instantiate an app or a client (even using `get_local_client()`).
Passing a dummy context is easy (only a dict),
but is there a way to pass a dummy request for functions
that want to access the `request` built-in?

https://docs.pylonsproject.org/projects/pyramid/en/latest/api/testing.html#pyramid.testing.DummyRequest


## Application termination

Is there a way of running some code when the application exits?
Like closing database connections?


## Static resources

The default settings for static resources are confusing.
Setting the default value of `use_static` to `False`
and deprecating the feature after a few versions might be a good idea.

What's the use case for the `static_prefix` setting?

As a related note,
the webtop application uses `META_ASSETS_APP` for serving static assets
(if I understand correctly).
It would be better if all examples followed the same design,
it gets confusing when looking at the example application codes.


## Documentation

Where to go from here?

Enough tutorials for now, I believe.

Small descriptions and examples of existing middleware.

### How-Tos

how do I ...

- ... write a custom renderer (and why would I need to)?
- ... use mako/chameleon/other template engine?
- ... use sqlalchemy? (not my priority)
- ... write my own middleware (and why)?

### Authentication

- implementing one yourself
- something like flask-login? (personally, I find it complicated in fact; would be nice to have something simpler, if possible)
- something like flask-dance?
- integrating with python-social?
- jwt


## Extending Clastic

- Any plugin infrastructure?


## obj_browser app

Is this something like traversal routing in Pyramid/Morepath?

https://docs.pylonsproject.org/projects/pyramid/en/latest/narr/traversal.html

https://morepath.readthedocs.io/en/latest/quickstart.html#routing

> This is an application for browsing objects in the Python process space, useful for debugging live process with context objects, etc. It can help with memory/greenlet/connection leaks too.
> 
> Doesn't work so well in pools of processes, but handy for development.