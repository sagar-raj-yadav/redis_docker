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
-> architecture based on client-server model
->  Redis is a single-threaded, event-driven system.

# workflow of redis
user ne kuch data ka request kiya,jiske liye  hume kuch sql query perform karna hoga . 
server uss query ko database pe send karega dir wo query database pe perform hoga(like fetch data from different tables..),
and ye  user ko ye data response  me mil jayega. agar user me turant hi refresh kar diya to fir se wo sql query  database pe perform hoga and
fir se same time lagega fir response milega.isme same query perform karne ke liye 2 baar same time laga.
2 problems->response time increases , same query multiple times perform ho rha h.

we solve this problem using redis->hum ek new server banayenge redis
user ne server se kuch request kiya ->pehle server redis se wo data ka request karega ,(but currently redis ke paas wo data nhi h)
->fir wo query database me perform hoga and wo data redis me cache ho jayega and user ko bhi response mil jayega.
->ab jab user refresh kar dega to pehle sever redis ke cache me wo data check karega agar cache me data mil gya to wahi se user ko response mil jayega.
