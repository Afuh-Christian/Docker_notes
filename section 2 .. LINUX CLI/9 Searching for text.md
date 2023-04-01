# 9 Searching for text  ....  00:54:39  .....
# ______________________________________
> docker run -it ubuntu
# ______________________________________


# How to search for a string in a file .... 

> grep hello file1.txt 
or
- <To make the search case incensitive>
> grep -i hello file1.txt  


grep = global regular expression print

- <You can search in multiple files ... > 

> grep -i <texttosearch> <file1> <file3> <file3>

- <patern = all text starting with file> 

> grep -i  <texttosearch> <file>*



# To search a text in a directory .... 

> grep -i <texttosearch>  <pathtofile>

- <To search all files and folders ..> 

> grep -i -r <texttosearch> .
e.g 
> grep -i -r hello .

-r = search the current directory and all it's subdirectories .










# NB .... In linux we can combine two different option ... 
> grep -i -r hello .
or 
> grep -ir hello .

