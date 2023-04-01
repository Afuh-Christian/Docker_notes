# 5 Copying Files and Directories  ....   01:46:52   ....

- Now that we have the base image ,,, the next step is to copy the app files into the image ... 

# we have two instructions for this .. 
- <c 'COPY> 
- <c 'ADD>
- They both have thesame syntax ... but add has additional features ... 
- With this command , we can copy one or more files from the current directory into the image ..

# We'll use <the 'COPY>

# Dockerfile 

COPY <filestocopy> <directorytobecopiedinto>
COPY  package.json src /app/

- to copy everything into the dir 

COPY . /app/
or 
WORKDIR /app
COPY . .  

# explain .. 

WORKDIR /<create_workdir_of_image>
COPY <files&folders_in_current_directory>  <current_directory_of_image_created_above>




# IF we are copying files that have spaces .. 

WORKDIR /app 
COPY ["h bro.txt","."] 




# <The 'ADD has two additional featues > 
- We can add a file from <a 'url> 
WORKDIR /app 
ADD https://....   . 
- We can add <a 'compress_file ... Add will auto uncompress the file into the directory > 
WORKDIR /app
ADD file.zip   . 




# Dockerfile 
FROM  node:14.19.3-alpine3.16
WORKDIR /app 
COPY . .


# Now rebuild the image ....

> docker build -t react-app .


# all the files in our current directory are being sent to docker engine ..... 


# Let's start the container with shell so we can check the file system ... 

> docker run -it react-app sh

# Output ..
/app #

- We are inside the /app dir because in the Docker file , we set the current working dir to "/app" 

# Now check the files present in the working dir .. 

> ls -1 
# Output
Dockerfile
README.md
hello.md
package.json
public
src
yarn.lock




