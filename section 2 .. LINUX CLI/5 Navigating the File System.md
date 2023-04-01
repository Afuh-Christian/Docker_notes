# 5 Navigating the File System    00:39:53

# NB ... all command are run from ... 
> docker run -it ubuntu 

# preset working direcotory ...

> pwd






# list files and directories 

> ls 

- <for beter layout ... 

> ls -1

- <to see long listing with more detial ... 

> ls -l
<permisionoffile> | <userthatowensdirectory> | <size> | <date>






# To change the working directory ... 
- same as windows ... 

> cd <absolutepath/relativepath>

- <absolutepath = always starts from 'root 'dir> 
> cd /boot  

- <relativepath = files inside the current directory> 
> cd boot

e.g <press 'tap  after this command becuase we have multiple dirs starting with the 'a>
> cd etc/a/
adduser.conf  alternatives/ apt/
# Now ... 

> cd etc/ap/
# ouput ..
<the items with blue colors are 'directories .. while the others are files ..






# To get out of a directory ... 
- one level up
> cd ..
- 2 levels up
> cd ../..


# To view the content of a directory without navigating to that directory ... .e.g __all contents of <d 'bin>
- from root dir .... 

> ls bin 
or  
> ls /bin

# Output ... 
<you see that most of the commands in Linux are programs in the bin dir ....








# Shortcut to got to Home directory ..... for a user ... 
> cd /home 
or .. 
> cd  ~



