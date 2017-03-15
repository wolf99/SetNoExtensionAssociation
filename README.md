# Setting the Default Editor for Files With No Extension in Windows 10

On Windows some files do not have extensions, particularly those often used with 
UNIX-like operations. 

For example, files used with `make` should, by default have a filename of 
`Makefile`, `makefile`, or possibly `GNUmakefile`. None of these have an 
extension. While it is possible to tell `make` to use a non-default file name 
by using the command `make -f name.ext` doing this everytime is annoying. Equally 
annoying is having to select the editor to use every time you attempt to open 
the makefile for editing outside of a terminal.

To avoid this you can assign a file association for files with no extension.

**NB:** Be aware that this will change the association for *ALL* files without 
extensions even if they are not a type of file that should be opened with the 
program you choose to associate. If opening these types of files you can still 
right-click and select "Open with..." to select a different program.

In the following example we set the default editor for all extensionless files
to Notepad++ which has already been installed on the Windows system.

#### Find the file type token to use
For Notepad++, in a cmd prompt type: 
~~~ sh
> ftype | find /i "notepad"
~~~
From the resulting list find the token that has a command string for the 
Notepad++ executable (e.g. `Notepad++_file`).

#### Set the association to the file type
Assign the file type token found in the previous step to the type with no 
extension (just a dot "."). In an adminstrative cmd prompt type:
~~~ sh
> assoc .=Notepad++_file
~~~

### Check the current association
To check the currently set association, in cmd prompt type: 
~~~ sh
> assoc | find /i ".="
~~~

### Reset the association
To reset the association to the default (i.e. no association), in an 
adminstrative cmd prompt type: 
~~~ sh
> assoc .=
~~~
