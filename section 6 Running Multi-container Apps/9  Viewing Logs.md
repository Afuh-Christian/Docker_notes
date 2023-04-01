# 9  Viewing Logs     03:32:13     ..........

# How to view logs acrross all containers of the current app in one place ... 

> docker-compose logs 


- To see available options 

> docker-compose logs --help

-f = follow log output (continualy see new messages as they come out )


# To see logs for the vidly_frontend-1  .. randName 

> docker logs  vidly_frontend-1
or if you wish to follow the logs 
> docker logs -f vidly_frontend-1



# Output 

You can now view vidly-frontend in the browser.

  Local:            http://localhost:3000
  On Your Network:  http://172.18.0.4:3000 


- <Now we got the log's ... we can now put this on a separate monitor if we like ..... >