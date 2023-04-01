# 4 Provisioning a Host      03:52:18.040   .....  

- <Now we will use docker machine to create a 'digital 'private server  on 'digital 'ocean 

- run the commands in git bash ... 

> docker-machine create  
this command is very long  
> docker-machine  create \    <for linux >
> docker-machine  create `    <for windows > 

\ = go to next line 

# commands ... 
> docker-machine create \ 
>> --driver 
- Docker machine has drivers for different platforms  .... https://docs.docker.com/machine/drivers/  .... 03:52:56.032
- <NB if you have a server in your own network? You can set '--driver 'none 
>> --driver none  ... 
- <But here we will use 'digital 'ocean 
>> --driver digitalocean \ 
- <here we need to supply an option specific to 'digitalocean
>> --digitalocean-access-token
- <So now we need to go to 'digitalocean and get and 'access-token so that docker machine can talk remotely with digital ocean >
- Go to https://cloud.digitalocean.com/projects/
- Go to https://cloud.digitalocean.com/accounts/api/



