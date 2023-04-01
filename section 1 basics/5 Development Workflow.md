# 5 Development Workflow      00:15:28        ..... 

# - We  take an app and <dockerise> it
- We make a small change on the app so that it can be run by docker 

# How .. 
- We add a <dockerfile> to it ... 

# A dockerfile 
- Is a plain text file that includes <intructions> that docker uses to package up this application into an <IMAGE> 
- This <IMAGE> contains everything our app needs to run 

# IMAGE 
- A cut-down OS 
- A runtime environment(eg Node)
- Application files  
- Third-party libaries 
- Environment variables 

<So we create a dockerfile and give it to docker for packaging our application into and 'IMAGE> 

- Once we have an <IMAGE> , we tell <docker> to start a <container> using that <IMAGE>  

- A <container> is a special kind of process because  it has it's own file system which is provided by the <IMAGE> 

- Our app get's loaded inside a container or a process and this is how we run our app locally on our development machine

- So instead of launching the app and running it  inside a typical process , we tell , <docker to run it inside a container , and isolated environment ... >






# ..... DOCKER STRUCTURE...................... ..... 

                    |   <Registry>   |
                    |                |
       <Dev>        |                |      <TEST/PROD> 
    <APP IMAGE>     |                | 

- Once we have an <IMAGE> 
- we can <push> it to a <Docker Registry> (a <Doker Hub>) (this is like Github to git) 
    - <Docker Registy> is a storage for doker <IMAGES> that anyone can use 

                    |      <Registry>    |
                  <push>   <APP IMAGE>   |
       <Dev>        |                    |      <TEST/PROD> 
    <APP IMAGE>     |                    | 


- Once the app <IMAGE> is on <docker hub> ... we can pull it to any machine running <docker> .... 


                    |   <Registry>      |
                    |  <APP IMAGE>    <pull>
       <Dev>        |                   |      <TEST/PROD> 
    <APP IMAGE>     |                   |      <APP IMAGE>


- This <PROD> machine has thesame <IMAGE> we have on our <DEV> machine which contains  <the specific version of our application with everything it needs >  
- so we  can start our app thesame way we started it on our development machine .
- We just tell docker to <start a container using this 'IMAGE>
- All the instructions for <building> the <IMAGE> of our application is in the <dockerfile>  
- With that , we can package our application into an <IMAGE> and run it vertually anywhere . 







