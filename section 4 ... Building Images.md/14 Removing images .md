# 14 Removing images      02:17:21    

- check list of images ... 

> docker images

REPOSITORY     TAG       IMAGE ID       CREATED             SIZE
react-app      latest    d06a44bf0999   About an hour ago   446MB
<none>         <none>    341bb72204c2   About an hour ago   446MB
<none>         <none>    d088df47a6db   About an hour ago   446MB
<none>         <none>    d014caf3865f   2 hours ago         446MB
<none>         <none>    ee567e1e0e60   3 hours ago         446MB
<none>         <none>    b522a50beec1   4 hours ago         446MB
<none>         <none>    baaad14ecd50   5 hours ago         446MB
<none>         <none>    6a6574af9b6e   10 hours ago        445MB
<none>         <none>    5eec74722f53   10 hours ago        120MB
<none>         <none>    c54dad845bc8   11 hours ago        120MB
alpine         latest    b2aa39c304c2   17 hours ago        7.05MB
hello-docker   latest    5dba029975f2   6 days ago          176MB
<none>         <none>    047756bd07e0   8 days ago          176MB
ubuntu         latest    58db3edaf2be   2 weeks ago         77.8MB
<none>         <none>    72436c3602b4   8 months ago        119MB




- <We have a bunch of images with no name and no tag ... these are 'dangling_images or 'loose_images >
- These are layers that have no relationship  with the <tagimage> 
- This happens as we were rebuilding our image , docker was creating these layers and at some point these layers lossed there relationship , with the react-app image 
- As you work with docker ... you will always see dangling images poping op 

- <To remove all dangling images .... use th 'prune command 

> docker image prune 


- Nothing is deleted because we have <a container running an older react-app image .>


> docker ps
- no container is running .

- these containers are probably in the stop state ... 

> docker ps -a 


- To get rid of those extra containers .. 

> docker container prune
- take  yes

# Now run 

> docker image prune


# If you check the list of images ... you only see the proper images ... 

> docker images 

REPOSITORY     TAG       IMAGE ID       CREATED             SIZE
react-app      latest    d06a44bf0999   About an hour ago   446MB
alpine         latest    b2aa39c304c2   17 hours ago        7.05MB
hello-docker   latest    5dba029975f2   6 days ago          176MB
ubuntu         latest    58db3edaf2be   2 weeks ago         77.8MB




# To remove one of these images.... 

- see the list of commands available ...

> docker image 

> docker image rm <imagename/imageID>
> docker image rm hello-docker



# verify if it's gone .. 

> docker images 



































# NB ..... 

> docker image build react-app .
or ....
> docker build -t react-app .