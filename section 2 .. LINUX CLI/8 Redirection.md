# 8 Redirection          ...    00:51:36

- One of the most inportant concept of linux 
    - <standard input and output> 
        <standard input = keyboard> 
        <standard output = screen> 
- <We can always change the 'source of the input or the ouput . This is called redirection .>


# Read the contents of one file and write it ot another file ...

> cat f1a.txt > f2.txt

 (>) = is the redirection from the screen to the file .... 

 - <Verify > 
 > ls -1
 > less f2.txt





# since cat = concatenate ... it can concatenate the content of multiple files ... 

> cat <file1> <file2> 
both file1 and file2 will be displayed on the screen ... 

> cat f1a.txt  f2.txt



# We can write the result of both files to a new file ... using the redirection operator ... 

> cat f1a.txt f2.txt > combined_f1a_f2.txt

<verify>
> cat combined_f1a_f2.txt









# We can use echo ... 
Normally  
> echo hello 
display "hello" on screen ... 

- <Now> 
> echo hello > f2.txt 
will redirect "hello" into a new file called f2.txt 





# get get long listing of a directory .. and print to a file ... 

> ls -l /etc > longlist.txt
























# NB ... 
- > = redirect the standard output 
- < = redirect the standard input 

