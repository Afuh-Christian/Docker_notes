# 8 Docker Networking   03:27:28.293

- When we run or <app with 'docker-compose , docker-compose will auto create a 'network and add our 'containers on that network so that these containers can talk to each other >

# Let's see the above in action ... 
- bring up the applicaiton in detached mode ... 

> docker-compose up -d 

# now let's view the list of networks created .... 

> docker network ls

# Output
NETWORK ID     NAME            DRIVER    SCOPE
3cbddbc1d040   bridge          bridge    local
89906774065c   host            host      local
6d4860a3afa3   none            null      local
3c60d831c48f   vidly_default   bridge    local

- #  NB <every 'docker_installation had '3_networks> 
    - <d 'bridge>
    - <d 'host>
    - <d 'none>

# The network that was created <is 'vidly_default .... >
- <projectname>_default
- The driver for this network <is 'bridge on 'linux ...... or 'nat on windows>
- This Network(<vidly_default>) contains 3 hosts(containers)
    - frontend 
    - backend 
    - db
- These hosts(containers can talk to each other using their names )




#  Let's see this in action .... (If the contianers can actually talk to each other using their names .... )   .... 

- check running containers 

> docker ps 

# Output 
CONTAINER ID   IMAGE              COMMAND                  CREATED      STATUS             PORTS                      NAMES
0f66e0acc43b   vidly-frontend     "docker-entrypoint.s…"   3 days ago   Up About an hour   0.0.0.0:3000->3000/tcp     vidly-frontend-1
ed5541f3ba37   vidly-backend      "docker-entrypoint.s…"   3 days ago   Up About an hour   0.0.0.0:3001->3001/tcp     vidly-backend-1
efb2385c6b57   mongo:4.0-xenial   "docker-entrypoint.s…"   3 days ago   Up About an hour   0.0.0.0:27017->27017/tcp   vidly-db-1

- <Let's start a shell on the 'frontend  and then 'ping the 'backend

NB ... log in as root user 
> docker exec -it -u root vidly-frontend-1 sh

> docker exec -it vidly-frontend-1 sh


# Output ... 
PING backend (172.18.0.3): 56 data bytes
64 bytes from 172.18.0.3: seq=0 ttl=42 time=0.172 ms
64 bytes from 172.18.0.3: seq=1 ttl=42 time=0.164 ms


# This is what happend under the hood .... 03:29:43   

- <Docker comes with and 'embedded 'DNS 'server that container the 'Name and  'Ip of these 'containers>
- <Inside this 'container , we have a component called a 'DNS 'resolver>
    - <This 'DNS_resolver tells the 'DNS_server to find the 'Ip address of the 'target container ...........                                      So when we 'ping the 'backend container , the 'DNS_resolver as the 'DNS_server , what is the 'IP_ADDRESS of the 'backend>
    - <The 'dns_server returns the 'IP_address and now the 'frontend container can directly talk to the 'backend container using it's 'IP_ADDRESS  >

- <So this means each container has an 'ip_address and is part of a 'network>


# To see the Ip address of the container you're on .. 

/app$ 
> ifconfig

#  Output ... 
eth0      Link encap:Ethernet  HWaddr 02:42:AC:12:00:04
          inet addr:172.18.0.4  Bcast:172.18.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:186 errors:0 dropped:0 overruns:0 frame:0
          TX packets:171 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:16820 (16.4 KiB)  TX bytes:15842 (15.4 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:559 (559.0 B)  TX bytes:559 (559.0 B)



# this conatiner <has '2__network__adaptors> 
- eth0   =   ethernet 0 
    - contains IP_address of the web container 
- lo   
    - contains local ip


# In <the 'docker-compose.yml file  ......    03:30:30      ..> 
 - If the <backend server> 
    - We had and <environment variable  that  contains a database connnection string >
# ....................
    environment: 
      DB_URL: mongodb://db/vidly
# .....................
# db = db container or db host 

the backend container can talk to the db container  <because both containers in this application are part of thesame 'network> 

NB <the 'db_host is only available inside the docker environment>

NB ... to access <the 'db_container(db_host) we need to do 'Port_mapping> ... that's why we have port mapping 

  db:
    image: mongo:4.0-xenial
#   ports:
#     - 27017:27017 
    volumes:
      - vidly:/data/db






# Continue on  monodb compas  ......   03:31:43  ....
























