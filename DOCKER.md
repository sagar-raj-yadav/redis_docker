### **Docker in Simple Terms**  

#### **1) Why Do We Need Docker?**  
Agar ek project specific versions pe run ho raha hai (e.g., React Native v19, Node.js v17, MongoDB v4) aur ek new developer ke system pe updated versions hain, to dependency mismatch ke wajah se errors a sakte hain. **Docker** ise fix karta hai by creating a consistent environment across all systems.  

#### **2) What is Docker?**  
Docker ek **containerization platform** hai jo applications ko **lightweight, portable, and scalable** banata hai.  
👉 **Without Docker:** Har system pe manually dependencies install karni padti hain.  
👉 **With Docker:** Ek hi container har system pe same tarike se chalega.  

#### **3) What is a Container?**  
Container ek **isolated unit** hai jo application aur uski **dependencies** ko ek saath pack karta hai.  
✔ **Portable:** Har OS pe same tarike se chalega.  
✔ **Lightweight:** Virtual Machine (VM) se faster aur kam resources consume karta hai.  

#### **4) How is Docker Different from a Virtual Machine?**  
| Feature | Docker (Containers) | Virtual Machine (VM) |  
|---------|---------------------|----------------------|  
| **Boot Time** | Seconds | Minutes |  
| **Performance** | High | Comparatively Slow |  
| **Storage** | Lightweight | Heavy |  
| **OS Dependency** | No (Runs on Host OS) | Yes (Each VM has its own OS) |  

#### **5) What is a Docker Image?**  
Docker Image **containers** banane ke liye use hota hai.  
✔ **Reusable:** Ek baar image bana lo, multiple containers create kar sakte ho.  
✔ **Portable:** Kisi bhi system me transfer aur run kar sakte ho.  

#### **6) Why Should Developers Learn Docker?**  
✔ **Cross-Platform Compatibility** → Code har OS pe same chalega.  
✔ **Version Control** → Dependencies ko freeze kar sakte hain.  
✔ **Easy Deployment** → Server pe deploy karna simple ho jata hai.  
✔ **Fast & Lightweight** → VM se zyada efficient hai.  
✔ **Scalability** → Multiple containers ek saath manage kar sakte hain.  


#### **6) Docker version and commands ?**
✔ **docker** -v ->verson .
✔ **docker** ->all command of docker .

# Docker Commands  

## **Basic Commands**
docker pull IMAGE_NAME             # Download an image from Docker Hub  
docker images                      # List all downloaded images  
docker run IMAGE_NAME              # Ek naya container create karega aur run karega
docker ps -a                       # Sab containers list karne ke liye  
docker start CONTAINER_ID          # Pehle se existing container ko start karne ke liye   
docker run -it IMAGE_NAME          # Run a container in interactive mode  
docker stop CONTAINER_NAME or CONTAINER_ID   # Stop a running container  
docker start CONTAINER_NAME or CONTAINER_ID  # Start a stopped container  
docker rmi IMAGE_ID                 # delete image
docker rm CONTAINER_ID              # delete container

Note: root@b1e8b8bab62b:/# ->supose ye container ke andar chale gye aur yaha se bahar nikalna h then  root@b1e8b8bab62b:/# exit  .

REPOSITORY                 TAG       IMAGE ID       CREATED         SIZE  
hello-world                latest    74cc54e27dc4   6 weeks ago     10.1kB  
docker/welcome-to-docker   latest    c1f619b6477e   16 months ago   18.6MB  

Note: TAG -> version of Image



## **create container**
CONTAINER ID   IMAGE        COMMAND       NAMES
5d8a0f7c2a12   hello-world   "bash"       zen_blackwell
->docker container ko random name de deta h. 

## **steps to create docker container**
->docker client contact karta h docker daemon ko.
->docker daemon pull karta h hello-world image from docker hub.
-> docker daemon ek new container create krta h uss image se.

## **Normal docker run IMAGE_NAME** :-  Ek naya container create hoga aur turant exit ho jayega.
Interactive Mode (docker run -it IMAGE_NAME) :- Ek naya container create hoga aur start hoga.
Tum container ke andar enter karoge aur tmhe ek terminal bhi milega jispe tm command run kar sakte ho.


## Versions
i. docker pull IMAGE_NAME:version
ii. docker run -d IMAGE_NAME   { -d means , detach(koi container ko background me run karna ,Tumhara terminal free rahega)
normally container "-a" attach mode me run hota h) }
(-a => container foreground me run hota aur tum terminal pe logs dekhte rehte. ) 
iii. docker run --name YAHA_TUM_CONTAINER_KA_NAAM_LIKH_SAKTE_HO -d IMAGE_NAME


-> docker pull mysql :- agar hum koi specific version mention nhi karte to bydefault latest version pull ho jayega.
->suppose we want to pull version 8.2 then, docker pull mysql:8.2
->hum mysql ka latest version and mysql ka 8.0 version dono ko ek sath docker me pull kar sakte h.


## Note:-
 C:\Users\sagar>docker run -it ubuntu bash ->isko run krne ke baad , terminal pe ye show hoga root@b1e8b8bab62b:/#  ->it means hum ubuntu contianer ke andar jaa chuke hai.

## Note:-  green circle button means wo container running state me h.

# example to create docker container:-
i)
C:\Users\sagar>docker run -d -e MYSQL_ROOT_PASSWORD=sagarraj  mysql
1e6eae5f1fc1b39ea667471589064b685c2b01341e990de37470642645a58e42
ii)
C:\Users\sagar> docker run -d  -e MYSQL_ROOT_PASSWORD=sagar8 --name my_sql_older  mysql:8.0
9aefd3dc1f48ba4093689143693b605f6e2077c24963ccfc7dd15f48fe3eeae0

## DOCKER IMAGES LAYERS
->any docker image is made up of different layers.
{ container (top layer) ->layer 2->layer 1->base layer (last layer) }
->sirf container layer ko change kar skate h ,iske alawa koi bhi layer me change nhi kar sakte 
 (i.e, baki sari layer read only layer hota h) .
->conatiner layer ko change kar sakte h ,jisse dusra new container build kar sakte h.
->suppose agar same image do different version me install karte h to dono images me kuch layer same hota h (pull krte time jo layer same hai usme "Already exists" likha hua aayega ).


## PORT BINDING
haar container ka apna ek different port hota h.
machine ka port alag and container ka port alag hota h.
machine port ->8081,5000
container port-> 3306/tcp

But,hum container ke port ko machine ke port se bind kar sakte h.

suppose agar koi request machine pe port 8080 pe aa rha h ,hum cahte h ki wo request container ke 3306 port pe chala jaye,then we use  " docker run -p8080:3306 IMAGE_NAME " ->this mapping is called port binding.

Note:agar machine 8080 port ek conatiner ka port 3306 se bind ho gya ,to same 8080 port dudre container se bind nhi ho sakta.


## TROUBLESHOOT COMMANDS  ->errors ko resolve karne ke liye
docker logs CONTAINER_ID
docker exec -it CONTAINER_ID/bin/bash
docker exec -it CONTAINER_ID/bin/sh


## DOCKER VS VIRTUAL MACHINE

virtual machine->  
application layer
    |
    OS 
    |
    Hardware
docker virtual machine ka hi OS use karta h.

# Virtual Machine 
->Har VM apna alag OS use karta hai.
->Heavy hota hai kyunki har VM ka apna alag OS hota hai.
Startup slow hota hai kyunki pura OS boot hota hai.

# Docker 
*->Docker host(machine) OS ka hi use karta hai, alag OS load nahi karta*.
->Sirf application aur uski dependencies ko isolate karta hai.
->Lightweight hota hai, kyunki har container ek full OS nahi chalata.
->Jaldi start hota hai, kyunki OS boot nahi karna padta.
Ek Example
🚗 VM = Alag-alag cars jo apna pura engine (OS) lekar chal rahi hain.
🚌 Docker = Ek hi bus (OS) jisme alag-alag passengers (applications) hain.

# Docker Linux ke liye bana hai, to Windows/Mac pe Docker kaise run hota hai?
- Docker Linux ka virtual environment create karta hai.
- Yeh ek lightweight VM hota hai jo background mein chalu rehta hai.
- Windows pe Docker **Docker Desktop** ki madad se run hota hai.
- Agar Windows hai toh **WSL2 (Windows Subsystem for Linux)** ka use hota hai.

## DOCKER NETWORK
agar hume 2 container ko apas me interact karwana hai to hume docker network ka use karna padega.

# list of all docker networks
-docker network ls              

# create new network
-docker network create NETWORK_NAME



# pull and run mongo and mongo-express container
-e -> environment variable
root_username-> admin and  root_password-> querty

=>mongo :- Ye actual database server hota hai.
=>command to run mongo in terminal:-
docker run -d 
-p 27017:27017
--name mongo 
--network mongo-network 
-e MONGO_INITDB_ROOT_USERNAME=admin 
-e MONGO_INITDB_ROOT_PASSWORD=querty 
mongo



=>mongo-express :- Ye GUI (Graphical Interface) hota hai, jo tumhare MongoDB ke upar run karta hai.Tum MongoDB ko web browser se easily dekh sakte ho, usme data insert/update/delete kar sakte ho.mongo-express MongoDB se connect karta hai using same username, password, host, port.

=>run mongo-express:-
docker run -d 
  -p 8081:8081 
  --name mongo-express 
  --network mongo-network 
  -e ME_CONFIG_MONGODB_ADMINUSERNAME=admin 
  -e ME_CONFIG_MONGODB_ADMINPASSWORD=querty 
  -e ME_CONFIG_MONGODB_SERVER=mongo 
  -e ME_CONFIG_MONGODB_URL="mongodb://admin:querty@mongo:27017"
  mongo-express


note:- "mongodb://username:password@container_name:port_jisme_mongo_contaienr_run_kar_rha"

# how to run GUI of mongo Db
go to browser->http://localhost:8081 -> enter username:admin and password:pass

# how my project connect with mongo database of docker?
              Outside Docker
           ┌──────────────────┐
           │   server.js      │
           │ (your project)   │
           └────────┬─────────┘
                    │  Read/Write/Post
                    ▼
          ┌──────────────────────┐
          │    Docker Network    │
          │  (Internal Bridge)   │
          │                      │
          │  ┌───────────────┐   │
          │  │   MongoDB     │◄──┐
          │  └───────────────┘   │
          │                      │
          │  ┌────────────────┐  │
          │  │ mongo-express  │◄─┘
          │  └────────────────┘
          └──────────────────────┘

MongoDB – The NoSQL database.
Mongo Express – A web-based GUI for MongoDB.

i) server.js directly MongoDB se interact karta hai to perform all database operations (read, write, post, etc.).
ii) server.js ke through jitne bhi updates hote hain, wo sab turant Mongo Express GUI me visible hote hain.
iii) MongoDB aur Mongo Express same Docker network me hain, isliye dono ek dusre se easily communicate kar lete ha

Note:- for all other database we can use their GUI .
like  MySQL	-> phpMyAdmin	 and PostgreSQL ->	pgAdmin	


# Docker compose
`.yaml` → **Yet Another Markup Language** 

→ Multiple Docker containers ko ek saath manage karne ke liye use hota hai. 
Jab aapko ek se zyada services (jaise frontend, backend, database) ko ek saath run karna hota hai, tab Docker Compose kaafi useful hota hai.  
→ Docker Compose ek YAML file (`docker-compose.yml`) ke through kaam karta hai jisme aap define karte ho ki kaun-kaun se containers chahiye, unka image kya hoga, ports kaise map karne hain, environment variables kya rahenge, etc.

---

## Example Use Case:
Agar aap ek full stack project bana rahe ho jisme:
- React frontend  
- Node.js backend  
- MongoDB database  

To normally aapko teen alag Docker commands chalani padengi, lekin Docker Compose me aap sab kuch ek hi command me kar sakte ho:

---

## Example `docker-compose.yml` File:
version: "3.8"
services:
  frontend:
    image: react-app
    ports:
      - "3000:3000"

  backend:
    image: node-app
    ports:
      - "5000:5000"    
    depends_on:
      - mongo

  mongo:
    image: mongo
    ports:
      - "27017:27017"
    environment:
      MONGO_INITDB_ROOT_USERNAME: admin
      MONGO_INITDB_ROOT_PASSWORD: qwerty


Note: ("5000:5000" = host_port:container_port ) ->this is called  port binding or  port mapping
->Tumhare system pe agar koi localhost:5000 pe request karega, to wo Docker container ke andar wale port 5000 pe chala jayega.


docker-compose up: sabhi containers start karega.
docker-compose down: sabhi containers stop karega.
docker-compose build: images ko build karega agar needed ho.








