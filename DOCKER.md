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
Docker Image ek **blueprint** hota hai jo **containers** banane ke liye use hota hai.  
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
docker stop CONT_NAME or CONT_ID   # Stop a running container  
docker start CONT_NAME or CONT_ID  # Start a stopped container  

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

## **Note**:-
 C:\Users\sagar>docker run -it ubuntu bash ->isko run krne ke baad , terminal pe ye show hoga root@b1e8b8bab62b:/#  ->it means hum ubuntu contianer ke andar jaa chuke hai.

