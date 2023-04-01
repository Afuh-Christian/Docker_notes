# 12 Environment Variables   ..   01:05:27       ..


- <We have environment variables that we can set for storing 'configuration 'settings for our application 
- <So our applications can read config settings from these 'environment 'variables> 


# A few commands for viewing environment variables and setting them ...... 



# _____to see all environment variables in this machine ... 

> printenv

<p 'HOSTNAME = 8a3af281321e  .... this is the ID of our machine

<p  'PATH = /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
_=/usr/bin/printenv
    - the paths in which when you run a program or a command ... it searches the command in this list of paths
    - the paths are separted by ':  

# _________see a value of an env virable  .... case sensitive ...

# method 1 __

> printenv <VARIABLENAME>

e.g for path ...

> printenv PATH  

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

# method 2 __ <p '$>

> echo $<VARIABLENAME>

E.G for hostname 

> echo $HOSTNAME

8a3af281321e





# How to set a variable _______________________________ <p 'export> ..... NB ... no spaces   e.g DB_USER=christian
- define a variable called DB_USER and set to christian 

> export DB_USER=christian

<This 'new 'variable is stored in the current 'terminal 'session ie .. if we close the terminal and open a new terminal session , the variable not exist>









# terminate this session 

> exit 

- Now we are outside of the container environment ..... and back on the windows terminal .... 




# Check the containers that are running ... or docker process ...

> docker ps

# check the stop containers .. 

> docker ps -a 

8a3af281321e   ubuntu         "/bin/bash"              7 hours ago   Exited (0) 14 seconds ago             sleepy_moser
ca6ba83e23fa   ubuntu         "/bin/bash"              8 hours ago   Exited (0) 8 hours ago                eager_meitner
d28b852baf66   hello-docker   "docker-entrypoint.s…"   3 days ago    Exited (0) 3 days ago                 epic_goodall
70070b4ec85e   047756bd07e0   "docker-entrypoint.s…"   3 days ago    Exited (0) 3 days ago                 charming_chatterjee


# 8a3af281321e is the contianer we have been working with ..

# just like vertial machines we can  <a 'start or 'stop a container > 

# <To 'start a container> 

> docker start  -i <containerID> 
e.g ... 
> docker start -i 8a3af281321e

-i = so we can interact with it ... 



# ouput .... 
root@8a3af281321e:/#    

we are base with the machine ..... 

# Now let's see if the user we created in the last session will exist in this new session .. 

> echo $DB_USER 

# Output ... 
Nothing ..... 

















# To create a new variable and make it persistent(<It does not get deleted when we create a new session > ) 
- we have to write it through a special file ... 

# __________________________________________

# step 1 .. 
- enter home dir ... 

> cd ~ 

# step 2 ..

- <check all fils > 
> ls -a 

- <the '.bashrc file is a user's personal 'starter-file .
- <everytime a user loggs in , linux loads  the '.bashrc commnad from the user's home dir>
- We can edit this file using nano 

> nano .bashrc 
or <using redirection>
> echo DB_USER=christian >> .bashrc 

# __________________________________________


# NB ... never store sensitive data in environment variable .. because these variables are just plain text files .... 

# NB ... the variables we create and store in the .bashrc will be added in the next session to the environment varaible ...
if you create a variable and store in the .bashrc in the current sesion .. you won't find it in the env variables in this session ... 

# we can reload the .bashrc file so it sets the variables emidiatle .. 

> source .bashrc 

# now try to check the env variable you just created ... 

















# NB ... all the above should be done in the home directory ...