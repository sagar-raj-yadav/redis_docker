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
ii. docker run -d IMAGE_NAME   { -d means , detach(kisi bhi container ko background ke andar run 
                                kar sakte h,normally container "-a" attach mode me run hota h) }
iii. docker run --name YAHA_TUM_CONTAINER_KA_NAAM_LIKH_SAKTE_HO -d IMAGE_NAME


-> docker pull mysql :- agar hum koi specific version mention nhi karte to bydefault latest version pull ho jayega.
->suppose we want to pull version 8.2 then, docker pull mysql:8.2
->hum mysql ka latest version and mysql ka 8.0 version dono ko ek sath docker me pull kar sakte h.


## Note:-
 C:\Users\sagar>docker run -it ubuntu bash ->isko run krne ke baad , terminal pe ye show hoga root@b1e8b8bab62b:/#  ->it means hum ubuntu contianer ke andar jaa chuke hai.

## Note:-  green circle button means wo container running state me h.

example to create docker container:-
i)
C:\Users\sagar>docker run -d -e MYSQL_ROOT_PASSWORD=sagarraj  mysql
1e6eae5f1fc1b39ea667471589064b685c2b01341e990de37470642645a58e42
ii)
C:\Users\sagar> docker run -d  -e MYSQL_ROOT_PASSWORD=sagar8 --name my_sql_older  mysql:8.0
9aefd3dc1f48ba4093689143693b605f6e2077c24963ccfc7dd15f48fe3eeae0

## DOCKER IMAGES LAYERS
->any docker image is made up of different layers. (container->layer 2->layer 1->base layer)

