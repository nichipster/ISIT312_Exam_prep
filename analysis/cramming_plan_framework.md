# ISIT312 Exam Preparation - Cramming Plan Framework

## ⚠️ PRELIMINARY VERSION
**This is a framework based on typical ISIT312 curriculum. Once PDFs are extracted, this will be updated with specific content from YOUR lectures and sample exam.**

---

## Exam Structure Analysis

### Based on typical ISIT312 exams:
- **Duration**: Usually 2-3 hours
- **Format**: Mix of theory, short answer, and problem-solving questions
- **Coverage**: All major topics with emphasis on practical application

### Typical Question Distribution:
1. **Big Data Fundamentals & Hadoop** (25-30%)
   - Cluster computing concepts
   - MapReduce framework and execution
   - HDFS architecture and operations
   - Hadoop ecosystem

2. **Data Warehousing** (25-30%)
   - DW concepts and architecture
   - Star schema vs Snowflake schema
   - Dimension and fact tables
   - ETL processes
   - SQL for DW (OLAP operations)

3. **Hive** (15-20%)
   - HiveQL queries
   - Data structures and file formats
   - Partitioning and bucketing
   - UDFs

4. **HBase** (10-15%)
   - Data model and architecture
   - Column families and qualifiers
   - CRUD operations
   - Comparison with RDBMS

5. **Spark** (15-20%)
   - RDD operations (transformations & actions)
   - Spark SQL and DataFrames
   - Spark Streaming basics
   - DAG execution model

---

## Topic Priority Matrix

### 🔴 HIGH PRIORITY (Must Master - 60% of exam)

#### Topic 1: MapReduce Framework & Model
- **Weightage**: Very High (15-20%)
- **Difficulty**: Medium
- **Exam Type**: Theory + Practical coding
- **Study Time**: 4-5 hours
- **Why Important**: Core concept, appears in multiple question types
- **Key Areas**:
  - Map and Reduce function logic
  - Word count and similar examples
  - Shuffle and sort phase
  - Execution flow
  - Java MapReduce code structure

#### Topic 2: Data Warehousing Design
- **Weightage**: High (15-20%)
- **Difficulty**: Medium-High
- **Exam Type**: Schema design + SQL queries
- **Study Time**: 4-5 hours
- **Why Important**: Heavily tested with practical problems
- **Key Areas**:
  - Star vs Snowflake schema
  - Fact and dimension tables
  - Slowly Changing Dimensions (SCD)
  - Conceptual/Logical/Physical design
  - OLAP operations (drill-down, roll-up, slice, dice)

#### Topic 3: HDFS Architecture
- **Weightage**: High (10-15%)
- **Difficulty**: Medium
- **Exam Type**: Theory + architecture diagrams
- **Study Time**: 3-4 hours
- **Why Important**: Fundamental to Hadoop ecosystem
- **Key Areas**:
  - NameNode and DataNode roles
  - Block replication
  - Read/write operations
  - Fault tolerance mechanisms
  - Secondary NameNode

#### Topic 4: Hive & HiveQL
- **Weightage**: High (15-20%)
- **Difficulty**: Medium
- **Exam Type**: HiveQL queries + theory
- **Study Time**: 4-5 hours
- **Why Important**: Practical queries frequently tested
- **Key Areas**:
  - HiveQL syntax (similar to SQL)
  - Partitioning and bucketing
  - Internal vs external tables
  - File formats (ORC, Parquet)
  - JOIN operations

### 🟡 MEDIUM PRIORITY (Important - 30% of exam)

#### Topic 5: Spark RDD Operations
- **Weightage**: Medium (10-15%)
- **Difficulty**: Medium-High
- **Exam Type**: Code analysis + operations
- **Study Time**: 3-4 hours
- **Key Areas**:
  - Transformations (map, filter, flatMap, reduceByKey)
  - Actions (collect, reduce, count, take)
  - Lazy evaluation
  - DAG visualization
  - Spark vs MapReduce

#### Topic 6: HBase Data Model
- **Weightage**: Medium (8-12%)
- **Difficulty**: Medium
- **Exam Type**: Schema design + operations
- **Study Time**: 2-3 hours
- **Key Areas**:
  - Row keys and column families
  - Versioning and timestamps
  - Get, Put, Scan operations
  - Comparison with RDBMS
  - When to use HBase

#### Topic 7: Hadoop Architecture & Ecosystem
- **Weightage**: Medium (8-10%)
- **Difficulty**: Low-Medium
- **Exam Type**: Theory + diagrams
- **Study Time**: 2-3 hours
- **Key Areas**:
  - YARN architecture
  - Resource Manager and Node Manager
  - Job submission flow
  - Hadoop ecosystem components

### 🟢 LOWER PRIORITY (Good to Know - 10% of exam)

#### Topic 8: Cluster Computing Concepts
- **Weightage**: Low (5-8%)
- **Difficulty**: Low
- **Exam Type**: Theory/definitions
- **Study Time**: 1-2 hours
- **Key Areas**:
  - Distributed computing basics
  - Scalability concepts
  - CAP theorem basics

#### Topic 9: Spark Streaming
- **Weightage**: Low (5-8%)
- **Difficulty**: Medium
- **Exam Type**: Conceptual
- **Study Time**: 1-2 hours
- **Key Areas**:
  - DStream basics
  - Window operations
  - Streaming vs batch

#### Topic 10: Advanced SQL for DW
- **Weightage**: Low-Medium (5-10%)
- **Difficulty**: Medium
- **Exam Type**: SQL queries
- **Study Time**: 2-3 hours
- **Key Areas**:
  - Window functions
  - ROLLUP and CUBE
  - Materialized views

---

## Recommended Study Schedule

### 🚀 INTENSIVE (3-4 Days Before Exam)

**Day 1: Big Data Fundamentals (8-10 hours)**
- Morning: MapReduce Framework (2-3 hrs)
  - Read theory
  - Work through examples
  - Practice word count variations
- Afternoon: HDFS & Hadoop Architecture (2-3 hrs)
  - Understand architecture
  - Draw diagrams
  - Memorize component roles
- Evening: Revision + Practice Questions (3-4 hrs)

**Day 2: Data Warehousing (8-10 hours)**
- Morning: DW Concepts & Design (3-4 hrs)
  - Star/Snowflake schemas
  - Fact and dimension tables
  - Design principles
- Afternoon: SQL for DW (2-3 hrs)
  - OLAP operations
  - Complex queries
  - Practice problems
- Evening: Hive & HiveQL (3-4 hrs)
  - HiveQL syntax
  - Partitioning/bucketing
  - Practice queries

**Day 3: Spark & HBase (6-8 hours)**
- Morning: Spark RDD & Operations (3-4 hrs)
  - Transformations and actions
  - Code tracing
  - Practice problems
- Afternoon: HBase (2-3 hrs)
  - Data model
  - Operations
  - Schema design
- Evening: Spark Streaming basics (1-2 hrs)

**Day 4: Review & Practice Exam (6-8 hours)**
- Morning: Review all high-priority topics (3-4 hrs)
- Afternoon: Complete sample exam (2-3 hrs)
- Evening: Review mistakes and weak areas (2-3 hrs)

### 📚 MODERATE (1 Week Before Exam)

**Days 1-2**: Big Data & Hadoop (4-5 hrs/day)
**Days 3-4**: Data Warehousing & Hive (4-5 hrs/day)
**Days 5-6**: Spark & HBase (3-4 hrs/day)
**Day 7**: Complete revision + sample exam (6-8 hrs)

### 🎯 RELAXED (2 Weeks Before Exam)

**Week 1**: Cover all topics systematically (2-3 hrs/day)
- Days 1-3: Big Data fundamentals
- Days 4-5: Data Warehousing
- Days 6-7: Hive & HBase

**Week 2**: Deep dive + practice (2-3 hrs/day)
- Days 1-3: Spark + advanced topics
- Days 4-5: Practice problems
- Days 6-7: Sample exam + revision

---

## Study Techniques

### 1. **Active Recall**
- Don't just read - test yourself
- After each topic, close notes and write what you remember
- Use flashcards for definitions and concepts

### 2. **Practice Problems**
- Work through at least 5 MapReduce examples
- Design 3-4 data warehouse schemas
- Write 10+ HiveQL queries
- Trace 5+ Spark RDD operations

### 3. **Visualization**
- Draw architecture diagrams from memory
- Create comparison tables (HDFS vs RDBMS, MapReduce vs Spark)
- Sketch schema designs

### 4. **Teach Someone**
- Explain concepts out loud
- If stuck, you've found a weak area

### 5. **Focus on Patterns**
- Many questions follow similar patterns
- Recognize question types from sample exam
- Create templates for common solutions

---

## Common Exam Question Types

### Type 1: MapReduce Logic
**Format**: "Write Map and Reduce functions for..."
**Preparation**:
- Know the template structure
- Practice word count variations
- Understand input/output formats

### Type 2: Schema Design
**Format**: "Design a star/snowflake schema for..."
**Preparation**:
- Identify facts vs dimensions
- Practice SCD types
- Know normalization levels

### Type 3: HiveQL Queries
**Format**: "Write a Hive query to..."
**Preparation**:
- Practice JOINs
- Know partitioning syntax
- Understand window functions

### Type 4: Architecture Explanation
**Format**: "Explain how [component] works..."
**Preparation**:
- Draw diagrams
- Memorize component interactions
- Know data flow

### Type 5: Spark Operations
**Format**: "What is the output of this RDD transformation?"
**Preparation**:
- Trace code step-by-step
- Understand lazy evaluation
- Know transformation vs action

### Type 6: Comparison Questions
**Format**: "Compare X with Y"
**Preparation**:
- Create comparison tables
- Know when to use what
- Understand trade-offs

---

## Quick Reference Checklist

### Before the Exam, Can You:

#### MapReduce
- [ ] Explain MapReduce execution phases
- [ ] Write map and reduce functions
- [ ] Trace a word count example
- [ ] Explain shuffle and sort

#### HDFS
- [ ] Draw HDFS architecture
- [ ] Explain read/write operations
- [ ] Describe replication mechanism
- [ ] Know NameNode functions

#### Data Warehousing
- [ ] Design star schema from requirements
- [ ] Identify fact vs dimension tables
- [ ] Explain SCD types
- [ ] Write OLAP queries

#### Hive
- [ ] Write basic to complex HiveQL
- [ ] Explain partitioning and bucketing
- [ ] Know internal vs external tables
- [ ] Understand file formats

#### HBase
- [ ] Design row key and column families
- [ ] Write Get/Put/Scan operations
- [ ] Explain versioning
- [ ] Know when to use HBase

#### Spark
- [ ] List common transformations
- [ ] Differentiate transformations vs actions
- [ ] Trace RDD lineage
- [ ] Explain lazy evaluation

---

## Emergency Cramming (12-24 Hours Before Exam)

If you only have 12-24 hours:

### Hour 1-3: MapReduce
- Read summary
- Do 2-3 examples
- Memorize template

### Hour 4-6: Data Warehousing
- Understand star/snowflake
- Practice 1-2 designs
- Review OLAP operations

### Hour 7-9: Hive & HBase
- HiveQL syntax review
- HBase data model
- Key operations

### Hour 10-12: Spark & Review
- Spark RDD operations
- Quick review of all topics
- Skim sample exam

### If 24 hours:
- Double the time per topic
- Complete full sample exam
- Review weak areas thoroughly

---

## Resources to Use

### Priority 1 (Essential):
1. Your lecture slides (this material)
2. Sample exam paper
3. Your lecture notes

### Priority 2 (Helpful):
1. Official Hadoop documentation
2. Hive language manual
3. Spark programming guide

### Priority 3 (If time permits):
1. Online tutorials
2. Additional practice problems
3. YouTube explanations

---

## Final Tips

1. **Focus on Understanding, Not Memorization**
   - Understand WHY not just WHAT
   - Be able to apply concepts to new scenarios

2. **Practice Under Time Pressure**
   - Set timers for practice problems
   - Complete sample exam in exam conditions

3. **Get Enough Sleep**
   - Don't study all night before exam
   - Your brain needs rest to consolidate learning

4. **Read Questions Carefully**
   - Many marks lost due to misreading
   - Underline key words

5. **Show Your Work**
   - Partial credit is available
   - Write out your thought process

6. **Time Management in Exam**
   - Don't spend too long on one question
   - Answer easy questions first
   - Leave time for review

---

## Update Instructions

**⚠️ IMPORTANT**: After running the PDF extraction script, provide the extracted text to Claude with the message:

"I've completed the extraction. Please read the extracted content and update this cramming plan with specific information from my lectures and sample exam."

Claude will then:
1. Analyze your actual lecture content
2. Review the sample exam questions
3. Update topic weightages based on actual exam
4. Add specific examples from YOUR lectures
5. Create precise study schedule based on YOUR content
6. Add topic-specific tips based on YOUR materials

---

*This framework will be replaced with personalized content once PDF extraction is complete.*
*Created: November 2025*
*Status: AWAITING LECTURE CONTENT EXTRACTION*
