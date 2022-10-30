Breaking it Down
================

In this section, we will break down the code you copied and pasted in in order to gain an understanding of what it actually does.

The C++ Code
----------------
The first 3 lines of code are just includes and defines, but the first line does need some explaining.

.. code-block:: cpp
    :linenos:

    #define IMPLEMENT_API
    #include <hx/CFFI.h>
    #include <iostream>

``#define IMPLEMENT_API`` must be called in exactly **ONE** of your cpp files **BEFORE** `#include <hx/CFFI.h>`.
This is for reasons that I don't entirely understand and that I don't want to copy and paste.

Now, onto the actual code.

.. code-block:: cpp
    :lineno-start: 5

    extern "C" {

`extern "C"` is required in order to prevent name mangling. This way, the functions are named consistently.

After this are some function declarations.

.. code-block:: cpp
    :lineno-start: 6

        void hello() {
            std::cout << "Hello from C++ Dll!" << std::endl;
        }
                
        value sum(value a, value b) {
            if( !val_is_int(a) || !val_is_int(b) ) return val_null;
            return alloc_int(val_int(a) + val_int(b));
        }

The main odd thing here is the `value` type, and all the other functions associated with it such as `alloc_int` and `val_is_int`.
This will be explained in the next section.

Finally, at the bottom are two lines that start with `DEFINE_PRIM`.

.. code-block:: cpp
    :lineno-start: 8

    DEFINE_PRIM(hello, 0);
    DEFINE_PRIM(sum, 2);

These macro calls "mark" the functions so that they can be loaded in haxe. 
The first argument is the function name, and the second argument is the number of arguments that function takes.

The Haxe Code
-------------
The main thing that needs to be explained here are the lines with `cpp.Lib.Load`.

.. code-block:: haxe
    :lineno-start: 4

        static var hello:Void->Void = cpp.Lib.load("example", "hello", 0);
        static var sum:Int->Int->Int = cpp.Lib.load("example", "sum", 2);

First of all, You may be wondering what types like `Int->Int->Int` mean. These are function types.
In this example code, `Int->Int->Int` means a function that takes two Ints and returns and Int, and `Void->Void` means a function that takes nothing and returns nothing. A function that would, for example, take a String and an Int, and return a Bool would be a `String->Int->Bool`.
As for `cpp.Lib.load` itself, the first argument is the name of the NDLL file (without the file extension),
the second argument is the name of the function you want to load, and the third argument is the number of arguments the loaded function takes.