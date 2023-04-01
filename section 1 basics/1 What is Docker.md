# 1 What is Docker 00:03:16

- A platform for building , running and shipping applications   in a consistent mannar  
    - So if you app works on your development machine , it can run and funtion thesame way on other machines 
    - (<Example , you run a software on your development maching and it doesn't run on any other pc ... ... this usually happens when .. 
        - <One or more files are mission> 
        - <Software version mismatch>
        - <Different configuration settings>
    >)
    - <This is where "docder helps > 

# With docker ... 
- we can easily package our application with everything it needs and run it anywhere so far as the machine has <docker>
    - <Example , if my app needs a cirtain version of node , mongodb ..... they will be included in the application package ..>
    - Now we can run this <application package > on any machine that runs docker
        - so if it runs on your dev machine , it will definitely run on your test and production machines ...

# Also if someone joins your team .. 
- they don't have to set up their machine to run your app
- They simply tell docker , bring up your application 

> docker-compose up 

- docker itself , will auto download and run these dependencies inside an isolated environment called a <container>
    - These <isolated environment> allows multiple applicaitons use different versions of some software side by side
        - <Example , one app1 may use one node 14 and another app2 using node 9>
        - both  <app1> and <app2> can run side by side on thesame machine without messing with each other ..
        - this is how docker allows us to consistently run our apps on different machine .


  <container1>                          <container2> 
     <app1>                                <app2> 
    <node 15>                             <node 9>
    <mongo 4>                             <mongo 3>  





# Advantage .... .
- When we are done with <app2> , we can remove the app and all its dependencies at once

> docker-compose down --rmi all






# Summary , ... 

- Docker helps us to <consistently build , run and ship applications>   