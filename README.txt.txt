CMPSC 473 - Project 4

Group Members: Gabe Harms
	John Guda
	Luke Uliana
-----------------------------------------

This was assignment was a group project that we were assigned in our 
Operating Systems class. The goal of this program is to simulate a 
file system with an interface identical to the linux command line.
All commands such as mkdir, mvdir, cd, and others work just as if 
you were navigating a file system on a command line.

The file system is simulated by allocating a large fixed block of 
memory to the program. The program then sets up the file descriptor
and root directory at the beginning of this memory. All created 
directories and files are added contiguously to this memory. 

We chose to simulate a disk partition with the use of malloc on a char
array. We chose a size of 40,000,000 bytes (about 40MB), and we split
this up into blocks of size 5,000. The file system descriptor is at
the beginning of the memory (char array), and it takes up 2 blocks.
Directories each take up 1 block, and files take up 1 block for the
descriptors, and as many extra blocks as they need for data.

We implemented files, directories, and the file system descriptor with
structs the contain all the information needed for each type. For
example, directories contain: name, top level, subitems[], subitem 
types, and subitem count.

Whenever files or directories were created, removed, or edited, we
had to make sure to apply the relevent changes to all of the
directories and descriptors that would be affected.

In order to improve our debugging, we have many print statements that
are used only if in debug mode. We also included a print_descriptor
function that could be used any time to display the content of the 
descriptor block and free block table.

For more information about the implemented functions, we included many
comments in our code to help understand how each works.

