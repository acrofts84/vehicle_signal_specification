Attached is a patch with my attempt to generate a native tree from the vspec files. 
The following will create the native tree in the file vss_rel_1.0.cnative. 

In the c_native directory, build the library cnativenodelib.so.
$ gcc -shared -o cnativenodelib.so -fPIC cnativenodelib.c

In the tools directory, run the c-native tool. Input is the root vspec file, and an unused dummy file.
$ Python vspec2cnative.py ../spec/VehicleSignalSpecification.vspec dummyfile

The created file (vss_rel_1.0.cnative) can then be tried out using the testparser, after building it.

cc vsstestparser.c vssparserutilities.c -o vsstestparser

In the tesparser you can traverse the tree from the keyboard keys r/l/u/d as shown in the simple UI. 
You can also search the tree by first enter the key g, and a path (E.g. Root.Signal.Cabin.Door.*.*.IsOpen)
The UI will then display the path to all nodes found matching search path. 
