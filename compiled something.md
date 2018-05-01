Getting the source from http://patches.freeiz.com/alpine/
#wget http://patches.freeiz.com/alpine/release/src/alpine-2.20.tar.xz

needs to be extracted,  You can use the same command for archives that end in .tar.gz and .tar.bz2:
#tar xfv alpine-2.20.tar.xz

when done extracted you will see files on the screen. When it done cd to alpine-2.20 to switch into it.
check to see if there a file call "configure".
Go and check out the README files for required to build the source code,executable files that will be produced.
we downloading the source and reading the documentation.
Now move that file into your alpine-2.20/ directory.
#zless fancy.patch.gz

Lines starting with “***” show which source code files are to be modified
 the “+” and “!” characters at the start of a line show lines that should be added or changed respectively
see something like this:
   char *debug_str = NULL;
   char *sort = NULL;
+  char *threadsort = NULL;

 apply a patch, you need the (surprise!) “patch” command. You can test the effects of the patch without actually changing the code 
using the “–dry-run” option like so:
#zcat fancy.patch.gz | patch -p1 --dry-run
“zcat” extracts the patch into plain text, and then it’s piped with the “|” 
“-p1″ here because we’re already inside the source code directory
if you’re outside it or the patch doesn’t work, try removing it. 
Once you execute this command, you’ll see lines like:

patching file alpine/setup.c
If it all works, re-run the command omitting the “–dry-run” option, and the changes will be made permanent.

configuration
#./configure --help | less

Scroll down and you’ll see that there’s a huge list of options you can change
scroll down to the “Optional Features” section
section you’ll find features specific to Alpine
you can run the configure script on its own
#./configure
if you dont have GCC installed, you’ll see an error message saying that you don’t have a compiler.
on Ubuntu
#sudo apt-get install build-essential

Once the configure script has run without any problems
 enter the command
#make
Once the compilation is complete, you’ll need to copy the files into your filesystem
on Ubuntu
#sudo make install
