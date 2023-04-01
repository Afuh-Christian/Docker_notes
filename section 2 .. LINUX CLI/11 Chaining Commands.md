# 11 Chaining Commands  01:00:21

- We have was to combine 2 or more commands ... 

# we use the <a ';> to join multiple commands together ...

- create a folder
- go into folder 
- create a file in folder and write "done" to it 

> mkdir test ; cd test ; echo done > f1.txt



# NB ... if the commands are too long and you want to see all of them in an organise manner when typing them .... 

# _________________________________01:04:56

- type 1st command , ; , \ (backslash) , press enter 
> mkdir hello;\ + enter 
> cd hello;\ + enter 
> echo hello; + enter 

- you leave out the "\" on your last command ....

# _________________________________









# To make constrains .use <a '&&>.... If a command at the top fails the next should not get executed 

> mkdir test && cd test && echo done && f1.txt















# To make another command to get executed if one fails ..  

> mkdir test ||  echo test done 

- if 1st command get's executed ... the 2nd will not be ..
- if 1st fails ... 2nd will get executed 














# Aother way to chain commands .... PIPING ..... 

# PIPING __________________________________________________________________________________________________________________________________________

- <p '|'> 

- <first command> | <input from firt command , apply second command>

> ls /bin | less

- 1st command returns the list of files in bin 
- the second command makes you to <p 'scroll up and down to see these files and folders>

- Examples 

> ls /bin | head 
> ls /bin | head -n 5 
etc






















