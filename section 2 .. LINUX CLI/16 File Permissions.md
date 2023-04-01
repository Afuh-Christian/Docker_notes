# 16 File Permissions      01:26:15        .... 


- logged in as root ... 
> cd ~ 
> cd /home

- <create a file called 'deploy.sh ... files with the 'sh extension are called 'shellscript ... in these files we can write 'linux_commands >  
- So we can write all our commands and create a deployment script ... 

> echo echo hello > deploy.sh 

- verify 

> cat deploy.sh

# Now when <we 'execute the 'deploy.sh file , we will see "hello" on the terminal .... >

- <view the long  listing to see the permisions of these files ... >

> ls -l 
-rw-r--r-- 1 root root   11 Feb 10 12:58 deploy.sh
drwxr-x--- 2 john john 4096 Feb  9 20:33 john


- drwxr-x--- 2 and  -rw-r--r-- 1 are <permisions>
- <p drwxr-x--- 2 = starts with 'd' means it's a directory>



# Permisions     <Are 'read , 'write , 'execute>
- drwxr-x--- 2 
    - <The 1st character = whethere it's a directory or a file>
        - <for 'd = directory> 
        - <for '- = file> 
    - rwxr-x--- 2 = these 9 characters left are divided <into '3-groups> 
        - <The '1st-group = rwx = 'read, 'write , 'execute    
        - <The '2nd-group = r-x = 'read, '---- , 'execute    
        - <The '3rd-group = --- = 'read, '---- , 'execute     
    - <The '1st-group = holds permisions for the 'user that owns the file >
    - <The '2nd-group = holds permisions for the 'group that owns the file >
        - by default , every user that is created is auto placed in a group with thesame name ....
    - <The '3rd-group = holds permisions for 'everyone-else >
    


# To execute the file ... 
./ = current dir 

> ./deploy.sh 

bash: ./deploy.sh: Permission denied


# We can use the change mode command <to change the 'permisions for the user that owns the file or the group or others ..>

- <for User>
> chmod u
- <for group>
> chmod g
- <for others>
> chmod 0

- Lets add the <execute permission > for the user .... 

> chmod u+x deploy.sh
 

- <Now try executing the file ..> 

> ./deploy.sh

- <check the long listinh .... the color of the file is now green because it's now executable by the user who created it > 

# ______________________________________
- <To remove the persmion> 

> chmod u-x deploy.sh
# ______________________________________






















# Giving permision to other users ..... 
- go to a new terminal and logg in as john 

> docker exec -it -u john <containerID> bash 

john@0850b8c7aa34:/home$

> cd /home

- if we john tries to execute deploy.sh , he will be denied ...


# so we go back to the other terminal where the person who created this file  is and allow permissons for others to execute this file ... 

root@0850b8c7aa34:/home# 

> chmod o+x  deploy.sh



# Now we can go back to john's terminal an execute the ./deploy.sh file  ...

john@0850b8c7aa34:/home$

> ./deploy.sh





























# VARIATIONS OF THE CHANGE MODE COMMAND .. 
<we can also 'combine_groups >

- Others and group that owns the file  =   og 
- add execute and write permissions 
- remove the read permission.

> chmod og+x+w-r  *.sh

<We can also type multiple filenames or use patterns>







