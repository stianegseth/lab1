##Important Instructions

Please preserve the structure of this file, as it will subjected to *partial*
automatic analysis. **Only insert your answers by replacing the text `YOUR ANSWER HERE`; do not delete anything else.** 

Please use [markdown](https://help.github.com/articles/markdown-basics) formating to typeset code and Unix commands with the backtick character, for example, `ls -la`, or if you want to write code blocks, each line should be indented with four spaces, as done in the code below:

    #include <stdio.h>
    
    int main(void) {
    	printf("Hello, world!\n");
    	return 0;
    }


##Exercises from the online Unix tutorial

###Exercise 1a

Make another directory inside the `unixstuff` directory called `backups`

**Answer:** `makedir backups`

###Exercise 1b

Use the commands `cd`, `ls` and `pwd` to explore the file system.

(Remember, if you get lost, type `cd` by itself to return to your home-directory)

**Answer:** *YOUR ANSWER HERE*

###Exercise 2a

Create a backup of your `science.txt` file by copying it to a file called `science.bak`

**Answer:** `cp science.txt science.bak`

###Exercise 2b

Create a directory called `tempstuff` using `mkdir`, then remove it using the `rmdir` command.

**Answer:** `mkdir tempstuff`   `rmdir tempstuff`


###Exercise 3a

Using the above method, create another file called `list2` containing the following fruit: orange, plum, mango, grapefruit. Read the contents of `list2`.

**Answer:** `cat > list2`
	`orange``plum``mango``grapefruit`
	`cat list2`

###Exercise 3b

Using pipes, display all lines of `list1` and `list2` containing the letter 'p', and sort the result.

**Answer:** ` cat list1 list2 | grep -i p | sort`

###Exercise 5a

Try changing access permissions on the file `science.txt` and on the directory `backups`.

Use `ls -l` to check that the permissions have changed.

**Answer:** `chmod o-rw science.txt`
	    `chmod o-rw backups`

##Shell questions

1. What option with the command `rm` is required to remove a directory?
  - **Answer:** `rmdir`
1. What is the command used to display the manual pages for any command?
  - **Answer:** `man`
1. What command will show the first 5 lines of an input file?
  - **Answer:** `head -5`
1. What command can be used to rename a file?
  - **Answer:** `mv`
1. What option can we given to `ls` to show the hidden files?
  - **Answer:** `ls -a`
1. What will the command `cat -n file` do?
  - **Answer:** It gives each line a number, at the start. And prints the text.
1. What will the command `echo -n hello` do?
  - **Answer:** echo is the command to display something on the command line. The -n part stops it from printing.
1. What command will display s list of the users who currently logged in in the system?
  - **Answer:** `who`
1. How do you change password on your account?
  - **Answer:** First you have to SSH onto either Johanna 2 or 10. From there you issue the command `passwd`. The system will prompt you for the old password and your new password.
1. How can you list a file in reverse order?
  - **Answer:** `cat`
1. What does the `less` command do?
  - **Answer:** It prints a file one screen at a time. Press space to go to the next screen in the file.
1. With `less` how do you navigate?
  - **Answer:** space
1. What command will display the running processes of the current user?
  - **Answer:** `ps`
1. What command can be used to find the process(es) consuming the most CPU?
  - **Answer:** `top`

##vi questions
1. How do we save a file in `vi` and continue working?
  - **Answer:** we first go to COMMAND mode. Here we type and return `:w list2`  forinstance, this will save the file as "list2"
1. What command/key is used to start entering text?
  - **Answer:** `i` this enables INSERT mode
1. What are the different modes the editor can be in?
  - **Answer:** INSERT and COMMAND
1. What command can be used to place the cursor at the beginning of line 4?
  - **Answer:** `:4`
1. What will `dd` command do (in command-mode)?
  - **Answer:** It will delete the entire line where the cursor is located.
1. How do you undo the most recent changes?
  - **Answer:** `u`  this is the undo command
1. How do you move back one word?
  - **Answer:** `b`

##The C Language and Make tool Questions

1. How do you use `gcc` to only produce the `.o` file?  What is the difference between generating only the `.o` file, and building the `hello` executable done in the previous compilation above?
  - **Answer:** If we want gcc to only produce an .o file . We add the flag   in the command. The command  ` gcc -o nyaste.o -c ny.c` will yield a new .o file, nyaste.o, from the .c file ny.c  .    A .o file only containes object code, we could think of this as follows. The complete .exe program is when all .o files have been linked, this is the final stage before the program is ready for use. o.file can be code modules that we have made, that togheter make up the final program. Libraries also come in .o files. 
1. Give the command for compiling with `debug` enabled instead of normal compilation for the two examples shown in Listing 2 and Listing 3. Explain how to turn debugging on/off for the two cases.
  - **Answer:** When compiling the code from listing 2 we use the command `gcc eskimo.c -D DEBUG -o eskimo.exe` This command will define the DEBUG macro in the code, this will inturn activate the code defined. If we compiled it whitout the `-D DEBUG` command, the debug code will be disabled.  In listing 3, the debug code is allways going to be part of the end product. The debug code is only activated when the condtions are meet at runtime.

1. Give a brief pros and cons discussion for the two methods to add debug code shown in Listing 2 and Listing 3.
  - **Answer:** The advantage with the approach used in listing 2 is that one can decide wheter to compile the progam with or without the debug code. This will save memory and might also be quicker to compile. In listing 3 the code is allways going to be present. The disatvantage is that one has to remove the code before compilation to deactivate debugging. 
1. Provide the command for generating the *map* file. Which of the `gcc` tools is responsible for producing a *map* file?
  - **Answer:** `gcc hello.c -o hello.exe -Wl,-Map=mymap.txt`  It's the `-Wl,-Map=mymap.txt`
1. What is the content of each of the sections in a *map* file. Explain briefly.
  - **Answer:** *YOUR ANSWER HERE*
1. Rewrite `hello.c` to produce entries in the *map* file for `.data`, `.bss`, and `.rodata`. Hint: This can be done by adding one variable for each type to the file.
  - **Answer:** 
#include <stdio.h>

int main(void)
{
        printf("Hello world!\n");
        int myvall1=1;
        int myvall2=0;
        const int myvall3 =3;




        return 0;
}

1. Add the following function to `hello.c`: `double multiply(double x1, double x2)`, which returns `x1*x2`. Use `gcc` to generate an assembly code listing for the program, and examine the assembly code. What assembly instructions are used to do this? Repeat this task, but now replace `double` with `float`. Explain!
  - **Answer:** The assembly instruction used to multiply 2 float numbers is `mulss` and for double, it is `mulsd.
1. How does `make` know if a file must be recompiled?
  - **Answer:** Make checks is the source files are newer then the previous compiled file.
1. Provide a `make` command to use a file named `mymakefile` instead of the default `makefile`.
  - **Answer:** `make -f mymakefile`
1. How do you implement an *include guard*, and why is it needed?
  - **Answer:** *YOUR ANSWER HERE*

##Library Task

Insert your code between the brackets `{}`:

    void main( int argc, char *argv[] )
	{
    }
    
	double tab_sort_sum( double *tab, int tab_size )
	{
	}


