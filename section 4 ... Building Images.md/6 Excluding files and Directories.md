# 6 Excluding files and Directories        01:52:25      .

- In the last lession , we saw that when we build or application , docker client takes everything in the root dir (context dir or build context) of the app and sends to docker engine or docker damon


# Create a file <called '.dockerignore> in the root dir of app
- We can list the files and directories that should be exclude from this project ....    

# .dockerignore
node_modules/ 



# Now we rebuild the app .... 

> docker build -t react-app . 


# docker will ignore this dir ....