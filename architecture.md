Gonne be theroy class !!!!! Don't be sad make your face sleepy -> joke 

i"m gonne try to take it intresting

General concepts:

Replication:
making multiples copies of data spread across nodes to prevent data loss

sharding:
dividing data into smaller parts (shards) and storing across various nodes

these two are database techniques for which used for improving scalability, availablity, and fault tolerance

node -> a database instance which is used to store the data 

cluster -> a group of node to form a cluster -> store and replicate data 


Scylla db Architecture:
1. it is a shared nothing architecture which means there is no single 




Lets go one by one 

Shared nothing Acrhitecture means user can be able to create aa single node or multiple node
node s nothing but database instances, lets talk about both single and multiple node 

In single node:
the entire data is stored on that node 
using sharding technique data is spread across no.of available cpu cores 
since this is single node no replication happens here 

IN mUltiple nodes :

lets assume user create aa 3 nodes:

now data is spread across partitioned and stored across three nodes
each nodes has is own set of data need to be managed 
same as single node using sharding technique data is sharding within its node 

when creating aa replication the original data is stay inside the assigned node but the copies of data which is replica whoch will be shared 
across the all node for higher availability and higher perfromance 

here shared nothing architetcure is said by there is no shared memory, cpu, disk space each node has it own 


TOO many therory right ?
just few more cocepts then we will go into actually examples:

then comes Sharding:
sharding we already knows split data into smaller data (shards) 

how sharding works:
here lets take aa example:
imagine we have 10 rows to store we hvaing are using single node 

instead of stroing all 1 data in single core in cpu we are diving 1 data into 10 chunks 
store each chunks into various part of core 

why it is helpful if user ask for one row why we need to scan the entire table to return 
we are storing each row in various part of core we look for that one row in core and return 

Understands too many theroy again we go by exmaple:
imagine we have 10 tasks -> we know we need to shared the data 
ok how we shared?
we need to find the primary key -> new word (primary key is value which is unique for each row)
for those data there is key called _id which is unique for each row in table 

now primary key is converting into a token (using some hashing technique)
these token will helps scylladb decide which core will store the data 

based on the token range and available core the data is spread across the core 

these entire sharding process is taken care by scyllaDB 
we will see more exmaples and relaizes hwo it works internally for now lets understand the cocnrpts 

Replication:
replication enusres higher availablity and fault tolerance by storeies a multiple copies of data acorss various nodes 



Key componenet of replication 
replication factor, replication strategies

replication factor -> 
Already we know we have aa data in single node we ahve aa option called replication factor which is no determines teh no of copies stored across the other nodes 
due to some reason if one node faials other node serve that data 

replication stragtegies: 
simple strategy, network topology 

simple staregty:
badsicllay it contains only one data center (here data center determines aa cluster of dtaabse)
iamgine aa cluster 1 data center conatins one cluster and cluster conatins multiple nodes 
replication is done maong various all nodes 


network topologty is we can have multipel dta center each data center has it own cluster and each cluster has aa mutplie nodes herw 
can we can giev replication for each center 

eg: imagine we have data cenetr in USA & india we can determine teh replication factore USA DC around 4 replica 
and for INDIA DC around 3 rpelica 