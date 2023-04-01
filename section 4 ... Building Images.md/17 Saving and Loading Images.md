# 17 Saving and Loading Images   ....    02:29:59

- Let's say we have an image on this machine and you want to put on another machine but without going through docker hub
    - In this case we <can 'save_the_image_as a 'commpressed_file and load it on the other machine ...> 



# NB .... for any of the commands ...  if you wish to  know more about the <add '--help at the end of them ..> 

- To chech the commands available ....

> docker image save --help  

Usage:  docker image save [OPTIONS] IMAGE [IMAGE...]

Save one or more images to a tar archive (streamed to STDOUT by default)

Options:
  -o, --output string   Write to a file, instead of STDOUT



# so ... 

> docker image save -o <thefiletosaveto> <image>
> docker image save -o react-app_compressed.tar react-app:v3

.tar = like a  .zip file on windows

<the compressed file was successfully created ... >




















# We can decompress the file by clicking on it .... 

- To find all the layers and the files in them ... 






# LOADING ... 

- To demonstrate this will remove the react-app:v3 and then load it back from the zip file ..... 
- Remove all the tags pointing to that image .... 


> docker image rm  <imagename/imageID>
> docker image rm react-app:v3 
> docker image rm afuhchristian/react-app:v3

- verify if it's gone 

> docker images 

afuhchristian/react-app   v4        bfba57d727b5   About an hour ago   446MB
react-app                 v4        bfba57d727b5   About an hour ago   446MB
afuhchristian/react-app   v2        3ceeeaf1c709   12 hours ago        446MB
react-app                 latest    3ceeeaf1c709   12 hours ago        446MB
react-app                 v2        3ceeeaf1c709   12 hours ago        446MB
react-app                 v1        341bb72204c2   14 hours ago        446MB
alpine                    latest    b2aa39c304c2   30 hours ago        7.05MB
ubuntu                    latest    58db3edaf2be   2 weeks ago         77.8MB


# All v3 images are gone .... 
# Now load the v3 image from the compressed file .... 


> docker image load --help        ... to see the available commands .. 

> docker image load -i <zipfilecontianingImage> 
> docker image load -i react-app_compressed.tar


# Now verify to see if the image has been loaded ... 

> docker images 

REPOSITORY                TAG       IMAGE ID       CREATED             SIZE
afuhchristian/react-app   v4        bfba57d727b5   About an hour ago   446MB
react-app                 v3        bfba57d727b5   About an hour ago   446MB
react-app                 v4        bfba57d727b5   About an hour ago   446MB
afuhchristian/react-app   v2        3ceeeaf1c709   12 hours ago        446MB

<success> 


















