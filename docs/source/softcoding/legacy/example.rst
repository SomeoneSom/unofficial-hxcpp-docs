A Basic Example
===============

To ease you into writing these special DLLs required for CFFI, let's write a basic example project.

Project Setup
-------------

If you dont already have CMake installed, you can download it `here <https://cmake.org>`_.

Make a new folder for this example project. Then, add folders so that this is the folder structure:
  * **dlls**: This will house any and all DLLs that your C++ code needs.
  * **cpp**: This will house all your C++ code.
  * **include**: This will house all the hxcpp header files.
  * **src**: This will house all your Haxe code.

To begin, place all the DLLs from `this Google Drive zip <https://drive.google.com/file/d/1eY1j2peNM0JXXk5_Dbd2mgLvyC--gjRg/view?usp=sharing>`_ into the **dlls** folder. These are the required DLLs from the VC++ Redist so that your code will work for end users.
Additionally, go to your hxcpp folder (``haxelib path hxcpp``), then go to the folder named include. Copy all these files to your **include** folder.

The C++ Code
------------

Now, go to your **cpp** folder and create a file named example.cpp, and copy and paste this code in.

.. code-block:: cpp
    :linenos:

    #define IMPLEMENT_API
    #include <hx/CFFI.h>
    #include <iostream>
    
    extern "C" {
        void hello() {
            std::cout << "Hello from C++ Dll!" << std::endl;
        }
            
        value sum(value a, value b) {
            if( !val_is_int(a) || !val_is_int(b) ) return val_null;
            return alloc_int(val_int(a) + val_int(b));
        }
    }
    DEFINE_PRIM(hello, 0);
    DEFINE_PRIM(sum, 2);

All of what this code means will be explained in the next section.

The Haxe Code
-------------

For the Haxe code, go into the **src** folder and make a file named Main.hx, and paste this code into it (this will be explained in the next part):

.. code-block:: haxe
    :linenos:

    package;

    class Main {
        static var hello:Void->Void = cpp.Lib.load("example", "hello", 0);
        static var sum:Int->Int->Int = cpp.Lib.load("example", "sum", 2);

        static function main() {
            hello();
            trace("3 + 4 = " + Std.string(sum(3, 4)));
        }
    }

The stand-out code from this will additionally be explained in the next section.

Since we are using CMake for this example, we also need to put a CMakeLists.txt file in the root directory of your project. Make that file, and paste this code in:

.. code-block:: cmake

    cmake_minimum_required(VERSION 3.20)
    project(example)
    set(CXX_STANDARD 17)
    include_directories(include include/hx include/cpp)
    file(GLOB src "cpp/*.cpp")
    add_library(example SHARED ${src})
    install(TARGETS example RUNTIME DESTINATION ${CMAKE_SOURCE_DIR})

Replace 3.20 with the version of CMake you have, and replace 17 if you are using a feature from a newer C++ standard.

Compililng
----------
First run ``cmake .``, and then ``cmake --build . --target install`` in order to build your dll file.
Then, run ``haxe -cp src -main Main -cpp bin -D HXCPP_M64`` in order to build the haxe code. 

Finally, take your DLL, change the file extension to ``.ndll``, and copy it to the ``bin`` folder, along with all the DLLs in your **dlls** folder.


When you run the compiled program, it should print out ``Hello from C++ Dll!`` and ``3 + 4 = 7``.