# 9 cashed intructions in dockerfile  .... 


# Dockerfile .... 

FROM  node:14.19.3-alpine3.16
WORKDIR /app 
COPY package.json package-lock.json ./
RUN npm install 
COPY . .
ENV API_URL=http://api.myapp.com/ 


# - The instructions before <the 'last 'COPY instruction (COPY . . ) are being cached ..... this means they are not ran more than once if everything is still thesame ......>

this means ..

- WORKDIR /app 
- COPY package.json package-lock.json ./
- RUN npm install 
are all cached .....

# this is done so that you should install npm packages everytime you want to build .... and also increases build speed .... 







