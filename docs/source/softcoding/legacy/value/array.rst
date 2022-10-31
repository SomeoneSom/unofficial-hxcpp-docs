.. role:: cpp(code)
   :language: cpp

Arrays
======

The Haxe type ``Array<T>`` is represented in C++ as a `T *`, where ``T`` is a type.
Both of these represent a list of objects.

Encoding
--------

:cpp:`value alloc_array(int size)`

    Creates an array ``value`` objects of size ``size``.

Type Checking
-------------

:cpp:`bool val_is_array(value val)`

    Checks if ``val`` is an array object.

Array Access
------------

:cpp:`int val_array_size(value val)`

    Gets the size of ``val``.

:cpp:`void val_array_set_size(value val, int size)`

    Sets the size of ``val`` to ``size``.

:cpp:`value val_array_i(value val, int pos)`

    Gets the element in ``val`` at position ``pos``.

:cpp:`void val_array_set_i(value val, int pos, value val2)`

    Sets the element in ``val`` at position ``pos`` to ``val2``.

:cpp:`void val_array_push(value val, value val2)`

    Pushes ``val2`` onto ``val``.

Decoding
--------

:cpp:`bool *val_array_bool(value val)`

    Decodes ``val`` into a C++ ``bool *``.

:cpp:`int *val_array_int(value val)`

    Decodes ``val`` into a C++ ``int *``.

:cpp:`double *val_array_double(value val)`

    Decodes ``val`` into a C++ ``double *``.

:cpp:`float *val_array_float(value val)`

    Decodes ``val`` into a C++ ``float *``.

:cpp:`value *val_array_value(value val)`

    Decodes ``val`` into a C++ ``value *``.