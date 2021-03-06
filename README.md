## Flock of Birds Library

### Installation

To install/build the library, first determine if you must
boostrap the project.  If the 'configure' script does not
exist, run:

    ./bootstrap

You should only have to run 'bootstrap' once.

Installing the library should be as easy as:

    ./configure
    make install

You'll probably also want to build the test programs to make sure
everything is working:

    cd test
    make

This will generate two test programs: "fly" and "fly2".  "fly" simply
outputs received data from the flock to stderr.  "fly2" is an OpenGL
based program which shows you the bird's location/orientation.  Of the
two programs, you should definitely give "fly2" to a try.

Part of the fun of getting your flock to work with the library is
figuring out how long the library should wait between sending 
commands to the flock hardware.  By default the library waits 500ms
between commands.  This is very conservative and a bit slow.  A good
way to find the best wait time for your particular setup is to use
the test program "fly2":

    ./fly2 -s 250 /dev/ttyS0

The above command tells the library to wait 250ms between sending 
commands to the flock hardware.  To find the optimal wait time, keep 
decreasing the wait time until the the library is unable to initialize
the birds.  Once you've found a bad value, simply use the previous good
value.

It's important to note that this "command wait time" only affects
the amount of time it takes to start up the flock.  It does not affect
the operation of the flock once the "fly( )" has been called.

###CMAKE Installation

To install/build the library, you can use the cmake as usual as other projects.
If it's prepared to detect MSVC or others because libfob works differently 
between windows and linux.

For MSVC configuration, libfob uses w- prefix to indicate the file selected.
In the fob library, windows uses wfob.h/.cpp and e.g linux uses fob.h/cpp

Windows' requeriments:

	PTHREAD
	GLM
	

To config the examples you have use the variable:

	-DINCLUDE_EXAMPLE

Windows' example is the "wtest". The requeriments are:

	GLEW
	GLUT
	FREEIMAGE
	

Other system use the example "test". The requeriments are:

	GLEW
	OPENGL

Windows example (wtest) are tested and running, the other is not tested.
 

### Documentation

Wiki docs can be found at https://github.com/cournia/fob/wiki.

API documentation can be generated via Doxygen:

    make docs

This should create a directory named "api" in which you'll find both
html and tex based documentation.


### Feedback

Please send any comments, suggestions, code submissions to the
Nathan Cournia <nathan@cournia.com>.

CMake and Windows version:
Aaron Sujar <aaronsujar@gmail.com>
