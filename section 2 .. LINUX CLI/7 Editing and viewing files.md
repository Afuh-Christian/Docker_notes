# 7 Editing and viewing files  00:47:40         .....   

# _________________________________________________________-
> docker run -it ubuntu
# _________________________________________________________-


- How we can edit files ... 
- we will use <d 'nano> 
- install nano 
> apt install  nano  


# ............... now to edit a file .. 

> nano <filename> 
- do the changes 
- exit and save the changes .... 

e.g 

> nano fa1.txt 

<the above command creates a file and also make changes to that file ... .> 


 


# To see the contents of a file .... _________________________
# for a file with small content ..
> cat <filename> 
e.g 
> cat fa1.txt
e.g 
> cat /etc/adduser.conf

# for a file with large content ... <can only 'scroll down>
> more <filename>
e.g 
> more /etc/adduser.conf
<press 'space to go to the next page ...> 
<d 'problem with more = you can only scroll down ...>

# for a file content and  <can 'scroll down and up> through
> apt install less 

> less <filename> 
e.g 
> less /etc/adduser.conf


# to exit ..

> q 






# To show the first 5 lines  of a file .... 

> head -n 5 <filename> 
e.g 
> head -n 5 /etc/adduser.conf

# To show the last 4 lines of a file .... 

> tail -n 4 <filename> 
e.g 
> tail -n 4 /etc/adduser.conf