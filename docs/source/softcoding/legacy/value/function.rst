.. role:: cpp(code)
   :language: cpp

Functions
=========

It's possible to pass Haxe functions to C++, and call them within that C++.

Type Checking
-------------

:cpp:`bool val_is_function(value val)`

    Checks if ``val`` is a function object.

Function Access
---------------

:cpp:`int val_fun_nargs(value val)`

    Gets the number of arguments that ``val`` takes.

Function Calling
----------------

:cpp:`value val_call0(value val)`

    Calls ``val``.

:cpp:`value val_call0_traceexcept(value val)`

    Calls ``val``. Catches and prints any exceptions encountered.

:cpp:`value val_call1(value val, value val2)`

    Calls ``val`` with the argument ``val2``.

:cpp:`value val_call2(value val, value val2, value val3)`

    Calls ``val`` with the arguments ``val2`` and ``val3``.

:cpp:`value val_call3(value val, value val2, value val3, value val4)`

    Calls ``val`` with the arguments ``val2``, ``val3``, and ``val4``.

:cpp:`value val_callN(value val, value *vals, int argsN)`

    Calls ``val`` with the arguments in ``vals``. ``argsN`` should be the number of arguments in ``vals``.