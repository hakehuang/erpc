erpcgen
-------

# Create and use the eRPC generator
This chapter describes how to create and use the eRPC generator (_erpcgen_), a tool that generates the shim code for a server and client side.

The generated shim code handles marshalling and unmarshalling a request. After unmarshalling, on the server side, the shim code implements a function call to the appropriate function (based on the request). An IDL (interface definition language) is used to tell the generator tool about data types and RPC services.

## How to create an eRPC generator
This section can be skipped, because the _erpcgen_ is distributed within the Multicore SDK as a prebuilt application.
* The _erpcgen_ source files are located in the ``erpc/`` directory.
* On Windows operating system, users can use Visual Studio Express 2013 or higher (steps for using Visual Studio are in the ``erpc/windows/ReadMe.txt`` file).
* To build the _erpcgen_ application on Linux OS or MacOS, the compiler (gcc, g++), make, flex/bison applications, and boost libraries are needed.
* If you are using the Linux OS or MacOS, build the application using the command (which must be executed in the ``erpc/`` directory):
```
make erpcgen
```
or
```
make –f Makefile.erpcgen
```

The output _erpcgen_ applicaton is located in the ``erpc/Debug/<os_type>/erpcgen/`` folder. The ``<os_type>`` is set automatically, based on which build system is used.

## How to use an eRPC generator
When the _erpcgen_ application is available, you can run it from the command line using the appropriate command line options. Prebuilt applications are located in the ``<ksdk_install_dir>/middleware/multicore_<version>/tools/erpcgen/<os_type>/`` folder, where ``<os_type>`` is Windows OS, Linux OS, or MacOS.

## _erpcgen_ command line options
###### ``-?`` or ``—help``
Shows supported commands

###### ``-V`` or ``—version``
Displays tool version

###### ``-o <filePath>`` or ``—output<filePath>``
Sets output directory path prefix

###### ``-v`` or ``—verbose``
* When the verbose option is **not used**, it prints only warnings and errors.
* When the verbose option is **used once**, it prints standard output information.
* When the verbose option is **used twice or more**, it prints debugging information.

###### ``-I <filePath>`` or ``—path <filePath>``
Add search path for imports

The easiest way to use the eRPC generator is:
```
erpcgen <fileName>
```
_For example:_
```
erpcgen MyFirstErpcApp.erpc
```

If the IDL file is placed in different directory than the eRPC generator application, and the requested output directory is also in different directory, then the following example can help you to set all the options and paths correctly in this case:
```
erpcgen –I <filePathToIDL> -o <filePathToErpcOutput> <fileName>
```
_For example_:
```
erpcgen –I MyProject/MyFirstErpcAppIDL –o MyProject/MyFirstErpcAppErpc MyFirstErpcApp.erpc
```
The IDL file can contain annotations data that controls how output files are generated. Also see sections  and .