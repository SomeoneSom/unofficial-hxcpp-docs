.. role:: cpp(code)
   :language: cpp

Objects
=======

As you would probably expect, you can pass arbitrary Haxe class objects to C++.

Relevant Typedefs
-----------------

:cpp:`field`

    A typedef for ``int``.

:cpp:`__hx_field_iter`

    A typedef for a function that returns ``void`` and takes the arguments ``(value v, field f, void *v)``

Encoding
--------

:cpp:`value alloc_empty_object()`

    Creates an empty ``value`` Haxe object.

Type Checking
-------------

:cpp:`bool val_is_object(value val)`

    Checks if ``val`` is a Haxe object.

Field Getting and Setting
-------------------------

:cpp:`int val_id(const char *str)`

    Converts a name of a field in ``str`` to a usable field ``int``.

:cpp:`value val_field_name(field fld)`

    Converts ``fld`` to the name of that field.

:cpp:`value val_field(value val, int field)`

    Gets the field ``field`` of ``val``.

:cpp:`void alloc_field(value val, int field, value val2)`

    Sets the field ``field`` of ``val`` to ``val2``.

:cpp:`double val_field_numeric(value val, int field)`

    Gets the numeric field ``field`` of ``val``.

:cpp:`void alloc_field_numeric(value val, int field, double num)`

    Sets the numeric field ``field`` of ``val`` to ``num``.

Field Iteration
---------------

:cpp:`void val_iter_fields(value val, __hx_field_iter callback, void *v)`

    Iterates over the fields of ``val`` using the function ``callback``. ``v`` is passed as the third argument to ``callback``.

:cpp:`void val_iter_field_vals(value val, __hx_field_iter callback, void *v)`

    Iterates over the field values of ``val`` using the function ``callback``. ``v`` is passed as the third argument to ``callback``.

Field Calling
-------------

:cpp:`value val_ocall0(value val, int field)`

    Calls field ``field`` of ``val``.

:cpp:`value val_ocall1(value val, int field, value val2)`

    Calls field ``field`` of ``val``  with the argument ``val2``.

:cpp:`value val_ocall2(value val, int field, value val2, value val3)`

    Calls field ``field`` of ``val``  with the arguments ``val2`` and ``val3``.

:cpp:`value val_ocallN(value val, int field, value *vals, int argsN)`

    Calls field ``field`` of ``val`` with the arguments in ``vals``. ``argsN`` should be the number of arguments in ``vals``.