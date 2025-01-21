# DPR

**ML Project:**

1. HLD
2. LLD
3. Architecture
4. Wireframe
5. KPI
6. Pipeline
7. Coding
8. Audit
9. Production
10. Hypercare

&#x20;

**Requirement gathering:**

* Discussion

**Requirement analysis:**

* Whether it is feasible or not

&#x20;

One we decide to go ahead with the project then we start with HLD

&#x20;

**DSA:**

* Data sharing agreement
* Done even before HLD
  * No. of files
  * Mode of data transfer
  * Feature details
  * Language in which data will be transferred

&#x20;

**HLD:**

* Low level micro requirement gathering
* Business understanding
  * Data 🡪 Can be inside some DB or some other storage
    * Understand data and how it relates to the business
* Frequency of data 🡪 Daily, yearly etc
  * Batch – once in a day/week/hour
  * Mini batch – Couple of minutes
  * Streaming – continuous data
* No. of files:
  * Not all the fields will be in same file/db
* Overview/description of dataset fields
* Diagram of complete existing infra
  * From where data will come, db connections, API
* Problem statement
* Proposed solution
* Technical requirements
* Data requirements
* Hardware requirements
* Assumptions

&#x20;

**LLD:**

* Our own architecture
* Get data from different sources
* Then perform data validation

1. File name check
2. Extension check
3. No. of column check
4. Type of feature
5. Name of column
6. Null check

* After all this checks only we will move the data to the next step
* After data validation, it will data transformation

1. Date time transformation
2. Language transformation
3. Categorical transformation

* Data aggregation:

1. We receive data from multiple files and sources
2. Important data for the model
3. Joins/v lookup

* Data pre-processing:
  * Standardization
  * Normalization
  * Dimension reduction
* Decide whether to go for direct ML approach/customized ML approach
  * Direct – directly ML algo can be used
  * Customized – go for clustering, then for each cluster we will build multi model system
* Test the model
* Serve the model
  * Local hardware/cloud/mobile device
* Monitoring
* Model retraining
* Model re deploy

&#x20;

**Architecture:**

* Points to keep in mind while building architecture:

1. Scalability
2. Latency – within 1 sec response should come
   1. Based on latency we select
      1. DB
      2. Cloud platform
      3. API
      4. Monitoring tool
      5. Security tool
3. Frequency
4. Security

* Multiple environments
  * Dev 🡪 UAT 🡪 Prod

**Wireframe:**

* How user will interact

&#x20;

**KPI:**

* Dashboard all analytical information about performance
* What was business end goal will be an KPI

&#x20;

**Pipeline:**

&#x20;

**Coding:**

* After environment setup and all is done then based on HLD and LLD we start coding
* We breakup tasks
* Code merge will be done
* Review done by lead

&#x20;

**MLOps:**

* All of this comes under MLOps

&#x20;

**Hypercare:**

* Some bugs or issue in production

&#x20;

**Conceptual architecture:**

*

    <figure><img src="../../.gitbook/assets/image (515).png" alt=""><figcaption></figcaption></figure>
* E2E SCM for SCM
* There will be lakhs of spare parts
* In which service center which part can be required and accordingly the inventory should be filled
* Data stored in azure blob and SAP
* File watcher will keep watch of new files and once they are available it will pull it from there to here(Using shell script)
* File will be received as SupplierMaster\_DDMMYY\_HHMMSS.csv
* In ingestion we check file name, then file format, date to avoid duplication, etc.
* Data coming in batch mode
* Some files in real time using kafka(like sensor data)
* if get some data from sensors which can indicate issue can come in next few days or period, then we fill the inventory accordingly
* In quality check, check if number of columns are correct, data type is correct, if there are null records or duplicate records
