# ISIT312 Big Data Management - Exam-Focused Cramming Plan

**Course**: ISIT312 Big Data Management  
**Session**: SIM S4 2025  
**Lecturer**: Dr Fenghui Ren  
**Exam Date**: TBC  

---

## 📋 EXAM FORMAT CRITICAL INFORMATION

### Exam Structure
- **Duration**: 3 hours
- **Format**: Face-to-face, Closed-book
- **Total Marks**: 50 marks
- **Questions**: 6 short answer questions
- **No Multiple Choice Questions**
- **No Java Programming Questions**
- **Cheat Sheet Provided**: HDFS, HQL, HBase, and Spark examples will be provided

### ⚠️ CRITICAL: 40% Threshold Failure Clause
**You MUST score at least 40% (20/50 marks) on the final exam to pass the subject, regardless of your assignment performance.**

---

## 📚 EXAM CONTENT COVERAGE

Based on the Subject Review (Lecture 21), the exam covers these specific areas:

1. **Hadoop Architecture** (HDFS, YARN, MapReduce layers)
2. **MapReduce Model** (read → map → shuffle → sort → reduce)
3. **Basic Hadoop HDFS commands**
4. **Hive concept, structure**
5. **Basic HQL commands**
6. **Data Warehouse concept and design**
7. **Multidimensional data model**
8. **Relational data model**
9. **HBase model** (basic commands)
10. **Spark concept, data model, and operations** (basic commands)

---

## 🎯 TOPIC PRIORITY MATRIX

### 🔴 CRITICAL PRIORITY (Must Master - 70% of Exam Weight)

#### 1. MapReduce Model ⭐⭐⭐⭐⭐
**Exam Weightage**: 15-20%  
**Difficulty**: Medium  
**Study Time**: 5-6 hours  

**Why Critical**:
- Core concept tested extensively
- Understanding required for Hive and Spark
- Execution flow appears in every variant

**Must Know**:
- [ ] 5 phases: Read → Map → Shuffle → Sort → Reduce
- [ ] Key-value pair model
- [ ] Map function purpose and examples
- [ ] Reduce function purpose and examples
- [ ] Shuffle and sort phase (the "magic")
- [ ] Combiner function (optional optimization)
- [ ] Data locality concept
- [ ] Partition function
- [ ] WordCount example (by heart!)
- [ ] Map-Only jobs
- [ ] Narrow vs wide transformations

**Key Example to Memorize**:
```
Input: "Hello World Hello"
Map Output: (Hello, 1), (World, 1), (Hello, 1)
After Shuffle & Sort: (Hello, [1,1]), (World, [1])
Reduce Output: (Hello, 2), (World, 1)
```

---

#### 2. Data Warehousing Concepts & Design ⭐⭐⭐⭐⭐
**Exam Weightage**: 15-20%  
**Difficulty**: Medium-High  
**Study Time**: 5-6 hours  

**Why Critical**:
- Both conceptual and practical questions likely
- Schema design questions common
- OLAP operations frequently tested

**Must Know**:
- [ ] OLTP vs OLAP (complete comparison table)
- [ ] Multidimensional model components
- [ ] Fact vs Dimension tables
- [ ] Star schema vs Snowflake schema
- [ ] Measures: Additive, Semi-additive, Non-additive
- [ ] Dimension hierarchies
- [ ] OLAP operations: Roll-up, Drill-down, Slice, Dice, Pivot
- [ ] Grain declaration (most critical design step)
- [ ] Four-step design methodology
- [ ] SCD Types 1, 2, 3
- [ ] Surrogate keys

**Key Example to Memorize**:
```
Star Schema Example - Retail Sales:
Fact Table: Sales_Fact
  - date_key (FK)
  - product_key (FK)
  - store_key (FK)
  - customer_key (FK)
  - quantity (measure)
  - amount (measure)

Dimension Tables:
  - Date_Dim: date_key, day, month, quarter, year
  - Product_Dim: product_key, name, category, subcategory
  - Store_Dim: store_key, store_name, city, region, country
  - Customer_Dim: customer_key, name, city, segment
```

---

#### 3. HDFS Architecture & Commands ⭐⭐⭐⭐⭐
**Exam Weightage**: 12-15%  
**Difficulty**: Low-Medium  
**Study Time**: 4-5 hours  

**Why Critical**:
- Foundation of entire Hadoop ecosystem
- Commands frequently tested (cheat sheet provided but understand them!)
- Architecture diagrams may be required

**Must Know**:
- [ ] NameNode role and functions
- [ ] DataNode role and functions
- [ ] Secondary NameNode purpose
- [ ] Block size (128MB default)
- [ ] Replication factor (3 default)
- [ ] Read operation flow (6 steps)
- [ ] Write operation flow (7 steps)
- [ ] Virtual filesystem concept
- [ ] Common HDFS commands (even with cheat sheet, know when to use what)

**Commands to Know** (Even with cheat sheet):
```bash
hadoop fs -mkdir /user/bigdata
hadoop fs -ls /user/bigdata
hadoop fs -put localfile.txt /user/bigdata/
hadoop fs -cat /user/bigdata/file.txt
hadoop fs -get /user/bigdata/file.txt ./
hadoop fs -rm /user/bigdata/file.txt
hadoop fs -rm -r /user/bigdata/directory
```

---

#### 4. Hive Structure & HiveQL ⭐⭐⭐⭐⭐
**Exam Weightage**: 15-18%  
**Difficulty**: Medium  
**Study Time**: 5-6 hours  

**Why Critical**:
- Practical HQL queries likely
- Cheat sheet provided but must understand concepts
- Integration of multiple concepts

**Must Know**:
- [ ] Hive architecture (client, metastore, driver, execution engine)
- [ ] Metastore purpose and contents
- [ ] Managed vs External tables
- [ ] Partitioning concept and syntax
- [ ] Bucketing concept and syntax
- [ ] File formats (TextFile, ORC, Parquet)
- [ ] Basic HQL syntax (CREATE, SELECT, INSERT, LOAD)
- [ ] JOIN operations in HQL
- [ ] Hive vs RDBMS differences
- [ ] Schema-on-read concept

**Key Queries to Practice**:
```sql
-- Create partitioned table
CREATE TABLE sales (product STRING, amount DOUBLE)
PARTITIONED BY (year INT, month INT)
STORED AS ORC;

-- Load data
LOAD DATA LOCAL INPATH '/path/to/file' INTO TABLE sales PARTITION (year=2023, month=12);

-- Query
SELECT year, month, product, SUM(amount) 
FROM sales 
WHERE year = 2023 
GROUP BY year, month, product;

-- Join
SELECT s.product, s.amount, p.category
FROM sales s
JOIN products p ON s.product_id = p.product_id;
```

---

#### 5. Spark Data Model & Operations ⭐⭐⭐⭐
**Exam Weightage**: 12-15%  
**Difficulty**: Medium-High  
**Study Time**: 5-6 hours  

**Why Critical**:
- Modern framework replacing MapReduce
- Transformations vs Actions distinction crucial
- Cheat sheet provided for syntax

**Must Know**:
- [ ] RDD concept (Resilient Distributed Dataset)
- [ ] Transformations (lazy) vs Actions (eager)
- [ ] Narrow vs Wide transformations
- [ ] Common transformations: map, filter, flatMap, reduceByKey, groupByKey
- [ ] Common actions: collect, count, reduce, take, saveAsTextFile
- [ ] Lazy evaluation and DAG
- [ ] In-memory processing advantage
- [ ] Spark vs MapReduce comparison
- [ ] Persistence/Caching
- [ ] Basic Spark Streaming (DStream concept)

**Key Operations to Memorize**:
```python
# Transformations (lazy)
rdd.map(lambda x: x * 2)
rdd.filter(lambda x: x > 10)
rdd.flatMap(lambda x: x.split())
pairs.reduceByKey(lambda a,b: a+b)
pairs.groupByKey()

# Actions (trigger execution)
rdd.collect()
rdd.count()
rdd.reduce(lambda a,b: a+b)
rdd.take(5)
rdd.saveAsTextFile("output")
```

---

### 🟡 MEDIUM PRIORITY (Important - 25% of Exam Weight)

#### 6. HBase Data Model & Operations ⭐⭐⭐⭐
**Exam Weightage**: 10-12%  
**Difficulty**: Medium  
**Study Time**: 3-4 hours  

**Must Know**:
- [ ] Column-family oriented structure
- [ ] Row key design importance
- [ ] Cell structure: (row, CF, qualifier, timestamp, value)
- [ ] Versioning concept
- [ ] Basic operations: Put, Get, Scan, Delete
- [ ] HBase vs RDBMS differences
- [ ] When to use HBase

**Key Commands** (With cheat sheet):
```ruby
# Create table
create 'users', 'info', 'address'

# Put data
put 'users', 'user001', 'info:name', 'John Doe'

# Get data
get 'users', 'user001'

# Scan
scan 'users', {STARTROW => 'user001', STOPROW => 'user999'}

# Delete
delete 'users', 'user001', 'info:name'
```

---

#### 7. Hadoop YARN Architecture ⭐⭐⭐
**Exam Weightage**: 8-10%  
**Difficulty**: Medium  
**Study Time**: 3-4 hours  

**Must Know**:
- [ ] YARN components: ResourceManager, NodeManager, ApplicationMaster, Container
- [ ] Job submission flow
- [ ] Resource allocation process
- [ ] Difference between YARN and MapReduce v1

---

#### 8. SQL for Data Warehousing ⭐⭐⭐
**Exam Weightage**: 8-10%  
**Difficulty**: Medium-High  
**Study Time**: 3-4 hours  

**Must Know**:
- [ ] ROLLUP operation
- [ ] CUBE operation
- [ ] GROUPING SETS
- [ ] Window functions basics
- [ ] Materialized views concept

**Key Operations**:
```sql
-- ROLLUP (hierarchical subtotals)
SELECT year, quarter, SUM(sales)
FROM sales
GROUP BY ROLLUP(year, quarter);

-- CUBE (all combinations)
SELECT store, product, SUM(sales)
FROM sales
GROUP BY CUBE(store, product);

-- Window function
SELECT product, sales,
       SUM(sales) OVER (PARTITION BY product ORDER BY date) AS running_total
FROM sales;
```

---

### 🟢 FOUNDATIONAL PRIORITY (Good to Know - 5% of Exam Weight)

#### 9. Cluster Computing Concepts ⭐⭐
**Exam Weightage**: 3-5%  
**Difficulty**: Low  
**Study Time**: 1-2 hours  

**Must Know**:
- [ ] Cluster definition
- [ ] Master-slave architecture
- [ ] Horizontal vs vertical scaling
- [ ] Commodity hardware concept
- [ ] 3Vs of Big Data

---

#### 10. Physical DW Design ⭐⭐
**Exam Weightage**: 2-4%  
**Difficulty**: Low  
**Study Time**: 1-2 hours  

**Must Know**:
- [ ] Partitioning strategies
- [ ] Indexing (bitmap vs B-tree)
- [ ] Aggregation tables purpose

---

## 📅 STUDY SCHEDULES

### 🚀 INTENSIVE PLAN (3-4 Days Before Exam)

**Prerequisites**: Attend all lectures, complete assignments, have basic understanding

**Day 1: Big Data Fundamentals & MapReduce (10-12 hours)**

*Morning (4 hours): MapReduce Deep Dive*
- ⏰ Hour 1-2: Read MapReduce topic summary
  - Take notes on 5 phases
  - Draw execution flow diagram
  - Memorize WordCount example
- ⏰ Hour 3-4: Practice MapReduce problems
  - Work through 3-5 example problems
  - Trace execution for each
  - Identify Map and Reduce functions

*Afternoon (3-4 hours): HDFS & Hadoop Architecture*
- ⏰ Hour 5-6: HDFS Architecture
  - Draw NameNode/DataNode diagram
  - Memorize block size, replication factor
  - Learn read/write flows
- ⏰ Hour 7-8: HDFS Commands Practice
  - Practice all common commands
  - Understand when to use each
  - Create command cheat notes

*Evening (3-4 hours): Revision & Practice*
- ⏰ Review everything from today
- ⏰ Create summary flashcards
- ⏰ Practice explaining concepts out loud
- ⏰ Do self-test quiz

**Day 2: Data Warehousing & Hive (10-12 hours)**

*Morning (4-5 hours): Data Warehousing Concepts*
- ⏰ Hour 1-2: OLTP vs OLAP, Multidimensional Model
  - Create comparison table
  - Understand dimensions and facts
  - Learn OLAP operations
- ⏰ Hour 3-4: Schema Design
  - Star vs Snowflake differences
  - Practice designing schemas
  - SCD Types 1, 2, 3
- ⏰ Hour 5: Design Methodology
  - Four-step process
  - Practice grain declaration

*Afternoon (3-4 hours): Hive*
- ⏰ Hour 6-7: Hive Architecture & Structure
  - Metastore concept
  - Managed vs External tables
  - Partitioning and bucketing
- ⏰ Hour 8-9: HiveQL Practice
  - Write CREATE TABLE statements
  - Practice SELECT, JOIN queries
  - Work through 5-10 HQL examples

*Evening (3-4 hours): SQL for DW*
- ⏰ ROLLUP and CUBE operations
- ⏰ Window functions basics
- ⏰ Practice queries
- ⏰ Review Day 2 content

**Day 3: Spark & HBase (8-10 hours)**

*Morning (4-5 hours): Spark*
- ⏰ Hour 1-2: Spark Introduction
  - RDD concept
  - Transformations vs Actions
  - Narrow vs Wide transformations
- ⏰ Hour 3-4: Spark Operations
  - Practice map, filter, flatMap
  - Understand reduceByKey vs groupByKey
  - Learn common actions
- ⏰ Hour 5: Spark Streaming Basics
  - DStream concept
  - Window operations
  - Basic examples

*Afternoon (3-4 hours): HBase*
- ⏰ Hour 6-7: HBase Data Model
  - Row key, Column family, Qualifier
  - Cell structure and versioning
  - HBase vs RDBMS
- ⏰ Hour 8-9: HBase Operations
  - Put, Get, Scan, Delete
  - Practice commands
  - Understand filters

*Evening (2-3 hours): Integration & Review*
- ⏰ Review all topics from Days 1-3
- ⏰ Create mind maps connecting concepts
- ⏰ Identify weak areas

**Day 4: Comprehensive Review & Mock Exam (8-10 hours)**

*Morning (3-4 hours): Weak Area Focus*
- ⏰ Review topics you struggled with
- ⏰ Re-read relevant sections
- ⏰ Practice more problems in weak areas

*Afternoon (3 hours): Mock Exam*
- ⏰ Complete a full 3-hour mock exam
- ⏰ Simulate exam conditions
- ⏰ Time yourself strictly

*Evening (3-4 hours): Mock Exam Review & Final Prep*
- ⏰ Review mock exam mistakes
- ⏰ Understand why you got things wrong
- ⏰ Create final summary notes
- ⏰ Review all flashcards
- ⏰ Get good sleep!

---

### 📚 MODERATE PLAN (1 Week Before Exam)

**Days 1-2: Big Data & Hadoop (4-5 hours/day)**
- Day 1: Cluster Computing, MapReduce Framework
- Day 2: Hadoop Architecture, HDFS, MapReduce Model

**Days 3-4: Data Warehousing & Hive (4-5 hours/day)**
- Day 3: DW Concepts, Multidimensional Model, Schema Design
- Day 4: Hive Architecture, HiveQL, SQL for DW

**Days 5-6: HBase & Spark (3-4 hours/day)**
- Day 5: HBase Data Model and Operations
- Day 6: Spark Introduction, Data Model, Operations, Streaming

**Day 7: Complete Review & Mock Exam (6-8 hours)**
- Morning: Review all high-priority topics
- Afternoon: 3-hour mock exam
- Evening: Review mistakes, final preparation

---

### 🎯 RELAXED PLAN (2 Weeks Before Exam)

**Week 1: Complete Coverage (2-3 hours/day)**
- Days 1-2: Cluster Computing, MapReduce
- Days 3-4: Hadoop, HDFS
- Days 5-6: Data Warehousing
- Day 7: Rest or light review

**Week 2: Deep Dive & Practice (2-4 hours/day)**
- Days 1-2: Hive, HiveQL
- Days 3-4: HBase, Spark
- Day 5: SQL for DW, Physical Design
- Day 6: Complete review, practice problems
- Day 7: Mock exam + review

---

## 🎓 STUDY TECHNIQUES

### 1. Active Recall
- **Don't just read** - close notes and write what you remember
- **Test yourself** after each topic
- **Explain concepts out loud** (Feynman Technique)
- **Create flashcards** for definitions and commands

### 2. Spaced Repetition
- **Review material** at increasing intervals
- **Day 1**: Learn topic
- **Day 2**: Quick review
- **Day 4**: More detailed review
- **Day 7**: Final review

### 3. Practice Problems
**MapReduce**:
- Work through at least 5 different MapReduce examples
- Trace execution manually
- Identify phases in each

**Schema Design**:
- Design 3-4 different star schemas from requirements
- Practice identifying facts vs dimensions
- Draw ER diagrams

**HiveQL**:
- Write 15-20 different queries
- Cover all command types
- Practice JOINs extensively

**Spark**:
- Trace RDD transformations
- Identify which operations trigger execution
- Understand lineage graphs

### 4. Visual Learning
- **Draw diagrams** from memory
- **Create comparison tables**
- **Make mind maps** connecting concepts
- **Sketch architecture** diagrams

### 5. Teach Someone
- **Explain concepts** to a study buddy
- **Form study groups** to discuss topics
- **If stuck**, you've found a weak area!

---

## 📝 COMMON EXAM QUESTION PATTERNS

### Type 1: MapReduce Execution
**Format**: "Trace the MapReduce execution for the following input..."

**Preparation**:
- Know the template structure
- Identify Map output
- Show Shuffle & Sort
- Show Reduce output
- Practice with various examples (word count, max, average, join)

**Example**:
```
Input: "apple banana apple cherry"
Show Map output, Shuffle/Sort, and Reduce output
```

### Type 2: Schema Design
**Format**: "Design a star schema for..."

**Preparation**:
- Identify business process
- Declare grain explicitly
- List all dimensions
- List all facts
- Draw star schema diagram
- Know SCD types for changing dimensions

**Example**:
```
Design a star schema for a hospital patient admission system.
Include appropriate dimensions and facts.
```

### Type 3: HiveQL Queries
**Format**: "Write a Hive query to..."

**Preparation**:
- Practice CREATE TABLE (with partitioning)
- Practice SELECT with WHERE, GROUP BY, HAVING
- Practice JOINs (INNER, LEFT, RIGHT)
- Know partitioning syntax
- Understand bucketing

**Example**:
```
Write a HiveQL query to find the top 10 products by total sales amount in 2023.
```

### Type 4: Architecture Explanation
**Format**: "Explain how HDFS read/write operation works" or "Describe YARN job execution"

**Preparation**:
- Memorize step-by-step processes
- Know component interactions
- Be able to draw diagrams
- Understand data flow

**Example**:
```
Explain the process when a client reads a file from HDFS.
Include all components involved and the sequence of operations.
```

### Type 5: Spark Operations
**Format**: "What is the output of the following RDD transformations?"

**Preparation**:
- Trace code step-by-step
- Understand lazy evaluation
- Know transformation vs action
- Identify when shuffle occurs

**Example**:
```python
rdd = sc.parallelize([1, 2, 3, 4, 5])
rdd2 = rdd.map(lambda x: x * 2)
rdd3 = rdd2.filter(lambda x: x > 5)
result = rdd3.collect()

What is the value of result?
```

### Type 6: Comparison Questions
**Format**: "Compare X with Y" or "What are the differences between...?"

**Preparation**:
- Create comparison tables for all major comparisons
- OLTP vs OLAP
- Star vs Snowflake
- MapReduce vs Spark
- HBase vs RDBMS
- Managed vs External tables (Hive)
- Narrow vs Wide transformations (Spark)

**Example**:
```
Compare and contrast OLTP and OLAP systems.
Provide at least 5 differences.
```

### Type 7: HBase Operations
**Format**: "Write HBase commands to..." or "Show the result of..."

**Preparation**:
- Know basic commands (even with cheat sheet)
- Understand row key design
- Practice Put, Get, Scan, Delete
- Understand filters

**Example**:
```
Write HBase commands to:
1. Create a table 'products' with column families 'details' and 'pricing'
2. Insert a product with id 'prod001'
3. Retrieve all products with ids starting with 'prod0'
```

---

## 📊 QUICK REFERENCE CHECKLIST

### Before the Exam, Can You:

**MapReduce**
- [ ] Explain all 5 phases?
- [ ] Trace WordCount example from memory?
- [ ] Identify Map and Reduce functions in a problem?
- [ ] Explain shuffle and sort phase?
- [ ] Know when to use Combiner?

**HDFS**
- [ ] Draw HDFS architecture diagram?
- [ ] Explain read operation (6 steps)?
- [ ] Explain write operation (7 steps)?
- [ ] Know default block size and replication?
- [ ] Execute basic HDFS commands?

**Data Warehousing**
- [ ] Explain OLTP vs OLAP (5+ differences)?
- [ ] Design star schema from requirements?
- [ ] Identify facts vs dimensions?
- [ ] Explain all OLAP operations?
- [ ] Describe SCD Types 1, 2, 3?
- [ ] State four-step design methodology?

**Hive**
- [ ] Explain Hive architecture?
- [ ] Describe metastore purpose?
- [ ] Know managed vs external tables?
- [ ] Write CREATE TABLE with partitioning?
- [ ] Write SELECT query with JOIN?
- [ ] Explain partitioning and bucketing?

**HBase**
- [ ] Explain HBase data model?
- [ ] Describe cell structure?
- [ ] Know row key design importance?
- [ ] Execute Put, Get, Scan, Delete?
- [ ] Explain versioning?
- [ ] Know when to use HBase?

**Spark**
- [ ] Explain RDD concept?
- [ ] List 10 transformations?
- [ ] List 10 actions?
- [ ] Differentiate transformations vs actions?
- [ ] Explain lazy evaluation?
- [ ] Trace RDD lineage?
- [ ] Know reduceByKey vs groupByKey?
- [ ] Understand DStream for streaming?

**SQL for DW**
- [ ] Write ROLLUP query?
- [ ] Write CUBE query?
- [ ] Use window functions?
- [ ] Explain materialized views?

---

## ⚠️ COMMON MISTAKES TO AVOID

### During Study:
1. **Passive Reading**: Don't just read slides - practice actively
2. **Skipping Practice**: Must do problems, not just theory
3. **Ignoring Weak Areas**: Address difficulties early
4. **Cramming Too Late**: Start at least 3 days before
5. **Not Using Cheat Sheet**: Familiarize yourself with what's provided
6. **Memorizing Without Understanding**: Understand concepts, not just facts
7. **Neglecting Connections**: Understand how topics relate

### During Exam:
1. **Not Reading Instructions**: Read questions carefully
2. **Spending Too Long on One Question**: Move on if stuck
3. **Not Showing Work**: Show your thinking process
4. **Skipping Easy Questions**: Answer easy ones first
5. **Not Managing Time**: Allocate time per question
6. **Forgetting to Review**: Leave time to check answers
7. **Panic**: Stay calm, breathe, think clearly

---

## 🎯 EXAM DAY STRATEGY

### Before Exam:
- [ ] Get 7-8 hours of sleep
- [ ] Eat a good breakfast
- [ ] Arrive 15 minutes early
- [ ] Bring required materials (pens, student ID)
- [ ] Quick review of key concepts (don't cram!)

### During Exam (3 hours = 180 minutes):

**First 5 Minutes**:
- Read all questions quickly
- Identify easy vs hard questions
- Plan time allocation (30 minutes per question for 6 questions)

**Time Allocation** (suggested):
- Question 1: 25-30 minutes
- Question 2: 25-30 minutes
- Question 3: 25-30 minutes
- Question 4: 25-30 minutes
- Question 5: 25-30 minutes
- Question 6: 25-30 minutes
- Review: 15-30 minutes

**Answering Strategy**:
1. **Answer easy questions first** (build confidence, secure marks)
2. **Show your work** (partial credit possible)
3. **Draw diagrams** where helpful
4. **Be explicit** - don't assume examiner knows what you mean
5. **If stuck**, move on and come back
6. **Use provided cheat sheet** wisely
7. **Write legibly**

**Last 15 Minutes**:
- Review all answers
- Check for silly mistakes
- Ensure you answered all parts of questions
- Add any missed points

---

## 📖 TOPIC CORRELATION MAP

Understanding how topics connect helps with comprehensive answers:

```
Cluster Computing
    ↓
Hadoop Architecture (HDFS + YARN)
    ↓
MapReduce Model → Hive (Built on MapReduce)
    ↓               ↓
Spark (Faster)   HiveQL (SQL on Hadoop)
    ↓
Spark Streaming

Data Warehousing Concepts
    ↓
Multidimensional Model
    ↓
Schema Design (Star/Snowflake)
    ↓
SQL for DW → Hive (Implements DW concepts)

HBase (NoSQL on HDFS)
    ↓
Column-Family Model
```

---

## 🎓 FINAL TIPS

### Academic Success:
1. **Attend all remaining lectures** if any
2. **Review assignment feedback** - common mistakes
3. **Use office hours** - ask Dr. Ren questions
4. **Form study group** - teach each other
5. **Practice past papers** if available

### Mental Preparation:
1. **Stay positive** - you've learned this material
2. **Manage stress** - exercise, breaks, sleep
3. **Believe in yourself** - confidence helps performance
4. **Don't compare** yourself to others
5. **Focus on your preparation**, not others'

### Day Before Exam:
1. **Light review only** - no new material
2. **Organize materials** for exam day
3. **Set multiple alarms**
4. **Get good sleep** (minimum 7 hours)
5. **Prepare clothes/bag** the night before
6. **Eat well** and stay hydrated

### Remember:
- **You have a cheat sheet** - use it!
- **Exam is 3 hours** - plenty of time if managed well
- **Short answer format** - concise but complete answers
- **40% to pass** - achievable with good preparation
- **No programming** - focus on concepts and commands

---

## 📚 RECOMMENDED FINAL REVIEW SEQUENCE

### 24 Hours Before Exam:
1. **Morning**: Review all topic summaries (2-3 hours)
2. **Afternoon**: Practice 1-2 questions from each type (2-3 hours)
3. **Evening**: Light review of flashcards, early bed (1-2 hours)

### 12 Hours Before Exam:
1. **No intense studying**
2. **Light review of key concepts**
3. **Review common mistakes list**
4. **Prepare materials**
5. **Relax and sleep well**

### 2 Hours Before Exam:
1. **Light breakfast**
2. **Quick scan of summary notes**
3. **Review provided cheat sheet format**
4. **Arrive early at exam venue**

---

## ✅ SUCCESS CHECKLIST

Use this checklist to track your preparation:

### Study Completion:
- [ ] Read all topic summaries
- [ ] Created own notes for each topic
- [ ] Practiced MapReduce problems (5+)
- [ ] Designed DW schemas (3+)
- [ ] Wrote HiveQL queries (15+)
- [ ] Traced Spark operations (5+)
- [ ] Practiced HBase commands
- [ ] Created comparison tables
- [ ] Drew architecture diagrams
- [ ] Completed mock exam
- [ ] Reviewed mock exam mistakes
- [ ] Created flashcards for key concepts
- [ ] Identified and strengthened weak areas

### Materials Ready:
- [ ] Student ID
- [ ] Multiple pens (blue/black)
- [ ] Pencil and eraser
- [ ] Watch (for time management)
- [ ] Water bottle
- [ ] Tissues
- [ ] Exam venue location known
- [ ] Travel time calculated

### Mental Preparation:
- [ ] Confident in MapReduce
- [ ] Confident in Data Warehousing
- [ ] Confident in HDFS
- [ ] Confident in Hive
- [ ] Confident in HBase
- [ ] Confident in Spark
- [ ] Know exam format
- [ ] Planned time management strategy
- [ ] Ready for success!

---

## 🌟 FINAL WORDS OF ENCOURAGEMENT

You've worked hard throughout the semester. You've completed assignments, attended lectures, and engaged with complex Big Data concepts. The exam is your opportunity to demonstrate what you've learned.

**Remember**:
- This exam is testing your understanding, not trying to trick you
- The cheat sheet is provided to help you, use it wisely
- Dr. Ren wants you to succeed
- You know more than you think you do
- Preparation beats panic every time

**You've got this! Good luck! 🚀**

---

*Study Plan Created: November 17, 2025*  
*Course: ISIT312 Big Data Management*  
*Session: SIM S4 2025*  
*Lecturer: Dr Fenghui Ren*

---

## 📞 SUPPORT RESOURCES

**Lecturer**: Dr Fenghui Ren  
Email: fren@uow.edu.au

**Tutor**: Mr. Sionggo Japit  
Email: sjapit@uow.edu.au

**Course Support**: https://support.claude.com  
**Technical Documentation**: Check Moodle announcements regularly

**Remember**: Read your emails in time and watch closely on the Moodle announcements!