# Azure Data Fundamentals

## Cloud Concepts
- Cloud computing is the delivery of computing services over the Internet.
- Cloud services categories:
    - Infrastructure as a Service (IaaS)
    - Platform as a Service (PaaS)
    - Software as a Service (SaaS).
- Deployment models:
    - The public cloud is owned by a cloud service organization that sells services to anyone who wants to buy them.
    - The private cloud is a cloud that is set up for the exclusive use of a single organization.
    - The hybrid cloud is a combination of public cloud and private cloud.
    - The community cloud is a cloud that is shared among several organizations that have a common interest.
- Advantages:
    - scalability: adapt to the changing needs of the business.
    - elasticity: adapt to the current workload.
    - agility
    - geographic distribution.
- Pricing models:
    - pay-as-you-go
    - reserved capacity
    - spot
    - subscription (tipically SAAS)
    - tier

## Responsibility Matrix for Cloud Service Categories

| Responsibility          | IaaS                     | PaaS                     | SaaS                     |
|-------------------------|--------------------------|--------------------------|--------------------------|
| Data                    | Customer                 | Customer                 | Customer (sometimes)     |
| Applications            | Customer                 | Customer                 | Cloud Provider           |
| Runtime                 | Customer                 | Cloud Provider           | Cloud Provider           |
| Middleware              | Customer                 | Cloud Provider           | Cloud Provider           |
| Operating System        | Customer                 | Cloud Provider           | Cloud Provider           |
| Virtualization          | Cloud Provider           | Cloud Provider           | Cloud Provider           |
| Servers                 | Cloud Provider           | Cloud Provider           | Cloud Provider           |
| Storage                 | Cloud Provider           | Cloud Provider           | Cloud Provider           |
| Networking              | Cloud Provider           | Cloud Provider           | Cloud Provider           |


## Azure Storage

1. Blob storage

Store large amounts of unstructured object data, such as text or binary data. Container has permissions, files is only a domain name.

Types:
- Block blobs: store text and binary data, up to about 4.7 TB.
- Append blobs: optimized for append operations, such as logging.
- Page blobs: store random access files up to 8 TB.

Tiers:
- Hot: optimized for storing data that is accessed frequently. Hot is the default.
- Cool: optimized for storing data that is infrequently accessed and stored for at least 30 days.
- Archive: optimized for storing data that is rarely accessed and stored for at least 180 days with flexible latency requirements.

2. Data Lake Storage

Store big data. You must enable hierarchical namespace when you create the account. OneLake is built upon Azure Data Lake Gen 2.

3. Azure files

Shares of files. It needs a storage account. You can upload using AZCopy. Two network protocols: Server Message Block (SMB) and Network File System (NFS).

4. Azure Table Storage

NoSQL key-value store. It is good for storing large amounts of non-relational data. Elements: partition key, row key, timestamp, properties.

## Choose an API for Azure Cosmos DB
https://learn.microsoft.com/en-us/azure/cosmos-db/choose-api

## Roles
https://learn.microsoft.com/en-us/training/modules/explore-roles-responsibilities-world-of-data/2-explore-job-roles
