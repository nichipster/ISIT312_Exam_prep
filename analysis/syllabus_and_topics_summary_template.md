# ISIT312 - Topic-Wise Summary

## ⚠️ PRELIMINARY VERSION
**This summary will be updated with specific content from your lectures once PDF extraction is complete.**

---

## Overview

ISIT312 covers Big Data technologies and Data Warehousing concepts, focusing on:
- Distributed computing and cluster architectures
- MapReduce programming paradigm
- Hadoop ecosystem (HDFS, YARN, Hive, HBase)
- Data Warehousing design and implementation
- Apache Spark for big data processing
- NoSQL databases and streaming data

---

## Topic 1: Cluster Computing

**Summary**: Cluster computing involves connecting multiple computers to work together as a single system, providing increased computational power, storage, and reliability. This foundational concept enables distributed processing of large datasets by dividing work across multiple nodes. Key challenges include data distribution, fault tolerance, and coordination between nodes. Understanding cluster computing is essential as it forms the basis for all big data processing frameworks.

**Key Concepts**:
- Distributed computing architecture
- Horizontal vs vertical scaling
- Shared-nothing architecture
- Network topology in clusters
- Node roles (master/worker)

**Important Terms**:
- **Cluster**: Group of interconnected computers working together
- **Node**: Individual computer in a cluster
- **Scalability**: Ability to handle increased load
- **Fault Tolerance**: System continues operating despite failures
- **Load Balancing**: Distributing work evenly across nodes

---

## Topic 2: MapReduce Framework

**Summary**: MapReduce is a programming model for processing large datasets in parallel across a distributed cluster. It divides computation into two phases: Map (processing and transforming data) and Reduce (aggregating results). The framework automatically handles parallelization, fault tolerance, and data distribution, allowing programmers to focus on business logic. MapReduce is the foundation of Hadoop and inspired many modern big data processing systems.

**Key Concepts**:
- Map function: processes input data into key-value pairs
- Reduce function: aggregates values by key
- Shuffle and sort phase: redistributes data between map and reduce
- Combiner function: local aggregation before reduce
- Execution flow and job scheduling

**Important Terms**:
- **Mapper**: Processes input splits and emits intermediate key-value pairs
- **Reducer**: Aggregates intermediate values by key
- **Shuffle**: Data transfer between map and reduce phases
- **Partition**: Division of map output to reducers
- **Job**: Complete MapReduce program execution

**Key Model**:
```
Input → Split → Map → Shuffle/Sort → Reduce → Output
```

---

## Topic 3: Hadoop Architecture

**Summary**: Hadoop is an open-source framework for distributed storage and processing of big data. Its architecture consists of two main components: HDFS for storage and YARN for resource management and job scheduling. Hadoop provides fault tolerance through data replication, scalability through horizontal scaling, and cost-effectiveness by running on commodity hardware. The ecosystem has expanded to include numerous tools like Hive, HBase, and Spark.

**Key Concepts**:
- HDFS (Hadoop Distributed File System)
- YARN (Yet Another Resource Negotiator)
- Master-slave architecture
- Commodity hardware utilization
- Hadoop ecosystem components

**Components**:
- **NameNode**: Manages HDFS metadata
- **DataNode**: Stores actual data blocks
- **ResourceManager**: Manages cluster resources (YARN)
- **NodeManager**: Manages resources on individual nodes
- **ApplicationMaster**: Coordinates specific job execution

**Architecture Diagram Concepts**:
- Data flow during read/write operations
- Heartbeat communication
- Block replication across racks

---

## Topic 4: HDFS Interfaces

**Summary**: HDFS provides multiple interfaces for interacting with the distributed file system, including command-line tools, Java API, and web interfaces. These interfaces allow users to upload, download, manipulate, and monitor files stored across the cluster. Understanding HDFS operations is crucial for managing big data applications, configuring storage, and troubleshooting issues.

**Key Concepts**:
- Command-line interface (CLI) operations
- Java API for programmatic access
- WebHDFS for REST-based access
- File system operations (read, write, delete, rename)
- Permission management and security

**Important Commands**:
- `hdfs dfs -ls`: List files
- `hdfs dfs -put`: Upload files
- `hdfs dfs -get`: Download files
- `hdfs dfs -cat`: View file contents
- `hdfs dfs -rm`: Delete files

---

## Topic 5: MapReduce Model (Detailed)

**Summary**: The MapReduce model provides a structured approach to parallel data processing with three key phases: Map, Shuffle/Sort, and Reduce. Data locality is optimized by moving computation to data rather than vice versa. The model handles failures automatically through task re-execution and provides progress monitoring. Understanding the detailed execution model is essential for writing efficient MapReduce jobs and debugging performance issues.

**Key Concepts**:
- Input splits and RecordReader
- Data locality optimization
- Speculative execution
- Task failure recovery
- Combiners for local aggregation

**Execution Phases**:
1. Input splitting
2. Map task execution
3. Shuffle and sort
4. Reduce task execution
5. Output writing

**Important Equations/Metrics**:
- Speedup = T₁ / Tₙ (where T₁ is sequential time, Tₙ is parallel time)
- Data locality percentage
- Task completion time

---

## Topic 6: Java MapReduce Application

**Summary**: Java is the native language for writing MapReduce applications in Hadoop. A typical application includes Mapper and Reducer classes extending Hadoop's base classes, a Driver class to configure and submit jobs, and supporting classes for custom data types. Programmers must handle data serialization, configure input/output formats, and optimize for performance. Understanding Java MapReduce is essential for building production big data applications.

**Key Concepts**:
- Mapper class implementation
- Reducer class implementation
- Job configuration and submission
- Custom Writable types
- Input/Output formats

**Code Structure**:
```java
// Mapper class
public class MyMapper extends Mapper<KeyIn, ValueIn, KeyOut, ValueOut> {
    public void map(KeyIn key, ValueIn value, Context context) {
        // Process and emit
    }
}

// Reducer class
public class MyReducer extends Reducer<KeyIn, ValueIn, KeyOut, ValueOut> {
    public void reduce(KeyIn key, Iterable<ValueIn> values, Context context) {
        // Aggregate and emit
    }
}

// Driver class
public class MyJob {
    public static void main(String[] args) {
        // Configure and submit job
    }
}
```

---

## Topic 7: Hive Introduction

**Summary**: Hive is a data warehouse system built on top of Hadoop that provides SQL-like query capabilities for large datasets. It translates HiveQL (Hive Query Language) into MapReduce jobs, making big data accessible to SQL users without requiring MapReduce programming. Hive is ideal for batch processing, data analysis, and reporting but not suitable for real-time queries or transactional operations.

**Key Concepts**:
- HiveQL: SQL-like query language
- Schema-on-read approach
- Metastore for metadata management
- SerDe (Serializer/Deserializer)
- Partitioning and bucketing

**Important Terms**:
- **Metastore**: Database storing Hive metadata
- **External Table**: Data stored outside Hive warehouse
- **Managed Table**: Data managed by Hive
- **Partition**: Subdivision of table data
- **Bucket**: Further subdivision within partitions

---

## Topic 8: Hive Data Structures

**Summary**: Hive organizes data into databases, tables, partitions, and buckets, providing a familiar relational structure over HDFS files. Different file formats (TextFile, SequenceFile, ORC, Parquet) offer various trade-offs between storage efficiency and query performance. Partitioning divides data by specific columns for faster queries, while bucketing enables sampling and efficient joins. Understanding these structures is crucial for designing efficient Hive schemas.

**Key Concepts**:
- Tables (managed vs external)
- Partitions for data organization
- Buckets for data distribution
- File formats and compression
- Complex data types (arrays, maps, structs)

**Data Types**:
- Primitive: INT, STRING, BOOLEAN, FLOAT, DOUBLE
- Complex: ARRAY, MAP, STRUCT, UNION

**File Formats**:
- TextFile: Human-readable, inefficient
- SequenceFile: Binary format
- ORC: Optimized Row Columnar
- Parquet: Columnar storage

---

## Topic 9: Data Warehousing Concepts

**Summary**: Data warehousing involves collecting, storing, and managing data from multiple sources to support business intelligence and decision-making. Unlike operational databases (OLTP), data warehouses are optimized for analytical queries (OLAP). They employ dimensional modeling with fact and dimension tables, support historical data tracking, and enable complex analysis through tools like OLAP cubes. Data warehouses are essential for enterprise analytics and reporting.

**Key Concepts**:
- OLTP vs OLAP
- ETL (Extract, Transform, Load)
- Dimensional modeling
- Star schema and Snowflake schema
- Fact and dimension tables

**Important Terms**:
- **OLTP**: Online Transaction Processing (operational)
- **OLAP**: Online Analytical Processing (analytical)
- **Fact Table**: Stores measurable events
- **Dimension Table**: Stores descriptive attributes
- **ETL**: Process of loading data into warehouse

**OLTP vs OLAP Comparison**:
| Aspect | OLTP | OLAP |
|--------|------|------|
| Purpose | Operations | Analysis |
| Queries | Simple, frequent | Complex, ad-hoc |
| Data | Current | Historical |
| Design | Normalized | Denormalized |

---

## Topic 10: Conceptual Data Warehouse Design

**Summary**: Conceptual DW design focuses on identifying business processes, defining facts and dimensions, and determining granularity without considering implementation details. This phase involves understanding business requirements, selecting measures, identifying dimension attributes, and ensuring the model supports required analyses. A well-designed conceptual model forms the foundation for successful implementation and user adoption.

**Key Concepts**:
- Business process identification
- Fact determination
- Dimension identification
- Granularity selection
- Fact and dimension relationship

**Design Steps**:
1. Identify business process
2. Declare grain (level of detail)
3. Identify dimensions
4. Identify facts/measures

---

## Topic 11: Logical Data Warehouse Design

**Summary**: Logical DW design translates the conceptual model into detailed schemas (star or snowflake), defines relationships, and specifies attributes while remaining independent of physical implementation. This phase includes designing slowly changing dimensions (SCD), defining surrogate keys, handling hierarchies, and ensuring referential integrity. The logical model serves as a blueprint for physical implementation.

**Key Concepts**:
- Star schema design
- Snowflake schema design
- Slowly Changing Dimensions (SCD Types 1, 2, 3)
- Surrogate keys
- Dimension hierarchies

**Schema Types**:
- **Star Schema**: Denormalized, single fact table surrounded by dimensions
- **Snowflake Schema**: Normalized dimensions
- **Fact Constellation**: Multiple fact tables sharing dimensions

**SCD Types**:
- **Type 1**: Overwrite old values
- **Type 2**: Add new row with version/timestamp
- **Type 3**: Add new column for old value

---

## Topic 12: SQL for Data Warehousing

**Summary**: SQL for data warehousing extends standard SQL with OLAP operations like ROLLUP, CUBE, window functions, and materialized views. These features enable complex analytical queries including trend analysis, ranking, running totals, and multi-dimensional aggregations. Mastering DW SQL is essential for effective data analysis and reporting.

**Key Concepts**:
- ROLLUP and CUBE operations
- Window functions
- GROUPING SETS
- Materialized views
- Analytical functions

**OLAP Operations**:
- **Roll-up**: Aggregation up hierarchy
- **Drill-down**: Disaggregation down hierarchy
- **Slice**: Selection on one dimension
- **Dice**: Selection on multiple dimensions
- **Pivot**: Rotate data view

**Key SQL Extensions**:
```sql
-- Window function
SELECT name, salary, 
       AVG(salary) OVER (PARTITION BY dept) as avg_dept_salary
FROM employees;

-- ROLLUP
SELECT year, quarter, SUM(sales)
FROM sales_data
GROUP BY ROLLUP(year, quarter);

-- CUBE
SELECT store, product, SUM(sales)
FROM sales_data
GROUP BY CUBE(store, product);
```

---

## Topic 13: Hive Programming

**Summary**: Advanced Hive programming covers complex queries, performance optimization, user-defined functions (UDFs), and integration with other Hadoop tools. Effective Hive programming requires understanding query execution plans, using appropriate file formats and compression, implementing partitioning strategies, and optimizing joins. These skills are essential for building efficient data pipelines and analytics solutions.

**Key Concepts**:
- Complex HiveQL queries
- JOIN optimizations
- UDF (User Defined Functions)
- Query performance tuning
- Partitioning and bucketing strategies

**Advanced Features**:
- Window functions in Hive
- Lateral views
- Complex data type manipulation
- Streaming with Hive

---

## Topic 14: Physical Data Warehouse Design

**Summary**: Physical DW design involves implementing the logical model with consideration for storage, indexing, partitioning, and performance optimization. This phase includes selecting appropriate data types, creating indexes, defining aggregation tables, and implementing security. Physical design decisions significantly impact query performance, storage costs, and system maintainability.

**Key Concepts**:
- Index design and selection
- Partitioning strategies
- Aggregation tables
- Storage optimization
- Maintenance procedures

**Implementation Considerations**:
- Bitmap indexes for low-cardinality columns
- B-tree indexes for high-cardinality columns
- Horizontal partitioning for large tables
- Vertical partitioning for wide tables
- Compression techniques

---

## Topic 15: HBase Data Model

**Summary**: HBase is a NoSQL, column-oriented database built on HDFS, designed for random, real-time read/write access to big data. Its sparse, distributed, persistent multi-dimensional sorted map stores data as column families, with flexible schema and automatic sharding. HBase is ideal for applications requiring fast lookups and updates on large datasets but not suitable for complex queries or transactional operations.

**Key Concepts**:
- Column-family oriented storage
- Row key design
- Versioning and timestamps
- Cell structure (row key, column family, column qualifier, timestamp, value)
- Region-based partitioning

**Important Terms**:
- **Row Key**: Primary key for data access
- **Column Family**: Group of related columns
- **Column Qualifier**: Specific column within family
- **Cell**: Intersection of row, column, and version
- **Region**: Contiguous set of rows

**Data Model**:
```
Table
  ├── Row Key
  ├── Column Family 1
  │     ├── Column Qualifier 1: Value [timestamp]
  │     └── Column Qualifier 2: Value [timestamp]
  └── Column Family 2
        └── Column Qualifier 1: Value [timestamp]
```

---

## Topic 16: HBase Operations

**Summary**: HBase provides CRUD operations (Create, Read, Update, Delete) through Put, Get, Scan, and Delete commands. These operations can be performed via Java API, shell commands, or REST interface. Understanding efficient row key design, scan strategies, and filter usage is crucial for application performance. HBase supports batch operations and provides consistency at the row level.

**Key Concepts**:
- Put: Insert/update data
- Get: Retrieve specific row
- Scan: Retrieve multiple rows
- Delete: Remove data
- Filters for efficient queries

**Operations**:
```
Put: put 'table', 'rowkey', 'cf:col', 'value'
Get: get 'table', 'rowkey'
Scan: scan 'table', {STARTROW => 'start', ENDROW => 'end'}
Delete: delete 'table', 'rowkey', 'cf:col'
```

**Best Practices**:
- Design row keys for query patterns
- Use appropriate column families
- Implement filters to reduce data transfer
- Batch operations when possible

---

## Topic 17: Spark Introduction

**Summary**: Apache Spark is a fast, unified analytics engine for big data processing, providing in-memory computation that can be 100x faster than MapReduce. Spark supports multiple programming languages (Scala, Python, Java, R) and provides unified APIs for batch processing, SQL queries, machine learning, and graph processing. Its core abstraction, RDD (Resilient Distributed Dataset), enables fault-tolerant parallel operations.

**Key Concepts**:
- RDD (Resilient Distributed Dataset)
- In-memory computation
- Lazy evaluation
- DAG (Directed Acyclic Graph) execution
- Spark vs MapReduce

**Spark Components**:
- **Spark Core**: Basic functionality and RDD API
- **Spark SQL**: Structured data processing
- **Spark Streaming**: Stream processing
- **MLlib**: Machine learning
- **GraphX**: Graph processing

**Advantages over MapReduce**:
- In-memory processing (faster)
- Rich API with high-level operations
- Interactive queries
- Unified platform for multiple workloads

---

## Topic 18: Spark Data Model

**Summary**: Spark's data model centers on RDDs, immutable distributed collections of objects that can be processed in parallel. RDDs support two types of operations: transformations (create new RDDs) and actions (return values). Spark also provides higher-level abstractions like DataFrames and Datasets for structured data processing with optimization through Catalyst query optimizer.

**Key Concepts**:
- RDD characteristics (immutable, distributed, resilient)
- Transformations (lazy execution)
- Actions (trigger execution)
- DataFrames and Datasets
- Persistence and caching

**RDD Operations**:
- **Transformations**: map, filter, flatMap, reduceByKey, groupByKey, join
- **Actions**: collect, count, reduce, take, saveAsTextFile

**Lazy Evaluation**:
- Transformations build execution plan
- Actions trigger computation
- Optimization opportunities

---

## Topic 19: Spark Operations

**Summary**: Spark provides a rich set of transformations and actions for data processing, including map/filter, aggregations, joins, and set operations. Understanding the difference between narrow (no shuffle) and wide (requires shuffle) transformations is crucial for performance. Spark's DAG scheduler optimizes execution by pipelining narrow transformations and efficiently managing shuffles.

**Key Concepts**:
- Narrow vs wide transformations
- Common transformations and actions
- Key-value pair operations
- Shared variables (broadcast, accumulator)
- Performance optimization

**Transformation Types**:
- **Narrow**: map, filter, union (no shuffle, fast)
- **Wide**: reduceByKey, groupByKey, join (shuffle required, slower)

**Common Patterns**:
```python
# Map: Transform each element
rdd.map(lambda x: x * 2)

# Filter: Select elements
rdd.filter(lambda x: x > 10)

# ReduceByKey: Aggregate by key
pairs.reduceByKey(lambda a, b: a + b)

# Join: Combine RDDs
rdd1.join(rdd2)
```

---

## Topic 20: Spark Streaming

**Summary**: Spark Streaming enables scalable, high-throughput, fault-tolerant stream processing by treating streams as continuous series of RDDs (micro-batches). It provides the same APIs as batch processing, allowing code reuse and unified analytics. Spark Streaming supports various sources (Kafka, Flume, TCP) and provides windowing and stateful operations for complex stream processing.

**Key Concepts**:
- DStream (Discretized Stream)
- Micro-batch processing
- Window operations
- Stateful operations
- Input sources and output operations

**Important Terms**:
- **DStream**: Continuous stream of RDDs
- **Window**: Time-based grouping of batches
- **Batch Interval**: Duration of each micro-batch
- **Sliding Interval**: How often window operations execute

**Window Operations**:
```python
# Window of 30 seconds, sliding every 10 seconds
windowed = stream.window(30, 10)

# Count by window
windowCounts = pairs.reduceByKeyAndWindow(lambda a, b: a + b, 30, 10)
```

---

## Summary Statistics

**Total Topics**: 20
**High Priority Topics**: 7-8 (MapReduce, HDFS, DW Design, Hive, Spark)
**Medium Priority Topics**: 6-8 (HBase, SQL for DW, Advanced topics)
**Foundational Topics**: 4-5 (Cluster Computing, Architecture basics)

**Major Categories**:
1. **Big Data Processing**: Lectures 1-6 (MapReduce, Hadoop)
2. **Data Warehousing**: Lectures 9-14 (DW concepts, design, SQL)
3. **Hive**: Lectures 7-8, 13 (Hive data structures and programming)
4. **HBase**: Lectures 15-16 (NoSQL operations)
5. **Spark**: Lectures 17-20 (Processing and streaming)

---

## Next Steps

1. **Run PDF extraction** (see README.md)
2. **Provide extracted content to Claude**
3. **Receive updated summary with**:
   - Specific definitions from YOUR lectures
   - Exact diagrams and examples used
   - Professor's emphasis areas
   - Specific exam question types from sample exam
   - Detailed formulas and equations
   - Code examples from lectures

---

*This template will be replaced with detailed content from your lectures.*
*Status: AWAITING CONTENT EXTRACTION*
*Last Updated: November 2025*
