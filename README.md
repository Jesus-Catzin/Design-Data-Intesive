# Design-Data-Intesive

## Chapter One.
### Reliable, Scalable and Maintainable Applications:

1- What is the difference between *fault* and *Failure*?
* Fault: It's defined as one component of the system deviating from its spect.
* Failure: It's when the system as a whole stop providing the required service to the user. 

2- Which are common Hardware faults?
* Hard disks crash, RAM becomes faulty, the power grid has a blockut, someone unplugs the wrong network cable. 

3- Which are some common Software errors?
* Software bugs that causes crashes.
* A runaway process used up some shared resource.
* A service that depend on slows down, becomes unresponsive or starts returning corrupted responses. 
* Cascading Failures.

4- What can we do to make our system reliable from Human Errors?
* Design Systems in a way that minimizes opportunities for error.
* Decouple the place where people make the most mistakes from the places where they can cause failures. 
* Test thoroughly at all levels, from unit test to the whole-system integration test and manual test.
* Allow quick and easy recovery from humman errors, to minimize the impact in the case of failure.
* Set up detailed and clear monitoing, such as performance metrics and error rates. 
* Good management practices and training.

5- What are load parameters?
* Tjese are configuration values that specify how Source System data is loaded.

6- Why is important to know how work with the load?
* Becuase sometimes it's important to decide if is preferable to do more work at write time or at read time. 

7- What are Latency and Response time?
* Response time is what the client sees: besides the actual time to process the request, including network delays and queueing delays.
* Latency is the duration that a request is waiting to be handled. 

8- Why is important to think of response time as a distribution and not as a single number?
* Because the response time can vary a lot even for the same request, so it's better to thing as a possible distribution range that we can measure.

9- Why we must not use the *average* as a service reported and what wee should use instead?
* We mustn't use it because it doesn't tell us how many users actually experimenced that delay.
* Usually, it's better use percentiles, in this case the median because is the half-way point. 

10- Which are the three of the important design principles for software systems?
* Operability: Make it easy for operations teams to keep the system running smoothly.
* Simplicity: Make it easy for new engineers to understand the system, by removing as much
complexity as possible from the system.
* Evolvability: Make it easy for engineers in future to make changes to the system, adapting it
for unanticipated use cases as requirements change.

## Chapter Two:

1- Which are the root of relational databases and which where the most case uses?
* It lies in business data processing  and it's typically used for transaction processing (entering sale or bank transactions etc) and batch processing (customer invoicing, payroll, reporting)

2- What was the goal of relational model?
* It was to hide that implementation detail bethind a cleaner interface. 

3- Which were some of the most stronger reasons behind the adoption of NoSQL databases?
* Need for greater scalability 
* Widespread preference of free and open source software over commercial database products. 
* Specialized query
* Deside for more dynamic and expressive data model. 

4- What is Polyglot Persistence?
* Refers to using different data storage technologies to handle varying data storage needs. It’s an offshoot of polyglot programming, which means using different programming languages to build an application.

5- Which are some of the advantages from having standardized lists of grographic regions and industries?
* Consistent style and spelling.
* Avoiding ambiguity
* Name is stored in one only place
* Better search. 

6- When is recommended to use the IMS (Hierarchical Model)?
* It works well for one-to-many relationship but not for many-to-many no :c 

7- How are the links in the network model?
* Those are more like pointers in a programming language. 

8- What is the problem of no having schema?
* Means that arbitrary keys and values can be added to a document, and when reading clients have no guarentees as to what fields the documents may contain. 

9- Which is one disavantages in uses interactive language over declarative? 
* It's harder to understand and if the class is removed the change won't do anything even if you re-run the code.

10- What is map reduce in general terms?
* Is a programming model for processing large amounts of data in bulk across many machines. 

11- Wich are the propierties of a vertex?
* a unique identifier,
* a set of outgoing edges,
* a set of incoming edges, and
* a collection of properties (key-value pairs).

12- Which are the propierties of edges?
* a unique identifier,
* the vertex at which the edge starts (the tail vertex),
* the vertex at which the edge ends (the head vertex),
* a label to describe the kind of relationship between the two vertices, and
* a collection of properties (key-value pairs).

13- Which are some of the most important aspect of graph-like database model?
* Any vertex can have an edge connecting it with any other vertex.
* Given any vertex, you can efficiently find both its incoming and its outgoing edges, and thus traverse the graph — follow a path through a chain of vertices —both forwards and backwards.
* By using different labels for different kinds of relationship, you can store several different kinds of information in a single graph, while still maintaining a clean data model.

14- What is Cypher Query Language?
* It is a declarative query language for property graphs, created for the Neo4j graph database

15- How is written RDF objects?
* IN XML format

## Chapter 3:

1- Which are the most two fundamentals things a database needs to do?
* It should store and give you data when you need it!

2- Why is too important choose addecaute indexs?
* Becuase it speeds up read queries.

3- What is a Hast Map?
* Basically, a HashMap allows you to store items with identifiers. They are stored in a table format with the identifier being hashed using a hashing algorithm. 

4- When is well situed use engines like Bitcask?
*  When we have situations where for each key is updated frequently.

5- What does mean Compaction? 
* Means throwing away duplicate keys in the log, and kep only the most recent update for each key. 

6- Which are some of the issues in real implementations using the log?
* File Format: CSV not the best format for log. It faster and simplier to use a binary format.
* Deleting Records: If you want to delete a keys and its values, you have to append a special deletion (Tombstone)
* Chash Recovery: If the database is restarted, the in-memory has maps are lost.
* Partially writting records: Use of checksums which allow ignore and detect corrupted parts of the log.
* Concurrency control: Use one writer thread but with some consecuences.

7- Which are some limitation of the Hash Table: 
* Must fit in memory (Small numbers of keys)
* Ranges queries are not efficient, the fetch is not easy to match. 

8- What is the main differences of the SStables?
* The keys are sorted by using the Merge Sort Algorithm.1

9- In TBR what is called "Memtable"?
* To add a write into an in-memory balanced tree. 

10- What is a Bloom Filter and its is benefy?
* It's a a memory-efficient data structure for approximating the contents of a set. It can tell you if a key does not appear in the database, and thus saves many unnecessary disk reads for non-existent keys.

11- Which are some advantages of update and add a new key in a B-Tree?
* Update: You search for the leaf page containing that key and change the value that page, and write the page back to disk.
* New Key: Find the page whose range encopasses the new key, and it to that page.

12- We know that the B-tree overwrite the page on disk even including the parent and childs. What is used to avoid crashes? 
* It used write-ahead log (WAL or Redo Log). This is an append-only file to which every B-tree modification
must be written before it can be applied to the pages of the tree itself. 

13- Mention some of the most diferences between B-trees and LMS-trees:
* B-Trees:
  * Are  faster for reads 
* LMS-trees:
  * Sustain much higher throughput of random writes
  * Are typically faster for writes

14- Why is common used the Heap File?
* Because because it avoids duplicating data when multiple secondary indexes are present: each index just references a location in the heap file, and the actual data is kept in one place.

15- What is clusted index?
* Cluster index is a type of index which sorts the data rows in the table on their key values. In the Database, there is only one clustered index per table.
A clustered index defines the order in which data is stored in the table which can be sorted in only one way. So, there can be an only a single clustered index for every table. In an RDBMS, usually, the primary key allows you to create a clustered index based on that specific column. 

16- Whad does do a *concatened index*?
* Simply combines several field into one key by appending one column to another.

17- What is the best advantages of Fuzzy Index?
This allow search Similar keys.

18- What is a Data Warehouse?
*  is a separate database that analysts can query to their heart’s content, without affecting OLTP operations.

19- How does save the data the *column-oriented storage*?
* It doesn't store all the values from one row together, but store all the values from each column together instead. 

20- Why is too important the use of RLE to sort in column storage? 
* Because the RLE can compress many characters repeat in the key to some few kilobytes.

21- Whart is *Materialized View*? 
* It's similar to a standar (virtual) view.

## Chapter 4:

1- What is *Rolling Upgrade*
* We used the term “Rolling Upgrade” to describe a situation where we have multiple servers (usually load-balanced) and we needed to keep “the application” online, while deploying a new version of software.

2- Which are the two things that we need to keep running smoothly the system?
* Backward compatibility: Newer code can read data that was written by older code.
* Forward compatibility: Older code can read data that was written by newer code.

3-Which are some of the most subtle problems to use JSON, XML and CSV?
* XML and CSV: Cannot distinguish between a number and a string. 
* JSON: cannot distinguish between intenger and floating-point. 
* Java and JSON: After 2¹³ cannot be exaclty represented in IEE 754 double precision flotaing-point number. 
* JSON and XML: Don't support binary strings (sequences of bytes without a character encoding).

4- What are *BinaryProtocol* and *CompactProtocol*?
* BinaryProtocol: is the protocol implemented by the Network plugin and some external implementations to exchange data collected by collectd or to send data to an instance of collectd. 
* CompactProtocol: It implements the standard Thrift TCompactProcotol which is similar to the TBinaryProtocol, but takes less space on the wire. Integral types are encoded using as varints.

5- What is *writer's schema*?
* It's when an application wants to encode some data (To write it to a file or database)

6- What is *Reader's Schema?*
* It's when an application wants to decode some data (To read it from a file or database)

7- How does work the *accessing a data base at the same time*? 
* The writing process: This may be written a *newer* versions of the code which is being update in the moment of the code running and some will be runing older code
* The reading process: This is like a batch which reads the older version of the codad that is still running. 

8- Wich are some of the most important differences between a local function and Network?
* Local is predictable, and ehiter succes or fails depenf only on parameters that are under your control whereas network you will don't, it can be caused by lost due a nerwork problem, or the remote machine maybe slor or unaviable etc.
* Local function call either returns a result, or throws an exception, or neceer return meanwhile network can return no result(*timeout*). 
* Local it normally takes about the same time to execute, meanwhile a network can be slower (latency)
* The client and service may be implemented in different programming languages.
9- Why are so important the **actors** in *distributed actor frameworks*?
* It's because the actos already assumes that messages may be lost, even within a single process. 

## Chapter 5.

1- Tells some reasons why you might want to replicate data:
* To keep data geographically close to your users and reduce latency.
* To allow the system to continue working even if some parts of the system have failed (Aviability).
* To scale out the number of machine that can serve red queries (Increase read throughput)

2- Which are the main components *leader-based-replication* for?
* Leader/master/primary
* Replicas known as follower/read replicas/ slaves or hot standbys.

3- WHich are the advantages/disadvantages of synchronous replication?
* It guarantes to have an *up-to-date* copy of the data but if one follower doesn't respond the write cannot be processed. 

4- When a *master or leader* fais a **follower** need to be promoted to be the new leader and the clients need to be reconfigurated. This is known as **Failover**.<br> How do we automatize the process?
* Determining that the leader has failed: Detect the fail in general.
* Choosing a new leader: Use a election process or appoint by a previously-elected controller node.
* Reconfiguring the system to use the new leader: Clients now need to send thier write request to the new leader.

5- What does guarantee *read-your-writes-consistency*?
* It guarantee that if the user reload the page, they will always seen any updates they submmited themselves but not promises about the other users. 

6- Why is better to used *Multi-leader* configurations than *single-leader*?
* Performance: Every write can be processed in the local datacenter and is replicated asynchronously to other datacenters.
* Tolerance of datacenter outages: It allows each datacenter can continue operating idenpendently of the others. 
* Tolerance of networks problems: It uses asynchronous replication can usually tolerate newtwork problems.

7- When we are working with Multiple-leader, which are the way to achieve *Convergent* in order to have synchronic?
* Give unique ID, pik the write with the highest ID as winner, and throw away the others. Tis is known as LWW.
* Give each replica a unique ID, and let writes that originated at a higher-numbered replica always take precedence over writes that originated at a lower-numbered replica. This also implies data loss.
* Somehow merge the values together.
* Record the conflict in an explicit data structure that preserves all information, and write application code which resolves the conflict at some later time (perhaps by prompting the user).

8- Which are the two main mechanisms that which are used in Dynamo-style? 
* Read Repair
* Anti-entropy process

9- What is *Hinted handoff*?
* It's the fact that other node that was accepting any writes send it to the appropiate "home".

## Chapter 6
1- How is called partitions in MongoDB, Elasticsearch, HBase, BigTable, Cassandra, vBucket?
* MongoDB, Elasticsearch, : Shard
* Hbase: Region
* BigTable: Tablet
* Cassandra, Riak: Vnode
* Couchbase: vBucket

2- Which is the main reason to use partition?
* To allow scalability

3- What is *skewed* and *hot spot*?
* To have some partitions that have more data or queries than others. 
* To have partitions with disproportionately high load

4- When we avoid Hot Spot assigning record to node randomly, What is the disadvantage?
* Whe you're trying to read a particular item, you have no way of knowning which node it is on. 

5- What is *rebalancing*?
* The process of moving data around between nodes in the cluster

6- Why you shold never use mod N to assing range in hash partition?
* Because if you use it, it would return a number between 0 to n, and if you a new node, you would need to reassign it moving it to another node.

7- How does the database know if a query result might have changed?
* Detecting reads of a stale MVCC object version (uncommitted write occurred before the read)
* Detecting writes that affect prior reads (the write occurs after the read)


## Chapter 7

1- What is *transactions* and how does it work? 
* It's a way for an application to group several read and writes together into a logical unit.<br>In this case all the reads and writes in a transaction are executed as one operation: Either the entire transactions succeeds or it fails. 

2- What does mean ACID and BASE*
* ACID: Atomicity, Consistency, Isolation and Durability
* Basically Available, Soft state and Eventual consistency.

3- What is Atomicity in the context of ACID?
* It's describe what happens if a client wants to make several writes, but a fault occurs after some of the writes have been processed.<br> If the writes are grouped together into an atomic transaction, and the transaction cannot be completed (committed) due to a fault, then the transaction is aborted and the database must discard or undo any writes it has made so far in that transaction.

4- Which is the philosophy of the ACID databases? 
* If the database is in danges of any violation its guarantee the ACID, it would rather abandon the transaction entirely than allow it to continue. 

5- Which is the most basic level of Isolation and what guarrantees?
* It's *read commited*: 
 * When  redaing from database, you will only see data that has been committed (No dirty reads)
 * When writing to thje database, you will ony overwrite data that has benn commited (No dirty writes)

6- What is non-repeatable read or read skew?
* It's the fact that one data is late and not update so fast, and when you do a query you would see inconsistencies in that momento, but wainting for a time and requesting again it would show the information correctly. 

7- Describe the mechanisms used in Dynamo-style datastores?
* Read repair: when a client makes a read from several nodes in parallel, it can detect any stale responses.
* Anti-entropy process: some datastores have a background process that constantly looks for differences in the data between replicas and copies any missing data from one replica to another.

8-  What are skewed workloads?
* Some partitions that have more data or queries than others. The presence of skew makes partitioning much less effective. In an extreme case, all the load could end up on one partition, so 9 out of 10 nodes are idle and your bottleneck is the single busy node.

9- Why are concurrency bugs hard to find by testing?
* Because such bugs are only triggered when you get unlucky with the timing. Such timing issues might occur very rarely, and are usually difficult to reproduce.

10- What is the idea of snapshot isolation?
* The idea is that each transaction reads from a consistent snapshot of the database—that is, the transaction sees all the data that was committed in the database at the start of the transaction. Even if the data is subsequently changed by another transaction, each transaction sees only the old data from that particular point in time.
