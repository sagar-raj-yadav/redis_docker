Redis is a NoSQL database.
Redis->full form ->remote directory server (redis bhi ek server h)(port of this server =6379)

# redis mostly tab use karte h jab humara application frequently read-write operation perform karta h.

# Redis is is in-memory data structure that can be used as a database ,caching,message broker

# Redis supports various data structure such as string,hashes,list,set,sorted set,bitmap(image),hyperloglog,geospatial index,stream

# Redis supports master-slave replication.
means, Master node data ka primary source hota h and slave node uss data ka read-only copies hota h.
(slave node master node me hone wala changes ko asynchrounously replicate karta h)
Isse scalability increase hota h and fault tolerance decrease hota h.

->slave node independently reads ko serve kar sakta h.isse load balance and performance aacha hota h.

->if master node fails then slave node se data serve kar sakte h ,then redis cluster ke help se slave nodes me se kisi ek ko master node bana sakte h.

# 2. Redis as a Cache
Redis in-memory data ko store karta hai ,, matlab data ko RAM me rakhta hai, jo bahut fast read aur write operations ke liye helpful hota hai. 

# 1. Redis as a Database
-> Redis permanent data storage ka option bhi deta h.

Jab kisi application me frequently accessed data (jaise user sessions ya API responses) ko fast access karna ho, to Redis ko use kiya jata hai.

# 3. Redis as a Message Broker
Redis publish-subscribe (Pub/Sub) aur streams ke through message brokering ka kaam karta hai.
 Yeh real-time messaging ke liye kaafi useful hota hai, jaise chat applications ya notifications ke liye.

# Pub/Sub Workflow:
Publisher ->ek channel par message send karta hai.
Subscribers ->usi topic channel subscribe karte hain aur messages receive karte hain.

# Redis supports various data structure such as string,hash,list,set,bitmap(for image)

# redis architecture 
->  based on client-server architecture
->  Redis is a single-threaded, event-driven system.

# workflow of redis
problem=>
user ne kuch data ka request kiya,jiske liye  hume kuch sql query perform karna hoga . 
server uss query ko database pe send karega fir wo query database pe perform hoga(like fetch data from different tables..),
and ye  user ko ye data response  me mil jayega. agar user me turant hi refresh kar diya to fir se wo sql query  database pe perform hoga and
fir se same time lagega fir response milega.isme same query perform karne ke liye 2 baar same time laga.
2 problems->response time increases , same query multiple times perform ho rha h.

solution=>
we solve this problem using redis-

1.user data ka request karega (GET)

->Client (user) server ko ek data ke liye request bhejta hai, jaise /get-data API ke through.
->Pehle server Redis cache me data check karega:
      i.Agar Redis me data mil gaya (Cache Hit):
        Server wahi se data le lega aur client ko return kar dega.
        Ye bahut fast hota hai kyunki Redis memory (RAM) me kaam karta hai.
      
      ii.Agar Redis me data nahi mila (Cache Miss):
         Server database se query karega (e.g., SQL query run karega) aur wahan se data le aayega.
        Database ka response Redis cache me save hoga future use ke liye (so that agle request pe directly Redis se mile).
        Server client ko data send kar dega.

2.user database me data save karega(POST)
->User server ko data bhejta hai, jaise /insert-data API call karke.
->Server client ke bheje hue data ko Redis ke buffer (temporary memory) me save karta hai.
->Redis yahan ek queue/list ki tarah kaam karta hai, jisme saare incoming data ko temporarily rakha jata hai.
->Jab user saara data bhej deta hai ya ek specific interval ke baad (e.g., har 1 minute):
     i.Server Redis se saare data ek saath fetch karega (batch form me).
     ii.Ye saare data ek baar me hi database me insert ho jata hai (Bulk Insert).
->Is process se frequent database writes ki cost aur latency kam ho jati hai.

# NOTE
i.GET
Client -> Server -> Redis -> [Cache Hit] -> Response
                       |
                       -> [Cache Miss] -> Database -> Redis -> Response

ii.POST
Client -> Server -> Redis (Buffer) -> [Batch Process] -> Database


# Download redis
i.search on google -> redis download for windows git
ii.download zip
iii.extract zip
iv.file path ko system environment se save karo (jaha zip extract kiya ,uss path ko )
v.open terminal->
             a.redis-server
             b.redis-cli   (server on krne ke baad hi cli open karna and server ko close mat karna)

vi.saara command redis-cli me likhte h

# type this in redis server to get all commands
i.help @server ->saara commands mil jayega
ii.help  @string ->  (string->ye ek command h) ->for any specific command

yese hi koi bhi command ke baare me details find kar sakta h.

# Note:redis me Data ko store karne ke liye,we need some data structures.

### Redis Data Types
1. Strings
Commands=>
SET key value
GET key
INCR key (increment the integer value of a key by one)
APPEND key value


suppose databse me data yese store h.
id   name
1    akash
2    megha
3    bittu

example-> SET user:1 akash   (user:1 means user with id=1 uska value akash h)
          GET user:1
yese karne se humara saara user ka group ban jayega.(saara user ek hi group me h)

=> SET msg:3 byee nx -> nx means ,isko set karo only if ye key(msg:3) exist nhi karta ho and agar msg:3 already exist karta hoga to mujhe (nil) return karega.

=>MGET user:1 user:2  ->mget means,multiple values ek sath get krne ke liye

similarly,  MSET bike:1 "Deimos" bike:2 "Ares" bike:3 "Vanth"




