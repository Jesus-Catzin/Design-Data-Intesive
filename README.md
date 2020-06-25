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
* Ranges queries are not efficient.

8- 
