# 13 Speeding Up Builds    ...   02:10:43 ... 

- Our build are slow , because each time we make a change and try to build , we wait for very long ..



# LAYERS ....
- <An 'image is a collection of 'layers>
- <A 'layer is a small file system that only includes modified files >

- <So when docker tries to build an image for us , it executes each of the intructions in the Dockerfile and creates a 'new_layer , this layer only includes the files that were modified as a result of that instruction


# Dockerfile .. 
FROM  node:14.19.3-alpine3.16
RUN addgroup admin && adduser -S -G admin admin 
USER admin
WORKDIR /app 
COPY package.json package-lock.json ./
RUN npm install 
COPY . .
ENV API_URL=http://api.myapp.com/ 
EXPOSE 3000 
CMD [ "npm","start"] 





# So to optimize you builds ... you should organise the instructions such that .... 

# Dockerfile          
                |        stabe instructions 
......          |
......          |
......          |
......          |
......          |
......          |
                V        changing instructions 