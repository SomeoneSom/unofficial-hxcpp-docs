.. role:: cpp(code)
   :language: cpp


Miscellaneous
=============

These are value functions that dont fit in any other section, or are defines that are equivalent to other functions.

Functions
---------

:cpp:`void *val_data(value val)`

    Decodes ``val`` into a C++ ``void *``.

Defines
-------

:cpp:`val_null`

    Equivalent to ``alloc_null()``.

:cpp:`val_true`

    Equivalent to ``alloc_bool(true)``.

:cpp:`val_false`

    Equivalent to ``alloc_bool(false)``.