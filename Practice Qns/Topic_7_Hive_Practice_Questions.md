# Topic 7: Hive - Exam Practice Questions
## ISIT312 Big Data Management - Session SIM S4 2025

**Format**: 5 short answer questions matching actual exam difficulty  
**Total Marks**: 50 marks (10 marks each)  
**Time Allocation**: ~30 minutes  
**Exam Type**: OPEN BOOK

---

## Question 1: Hive Architecture and Query Processing (10 marks)

**a)** Explain the role of the **Metastore** in the Hive architecture. What three types of critical information does it store, and why is this information essential for query execution? (4 marks)

**b)** Describe the process by which Hive translates an HQL query into MapReduce jobs. List the four main stages in order. (4 marks)

**c)** Hive is not suitable for OLTP (Online Transaction Processing) applications. Give two specific technical reasons why. (2 marks)

---

## Question 2: Hive Data Types and Table Design (10 marks)

A social media platform stores user posts with the following requirements:
- Post ID and timestamp
- User name  
- List of hashtags used in the post
- Comments on the post, where each comment has: commenter name, comment text, and comment timestamp
- Total number of likes

**a)** Write a HiveQL `CREATE TABLE` statement that uses appropriate complex data types (ARRAY, STRUCT, MAP) to efficiently model this data. Include the `ROW FORMAT` and `STORED AS` clauses. (6 marks)

**b)** Explain one advantage of using complex data types in this scenario compared to creating multiple normalized tables. (2 marks)

**c)** Write a SELECT statement to access the second hashtag from a post. (2 marks)

---

## Question 3: Partitions, Buckets, and Performance (10 marks)

A retail company stores transaction data in a Hive table with the following columns: transaction_id, customer_id, product_id, amount, payment_method, and transaction_date. The table contains billions of records spanning multiple years.

**a)** Design a partitioning strategy for this table. Write the `CREATE TABLE` statement with appropriate partition columns and justify your choice. (4 marks)

**b)** Explain the difference between partitioning and bucketing in Hive. When would you add bucketing on top of partitioning? (3 marks)

**c)** Write the HQL command to load data into a specific partition (e.g., year=2024, month=11). (3 marks)

---

## Question 4: Internal vs External Tables and Data Management (10 marks)

**a)** Explain the key differences between **internal (managed)** tables and **external** tables in Hive. In your answer, address:
   - How data is managed
   - What happens when the table is dropped
   - Typical use cases for each type (6 marks)

**b)** Given that a data file already exists in HDFS at `/user/data/sales/sales_2024.csv`, write the HQL statements to:
   1. Create an external table pointing to this location
   2. Verify the table was created successfully (4 marks)

---

## Question 5: HiveQL Query Operations and Optimization (10 marks)

Given the following Hive tables:

```sql
CREATE TABLE products (
    product_id INT,
    product_name STRING,
    category STRING,
    price DECIMAL(10,2)
) PARTITIONED BY (supplier_country STRING);

CREATE TABLE sales (
    sale_id INT,
    product_id INT,
    quantity INT,
    sale_date DATE
);
```

**a)** Write an HQL query to find the total revenue (price × quantity) for each product category, showing only categories with total revenue exceeding $100,000. Sort results by revenue in descending order. (5 marks)

**b)** Explain what a **map-side join** is and under what conditions it can be used in Hive. What specific performance benefit does it provide compared to a regular join? (3 marks)

**c)** If the `products` table is small (fits in memory) and `sales` table is large, write the query from part (a) using a hint to enable map-side join. (2 marks)

---

# ANSWER GUIDE

## Question 1 - Model Answer

**a) Metastore role (4 marks):**

The Metastore is a relational database that stores metadata about Hive tables. Three critical types of information:

1. **Table-to-HDFS mappings** (1 mark): Stores the directory locations in HDFS where table data is physically stored, enabling Hive to locate data files.

2. **Schema information** (1 mark): Contains column names, data types, table properties, and partition definitions that define the logical structure of tables.

3. **SerDe and file formats** (1.5 marks): Stores Serialization/Deserialization functions and input/output formats (e.g., CSV, ORC, Parquet) used to extract records and fields from files.

**Why essential** (0.5 marks): This metadata allows Hive to interpret unstructured HDFS files as structured tables and execute queries correctly.

**b) Query translation stages (4 marks - 1 mark each):**

1. **Parser**: Converts HQL statement into an Abstract Syntax Tree (AST)
2. **Semantic Analyzer**: Validates the query against schema in Metastore and checks for semantic correctness
3. **Logical Plan Generator**: Creates a logical operator tree representing the query operations
4. **Physical Plan Generator**: Translates logical plan into MapReduce jobs that execute on Hadoop

**c) Not suitable for OLTP (2 marks - 1 mark each):**

1. **High latency**: Hive queries take seconds to minutes (not milliseconds) because each query requires MapReduce job initialization and execution
2. **No row-level updates/transactions**: Hive uses an append-only architecture without traditional ACID transactions or fine-grained updates/deletes

---

## Question 2 - Model Answer

**a) CREATE TABLE statement (6 marks):**

```sql
CREATE TABLE IF NOT EXISTS social_posts (
    post_id STRING,
    post_timestamp TIMESTAMP,
    user_name STRING,
    hashtags ARRAY<STRING>,
    comments ARRAY<STRUCT<
        commenter_name: STRING,
        comment_text: STRING,
        comment_timestamp: TIMESTAMP
    >>,
    total_likes INT
)
ROW FORMAT DELIMITED
FIELDS TERMINATED BY '|'
COLLECTION ITEMS TERMINATED BY ','
MAP KEYS TERMINATED BY ':'
STORED AS ORC;
```

**Marking breakdown:**
- Table structure and column names (1 mark)
- ARRAY for hashtags (1 mark)
- ARRAY<STRUCT<...>> for comments with correct fields (2 marks)
- ROW FORMAT DELIMITED clause (1 mark)
- STORED AS clause with appropriate format (1 mark)

**b) Advantage of complex data types (2 marks):**

Using complex data types keeps related data in a single row, eliminating the need for JOIN operations (1 mark). This reduces disk I/O, maintains data locality, and improves query performance since all information about a post is stored together (1 mark).

**c) Access second hashtag (2 marks):**

```sql
SELECT hashtags[1]
FROM social_posts
WHERE post_id = 'specific_post_id';
```

Note: Array indexing is 0-based (1 mark), so index [1] accesses the second element (1 mark).

---

## Question 3 - Model Answer

**a) Partitioning strategy (4 marks):**

```sql
CREATE TABLE IF NOT EXISTS transactions (
    transaction_id STRING,
    customer_id INT,
    product_id INT,
    amount DECIMAL(10,2),
    payment_method STRING
)
PARTITIONED BY (year INT, month INT)
ROW FORMAT DELIMITED
FIELDS TERMINATED BY ','
STORED AS PARQUET;
```

**Justification** (2 marks):
- Partition by year and month (date components) because queries typically filter by time periods (1 mark)
- This eliminates scanning billions of records for time-based queries and creates manageable partition sizes (1 mark)
- Two-level partitioning provides flexibility for both annual and monthly analysis

**b) Partitioning vs Bucketing (3 marks):**

**Partitioning** (1 mark): Divides data into separate HDFS subdirectories based on column values. Each unique partition value creates a new directory. Reduces data scanned during queries with partition filters.

**Bucketing** (1 mark): Uses hash function to distribute data into a fixed number of files within partitions. Creates evenly distributed data segments regardless of value distribution.

**When to add bucketing** (1 mark): Use bucketing when you need efficient sampling, or when joining tables on the bucketed column (bucket map join). Also useful for evenly distributing data when partition column has skewed values.

**c) Load data into partition (3 marks):**

```sql
INSERT INTO TABLE transactions 
PARTITION(year=2024, month=11)
SELECT transaction_id, customer_id, product_id, amount, payment_method
FROM staging_transactions
WHERE YEAR(transaction_date) = 2024 
  AND MONTH(transaction_date) = 11;
```

**Alternative with LOAD DATA:**
```sql
LOAD DATA LOCAL INPATH '/local/path/transactions_2024_11.csv'
INTO TABLE transactions
PARTITION(year=2024, month=11);
```

**Marking**: 1 mark for INSERT/LOAD syntax, 1 mark for PARTITION clause with correct values, 1 mark for source query/path.

---

## Question 4 - Model Answer

**a) Internal vs External tables (6 marks):**

**Internal (Managed) Tables:**
- **Data management** (1 mark): Hive fully controls the data lifecycle. Data is stored in Hive's warehouse directory (default: `/user/hive/warehouse/`).
- **Drop behavior** (1 mark): When dropped, both metadata AND data are permanently deleted from HDFS.
- **Use case** (1 mark): Use when Hive is the sole owner of the data, for temporary or intermediate results, or when you want automatic cleanup.

**External Tables:**
- **Data management** (1 mark): User manages the data independently. Data can exist anywhere in HDFS at a user-specified location.
- **Drop behavior** (1 mark): When dropped, only metadata is removed; the actual data remains in HDFS.
- **Use case** (1 mark): Use when data is shared across multiple systems/tools, for archival data, or when you want to preserve data after table removal.

**b) Create external table (4 marks):**

```sql
-- 1. Create external table (3 marks)
CREATE EXTERNAL TABLE IF NOT EXISTS sales_2024 (
    sale_id INT,
    customer_id INT,
    product_id INT,
    amount DECIMAL(10,2),
    sale_date DATE
)
ROW FORMAT DELIMITED
FIELDS TERMINATED BY ','
STORED AS TEXTFILE
LOCATION '/user/data/sales';

-- 2. Verify table created (1 mark)
DESCRIBE FORMATTED sales_2024;
-- OR
SHOW TABLES;
```

**Marking**: 
- EXTERNAL keyword (1 mark)
- Table structure (1 mark)
- LOCATION clause pointing to existing path (1 mark)
- Verification command (1 mark)

---

## Question 5 - Model Answer

**a) HQL query (5 marks):**

```sql
SELECT p.category, 
       SUM(p.price * s.quantity) AS total_revenue
FROM products p
JOIN sales s ON p.product_id = s.product_id
GROUP BY p.category
HAVING SUM(p.price * s.quantity) > 100000
ORDER BY total_revenue DESC;
```

**Marking breakdown:**
- Correct JOIN syntax between tables (1 mark)
- Revenue calculation (price × quantity) with SUM (1.5 marks)
- GROUP BY category (1 mark)
- HAVING clause with correct threshold (1 mark)
- ORDER BY descending (0.5 marks)

**b) Map-side join explanation (3 marks):**

A map-side join is performed entirely during the map phase without requiring a reduce phase (1 mark).

**Conditions** (1 mark):
- One table must be small enough to fit in memory
- Set `hive.auto.convert.join=true` or use `/*+ MAPJOIN(small_table) */` hint

**Performance benefit** (1 mark): Eliminates the shuffle and reduce phases, significantly reducing execution time and network I/O since data doesn't need to be redistributed across reducers.

**c) Query with map-side join hint (2 marks):**

```sql
SELECT /*+ MAPJOIN(products) */ p.category, 
       SUM(p.price * s.quantity) AS total_revenue
FROM products p
JOIN sales s ON p.product_id = s.product_id
GROUP BY p.category
HAVING SUM(p.price * s.quantity) > 100000
ORDER BY total_revenue DESC;
```

**Marking**: 
- Correct hint syntax `/*+ MAPJOIN(products) */` (1 mark)
- Hint placed correctly (after SELECT) and small table specified (1 mark)

---

# KEY CONCEPTS TO REMEMBER FOR EXAM

## Architecture Essentials
1. **Metastore = Relational DB** storing metadata (Derby default, MySQL/PostgreSQL for production)
2. **Hive Client** translates HQL → MapReduce jobs
3. **Query flow**: Parser → Semantic Analyzer → Logical Plan → Physical Plan (MapReduce)
4. **Schema-on-read**: Data interpreted at query time, not write time

## Critical Data Types
- **Primitive**: TINYINT, SMALLINT, INT, BIGINT, FLOAT, DOUBLE, DECIMAL, STRING, VARCHAR, CHAR, BOOLEAN, DATE, TIMESTAMP, BINARY
- **Complex**: 
  - ARRAY<type> - access with [index]
  - MAP<key_type, value_type> - access with ['key']
  - STRUCT<field:type, ...> - access with .field_name

## Table Types
| Feature | Internal (Managed) | External |
|---------|-------------------|----------|
| Keyword | None (default) | EXTERNAL |
| Data location | Warehouse directory | User-specified LOCATION |
| DROP behavior | Deletes data | Preserves data |
| Use case | Hive owns data | Shared/archived data |

## Performance Optimization

### Partitioning
```sql
PARTITIONED BY (year INT, month INT)
```
- Creates subdirectories in HDFS
- Eliminates full table scans
- Use for commonly filtered columns (time, geography)

### Bucketing
```sql
CLUSTERED BY (customer_id) INTO 10 BUCKETS
```
- Hash-based distribution into fixed number of files
- Enables efficient sampling and bucket map joins
- Use with `SET hive.enforce.bucketing = true;`

### Join Optimization
- **Regular Join**: Reduce-side join (shuffle required)
- **Map Join**: `/*+ MAPJOIN(small_table) */` - no reduce phase
- **Bucket Map Join**: Only fetches required buckets
- **Rule**: Put largest table last (STREAMTABLE hint)

## Important HQL Syntax

### File Format Options
```sql
STORED AS TEXTFILE    -- Default, human-readable
STORED AS ORC         -- Optimized Row Columnar (best compression)
STORED AS PARQUET     -- Columnar format (good for analytics)
STORED AS AVRO        -- Row-based with schema evolution
```

### Row Format
```sql
ROW FORMAT DELIMITED
FIELDS TERMINATED BY ','
COLLECTION ITEMS TERMINATED BY ';'
MAP KEYS TERMINATED BY ':'
LINES TERMINATED BY '\n'
```

### Loading Data
```sql
-- From local file system
LOAD DATA LOCAL INPATH 'file.csv' INTO TABLE table_name;

-- From HDFS
LOAD DATA INPATH '/hdfs/path/file.csv' INTO TABLE table_name;

-- Insert from query
INSERT INTO TABLE table_name PARTITION(year=2024)
SELECT * FROM source_table WHERE condition;
```

## Hive vs RDBMS - Key Differences

| Aspect | Hive | RDBMS |
|--------|------|-------|
| Purpose | Batch analytics | OLTP transactions |
| Latency | Seconds/minutes | Milliseconds |
| Updates | Partition-level | Row-level |
| Transactions | Limited ACID | Full ACID |
| Constraints | No enforcement | PK/FK enforced |
| Schema | Schema-on-read | Schema-on-write |
| Data format | Files (flexible) | Proprietary |

## Common Exam Traps
1. ⚠️ Array indexing is **0-based**: `array_col[0]` is first element
2. ⚠️ PARTITION columns are NOT in main column list
3. ⚠️ DROP on internal table = **data deleted**; external = data preserved
4. ⚠️ Hive has **no transactions** in traditional sense (pre-Hive 3)
5. ⚠️ Use `STORED AS ORC` for best performance (not TEXTFILE)
6. ⚠️ Map-side join requires small table to **fit in memory**
7. ⚠️ Partition columns should have **low cardinality** (not unique values)

## Quick Command Reference

```sql
-- Database operations
CREATE DATABASE db_name;
USE db_name;
SHOW DATABASES;
DROP DATABASE db_name;

-- Table operations
SHOW TABLES;
DESCRIBE table_name;
DESCRIBE FORMATTED table_name;  -- Detailed info
SHOW PARTITIONS table_name;

-- Partition operations
ALTER TABLE table_name ADD PARTITION(year=2024);
ALTER TABLE table_name DROP PARTITION(year=2024);

-- View operations
CREATE VIEW view_name AS SELECT ...;
DROP VIEW view_name;
```

---

## Study Strategy for Hive Questions

1. **Understand architecture first**: Metastore role, query translation process
2. **Master complex data types**: Practice ARRAY, STRUCT, MAP syntax
3. **Know table differences**: Internal vs External by heart
4. **Partition/Bucket patterns**: When to use each, how to create
5. **Join optimization**: Map-side join conditions and benefits
6. **Practice HQL syntax**: CREATE TABLE, LOAD DATA, SELECT with GROUP BY/HAVING
7. **File formats**: Know ORC, Parquet advantages for analytics

**Time allocation for Hive in exam**: 8-10 minutes per question (if worth 8-10 marks)

**Hive priority**: TIER 1 - HIGH (appears frequently, 20-30% exam weight)
