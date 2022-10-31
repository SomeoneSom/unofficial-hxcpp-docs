.. role:: cpp(code)
   :language: cpp

Strings
=======

The Haxe type ``String`` can be represented in C++ as ``char *``, ``wchar_t *``, ``const char *``, or ``comst wchar_t *``.
All of these represent the basic idea of a string of characters.

Encoding
--------

:cpp:`value alloc_string(const char *str)`

    Creates a string ``value`` object using ``str``.

:cpp:`value alloc_wstring(const wchar_t *str)`

    Creates a string ``value`` object using ``str``.

:cpp:`value alloc_string_len(const char *str, int len)`

    Creates a string ``value`` object using ``len`` characters of ``str``.

:cpp:`value alloc_wstring_len(const wchar_t *str, int len)`

    Creates a string ``value`` object using ``len`` characters of ``str``.

Type Checking
-------------

:cpp:`bool val_is_string(value val)`

    Checks if ``val`` is a string object.

Decoding
--------

:cpp:`const char *val_string(value val)`

    Decodes ``val`` into a C++ ``const char *``.

:cpp:`const char *val_get_string(value val)`

    Decodes ``val`` into a C++ ``const char *``. Throws an error if ``val`` is not a string object.

:cpp:`const wchar_t *val_wstring(value val)`

    Decodes ``val`` into a C++ ``const wchar_t *``.

:cpp:`char *val_dup_string(value val)`

    Decodes ``val`` into a C++ ``char *``.

:cpp:`wchar_t *val__dup_wstring(value val)`

    Decodes ``val`` into a C++ ``wchar_t *``.