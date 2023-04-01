# 15 Tagging Images     ....    02:20:08   ...

- When ever we pull an image or create one , by defualt docker <users the 'latest tag>  .....
- <this 'latest tag is just a lable>
- <We should always 'set_our_own_tags so we can know the version of our image ..... like in git .... >



# How to tag you images properly ..... 

# METHOD 1 ____________

> docker build -t <imagename>:<tagname>  . 

> docker build -t react-app:v0 . 

- <verify> 

> docker images 

REPOSITORY   TAG       IMAGE ID       CREATED        SIZE
react-app    latest    341bb72204c2   2 hours ago    446MB
react-app    v0        341bb72204c2   2 hours ago    446MB
alpine       latest    b2aa39c304c2   17 hours ago   7.05MB
ubuntu       latest    58db3edaf2be   2 weeks ago    77.8MB

# to remove the taged image ... 

> docker image rm react-app:v0

- And now we still have the react-app with tag  latest  ___ 

# METHOD 2 ______________

- here we tag the existing image with tag latest ... 

> docker image tag react-app:latest react-app:v1

# verify 

> docker images 

REPOSITORY   TAG       IMAGE ID       CREATED        SIZE
react-app    latest    341bb72204c2   2 hours ago    446MB
react-app    v1        341bb72204c2   2 hours ago    446MB
alpine       latest    b2aa39c304c2   17 hours ago   7.05MB
ubuntu       latest    58db3edaf2be   2 weeks ago    77.8MB





REPOSITORY   TAG       IMAGE ID       CREATED          SIZE
react-app    v2        3ceeeaf1c709   10 seconds ago   446MB
react-app    latest    341bb72204c2   2 hours ago      446MB
react-app    v1        341bb72204c2   2 hours ago      446MB
alpine       latest    b2aa39c304c2   17 hours ago     7.05MB
ubuntu       latest    58db3edaf2be   2 weeks ago      77.8MB

<Latest tag pointing to v1 instead of v2>


# NB ... The latest tag does not necessarily reference the latest image  , 
 - You have to explicitly apply it to the latest image 

 > docker image tag <latestimage> <latesttag>
 > docker image tag  react-app:v2 react-app:latest


 REPOSITORY   TAG       IMAGE ID       CREATED              SIZE
react-app    latest    3ceeeaf1c709   About a minute ago   446MB
react-app    v2        3ceeeaf1c709   About a minute ago   446MB
react-app    v1        341bb72204c2   2 hours ago          446MB
alpine       latest    b2aa39c304c2   18 hours ago         7.05MB
ubuntu       latest    58db3edaf2be   2 weeks ago          77.8MB

- <Latest tag now pointing to v2>
- Because 
    - react-app:latest ID    ===    react-app:v2 ID

