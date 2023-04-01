# 10 Finding Files and Directories  ...  00:56:58    ....
# ______________________________________
> docker run -it ubuntu
# ______________________________________



# To see all files in the current directories recursively ...

- this command goes through  every directory and list their files ...

> find

<We can supply a path if we wish to look somewhere else > 

> find /etc

<To see only 'directories>

> find -type d

<To see only 'files>

> find -type f

<To filter by name ... e.g all files whose name starts with f 

> find -type f -name "f*"

<Make the case incensitive

> find -type f -iname "f*"





# to see files an folders 

> ls 

# To see hidden files and directories ..

> ls -a 






# find all the python files ... and set result to a file python-f.txt 


> find / -type f -name "*.py" > python-f.txt