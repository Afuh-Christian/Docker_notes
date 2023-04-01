#    3 Managing Packages    00:34:21 

- ubuntu has a package manager called <d 'apt .. advanced package tool>

# NB all  command now ......  are run from ... 

> docker run -it ubuntu

# root@8a3af281321e:/# >

# ...older version . 
> apt-get 

# new version ... 
> apt 
# output ... all commands posible with apt .... 


# Let's install <d 'NANO = a basic text editor for linux>

> nano 
bash: nano: command not found

- nano is not installed ... 

> apt install nano
# OUput ... 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Package nano is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'nano' has no installation candidate 
<d 'Error = because in linux , we have a package database , these database might contain hundreds of packages but not all these packages are installed >

# To see all the Packages in the linux database ... 

> apt list

<Some of the packages are installed ... '[installed,local]>


# when we run <apt install nano> .. it checkes the database ... if nano is not found ... it returns an error .. 

# We need to  update the package database .

> apt update

# when you check the packages .. you see that  most of the new packages have not been installed ... 

> apt list  

# Now install nano 

> apt install  nano

<d 'success> 

# to  check if nano is installed ... 

> nano 

<A new window opens ... which is the text editor for linux ..>






# To remove a package ... 

> apt remove <packagename>










# summary ... 

- before installing a package ... run  <d apt update> to update package database ... then install 

> apt update 
> apt install <packagename> 









































# to open linux  text editor ... 

> docker run -it ubuntu 
> nano

