#   2 Viewing the Logs   ....   02:37:06      ....  

- Now we have two containers running inside the background ... but there's a problem 
    - <We 'don't know what is going on inside these containers >
        - What if something goes wrong ..e.g what if our server generates and error 

# check the running containers 

> docker ps

CONTAINER ID   IMAGE       COMMAND                  CREATED          STATUS          PORTS      NAMES
2d6f16230661   react-app   "docker-entrypoint.s…"   9 seconds ago    Up 2 seconds    3000/tcp   infallible_gould
0b07c3a8a573   react-app   "docker-entrypoint.s…"   18 minutes ago   Up 18 minutes   3000/tcp   react-sample

# check the logs for one container ... 

> docker logs <containerID/randomNAME>
> docker logs react-sample 

# ouput 

 react-app@0.1.0 start /app
 react-scripts start

ℹ ｢wds｣: Project is running at http://172.17.0.2/
ℹ ｢wds｣: webpack output is served from
ℹ ｢wds｣: Content not from webpack is served from /app/public
ℹ ｢wds｣: 404s will fallback to /
Starting the development server...

Compiled successfully!

You can now view react-app in the browser.

  Local:            http://localhost:3000
  On Your Network:  http://172.17.0.2:3000

Note that the development build is not optimized.
To create a production build, use yarn build.


# this is thesame out put we got we we ran the <command docker run react-app>




# The lods command has additional options ... 

> docker logs --help

-f = used when you container is continuesly producing output 
    - Like updating in real time on the terminal ... like in react , next js , (and or when using Nodemon)

> docker logs -f react-sample   

# Output ... 
Compiled successfully!

You can now view react-app in the browser.

  Local:            http://localhost:3000
  On Your Network:  http://172.17.0.2:3000




# To look at the last 5 lines of the log ... 

-n 

> docker logs -n  5 react-sample


# To see the timestamp of the logs ... the time when each process started ..

> docker logs -t react-sample

# Output

2023-02-12T12:01:15.846400800Z
2023-02-12T12:01:15.846456100Z > react-app@0.1.0 start /app
2023-02-12T12:01:15.846464600Z > react-scripts start
2023-02-12T12:01:15.846470500Z
2023-02-12T12:01:41.867422600Z ℹ ｢wds｣: Project is running at http://172.17.0.2/
2023-02-12T12:01:41.868135400Z ℹ ｢wds｣: webpack output is served from
2023-02-12T12:01:41.868256300Z ℹ ｢wds｣: Content not from webpack is served from /app/public
2023-02-12T12:01:41.868371600Z ℹ ｢wds｣: 404s will fallback to /
2023-02-12T12:01:41.868866500Z Starting the development server...
2023-02-12T12:01:41.868884700Z
2023-02-12T12:01:56.819035700Z Compiled successfully!
2023-02-12T12:01:56.820536600Z
2023-02-12T12:01:56.820678500Z You can now view react-app in the browser.
2023-02-12T12:01:56.820715500Z
2023-02-12T12:01:56.820855100Z   Local:            http://localhost:3000
2023-02-12T12:01:56.820892200Z   On Your Network:  http://172.17.0.2:3000
2023-02-12T12:01:56.820954400Z
2023-02-12T12:01:56.820987600Z Note that the development build is not optimized.
2023-02-12T12:01:56.821105600Z To create a production build, use yarn build.
2023-02-12T12:01:56.821123200Z








# NB ... so if you enconter any issues ... alway check the logs to see the errors .... 
