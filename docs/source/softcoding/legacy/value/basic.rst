.. role:: cpp(code)
   :language: cpp

Basic Types
===========

The basic value types in Haxe are ``Bool``, ``Int``, and ``Float``, which are represented in C++ as ``bool``, ``int``, and ``double`` respectively.
``null`` in both languages also fall in this category, though with slightly different functions.

Encoding
--------

:cpp:`value alloc_null()`

    Creates a null ``value`` object.

:cpp:`value alloc_bool(bool b)`

    Creates a boolean ``value`` object using ``b``.

:cpp:`value alloc_int(int i)`

    Creates an integer ``value`` object using ``i``.

:cpp:`value alloc_int32(int i)`

    Creates a 32-bit integer ``value`` object using ``i``.

:cpp:`value alloc_float(double d)`

    Creates a floating point ``value`` object using ``d``.

Type Checking
-------------

:cpp:`bool val_is_null(value val)`

    Checks if ``val`` is a null object.

:cpp:`bool val_is_bool(value val)`

    Checks if ``val`` is a boolean object.

:cpp:`bool val_is_int(value val)`

    Checks if ``val`` is an integer object.

:cpp:`bool val_is_float(value val)`

    Checks if ``val`` is a floating point object.

:cpp:`bool val_is_number(value val)`

    Checks if ``val`` is a floating point or integer object.

Decoding
--------

:cpp:`bool val_bool(value val)`

    Decodes ``val`` into a C++ ``bool``.

:cpp:`bool val_get_bool(value val)`

    Decodes ``val`` into a C++ ``bool``. Throws an error if ``val`` is not a boolean object.

:cpp:`int val_int(value val)`

    Decodes ``val`` into a C++ ``int``.

:cpp:`int val_get_int(value val)`

    Decodes ``val`` into a C++ ``int``. Throws an error if ``val`` is not an integer object.

:cpp:`double val_float(value val)`

    Decodes ``val`` into a C++ ``double``.

:cpp:`double val_number(value val)`

    Decodes ``val`` into a C++ ``double``.

:cpp:`double val_get_double(value val)`

    Decodes ``val`` into a C++ ``double``. Throws an error if ``val`` is not a floating point object.