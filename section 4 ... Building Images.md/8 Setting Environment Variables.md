# 8 Setting Environment Variables   01:56:55   ....

- Sometimes you need to set environment variables 

- <Example .. . lets say this frontend app needs to talk to a 'backend or an 'api ? 
    - Quite often we set <the 'url of the api using and environment variable .... this is where we use the 'ENV intruction>

# Dockerfile 
ENV API_URL http://api.myapp.com/
 or
ENV API_URL=http://api.myapp.com/

# Dockerfile 
FROM  node:14.19.3-alpine3.16
WORKDIR /app 
COPY . .
RUN npm install 
ENV API_URL=http://api.myapp.com/ 




# Now let's rebuild the image and inspect  this environment variable in our container .......   

> docker build -t react-app . 

- run the container ... 

> docker run -it react-app sh 

/app:# 

- verify if the variable we set has be added to environment variables ... 


> printenv 
OR 
> printenv API_URL
OR
> echo $API_URL





