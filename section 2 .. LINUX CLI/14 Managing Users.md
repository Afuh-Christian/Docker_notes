# 14 Managing Users       01:15:57           ... 

# How to create a new user and logg in as that user .... 

# - create new user .. with home ....
> useradd -m <username> 

- this user in stored in the config file in the <etc dir> 
- <To see user account info>
> cat /etc/passwd

john:x:1000:1000::/home/john:/bin/sh

- x = password is stored somewhere else
- 1st 1000 = userID 
- 2nd 1000 = groupID
- :/home/john = home dir of user 
- /bin/sh  = the shell program used when this user loggs in (the old original shell program)
    - we also have bash which is the enhanced version of this program














#  modify user 
> usermod 

- <setting the shell for the user ...'-s>
let's change the shell to bash .... 
> usermod -s /bin/bash john 

 

# view the userinfo ..
> cat /etc/passwd

john:x:1000:1000::/home/john:/bin/bash


<b 'success> 








# Where the passwords are stored in  an encrypted format ..

> cat /etc/shadow

- this file can only be accessed by the root user ....


















# How to logging as christian ________________________
- open a new terminal ...
- the container should still be running on the other terminal 

- check to see if container is running 
> docker ps

- Now we will execute <a 'bash session inside the running container > 

> docker exec <containerID> bash 
- this command does nothing because we didn't interact with bash ... 

> docker exec -it <containerID> bash

root@0850b8c7aa34:/#

# Now we have two bash session ... one on a terminal and onther on the other terminal

# But we want <to loggin  as 'john not as 'root> __________

> exit 

> docker exec -it -u john <containerID> bash

john@0850b8c7aa34:/$

-u = which user 














- delete user 
> userdel <username>

e.g 

> userdel john















# NB ... thers <s 'adduser and 'useradd> ....01:21:51
- <s 'useradd = is the original api that was built >

- <s 'adduser = is a pro-script that is more interactive and uses 'useradd under the hood> 
    - create a user with this ... auto creates <a 'group with thesame name>
    - <home dir created >
    - <your promt to set password> 