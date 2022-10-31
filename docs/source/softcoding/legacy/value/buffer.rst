.. role:: cpp(code)
   :language: cpp

Buffers
=======

Buffers, equivalent to ``haxe.io.BytesData`` in Haxe, are used for working with strings.
They have no type equivalent in C++.

Relevant Typedefs and Structs
-----------------------------

:cpp:`buffer`

    A typedef for a pointer to the struct ``_buffer``.

:cpp:`cffiByteBuffer`

    A typedef for ``buffer``. Functions with this only work if ``val_is_buffer`` returns true.

:cpp:`CffiBytes`

    A struct with the members of :cpp:`unsigned char *data` and :cpp:`int length`.

Encoding
--------

:cpp:`buffer alloc_buffer(const char *str)`

    Creates a ``buffer`` object using ``str``.

:cpp:`buffer alloc_buffer_len(int len)`

    Creates an empty ``buffer`` object of length ``len``.

:cpp:`cffiByteBuffer val_to_buffer(value val)`

    Creates a ``cffiByteBuffer`` object using ``val``.

:cpp:`CffiBytes getByteData(value val)`

    Creates a ``CffiBytes`` object using ``val``.

Type Checking
-------------

:cpp:`bool val_is_buffer(value val)`

    Checks if ``val`` is a buffer object. Will never return true on a neko host.

Buffer Access
-------------

:cpp:`void val_buffer(buffer buf, value val)`

    Appends ``val`` to ``buf``.

:cpp:`void buffer_append(buffer buf, const char *str)`

    Appends ``str`` to ``buf``.

:cpp:`void buffer_append_sub(buffer buf, const char *str, int len)`

    Appends ``len`` bytes of ``str`` to ``buf``.

:cpp:`void buffer_append_char(buffer buf, int chr)`

    Appends ``chr`` as a ``char`` to ``buf``.

:cpp:`int buffer_size(cffiByteBuffer buf)`

    Gets the size of ``buf``.

:cpp:`void buffer_set_size(cffiByteBuffer buf, int size)`

    Sets the size of ``buf`` to ``size``. Invalidates the data in ``buf`` (TEST TO SEE IF TRUE).

Decoding
--------

:cpp:`value buffer_to_string(buffer buf)`

    Converts ``buf`` into a string ``value`` object.

:cpp:`value buffer_val(cffiByteBuffer buf)`

    Converts ``buf`` into a string ``value`` object.

:cpp:`char *buffer_data(cffiByteBuffer buf)`

    Converts ``buf`` into a ``char *`` object. This pointer is invalidated if ``buf`` is ever resized.