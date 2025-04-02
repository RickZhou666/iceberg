# iceberg
practice of iceberg

# 1. Introduction to Apache Iceberg:

1. Understand what Apache Iceberg is and its use cases.
2. Learn about the problems Iceberg solves in data lakes.
3. Explore the history and development of Apache Iceberg.
4. Review case studies and real-world applications of Iceberg.

# 2. Table Format:

1. Study the Iceberg table format and its components (manifests, snapshots, metadata).
2. Learn how Iceberg tables are structured and how they differ from traditional table formats.
3. Examine the benefits of Iceberg's table format in terms of performance and scalability.
4. Compare Iceberg's table format with other modern table formats like Delta Lake and Hudi.

# 3. Schema Evolution:

1. Understand how Iceberg handles schema evolution without requiring table rewrites.
2. Learn about adding, dropping, renaming, and updating columns.
3. Explore the impact of schema changes on existing data and queries.
4. Review best practices for managing schema evolution in Iceberg.

# 4. Partitioning:

1. Study Iceberg's approach to partitioning and how it differs from traditional Hive-style partitioning.
2. Learn about hidden partitioning and how to define partition specs.
3. Understand the performance implications of different partitioning strategies.
4. Explore examples of partitioning schemes for common use cases.

# 5. Time Travel:

1. Understand how Iceberg supports time travel queries.
2. Learn how to query historical data and rollback to previous snapshots.
3. Explore the use cases for time travel in data analysis and debugging.
4. Review the limitations and considerations when using time travel in Iceberg.

# 6. Data Compaction:

1. Study the techniques Iceberg uses for data compaction and optimizing storage.
2. Learn about the maintenance operations like expiring snapshots and removing orphan files.
3. Understand the impact of data compaction on query performance.
4. Explore tools and utilities for automating data compaction in Iceberg.

# 7. Integration with Query Engines:

1. Learn how Iceberg integrates with various query engines like Apache Spark, Trino, Flink, and Hive.
2. Study the configuration and usage of Iceberg with these engines.
3. Explore the performance considerations when using Iceberg with different query engines.
4. Review examples of integrating Iceberg with popular data processing frameworks.

# 8. Performance Tuning:

1. Understand the performance tuning options available in Iceberg.
2. Learn about optimizing read and write performance.
3. Explore the impact of different storage formats on Iceberg's performance.
4. Review best practices for monitoring and tuning Iceberg performance.

# 9. Security and Access Control:

1. Study how Iceberg handles security and access control.
2. Learn about integrating Iceberg with data governance tools.
3. Understand the role of encryption and authentication in Iceberg.
4. Explore examples of implementing security policies in Iceberg.

# 10. APIs and Tools:

1. Familiarize yourself with the Iceberg API and its key operations.
2. Learn about the tools and utilities provided by Iceberg for table management.
3. Explore the use of Iceberg's API for custom data processing workflows.
4. Review examples of extending Iceberg with custom plugins and tools.

# 11. Community and Contributions:

1. Engage with the Iceberg community through mailing lists, forums, and GitHub.
2. Learn how to contribute to the Iceberg project.
3. Explore the roadmap and future developments of Apache Iceberg.
4. Review the process for submitting patches and participating in code reviews.

<br><br><br>


# [Udemy Course](https://www.udemy.com/course/getting-started-apache-iceberg/learn/lecture/45702165#overview)


# 1. intro

<img src="./img/Xnip2025-03-19_21-34-08.jpg" width="50%" />

Iceberg spec: https://iceberg.apache.org/spec/

Iceberg documentation: https://iceberg.apache.org/docs/nightly/

<br><br><br>

# 2. what is iceberg used for?

1. what is data warehouses?

<img src="./img/Xnip2025-03-19_21-42-37.jpg" width="50%" />


- Introduction to Data Warehouses
    - Definition and role as a centralized repository optimized for analytics and business intelligence.

-  Centralization and Organization
    - Goal of having a well-maintained, organized, and centralized data warehouse that stores most of
an organization’s data.

- Challenges with Structuring Data
    - The complex, messy task of structuring data to fit within a warehouse.
    - Issues arising from the ETL process: data duplication, delays in data availability, and reduced operational flexibility.

- Maintenance Costs and Challenges
    - Ongoing, expensive, and labor-intensive efforts required to maintain a data warehouse.
    - Consequences of inadequate maintenance: reduced data accessibility or a completely ineffective system.

- Evolving Needs and Limitations
    - Persistent challenges with cost, scalability, and maintenance that prompt the need for innovative solutions like Iceberg.


<br><br>

2. what is data lake?

<img src="./img/Xnip2025-03-19_22-32-43.jpg" width="50%" />


- the Concept of a Data Lake
    - Explanation of data lakes storing data in its native format, avoiding rigorous structuring and massive ETL workloads.
    - Highlight the cost reduction and simplification of the data management stack.

- Advantages and Simplification
    - Discussion of the operational streamlining promised by data lakes.
    - Transition: While appealing, this simplicity introduces significant challenges.

- Challenges of Data Lakes
    - Detailed look at the complexities of extracting information from unstructured data.
    - Impact on data scientists and analysts due to advanced requirements for data querying and management.
    - The evolution of data management challenges over time, leading to potential inefficiencies and data
bogs.

- A Thoughtful Consideration
    - Introduction to the idea of hybrid solutions like data lakehouses.
    - A proposed solution that blends the flexibility of data lakes with the structured benefits of data
warehouses.

<br><br>

3. Exploring data lakehouses
    - <img src="./img/Xnip2025-03-31_22-33-35.jpg" width="50%" />
    - <img src="./img/Xnip2025-03-31_22-37-38.jpg" width="50%" />

<br><br>

4. iceberg table format
    - <img src="./img/Xnip2025-03-31_22-39-48.jpg" width="50%" />
    - <img src="./img/Xnip2025-03-31_22-41-11.jpg" width="50%" />

    - apache iceberg explained
        - <img src="./img/Xnip2025-03-31_22-42-50.jpg" width="50%" />
        - <img src="./img/Xnip2025-03-31_22-44-46.jpg" width="50%" />




<br><br><br>

# 3. Apache Iceberg Technical Architecture

1. Understanding Apache Iceberg Core Concepts
    - <img src="./img/Xnip2025-04-01_21-43-33.jpg" width="50%" />


2. Iceberg Architecture
    - Catalog
        - point to table current metadata file
        - any add, delete modify to the data, write a new metadata file
        - update pointer to new metadata file
    - <img src="./img/Xnip2025-04-01_21-57-31.jpg" width="50%" />


3. Iceberg key benefits
    - ensure the data integrity
    - <img src="./img/Xnip2025-04-01_22-07-04.jpg" width="50%" />


4. Apache Iceberg Demonstration
```bash
CREATE TABLE aircraft (
    tail_number varchart(15),
    description varchart(150),
    class varchar(50),
    year integer
) WITH (
    type = 'iceberg'
)
```
- <img src="./img/Xnip2025-04-01_22-11-43.jpg" width="50%" />

    - Iceberg structure
        - after table creation
            - <img src="./img/Xnip2025-04-01_22-14-55.jpg" width="50%" />
        - metadata folder
            - <img src="./img/Xnip2025-04-01_22-15-43.jpg" width="50%" />
        - json file - metadata snapshot file, avro file - manifest list file
            - <img src="./img/Xnip2025-04-01_22-18-20.jpg" width="50%" />


5. Inserting records into iceberg table
```bash
INSERT INTO 
    aircraft (tail_number, description, class, year)
VALUES
    ('N12345', 'Boeing 737-800', 'Economy', 2010),
    ('N12346', 'Boeing 737-800', 'Jet', 1983),    
```
- <img src="./img/Xnip2025-04-01_22-29-51.jpg" width="50%" />
- data generated
    - <img src="./img/Xnip2025-04-01_22-37-04.jpg" width="50%" />
- metadata file updated
    - <img src="./img/Xnip2025-04-01_22-35-36.jpg" width="50%" />


6. Apache Iceberg Integration and Compatibility
    - <img src="./img/Xnip2025-04-01_22-39-38.jpg" width="50%" />
    - <img src="./img/Xnip2025-04-01_22-43-15.jpg" width="50%" />


7. Data Lake Compatibility
    - <img src="./img/Xnip2025-04-01_22-47-30.jpg" width="50%" />


- ACID
    - Atomicity, A transaction is treated as a single, indivisible unit of work. Either all operations within the transaction succeed, or none of them do, ensuring that the database remains in a consistent state. 
    - Consistency, Transactions must bring the database from one valid state to another, maintaining data integrity and adhering to predefined rules and constraints. 
    - Isolation, Concurrent transactions should appear to execute independently of each other, as if they were running sequentially, preventing interference and ensuring data accuracy. 
    - Durability, Once a transaction is committed, its changes are permanently stored and will persist even in the event of system failures or crashes. 



