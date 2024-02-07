open() #remember-for-later

- Needs filename (and fully qualified path)
- Mode:
    
    - "x" - create - errors out if file **exists**
    - "r" - read (default) - errors out if file **doesn't exist**
    - "a" - append - adds > creates file if doesn't exist
    - "w" - write - overwrites > creates file if doesn't exist
- You can also specify binary with "b" or text with "t" (text is default)

  

myfile = open("mydoc.txt", "rt") - will open mydoc.txt in pycharm directory

  

myfile = open(r"c:\temp\mydoc.txt") - the 'r' will make the path work (raw string rather than python auto translation of : and \)

myfile = open("c:\\temp\mydoc.txt") - this should also work

  

.read() - reads the whole file

.read(5) - reads first 5 characters

.readline() - reads line by line