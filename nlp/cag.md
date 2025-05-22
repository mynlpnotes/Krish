# CAG

* Cache Augmented Generation
* In a client, server, DB system
* Request goes Client ⇒ Server ⇒ DB ⇒ Server ⇒ Client
* In middleware we can cache the data
* It is called as KVC - Key value cache
* Using cache we are making the process faster
* Instead of hitting vectorDB again and again we can maintain cache
* If the same question is asked again, then we don't need to hit vectorDB and LLM
* Helps to maintain consistency (same answer for same question)

**2 Types:**

* In memory - Till the program is running
* Persist cache - We will keep it in some DB
