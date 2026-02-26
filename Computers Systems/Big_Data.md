# Big Data Analytics — Comprehensive Study Notes



# UNIT I — Introduction to Big Data

## 1. Evolution of Big Data

### 1800–1950: Mechanical & Early Digital Processing

- **Joseph Marie Jacquard (1801)** introduced punched cards to control textile looms — each hole directed the loom's needle, one of the earliest forms of programmatic data input.
- **Herman Hollerith (1890)** adapted punched cards for the U.S. Census, reducing a 10-year tabulation effort to just 3 months.
- **Alan Turing (1936)** proposed the Turing Machine — a theoretical model that became the foundation of all modern computing.
- **ENIAC (1946)**, the first general-purpose electronic computer, processed simple numeric data at speeds impossible for humans.

### 1950–1990: Rise of Digital Data & Databases

- **IBM 305 RAMAC (1956)** — the first hard disk drive, storing 5MB of data despite weighing over a ton.
- Early **Hierarchical (IBM IMS)** and **Network-based (IDMS)** databases required programmers to know the exact physical location of data on disk and manually follow pointers between records.
- **Edgar F. Codd (1970)** challenged this: users should simply see data as tables, not care about pointers or trees — this became the **relational model**, giving birth to SQL.
- **Oracle (1977)** and **IBM DB2 (1983)** became the commercial cornerstones of structured data management.

### 1980s–1990s: Personal Computers & the Internet

- Spreadsheets — **VisiCalc (1979)**, **Lotus 1-2-3 (1983)**, **Microsoft Excel (1985)** — brought data analysis to non-programmers.
- **Tim Berners-Lee's World Wide Web (1991)** enabled global data sharing, generating the first waves of unstructured internet data through web pages, emails, and forums.

### 2000s: The Data Explosion

- Social media — Facebook, Twitter, YouTube — created massive volumes of **unstructured data** (images, videos, posts) that relational databases could not scale to handle.
- **Google** developed the **Google File System (GFS)** and **MapReduce**, inspiring Yahoo to create **Apache Hadoop**.
- Cloud platforms — **AWS, Google Cloud, Microsoft Azure** — enabled businesses to store and process data at scale without owning physical infrastructure.

### 2010s: AI, Machine Learning & Real-Time Analytics

- **Apache Kafka** and **Apache Spark** enabled real-time streaming analytics at massive scale.
- ML models trained on Big Data enabled powerful predictions — Netflix's recommendation engine uses viewing history across millions of users to predict what you want to watch next.
- **Blockchain** emerged as a mechanism for secure, tamper-proof distributed data transactions.

### 2020s: 5G, IoT & Quantum Computing

- A 4G tower handles ~2,000 IoT devices per sq. km. A **5G** tower handles up to **1 million devices** — exponentially increasing real-time sensor data volume.
- Computing power hierarchy evolved: **CPU → GPU → QPU (Quantum Processing Units)**.
- Unlike GPUs (which still process bits sequentially), **QPUs process all bits simultaneously** — solving complex optimization problems that would take classical computers millions of years.


## 2. Types of Data

### Based on Structure

**Structured Data** — Organized in a predefined format of rows and columns. Stored in relational databases (SQL, Excel). Every record follows the same schema. Example: An employee table with columns for Employee_ID, Name, Department, Salary.

**Semi-Structured Data** — Does not follow a rigid table format but contains tags, keys, or markers that provide some organizational hierarchy. Common in JSON, XML, HTML. Example: An XML file storing personal records uses `<rec>`, `<n>`, `<age>` tags to organize data without a fixed schema.

```xml
<rec><n>Prashant Rao</n><gender>Male</gender><age>35</age></rec>
```

**Unstructured Data** — No fixed format or schema. Hardest to store and analyze with traditional databases. Example: CCTV footage, social media posts, voice recordings, PDF documents.

### Based on Nature

**Qualitative (Categorical) Data:**
- **Nominal** — No inherent order. Example: Colors, gender, country names.
- **Ordinal** — Ordered but no fixed interval between values. Example: Grades (A, B, C), customer ratings (Good, Better, Best).

**Quantitative (Numerical) Data:**
- **Discrete** — Countable, whole numbers. Example: Number of students in a class, cars sold per day.
- **Continuous** — Can take infinite values within a range. Example: Height, weight, temperature.

### Based on Source

**Primary Data** — Collected firsthand for a specific purpose. Example: Surveys, interviews, controlled experiments.

**Secondary Data** — Already collected and reused. Example: Census reports, research papers, government databases.

### Based on Sensitivity

**Public Data** — Freely available. Example: Weather forecasts, open government census data.

**Private Data** — Restricted and confidential. Example: Employee records, business financials.

**Sensitive Data** — Requires legal protection due to privacy concerns. Example: Biometric data, medical records (Personal Identifiable Information / PII).

**Confidential Data** — Highly restricted, authorized individuals only. Example: Military intelligence, trade secrets, business acquisition deals.


## 3. Introduction to Big Data

### What is Big Data?

Big Data refers to extremely large datasets that are too voluminous, fast-moving, or diverse to be processed using traditional database and software methods. The key definition: *"Extremely large data sets that may be analyzed computationally to reveal patterns, trends, and associations, especially relating to human behavior and interaction."*

Real-scale examples:
- The **New York Stock Exchange** generates approximately **1 terabyte** of new trade data every single day.
- **Facebook** ingests over **500 terabytes** of new data daily, from photo uploads, messages, likes, and comments.
- **Google** processes over **3.5 billion** search queries per day.

### Memory Size Reference Table

| Unit | Equal To | Size (Bytes) |
|------|----------|--------------|
| Bit | 1 bit | 1/8 |
| Byte | 8 bits | 1 |
| Kilobyte (KB) | 1,024 Bytes | 1,024 |
| Megabyte (MB) | 1,024 KB | ~1 Million |
| Gigabyte (GB) | 1,024 MB | ~1 Billion |
| Terabyte (TB) | 1,024 GB | ~1 Trillion |
| Petabyte (PB) | 1,024 TB | ~1 Quadrillion |
| Exabyte (EB) | 1,024 PB | ~1 Quintillion |
| Zettabyte (ZB) | 1,024 EB | ~1 Sextillion |
| Yottabyte (YB) | 1,024 ZB | ~1 Septillion |

By 2021, global data was estimated at approximately **40,000 Exabytes** — a scale that fundamentally demands Big Data technologies.


## 4. The 5 V's of Big Data

### Volume — *Amount of Data*
- Refers to the sheer scale of data generated every second from social media, sensors, transactions, and M2M communications.
- Requires distributed systems (like Hadoop) — no single machine can store it all.
- **Example:** Facebook ingests **500+ terabytes** of data daily from photos, messages, and likes.

### Velocity — *Speed of Data*
- Refers to the rate at which data is generated and the speed at which it must be processed.
- Data flows in continuously — it must be processed fast enough to be useful, not just stored.
- **Example:** Google handles **3.5 billion+ searches per day** — results must appear in milliseconds.

### Variety — *Diversity of Formats*
- Data arrives in structured (SQL tables), semi-structured (JSON, XML), and unstructured (images, videos, audio) forms.
- Traditional RDBMS handles only structured data — Big Data systems must handle all formats.
- **Example:** A hospital deals with structured patient records, semi-structured lab reports (XML), and unstructured MRI scans — all simultaneously.

### Veracity — *Quality & Trustworthiness*
- Big Data can be messy — missing values, duplicates, fake entries, sensor errors.
- Analyzing unverified data leads to flawed conclusions: *garbage in, garbage out.*
- **Example:** Amazon product reviews contain fake/paid reviews that distort ratings — veracity must be managed to surface genuine feedback.

### Value — *Meaningfulness of Data*
- Raw data at petabyte scale has zero worth unless it's transformed into actionable insights.
- The most important V — all other Vs are meaningless without extracting value.
- **Example:** IBM Watson Health analyzed genomic data from cancer patients to recommend personalized treatment plans — turning raw data into life-saving value.


## 5. Big Data Analytics

### Definition

Big Data analytics is the process of collecting, organizing, and analyzing large datasets to discover patterns, correlations, and actionable insights. It requires specialized software tools for predictive analytics, data mining, text mining, forecasting, and data optimization — collectively called **high-performance analytics**.

### Process of Big Data Analytics

1. **Objective** — Define the primary goal. What question are we trying to answer? What outcome do we expect?
2. **Collection** — Gather data from diverse sources: databases, social media, sensors, logs, APIs.
3. **Validation (Check)** — Since data is massive, it may contain errors, missing values, and inconsistencies. Data is checked against a predefined set of rules to ensure quality.
4. **Preparation** — Data is organized, cleaned, and transformed into a format compatible with the analytical tool or program.
5. **Analysis** — Apply statistical models, machine learning algorithms, or query engines to extract meaningful information.
6. **Visualization** — Convert results into visual form: graphs, charts, dashboards, heatmaps.
7. **Communication** — Deliver the insights to the organization for decision-making.

### Importance of Data Validation

Data validation ensures that only accurate and trustworthy data enters the analysis pipeline.

- **Accuracy & Reliability** — Prevents erroneous conclusions stemming from dirty data.
- **Data Quality** — Filters out corrupt, invalid, or irrelevant data at the ingestion stage.
- **Consistency** — Ensures data from multiple sources aligns in structure and meaning (e.g., date formats, units of measurement).
- **Compliance** — Ensures data meets industry regulations such as HIPAA (healthcare) or GDPR (data privacy in the EU).
- **Efficient Decision-Making** — Stakeholders can trust the analysis when the underlying data has been validated.

### Challenges of Big Data Analytics

- Breaking data silos — organizations store data in different departments, systems, and formats. Integrating this into one unified pipeline is difficult.
- Handling unstructured data — creating platforms that ingest images, audio, and free text as easily as tabular data.
- Scale — volumes are so large that traditional database methods fail, requiring distributed, parallel processing architectures.

### Benefits of Big Data Analytics

A survey of 540 enterprise decision-makers by Webopedia (QuinStreet) found that roughly **62% of organizations** use Big Data analytics to improve speed and reduce operational complexity. Approximately half of all respondents applied Big Data to improve customer retention, guide product development, and gain competitive advantage. Real impact includes: France's Orange Telecom anonymized 2.5 billion call records from 5 million users in the Ivory Coast and released them for public health research — enabling researchers to track population movement after emergencies and model disease containment strategies.


## 6. Applications of Big Data

### Healthcare
- Enables personalized medicine, predictive diagnostics, and real-time patient monitoring via wearables.
- Identifies disease outbreak patterns and accelerates drug discovery by mining clinical trial data.
- **IBM Watson Health** analyzed genomic datasets from cancer patients to suggest DNA-specific treatment plans, improving outcomes compared to generalized chemotherapy.

### Retail
- Analyzes loyalty program data, social media sentiment, and purchase history to predict demand and optimize inventory in real time.
- Enables personalized promotions and dynamic pricing based on customer behavior.
- **Walmart** processes over **2.5 petabytes** of customer transaction data every hour, enabling real-time shelf restocking decisions.

### E-Commerce
- Powers product recommendation engines using purchase history and browsing behavior.
- Enables dynamic pricing, fraud prevention, and supply chain optimization.
- **Amazon's** "Customers who bought this also bought..." recommendation engine drives an estimated **35% of its total revenue**.

### Finance
- Used for real-time fraud detection, algorithmic trading, risk modeling, and customer credit scoring.
- Detects anomalies in transaction patterns within milliseconds, before authorization is even complete.
- **Mastercard's** Decision Intelligence platform analyzes over **75 billion** transaction data points per year to flag fraud in real time.

### Media & Entertainment
- Drives content recommendations, informs original content investment decisions, and optimizes ad targeting.
- Analyzes viewer engagement data to determine what content to produce next.
- **Netflix** greenlit *House of Cards* based on Big Data showing a high overlap of users who loved David Fincher films, Kevin Spacey, and the original UK series — a statistically low-risk production decision.

### Telecom
- Maps network traffic density in real time to identify low-coverage zones and optimize infrastructure.
- Predicts customer churn and enables proactive, personalized retention offers.
- **Bharti Airtel** uses predictive Big Data analytics to identify at-risk customers and offer customized retention packages before they switch providers.

### Travel
- Enables dynamic pricing, personalized travel packages, and real-time flight/hotel suggestions.
- Optimizes logistics and predicts delays using historical and live data.
- **American Airlines** pioneered **yield management** — an algorithm that continuously adjusts seat prices based on demand, competitor pricing, and historical booking patterns to maximize revenue per flight.

### Education
- Tracks student performance metrics, predicts dropout risk, and identifies curriculum gaps.
- Enables personalized learning paths based on individual student progress data.
- **Georgia Tech** used Big Data to analyze early assessment patterns in its online Master's program, proactively intervening with at-risk students and significantly reducing dropout rates.


## 7. Data Storage Fundamentals

For Big Data to be stored effectively, the storage model must satisfy the following requirements:

**Scalable** — The system must expand horizontally (add more machines) as data volume grows. You cannot just buy a bigger hard drive — you add more nodes to the cluster.

**Flexible** — The storage system must handle data of any format — structured tables, JSON documents, images, raw text — without requiring a predefined schema.

**Distributed File System** — Data must be split and stored across multiple machines. No single machine can hold petabytes of data. Distributing the data also enables parallel processing.

**Parallel Processing** — Multiple machines should be able to process different portions of data simultaneously. Sequential processing of Big Data would be computationally prohibitive — it would take years to process what distributed systems handle in hours.

**Redundant (Fault Tolerant)** — Because data is spread across many machines, individual machine failures are inevitable. Each data segment must be replicated across multiple nodes so that if one machine crashes, the data is not lost. Hadoop's default replication factor is **3** — every data block is stored on three separate machines.


## 8. Hadoop Framework

Hadoop is an open-source distributed computing framework inspired by Google's GFS and MapReduce papers. It is designed to store and process massive datasets across clusters of commodity hardware.

### HDFS — Hadoop Distributed File System

HDFS is the storage backbone of Hadoop. Its architecture is designed around two key components:

**NameNode (Master)** — The NameNode stores **metadata** only — it does not store actual data. It keeps track of: the mapping of file names to their blocks, the location of each block on which DataNode, and DataNode IP addresses. Think of the NameNode as the library index — it tells you *where* a book is, but it doesn't contain the book itself.

**DataNode (Worker)** — DataNodes store the actual data in fixed-size units called **Blocks**. The default block size is **64 MB** (configurable up to 128 MB or more). When you upload a 1 GB file to HDFS, it is split into approximately 16 blocks of 64 MB each, distributed across different DataNodes.

**Fault Tolerance** — HDFS maintains a default **replication factor of 3**. Each 64 MB block is stored on 3 different DataNodes. If one DataNode crashes, the NameNode detects the loss (via heartbeat signals) and instructs other DataNodes to re-replicate the missing block to restore redundancy.

```
                        HDFS ARCHITECTURE
                        ─────────────────
          ┌─────────────────────────────────────┐
          │            CLIENT                   │
          │   "Write file.txt (200 MB)"         │
          └────────────┬────────────────────────┘
                       │  ① Ask where to store
                       ▼
          ┌────────────────────────┐
          │       NAMENODE         │  ← Metadata only
          │  (Master)              │    (file→block map,
          │  file.txt →            │     block locations)
          │   Block1 → DN1, DN2    │
          │   Block2 → DN2, DN3    │
          │   Block3 → DN1, DN3    │
          └────────────┬───────────┘
                       │  ② Returns block locations
                       ▼
          ┌────────────────────────────────────────────┐
          │             CLIENT writes directly          │
          └──────┬──────────────┬──────────────┬───────┘
                 │ Block1       │ Block2        │ Block3
                 ▼             ▼               ▼
          ┌──────────┐  ┌──────────┐  ┌──────────────┐
          │DataNode 1│  │DataNode 2│  │  DataNode 3  │
          │ Block1 ✓ │  │ Block1 ✓ │  │   Block2 ✓  │
          │ Block3 ✓ │  │ Block2 ✓ │  │   Block3 ✓  │
          └──────────┘  └──────────┘  └──────────────┘
              (replication factor = 3: each block on 3 nodes)
```

### GFS — Google File System

GFS is the distributed file system developed by Google internally (2003) that inspired Hadoop's HDFS. It was built to handle Google's massive and growing infrastructure needs.

**GFS Master** — Analogous to HDFS's NameNode, the GFS Master stores all metadata: file and directory structure, file permissions, mapping of files to their chunks, and chunk locations across chunkservers. Unlike HDFS, GFS uses a larger default chunk size of **64 MB**.

**Chunkservers** — Analogous to HDFS DataNodes, chunkservers store actual data chunks. They handle read/write requests from clients, manage replication, and ensure the correct number of chunk replicas exists at all times.

**Clients** — Applications or machines that interact with GFS to read and write data. Clients contact the GFS Master for metadata, then directly communicate with Chunkservers to perform actual data transfers — reducing load on the master.

*Key difference from traditional file systems:* GFS is designed for large sequential reads (not random access), optimized for workloads like MapReduce that scan terabytes of data from beginning to end.

```
                        GFS ARCHITECTURE
                        ────────────────
             ┌─────────────────────────────────┐
             │           CLIENT                │
             └────┬───────────────────────┬────┘
                  │ ① Metadata request     │ ③ Read/Write data
                  ▼                        │    directly
       ┌──────────────────┐                │
       │    GFS MASTER    │                │
       │  (Single Master) │                │
       │  - File → Chunks │                │
       │  - Chunk locations│               │
       │  - Permissions   │                │
       └────────┬─────────┘                │
                │ ② Chunk locations        │
                └──────────────────────────┘
                          │
          ┌───────────────┼───────────────┐
          ▼               ▼               ▼
  ┌─────────────┐ ┌─────────────┐ ┌─────────────┐
  │ Chunkserver │ │ Chunkserver │ │ Chunkserver │
  │     #1      │ │     #2      │ │     #3      │
  │  Chunk A ✓  │ │  Chunk A ✓  │ │  Chunk B ✓  │
  │  Chunk B ✓  │ │  Chunk C ✓  │ │  Chunk C ✓  │
  └─────────────┘ └─────────────┘ └─────────────┘
         (64MB chunks, replicated across chunkservers)
```


## 9. High-Performance Architecture

A high-performance architecture is engineered to maximize efficiency, speed, and scalability for data-intensive workloads. It is essential for Big Data analytics, scientific simulations, real-time processing, and machine learning.

### Layers of High-Performance Architecture

**1. Data Collection and Ingestion Layer**
This is the entry point — responsible for gathering data from IoT devices, application logs, databases, social media APIs, and external streams. Tools like **Apache Kafka** act as a high-throughput ingestion buffer, receiving millions of events per second and queuing them for downstream processing. Kafka is used by LinkedIn to process over **7 trillion messages per day**.

**2. Data Storage Layer**
High-performance, distributed storage systems handle both structured and unstructured data at scale. HDFS for batch storage, Amazon S3 for cloud object storage, and Apache Cassandra for distributed NoSQL storage are common choices.

**3. Data Processing and Compute Layer**
This is where analytics happens. **Apache Spark** processes data in-memory (unlike Hadoop's disk-based MapReduce), making it up to **100x faster** for iterative algorithms like machine learning. This layer coordinates the parallel execution of analytical tasks across the cluster.

**4. Real-Time Data Processing**
For latency-sensitive applications — fraud detection, live recommendations, real-time bidding — data must be processed as it arrives without being stored first. **Apache Kafka + Apache Spark Streaming** or **Apache Flink** are used here. VISA's fraud detection system processes transactions in **under 2 milliseconds** using real-time stream processing.

**5. Data Analytics and Machine Learning Layer**
This layer runs statistical models and machine learning algorithms on the stored data. Tools include Apache Spark's MLlib, TensorFlow (for deep learning), and scikit-learn (for classical ML). Feature engineering, model training, and batch prediction jobs run here.

**6. Data Visualization and Reporting Layer**
After analysis, results must be interpretable by stakeholders. Tools like **Tableau**, **Power BI**, or **Apache Superset** convert complex outputs into dashboards, charts, and interactive reports.

**7. High-Performance Networking**
Data transfer between compute nodes, storage systems, and clients must be fast. Low-latency, high-bandwidth networks like **InfiniBand** (used in HPC clusters) and **10/100 GbE Ethernet** are deployed to prevent network bottlenecks. Google's internal network — the **Jupiter network fabric** — achieves petabit-scale bisection bandwidth across its data centers.

**8. Distributed and Parallel Computing**
Big Data processing is inherently parallelized. Tasks are broken into smaller sub-tasks distributed across multiple machines or cores running simultaneously. MapReduce, Spark's RDD model, and GPU-accelerated computing (used in deep learning) all embody this principle.


# UNIT II — Clustering and Classification

## 1. Introduction to Data Clustering

Clustering is an **unsupervised machine learning** technique that groups similar data points together without being told the categories in advance — like dumping a box of mixed fruits on a table and naturally grouping apples, bananas, and oranges based on similarity, with no prior labeling. Formally, it partitions a dataset into groups (clusters) such that objects within the same cluster are more similar to each other than to objects in other clusters. Similarity is typically measured using **Euclidean distance**, **Manhattan distance**, or **cosine similarity**.

### Key Properties of Good Clusters

- **High intra-cluster similarity** — Points within a cluster should be as close to each other as possible.
- **Low inter-cluster similarity** — Points in different clusters should be as far apart as possible.

### Applications

Clustering powers customer segmentation, document organization, anomaly detection, and image compression. **Google News** uses clustering to group articles about the same event from hundreds of different sources, presenting them as a single story rather than hundreds of redundant links.


## 2. K-Means Clustering

K-Means is an iterative, partition-based clustering algorithm — think of it like splitting students into study groups: you randomly pick 3 "group leaders," every student joins the leader they're closest to, then each leader moves to the actual average position of their group. Repeat until no one switches groups. Formally, K-Means partitions `n` data points into `k` clusters by minimizing the **Within-Cluster Sum of Squares (WCSS)**, also called **inertia**:

$$WCSS = \sum_{i=1}^{k} \sum_{x \in C_i} ||x - \mu_i||^2$$

where `μᵢ` is the centroid of cluster `Cᵢ`.

### Algorithm Steps

1. **Initialize** — Choose `k` initial centroids randomly from the data points (or using the smarter **K-Means++** initialization).
2. **Assignment Step** — Assign every data point to the nearest centroid using Euclidean distance: `distance = √[(x₁-x₂)² + (y₁-y₂)²]`
3. **Update Step** — Recalculate each centroid as the **mean** of all points currently assigned to it.
4. **Repeat** — Repeat steps 2–3 until centroids no longer change (convergence), or a maximum number of iterations is reached.

```
         K-MEANS: ITERATION VISUALIZATION (k=2)
         ────────────────────────────────────────
  Iteration 1:               Iteration 2:
  Random centroids           Updated centroids

   ×  ×  ×  [C1]   ○  ○      ×  ×  ×      ○  ○
   1  2  3   4     7  8      1  2  3  [C1] 6  7
                             (centroid shifts to mean)

   [C1]=4  [C2]=7            [C1]=2   [C2]=8
   Assignment by distance    Reassign → Repeat

  Converged:
  Cluster 1: { × × × }    Cluster 2: { ○ ○ ○ }
              1  2  3                  7  8  9
              centroid=2              centroid=8
```

### Solved Numerical Example

**Dataset:** 6 points on a number line. `k = 2`. Initial centroids: **C1 = 2**, **C2 = 8**

| Point | Value |
|-------|-------|
| P1 | 1 |
| P2 | 2 |
| P3 | 3 |
| P4 | 7 |
| P5 | 8 |
| P6 | 9 |

**Iteration 1 — Assignment Step:**

Calculate distance of each point to C1=2 and C2=8, assign to nearest:

| Point | dist to C1=2 | dist to C2=8 | Assigned Cluster |
|-------|-------------|-------------|-----------------|
| P1=1 | \|1−2\| = 1 | \|1−8\| = 7 | C1 |
| P2=2 | \|2−2\| = 0 | \|2−8\| = 6 | C1 |
| P3=3 | \|3−2\| = 1 | \|3−8\| = 5 | C1 |
| P4=7 | \|7−2\| = 5 | \|7−8\| = 1 | C2 |
| P5=8 | \|8−2\| = 6 | \|8−8\| = 0 | C2 |
| P6=9 | \|9−2\| = 7 | \|9−8\| = 1 | C2 |

**Iteration 1 — Update Step (recalculate centroids as mean of assigned points):**

- New C1 = (1 + 2 + 3) / 3 = **2** *(unchanged)*
- New C2 = (7 + 8 + 9) / 3 = **8** *(unchanged)*

Centroids did not change → **Algorithm converged in 1 iteration.**

**Final Clusters:**
- **Cluster 1:** {1, 2, 3} — centroid = 2
- **Cluster 2:** {7, 8, 9} — centroid = 8

**Amazon** uses K-Means clustering on customer purchase behavior to identify segments for targeted marketing campaigns.

### Choosing the Value of K — The Elbow Method

A common challenge is selecting the right `k`. The **Elbow Method** plots WCSS against different values of `k`. As `k` increases, WCSS decreases. The "elbow" — the point where the rate of decrease sharply slows — is the optimal `k`. If the elbow is at k=3, adding a 4th cluster provides diminishing returns.

```
         ELBOW METHOD — Choosing optimal k
         ───────────────────────────────────
  WCSS
   │
  High ─  *
          │ \
          │  \
          │   *
          │    \
          │     *  ← ELBOW (optimal k=3)
          │      ────*────────*────────*──
  Low  ─               k=3   k=4   k=5
         k=1  k=2  k=3  k=4  k=5  k=6
                    ▲
             Adding more clusters
             beyond this gives very
             little reduction in WCSS
```

### Limitations of K-Means

- Must specify `k` in advance — not always known.
- Sensitive to outliers — a single extreme point can pull a centroid far from the true cluster center.
- Assumes clusters are roughly spherical and equally sized — fails for elongated or irregularly shaped clusters.
- Results vary based on initial centroid placement — running K-Means multiple times with different initializations is standard practice.


## 3. Basics of Classification

Classification is predicting which category a new item belongs to based on labeled examples you've already seen — like a spam filter trained on thousands of emails labeled "spam" or "not spam" that can then judge new emails. Formally, it is a **supervised machine learning** task where an algorithm learns a mapping function `f: X → Y` from labeled training data, where `X` is the input feature space and `Y` is the set of discrete class labels. The learned model then predicts the class of unseen data points.

### Key Terms

- **Training Set** — Labeled data used to train the model.
- **Test Set** — Unseen labeled data used to evaluate model performance.
- **Feature** — An input variable (attribute) used for prediction. Example: email word count, sender domain.
- **Label / Class** — The output category being predicted. Example: spam / not-spam.
- **Classifier** — The model that performs the classification.

### Types of Classification

- **Binary Classification** — Two possible classes. Example: Email spam detection (spam / not spam), disease diagnosis (positive / negative).
- **Multi-class Classification** — More than two classes. Example: Digit recognition (0–9), news categorization (Sports / Politics / Technology).
- **Multi-label Classification** — An instance can belong to multiple classes simultaneously. Example: A movie tagged as both "Action" and "Thriller."

### Evaluation Metrics

**Accuracy** — The proportion of correctly classified instances:
`Accuracy = (TP + TN) / (TP + TN + FP + FN)`

**Precision** — Of all instances predicted as positive, how many actually were:
`Precision = TP / (TP + FP)`

**Recall (Sensitivity)** — Of all actual positive instances, how many were correctly identified:
`Recall = TP / (TP + FN)`

**F1 Score** — Harmonic mean of Precision and Recall:
`F1 = 2 × (Precision × Recall) / (Precision + Recall)`

A **Confusion Matrix** summarizes all four outcomes (TP, TN, FP, FN) in a table.


## 4. Decision Trees

A Decision Tree works like the game "20 Questions" — you start at the top, ask a question, go left or right based on the answer, and keep going until you reach a final verdict at the bottom. Formally, it is a **tree-structured model** where each **internal node** represents a test on a feature (e.g., "Age > 30?"), each **branch** represents an outcome of that test, and each **leaf node** represents a class label. The key is selecting which questions to ask first — those that reduce uncertainty the most.

### How Splitting Works — Information Gain & Entropy

The algorithm chooses the best feature to split on at each node using **Information Gain**, which measures the reduction in **entropy (uncertainty)** after a split.

**Entropy** measures the impurity or randomness of a dataset:

$$Entropy(S) = -\sum_{i=1}^{c} p_i \log_2(p_i)$$

where `pᵢ` is the proportion of class `i` in set `S`. Entropy = 0 means all samples belong to one class (perfectly pure). Entropy = 1 means the classes are evenly split (maximum uncertainty).

**Information Gain** = Entropy(parent) − weighted average Entropy(children)

The feature with the **highest information gain** is selected as the splitting criterion at each node.

**Gini Impurity** is an alternative to entropy (used in CART algorithm):
$$Gini = 1 - \sum_{i=1}^{c} p_i^2$$

### Example: Loan Approval Tree

```
                [Income > 50K?]
               /               \
             Yes               No
              |                 |
     [Credit Score > 700?]   [REJECT]
        /          \
      Yes           No
       |             |
   [APPROVE]    [Employment > 2 yrs?]
                  /       \
                Yes        No
                 |          |
           [APPROVE]    [REJECT]
```

**FICO** (Fair Isaac Corporation) uses decision tree-based models in credit scoring — the same principle that banks use to decide whether to approve loan applications.

### Advantages

- Highly interpretable — you can explain exactly why a decision was made.
- Handles both numerical and categorical features.
- No need for feature scaling.
- Can model non-linear relationships.

### Disadvantages

- Prone to **overfitting** — a tree that's too deep memorizes training data and fails on new data. Solution: **Pruning** (removing branches that provide little power) or limiting maximum depth.
- Unstable — small changes in data can produce a very different tree.
- Biased toward features with more levels in categorical data.

### Pruning

Pruning reduces overfitting by removing branches that have low importance:
- **Pre-pruning (Early Stopping)** — Stop growing the tree before it perfectly fits training data (e.g., minimum samples per leaf = 5).
- **Post-pruning** — Grow the full tree, then trim branches that do not improve performance on validation data.

### Random Forest (Extension)

A **Random Forest** is an ensemble of many Decision Trees — instead of trusting one tree's judgment, you train hundreds of trees on different random subsets of data and features, then let them vote. The majority vote wins. One biased tree makes mistakes; 500 diverse trees together are far more reliable.

**How it works — step by step:**

- **Step 1 — Bootstrap Sampling (Bagging):** From the original dataset of `n` rows, randomly sample `n` rows *with replacement* to create a new training set for each tree. Because sampling is with replacement, some rows appear multiple times and some not at all (~37% of rows are left out per tree — these are called **Out-of-Bag (OOB)** samples).
- **Step 2 — Feature Randomness:** At each node split, instead of considering all features, only a **random subset of `m` features** is evaluated (typically `m = √total_features` for classification). This forces diversity — different trees focus on different features, preventing all trees from looking identical.
- **Step 3 — Grow each tree fully:** Each tree is grown without pruning — deliberately allowed to overfit its bootstrap sample. Individual trees have high variance but low bias.
- **Step 4 — Aggregation (Voting):** For a new data point, every tree in the forest independently predicts a class. The final prediction is the **majority vote** across all trees (for classification) or the **mean** (for regression).
- **Step 5 — OOB Evaluation:** The ~37% of rows not used to train each tree serve as a built-in validation set. OOB error is computed without needing a separate test set — a major practical advantage.

**Why it beats a single Decision Tree:**

- A single tree overfits — it memorizes noise in training data. Random Forest's diversity averages out individual errors.
- The key insight: **errors of different trees are uncorrelated** (because of random feature selection). When errors are uncorrelated, averaging reduces variance dramatically while keeping bias low.
- Mathematically: if each tree has error rate `p` and errors are independent, ensemble error approaches 0 as the number of trees grows.

**Feature Importance:**

- Random Forest naturally ranks features by how much they improve splits (measured by Gini impurity reduction) averaged across all trees.
- This makes it useful not just for prediction but for **understanding which features matter most** — e.g., in a loan default model, it might reveal that "credit utilization ratio" matters more than "annual income."

**Key hyperparameters:**

- `n_estimators` — Number of trees. More trees = more stable, but slower. Typically 100–500.
- `max_features` — How many features to consider at each split. Lower = more diversity, higher = stronger individual trees.
- `max_depth` — Maximum depth of each tree. `None` (fully grown) is typical in Random Forests since bagging already controls overfitting.

**Real-world use:** **Kaggle competition winners** consistently use Random Forest as a go-to baseline for structured data. Microsoft's **Xbox Kinect** uses Random Forest to classify body part positions from depth images in real time — processing 200 frames per second across millions of pixels.


## 5. Naïve Bayes Classifier

Naïve Bayes is a probabilistic classifier based on **Bayes' Theorem** — like a doctor diagnosing a patient by calculating: "Given these symptoms (fever, cough, fatigue), which disease is most probable?" The "naïve" part means we assume each symptom is completely **independent** of the others, which is rarely true in reality but works surprisingly well in practice. The algorithm calculates the probability of each class given the observed features and picks the class with the highest posterior probability.

**Bayes' Theorem:**

$$P(C | X) = \frac{P(X | C) \cdot P(C)}{P(X)}$$

Where:
- `P(C | X)` = **Posterior probability** — probability of class `C` given features `X`
- `P(X | C)` = **Likelihood** — probability of observing features `X` if the class is `C`
- `P(C)` = **Prior probability** — initial probability of class `C` before seeing any features
- `P(X)` = **Evidence** — constant for all classes, so it's ignored during comparison

For classification, we pick the class `C` that maximizes the posterior:

$$\hat{C} = \arg\max_{C} P(C) \cdot \prod_{i=1}^{n} P(x_i | C)$$

### Solved Numerical Example — Play Tennis Prediction

**Training Data (10 past days):**

| Day | Weather | Wind | Played Tennis? |
|-----|---------|------|----------------|
| D1 | Sunny | Weak | No |
| D2 | Sunny | Strong | No |
| D3 | Overcast | Weak | Yes |
| D4 | Rainy | Weak | Yes |
| D5 | Rainy | Weak | Yes |
| D6 | Rainy | Strong | No |
| D7 | Overcast | Strong | Yes |
| D8 | Sunny | Weak | No |
| D9 | Sunny | Weak | Yes |
| D10 | Rainy | Weak | Yes |

**Goal:** Predict if tennis will be played on a day with **Weather = Sunny, Wind = Weak**

**Step 1 — Prior Probabilities:**
- P(Yes) = 6/10 = **0.6**
- P(No) = 4/10 = **0.4**

**Step 2 — Likelihoods:**

From Yes days (D3, D4, D5, D7, D9, D10):
- P(Sunny | Yes) = 1/6 ≈ **0.167** *(only D9 is Sunny + Yes)*
- P(Weak | Yes) = 5/6 ≈ **0.833** *(D3, D4, D5, D9, D10 have Weak wind)*

From No days (D1, D2, D6, D8):
- P(Sunny | No) = 3/4 = **0.75** *(D1, D2, D8 are Sunny)*
- P(Weak | No) = 2/4 = **0.5** *(D1, D8 have Weak wind)*

**Step 3 — Compute Posteriors (ignoring the common denominator P(X)):**

P(Yes | Sunny, Weak) ∝ P(Yes) × P(Sunny|Yes) × P(Weak|Yes)
= 0.6 × 0.167 × 0.833 = **0.0835**

P(No | Sunny, Weak) ∝ P(No) × P(Sunny|No) × P(Weak|No)
= 0.4 × 0.75 × 0.5 = **0.15**

**Step 4 — Compare:**

Since 0.15 > 0.0835 → **Prediction: Tennis will NOT be played.**

*Interpretation: Even though it's a calm (Weak wind) day, historically Sunny weather has been strongly associated with not playing — so the model correctly predicts No.*

**Google's Gmail** spam filter uses a form of Naïve Bayes as one component of its multi-layer filtering system.

### Types of Naïve Bayes

- **Gaussian Naïve Bayes** — Features are continuous and assumed to follow a Gaussian (normal) distribution. Used for numerical data like sensor readings.
- **Multinomial Naïve Bayes** — Used for discrete count data. Most common for text classification (word frequencies).
- **Bernoulli Naïve Bayes** — Features are binary (present/absent). Suitable for document classification based on word presence, not frequency.

### Advantages

- Extremely fast to train and predict — computationally cheap even on large datasets.
- Works well with small training datasets.
- Handles high-dimensional data effectively (e.g., thousands of words in text classification).
- Naturally handles multi-class problems.

### Disadvantages

- The independence assumption is almost never true in reality — features are often correlated.
- Zero-frequency problem — if a feature value never appeared in training for a given class, its probability becomes 0, zeroing out the entire product. Solution: **Laplace Smoothing** (add 1 to all counts).
- Not a good estimator of raw probabilities — the numerical outputs are often not well-calibrated.


# UNIT III — Association and Recommendation Systems

## 1. Introduction to Association Rules

Association rule mining finds patterns of the form "if a customer buys X, they also tend to buy Y" — hidden correlations in transactional data. The classic example: **Walmart discovered in the 1990s** that customers who buy diapers frequently also buy beer. There was no intuitive reason for this, but the data revealed it, and Walmart placed beer near diapers — boosting sales of both. Formally, association rule mining discovers rules of the form `{Antecedent} → {Consequent}` in large transactional databases, quantified using Support, Confidence, and Lift.

### Key Metrics

**Support** — How frequently an itemset appears in the dataset:

$$Support(A \cup B) = \frac{\text{Transactions containing both A and B}}{\text{Total transactions}}$$

Support = 0.05 means the itemset appears in 5% of all transactions. Low support rules are rare and may not be commercially significant.

**Confidence** — Given that A is bought, how often B is also bought:

$$Confidence(A \rightarrow B) = \frac{Support(A \cup B)}{Support(A)}$$

Confidence = 0.80 means 80% of the time A is purchased, B is also purchased.

**Lift** — How much more likely B is purchased when A is purchased, compared to B's baseline probability:

$$Lift(A \rightarrow B) = \frac{Confidence(A \rightarrow B)}{Support(B)}$$

- Lift > 1: Positive correlation (buying A increases likelihood of buying B).
- Lift = 1: No relationship (independent events).
- Lift < 1: Negative correlation (buying A decreases likelihood of buying B).

A lift of 2.5 means the presence of A makes B **2.5 times more likely** to be purchased.


## 2. Apriori Algorithm

Apriori is built on one key insight: **if an itemset is rare (infrequent), any larger set containing it will also be rare** — so we can prune it early without wasting computation. We build upward: start with single items, keep only frequent ones, generate pairs from those, keep only frequent pairs, then triplets, and so on — like building a pyramid where only items that pass each layer advance to the next. This is called the **Apriori property** (or *downward closure / anti-monotone property*):

> **If an itemset is infrequent, all its supersets are also infrequent.**

The algorithm performs a **breadth-first search** over itemsets, using multiple full database scans — one per itemset size level.

### Algorithm Steps

Given a transaction database and a minimum support threshold (min_sup):

**Step 1 — Generate L₁ (Frequent 1-itemsets):**
Scan the database, count occurrences of each individual item. Keep only items with support ≥ min_sup.

**Step 2 — Generate C₂ (Candidate 2-itemsets):**
Join frequent 1-itemsets with themselves to generate candidate pairs.

**Step 3 — Prune C₂:**
Remove any candidate whose subset is not in L₁ (Apriori property).

**Step 4 — Generate L₂:**
Scan database, count occurrences of each candidate in C₂. Keep only those with support ≥ min_sup.

**Repeat** until no more frequent itemsets can be found.

**Step 5 — Generate Rules:**
For each frequent itemset, generate all possible rules and calculate confidence. Keep rules with confidence ≥ min_conf.

### Worked Example

Transactions (min_sup = 50% = 2/4 transactions):

| Transaction | Items |
|-------------|-------|
| T1 | Bread, Milk, Diaper |
| T2 | Bread, Beer, Diaper |
| T3 | Milk, Beer, Diaper, Cola |
| T4 | Bread, Milk, Beer, Diaper |

**L₁ (1-itemsets with support ≥ 2):**
- Bread: 3, Milk: 3, Diaper: 4, Beer: 3 → All frequent

**C₂ (Candidates):**
{Bread, Milk}, {Bread, Diaper}, {Bread, Beer}, {Milk, Diaper}, {Milk, Beer}, {Diaper, Beer}

**L₂ (2-itemsets with support ≥ 2):**
- {Bread, Milk}: 2 ✓, {Bread, Diaper}: 3 ✓, {Bread, Beer}: 2 ✓, {Milk, Diaper}: 3 ✓, {Milk, Beer}: 2 ✓, {Diaper, Beer}: 3 ✓

**Sample Rule generation:**
For {Diaper, Beer} with support = 3/4 = 0.75:
- Rule: `{Diaper} → {Beer}`: Confidence = Support({Diaper, Beer}) / Support({Diaper}) = 0.75/1.0 = **0.75 (75%)**
- Rule: `{Beer} → {Diaper}`: Confidence = 0.75/0.75 = **1.0 (100%)**

### Complexity and Limitations

The Apriori algorithm can be slow for large datasets because:
- It requires **multiple full database scans** — one for each itemset size level.
- It generates a large number of candidate itemsets.

## FP-Growth (Frequent Pattern Growth)

FP-Growth is a faster alternative to Apriori that eliminates the two biggest bottlenecks: multiple database scans and massive candidate generation. The core idea is to compress the entire transaction database into a compact tree structure called an **FP-Tree** in just **2 database scans**, then mine frequent patterns directly from the tree — never generating candidate itemsets at all.

### Why FP-Growth over Apriori?

- Apriori scans the database once per itemset size level (k scans for k-length itemsets) and generates huge numbers of candidates.
- FP-Growth always uses exactly **2 database scans** regardless of the length of patterns.
- No candidate generation means no memory wastage on itemsets that turn out to be infrequent.
- In practice, FP-Growth is **10–100x faster** than Apriori on dense datasets.

### Key Concepts

**FP-Tree** — A compressed, prefix-tree representation of the transaction database. Each path from root to leaf represents a set of transactions that share a common prefix of items. Shared prefixes are merged, making the tree much smaller than the original database.

**Header Table** — A table listing all frequent items (those meeting min_sup), sorted by their frequency in **descending order**. Each entry also holds a pointer to the first occurrence of that item in the FP-Tree, linking all nodes of the same item together via **node-link pointers**.

**Conditional Pattern Base** — For a given item X, it is the set of all prefix paths in the FP-Tree that end at a node labeled X. It tells you "what items always appear alongside X."

**Conditional FP-Tree** — An FP-Tree built from the Conditional Pattern Base of item X. Mining this tree gives all frequent itemsets that contain X.

### FP-Growth Algorithm — Steps

1. **Scan 1:** Count support of every individual item. Remove items below min_sup. Sort remaining items by frequency descending — this is the **frequent item order**.
2. **Build FP-Tree (Scan 2):** Re-read each transaction, keep only frequent items, sort them in the frequent item order, and insert into the tree. Shared prefixes are merged (count incremented). Build the Header Table simultaneously.
3. **Mine the FP-Tree:** For each item in the Header Table (least frequent first), find its Conditional Pattern Base, build its Conditional FP-Tree, and extract all frequent itemsets recursively.

### Solved Numerical Example

**Transactions (min_sup = 3):**

| TID | Items |
|-----|-------|
| T1 | A, B, C, D |
| T2 | A, B, D |
| T3 | A, B |
| T4 | A, C, D |
| T5 | B, C |

**Step 1 — Scan 1: Count item frequencies and filter**

| Item | Count | ≥ min_sup=3? |
|------|-------|--------------|
| A | 4 | ✓ |
| B | 4 | ✓ |
| C | 3 | ✓ |
| D | 3 | ✓ |

All 4 items are frequent. **Sort order by frequency (desc): A(4) → B(4) → C(3) → D(3)**
*(Tie between A and B, and C and D — break ties alphabetically)*

**Step 2 — Scan 2: Reorder each transaction and build FP-Tree**

Reorder items in each transaction according to the frequent item order:

| TID | Original | Reordered |
|-----|----------|-----------|
| T1 | A,B,C,D | A→B→C→D |
| T2 | A,B,D | A→B→D |
| T3 | A,B | A→B |
| T4 | A,C,D | A→C→D |
| T5 | B,C | B→C |

**Insert transactions one by one into the FP-Tree:**

After T1 `(A→B→C→D)`:
```
root
 └─ A:1
     └─ B:1
         └─ C:1
             └─ D:1
```

After T2 `(A→B→D)` — shares prefix A→B:
```
root
 └─ A:2
     └─ B:2
         ├─ C:1
         │   └─ D:1
         └─ D:1
```

After T3 `(A→B)` — shares prefix A→B:
```
root
 └─ A:3
     └─ B:3
         ├─ C:1
         │   └─ D:1
         └─ D:1
```

After T4 `(A→C→D)` — shares prefix A only:
```
root
 └─ A:4
     ├─ B:3
     │   ├─ C:1
     │   │   └─ D:1
     │   └─ D:1
     └─ C:1
         └─ D:1
```

After T5 `(B→C)` — no shared prefix with A, starts a new branch:
```
root
 ├─ A:4
 │   ├─ B:3
 │   │   ├─ C:1
 │   │   │   └─ D:1
 │   │   └─ D:1
 │   └─ C:1
 │       └─ D:1
 └─ B:1
     └─ C:1
```

**Final FP-Tree + Header Table:**

| Item | Count | Node Links |
|------|-------|------------|
| A | 4 | → A:4 |
| B | 4 | → B:3 → B:1 |
| C | 3 | → C:1 (under A→B) → C:1 (under A) → C:1 (under B) |
| D | 3 | → D:1 (under A→B→C) → D:1 (under A→B) → D:1 (under A→C) |

**Step 3 — Mine the FP-Tree (process least frequent items first: D, C, B, A)**

**Mining item D (support = 3):**

Follow node links for D to find all prefix paths (Conditional Pattern Base):
- D under A→B→C: prefix path = **{A:1, B:1, C:1}**
- D under A→B: prefix path = **{A:1, B:1}**
- D under A→C: prefix path = **{A:1, C:1}**

Conditional Pattern Base for D:

| Prefix Path | Count |
|-------------|-------|
| A, B, C | 1 |
| A, B | 1 |
| A, C | 1 |

Count items in the conditional pattern base: A=3, B=2, C=2. With min_sup=3, only **A** is frequent.

Conditional FP-Tree for D: just `{A:3}`

Frequent itemsets containing D: **{D:3}, {A,D:3}**

*(B and C don't meet min_sup=3 in D's context, so {B,D}, {C,D} are not frequent)*

**Mining item C (support = 3):**

Prefix paths for C nodes:
- C under A→B: **{A:1, B:1}**
- C under A: **{A:1}**
- C under B: **{B:1}**

Count in conditional pattern base: A=2, B=2. Neither meets min_sup=3.

Conditional FP-Tree for C: **empty**

Frequent itemsets containing C: **{C:3}** only.

**Mining item B (support = 4):**

Prefix paths for B nodes:
- B:3 under A: **{A:3}**
- B:1 (root-level): **{}** (empty prefix)

Count in conditional pattern base: A=3. Meets min_sup=3.

Conditional FP-Tree for B: `{A:3}`

Frequent itemsets containing B: **{B:4}, {A,B:3}**

**Mining item A (support = 4):**

A is the most frequent item. Its prefix path is always just the root (nothing above it).

Conditional Pattern Base: empty.

Frequent itemsets containing A: **{A:4}** only.

**Final Result — All Frequent Itemsets:**

| Itemset | Support |
|---------|---------|
| {A} | 4 |
| {B} | 4 |
| {C} | 3 |
| {D} | 3 |
| {A, B} | 3 |
| {A, D} | 3 |

These are all itemsets with support ≥ 3. Association rules can now be generated from these just like in Apriori — without ever having scanned the database more than twice or generated a single explicit candidate.


## 3. Practical Applications of Association Rules

**Market Basket Analysis** — The foundational application. Supermarkets analyze point-of-sale data to understand which products are frequently purchased together. **Target** famously predicted a teenage girl's pregnancy before her father knew, based on purchasing patterns (unscented lotion, large bags of cotton balls, hand sanitizer) — a real case of association rules revealing sensitive correlations.

**Cross-Selling and Upselling** — E-commerce platforms use association rules to show "Frequently Bought Together" suggestions. Amazon's "Customers who bought this also bought..." feature is powered by association rule-style collaborative recommendations.

**Medical Diagnosis** — Mining patient records to find co-occurring symptoms and diseases. Finding that patients with symptom A and symptom B frequently develop disease X enables early preventive treatment.

**Fraud Detection** — In insurance, association rules identify suspicious claim patterns — e.g., certain combinations of symptoms and treatments frequently appear in fraudulent auto accident claims.

**Web Usage Mining** — Websites analyze clickstream logs to find which pages are frequently visited together, enabling better navigation design and personalized content delivery.


## 4. MapReduce for Association Analysis

### Why MapReduce for Association Mining?

Association rule mining on billions of transactions (like those at Walmart or Amazon) cannot run on a single machine. The dataset cannot even fit in memory. MapReduce distributes the computation across a cluster.

### MapReduce Paradigm

MapReduce is a programming model for processing large datasets in parallel across a distributed cluster. It has two core phases:

**Map Phase** — Each mapper receives a partition of the data (a set of transactions) and emits `(key, value)` pairs. For association mining, a mapper might emit each item (or itemset) in a transaction as a key with value 1.

**Shuffle & Sort Phase** — The framework automatically groups all values by key, so all counts for the same item arrive at the same reducer.

**Reduce Phase** — Each reducer receives a key and a list of values, and aggregates them. For counting, it sums all the 1s to get the total support count for each itemset.

```
                    MAPREDUCE FLOW
                    ──────────────
  INPUT DATA (split into chunks)
  ┌──────────┐  ┌──────────┐  ┌──────────┐
  │ Chunk 1  │  │ Chunk 2  │  │ Chunk 3  │
  └────┬─────┘  └────┬─────┘  └────┬─────┘
       │              │              │
       ▼              ▼              ▼
  ┌─────────┐   ┌─────────┐   ┌─────────┐
  │ Mapper1 │   │ Mapper2 │   │ Mapper3 │   MAP PHASE
  │(A,1)    │   │(B,1)    │   │(A,1)    │   emit (key,1)
  │(B,1)    │   │(A,1)    │   │(C,1)    │   per item
  └────┬────┘   └────┬────┘   └────┬────┘
       │              │              │
       └──────────────┼──────────────┘
                      │ SHUFFLE & SORT
                      │ (group by key)
          ┌───────────┼───────────┐
          ▼           ▼           ▼
      (A,[1,1,1]) (B,[1,1])   (C,[1])
          │           │           │
          ▼           ▼           ▼
     ┌─────────┐ ┌─────────┐ ┌─────────┐
     │Reducer A│ │Reducer B│ │Reducer C│  REDUCE PHASE
     │  A = 3  │ │  B = 2  │ │  C = 1  │  sum values
     └─────────┘ └─────────┘ └─────────┘
  OUTPUT: { A:3, B:2, C:1 }
```

### Apriori with MapReduce

**Round 1 (L₁ generation):**
- **Map:** For each transaction, emit `(item, 1)` for every item.
- **Reduce:** Sum counts. Output items with count ≥ min_sup.

**Round 2 (L₂ generation):**
- **Map:** Generate all pairs from each transaction. Emit `(pair, 1)` for pairs where both items are in L₁.
- **Reduce:** Sum counts. Output pairs with count ≥ min_sup.

Each round requires one MapReduce job. Generating Lₖ requires `k` rounds.

### SON Algorithm (Savasere, Omiecinski, Navathe)

SON is an optimized two-pass algorithm designed for MapReduce:
- **Pass 1:** Divide data into chunks. Find frequent itemsets locally in each chunk (using min_sup scaled to chunk size). A globally frequent itemset must be locally frequent in at least one chunk.
- **Pass 2:** Use all locally frequent itemsets as candidates and count their global support across the full dataset.

This reduces false negatives while keeping the computational cost tractable.


## 5. Recommendation Systems

### Types of Recommendation Systems

**Content-Based Filtering** — Recommends items similar to items the user has previously liked, based on item features (content). If you watched sci-fi movies, the system recommends other sci-fi movies based on genre, director, cast. **Pandora's Music Genome Project** analyzes over 450 musical attributes per song and recommends music based on the attributes of songs you've liked.

**Collaborative Filtering** — Recommends items that similar users have liked, based on user-item interaction history — without using any content features. "Users like you also liked..."

- **User-Based CF:** Find users most similar to the target user. Recommend what they liked that the target hasn't seen yet.
- **Item-Based CF:** Find items most similar to what the target user has liked. **Amazon** uses item-based CF because items change less frequently than user preferences, making it more stable.

**Matrix Factorization (Model-Based CF)** — Represents the user-item interaction matrix as the product of two lower-dimensional matrices (user-factor matrix and item-factor matrix). **Singular Value Decomposition (SVD)** and **Alternating Least Squares (ALS)** are used. **Netflix Prize** ($1M competition) was won by a team using an ensemble of matrix factorization models — reducing Netflix's prediction error by 10%.

**Hybrid Systems** — Combine content-based and collaborative filtering. **Netflix** uses a hybrid: collaborative filtering to find similar users, content-based analysis of metadata (genre, cast, director), and deep learning on visual features of film thumbnails to optimize click-through rates.

### Challenges in Recommendation Systems

**Cold Start Problem** — For new users or new items, there is no interaction history to base recommendations on. Solutions: Ask users for initial preferences during onboarding, or use content-based filtering until enough interactions are collected. Spotify's "Discover Weekly" solves new-user cold start by using demographic data and brief listening sessions before building a full profile.

**Sparsity** — Most users interact with a tiny fraction of all available items. A user-item matrix for Netflix (millions of users × thousands of titles) is extremely sparse. Techniques: matrix factorization, dimensionality reduction.

**Scalability** — Computing similarities between all user pairs or all item pairs is O(n²). At millions of users, this is computationally prohibitive. Solutions: Approximate nearest neighbor algorithms (like **Locality Sensitive Hashing**) or distributed computing with Spark.


# UNIT IV — Stream Data and Real-Time Analytics

## 1. Understanding Stream Data

Traditional data processing is like filling a bucket, then analyzing it when full. Stream data processing is like measuring the flow as it comes out of the tap — you analyze it in real time, as it flows, without waiting for it to accumulate. Formally, **data streams** are sequences of data records generated continuously and rapidly from sources like IoT sensors, social media feeds, financial markets, clickstreams, and log files, with these key characteristics:

- **Unbounded** — There is no defined end to the stream.
- **Ordered** — Records arrive in time order (or approximately so).
- **Non-revisitable** — In pure streaming systems, you cannot go back and reprocess old data (unlike stored datasets). Data must be processed as it arrives or within a small time window.
- **High velocity** — Data arrives faster than it can be stored persistently in traditional databases.

### Sliding Windows

Since stream data is infinite, analysis is performed over **windows** — finite subsets of the stream:

- **Tumbling Window** — Fixed-size, non-overlapping time windows. Example: Aggregate Twitter mentions of a hashtag every 5 minutes. After each 5-minute window closes, it resets.
- **Sliding Window** — Overlapping windows that move at a fixed step. Example: Count tweets in the last 10 minutes, updated every 1 minute. The window slides forward by 1 minute each time.
- **Session Window** — Windows defined by user activity sessions. A window opens when activity begins and closes after a period of inactivity.


## 2. Introduction to Stream Computing

The fundamental limitation of batch processing (like Hadoop MapReduce) is **latency** — collect data, store it, then process it, introducing delays of minutes to hours. For fraud detection, this is unacceptable: you cannot detect a fraudulent credit card transaction 30 minutes after it happened. Stream computing processes data **as it arrives**, enabling responses in **milliseconds to seconds**.

### Key Stream Processing Frameworks

**Apache Kafka** — A distributed, fault-tolerant **message streaming platform**. Kafka acts as the data backbone — producers publish messages (events) to **topics**, and consumers subscribe to those topics and read messages in real time. Kafka persists messages on disk for a configurable retention period, allowing consumers to replay streams. **LinkedIn** originally developed Kafka to handle over **7 trillion messages per day** across its platform.

Kafka Architecture:
- **Producer** — Application that writes data to a Kafka topic.
- **Topic** — A named stream/channel for a specific category of data (e.g., "user-clicks," "transactions").
- **Partition** — Each topic is split into partitions for parallelism. Different consumers can read different partitions simultaneously.
- **Consumer** — Application that reads data from a Kafka topic.
- **Broker** — Kafka server that stores messages.
- **Zookeeper** — Manages cluster metadata and leader election (being replaced by Kafka's own KRaft protocol).

**Apache Spark Streaming** — An extension of Apache Spark that enables scalable, fault-tolerant stream processing. It uses a **micro-batch** model: incoming data is divided into small batches (e.g., every 1 second), and each batch is processed using Spark's batch engine. This achieves near-real-time processing. Spark's **Structured Streaming** (newer API) treats the stream as an unbounded table that continuously grows.

**Apache Flink** — A true **event-driven** stream processing framework (unlike Spark's micro-batch approach). Flink processes each event individually as it arrives, achieving genuine real-time processing with low latency. Flink is used by **Alibaba** to process over **4.4 trillion events per day** during peak shopping events like Singles' Day.

**Apache Storm** — One of the earliest real-time stream processing frameworks. Uses a **topology** model: a directed acyclic graph (DAG) of **Spouts** (data sources) and **Bolts** (processing units). Twitter (now X) developed Storm to process trending topics in real time.

### Lambda Architecture

A common Big Data architecture that combines batch and stream processing:

- **Batch Layer** — Recomputes results on the full historical dataset periodically. Slow but accurate. Hadoop/Spark batch jobs.
- **Speed Layer** — Processes real-time stream data for low-latency results. Results are approximate but fresh. Apache Storm/Flink.
- **Serving Layer** — Merges results from both layers to answer queries. Apache Cassandra, HBase.

**Twitter** uses Lambda Architecture to provide both real-time trending topics (speed layer) and accurate long-term analytics (batch layer).

```
                    LAMBDA ARCHITECTURE
                    ───────────────────
                ┌───────────────────────┐
                │      DATA SOURCE      │
                │  (events / streams)   │
                └──────────┬────────────┘
                           │
               ┌───────────┴────────────┐
               │                        │
               ▼                        ▼
  ┌────────────────────┐    ┌─────────────────────┐
  │    BATCH LAYER     │    │    SPEED LAYER       │
  │  (Hadoop / Spark)  │    │  (Storm / Flink /   │
  │                    │    │   Spark Streaming)   │
  │  Full recompute    │    │  Real-time only,     │
  │  on all history    │    │  recent data only    │
  │  Slow but accurate │    │  Fast but approx.    │
  └─────────┬──────────┘    └──────────┬───────────┘
            │                          │
            └──────────┬───────────────┘
                       ▼
           ┌───────────────────────┐
           │     SERVING LAYER     │
           │  (HBase / Cassandra)  │
           │  Merges batch views   │
           │  + real-time views    │
           │  → answers queries    │
           └───────────────────────┘
```


## 3. Real-Time Analytics Applications

**Financial Fraud Detection** — **VISA's** fraud detection system processes every card transaction through a real-time scoring engine powered by machine learning. Over **65,000 transaction messages per second** are processed, each scored and flagged within 2 milliseconds — before the merchant even receives authorization.

**Real-Time Recommendation Systems** — **Spotify's** "What's Playing Now" recommendation updates as you listen. If you skip a song, the system immediately adjusts the queue using real-time processing of your current behavior.

**Network Intrusion Detection** — Telecom and enterprise networks use stream processing to detect cyberattacks in real time. Unusual spikes in network traffic volume, unexpected connection patterns, and known malicious IP signatures trigger alerts within seconds.

**Smart Traffic Management** — Cities like **Singapore** and **Los Angeles** use IoT sensors and cameras to stream traffic density data to central analytics platforms. Real-time processing adjusts signal timing dynamically to minimize congestion.

**Healthcare Patient Monitoring** — ICU patient monitoring systems stream vital sign data (heart rate, blood pressure, SpO₂) to real-time analytics engines that trigger alerts when readings deviate from safe ranges. **Philips HealthSuite** processes telemetry streams from millions of connected medical devices globally.

**Social Media Trend Detection** — Twitter's trending topics algorithm processes hundreds of millions of tweets per day as a stream, detecting emerging trends by analyzing velocity and engagement of hashtags in real time using sliding windows.


## 4. Introduction to Graph Analytics

A graph is a network of connected entities — Facebook is a graph of people (nodes) connected by friendships (edges); the internet is a graph of web pages connected by hyperlinks. Graph analytics understands these networks: who is most influential, how information spreads, which nodes form communities, and what the shortest path between two nodes is. Formally, a **graph** `G = (V, E)` consists of **Vertices (V)** — entities — and **Edges (E)** — relationships between them.

Graphs can be:
- **Directed** — Edges have direction (A → B ≠ B → A). Example: Twitter followers (you can follow someone who doesn't follow you back).
- **Undirected** — Edges are bidirectional (A—B = B—A). Example: Facebook friendships (mutual).
- **Weighted** — Edges have numerical weights. Example: Road distances, transaction amounts.

### Key Graph Analytics Algorithms

**PageRank** — Developed by Larry Page and Sergey Brin as the foundation of **Google Search**. PageRank measures the importance of a web page by counting the number and quality of links pointing to it. A page linked by many highly-ranked pages gets a high PageRank. Mathematically, it assigns a probability score representing how likely a random internet user surfing from link to link would land on a given page.

$$PR(A) = \frac{1-d}{N} + d \sum_{i \in Links(A)} \frac{PR(i)}{L(i)}$$

where `d` is the damping factor (typically 0.85), `N` is total pages, `L(i)` is the number of outbound links from page `i`.

**Shortest Path (Dijkstra's Algorithm)** — Finds the minimum-cost path between two nodes in a weighted graph. **Google Maps** uses variants of Dijkstra's and A* algorithms to find the fastest route between two locations in real time, factoring in live traffic data.

**Community Detection (Louvain Algorithm)** — Groups densely interconnected nodes into communities. **Facebook** uses community detection to identify social circles and friend groups, which informs content ranking in the News Feed (posts from within your community rank higher).

**Centrality Measures:**
- **Degree Centrality** — Number of edges connected to a node. A person with many friends has high degree centrality.
- **Betweenness Centrality** — How often a node lies on the shortest path between other nodes. High betweenness nodes are "brokers" in the network — removing them disconnects others. Used in **epidemiology** to identify super-spreaders in disease networks.
- **Eigenvector Centrality** — A node is important if it is connected to other important nodes. PageRank is a variant of eigenvector centrality.

### Graph Processing Frameworks

**Apache Giraph** — Open-source graph processing framework inspired by Google's **Pregel**. Used at **Facebook** to process social graphs with over 1 trillion edges.

**Neo4j** — The most widely used **graph database**, built for storing and querying graph data natively. **eBay** uses Neo4j to power its shipping route recommendation system, finding optimal logistics paths across its global fulfillment network.

**GraphX** — Apache Spark's graph analytics library, integrating graph computation with Spark's broader distributed data processing ecosystem.

### Applications of Graph Analytics

**Social Network Analysis** — LinkedIn uses graph analytics to power "People You May Know" — finding second and third-degree connections (friends of friends). **Six Degrees of Separation** is a real graph property: on average, any two people on Earth are connected by at most 6 intermediate connections.

**Supply Chain Optimization** — Manufacturing companies model their supply chains as graphs (factories, warehouses, suppliers as nodes; shipping routes as edges). Graph analytics finds bottlenecks and optimizes logistics.

**Knowledge Graphs** — **Google's Knowledge Graph** represents facts about the world as a graph (entities and their relationships), enabling the information panels that appear in search results (e.g., "Elon Musk → CEO of → Tesla").

**Recommendation Systems via Graph** — Pinterest uses a graph-based recommendation algorithm called **Pixie**, which performs random walks on a graph of users and content (pins) to surface personalized recommendations.


# UNIT V — NoSQL Data Management

## 1. NoSQL Databases — Introduction

Relational databases are like a perfectly organized spreadsheet — every row has the same columns, and everything fits neatly. This is great for bank records but terrible for storing a tweet (0 to 100 hashtags), a product catalog (each product has entirely different attributes), or a social network (where relationships matter more than the data itself). **NoSQL** (Not Only SQL) refers to a broad class of database systems that abandon fixed tabular schemas in favor of flexibility, horizontal scaling, and distributed architecture — optimized for specific data models: key-value, document, wide-column, or graph.

### Why NoSQL?

Traditional RDBMS systems struggle with Big Data because:

- **Fixed Schema** — Adding a new attribute to a table with billions of rows in a traditional RDBMS requires an expensive `ALTER TABLE` operation that can take hours and lock the table.
- **Vertical Scaling Only** — SQL databases scale by upgrading hardware (bigger servers). NoSQL databases scale **horizontally** — add more commodity machines to the cluster.
- **Joins are Expensive at Scale** — JOINing tables with billions of rows is computationally intensive. NoSQL avoids joins by denormalizing data.
- **Unstructured Data** — RDBMS cannot natively store JSON, arrays, or nested objects. NoSQL handles these naturally.

### CAP Theorem

The **CAP Theorem** (Brewer's Theorem) states that a distributed system can guarantee at most **2 of 3** properties simultaneously:

- **Consistency (C)** — Every read receives the most recent write (or an error). All nodes see the same data at the same time.
- **Availability (A)** — Every request receives a response (not necessarily the most recent data).
- **Partition Tolerance (P)** — The system continues to operate even if some nodes cannot communicate (network partition).

Since network partitions are unavoidable in distributed systems, systems must choose between **CP** (consistent but may be unavailable during partition) and **AP** (always available but may return stale data).

```
                    CAP THEOREM TRIANGLE
                    ─────────────────────
                         Consistency
                              △
                             /|\
                            / | \
                           /  |  \
               MongoDB,   /   |   \  Traditional
               HBase,    / CP | CA \  RDBMS
               Zookeeper/    |    \ (MySQL, Postgres)
                        /─────┴─────\
                       /      P      \
                      /   Partition   \
                     /    Tolerance    \
                    ────────────────────
                   AP                  (impossible
             Cassandra,                 to achieve
             CouchDB,                  all 3 in a
             DynamoDB                  distributed
                                        system)
         ─────────────────────────────────────────
         Pick any 2. Since P is always required
         in distributed systems → choose CP or AP.
```

- **CP Systems:** MongoDB, HBase, Apache Zookeeper
- **AP Systems:** Cassandra, CouchDB, DynamoDB
- **CA Systems:** Traditional RDBMS (but these fail in distributed environments)

**PACELC** is an extension of CAP that also considers the trade-off between latency and consistency even when there is no partition.


## 2. Schema-less Models and Their Flexibility

A schema defines the structure of data — column names, data types, constraints. In relational databases, schemas are **rigid** and **predefined**. In NoSQL databases, schemas are **dynamic** (schema-less or schema-flexible).

**Schema-less** means each record (document, row, node) can have different fields. You do not need to define the structure in advance. This enables:

- **Rapid iteration** — Developers can add new fields to documents without database migrations.
- **Heterogeneous data** — Different records in the same collection can have different shapes. An e-commerce product database might have electronics with voltage/wattage fields and clothing with size/color fields — in the same collection.
- **JSON-native storage** — Most NoSQL document stores natively store data as JSON or BSON (binary JSON), matching the format used by web APIs and modern application code.

**Tradeoff** — Schema-less databases push validation responsibility to the application layer. There is no database-enforced constraint preventing insertion of invalid data. This requires disciplined application design.

**Mongoose** (ODM for MongoDB in Node.js) is a popular library that adds optional schema enforcement back to MongoDB — allowing teams to get NoSQL flexibility with some SQL-like structure guarantees.


## 3. Key-Value Stores

A key-value store is like a giant dictionary or hashmap — you store data under a unique key, and to retrieve it, you just provide that key. The database doesn't know or care what the value contains; it just stores and retrieves it at extremely high speed. Technically, data is stored as **`(key, value)`** pairs where the key is a unique identifier and the value is opaque data — a string, integer, JSON object, binary blob, or any data type. The database does not inspect or index the value.

Operations: `PUT(key, value)`, `GET(key) → value`, `DELETE(key)`.

### When to Use

Key-value stores excel when:
- Data access is **always by primary key** — you always know the exact key.
- You need **extremely fast reads and writes** — no parsing, no query planning.
- The data is **self-contained** per key — no need to query across keys.

### Examples

**Redis (Remote Dictionary Server)** — An in-memory key-value store with support for complex value types: strings, lists, sets, sorted sets, hashes. Redis stores data in RAM, making it extremely fast (microsecond latency). Used extensively as a **caching layer** in front of slower databases. **Twitter** uses Redis to cache timelines — each user's timeline is stored as a sorted set in Redis, giving sub-millisecond delivery of tweet feeds.

**Amazon DynamoDB** — A fully managed, distributed key-value store built by Amazon. It powers many of Amazon's own services internally. DynamoDB guarantees **single-digit millisecond latency** at any scale. **Samsung** uses DynamoDB to handle over 4 million+ requests per second from its IoT devices during peak hours.

**Apache Cassandra** (also a wide-column store) — Originally designed at Facebook for the Inbox search feature. Optimized for write-heavy workloads. **Netflix** uses Cassandra to store viewing history and manage session data for its 200+ million subscribers globally.

### Limitations

- No complex queries — you cannot filter by value or perform JOINs.
- No relationships between keys — data model must be designed around key access patterns.
- Requires denormalization — the same data may need to be stored under multiple keys for different access patterns.


## 4. Document Stores

Document stores are key-value stores where the "value" is a structured document (usually JSON) that the database understands and can query inside. Instead of a flat key → opaque blob, you store rich nested objects and can query any field within them — like a self-describing record that contains everything you need without JOINing other tables. Technically, document stores store, retrieve, and manage **semi-structured documents** (JSON, BSON, or XML), each with a unique **document ID** and a flexible set of nested key-value fields. No fixed schema — documents in the same collection can have completely different fields, but any field can be indexed for querying.

### MongoDB

MongoDB is the most widely used document database. Data model:
- **Database** → contains Collections
- **Collection** → contains Documents (analogous to a table of rows in RDBMS)
- **Document** → a BSON (Binary JSON) object

```json
{
  "_id": ObjectId("507f1f77bcf86cd799439011"),
  "name": "John Doe",
  "email": "john@example.com",
  "orders": [
    {"product": "Laptop", "price": 999.99, "qty": 1},
    {"product": "Mouse", "price": 29.99, "qty": 2}
  ],
  "address": {
    "city": "Mumbai",
    "pin": "400001"
  }
}
```

Key query operations:
```javascript
// Find all users from Mumbai
db.users.find({"address.city": "Mumbai"})

// Find expensive orders
db.users.find({"orders.price": {$gt: 500}})
```

**Uber** uses MongoDB to store **geospatial data** — driver locations are stored as GeoJSON documents, and MongoDB's geospatial indexes allow querying "find all available drivers within 5 km of this GPS coordinate" in real time.

### CouchDB

Apache CouchDB stores data as JSON documents and is accessed via a **RESTful HTTP API** — making it easily accessible from any programming language. CouchDB uses **Multi-Version Concurrency Control (MVCC)** and is designed for **offline-first** applications that can sync data when connectivity is restored. **IBM Cloudant** (built on CouchDB) is used in healthcare applications where field workers need to update patient records offline and sync to the central database when they return to a connected area.

### When to Use Document Stores

- Content management systems, catalogs, user profiles, product listings.
- Applications with flexible, evolving schemas.
- When data is naturally hierarchical (nested objects and arrays).
- When you need to query by multiple fields, not just a primary key.


## 5. Tabular (Wide-Column) Data Stores

Wide-column stores are like a spreadsheet where each row can have completely different columns — and there can be millions of them. Each row is identified by a **row key**, and under it, you store any set of column-value pairs, with different rows having totally different columns. This makes it ideal for time-series data (each timestamp is a column) and sparse data (most rows use only a fraction of possible columns). Technically, wide-column stores organize data as:

```
Row Key → Column Family → Column Qualifier → Value (with timestamp)
```

Each cell is **timestamped**, allowing multiple versions to coexist — the most recent version is returned by default. Column families are predefined at schema creation, but columns within a family are added dynamically at write time.

### Apache HBase

HBase is an open-source wide-column store built on top of HDFS, modeled after **Google BigTable** (2006). HBase architecture:

- **HMaster** — Manages region assignment, load balancing, and schema changes. Analogous to HDFS's NameNode.
- **RegionServer** — Manages a set of **Regions** (contiguous ranges of row keys). Handles read and write requests for its regions.
- **Region** — A subset of the HBase table, containing a range of rows. When a region grows too large, it is automatically split.
- **ZooKeeper** — Coordinates HBase's distributed components, manages HMaster failover, and maintains cluster state.

HBase Row Model:
```
Row Key: "user_12345"
  Column Family: profile
    name: "Ravi Sharma"
    city: "Delhi"
  Column Family: activity
    last_login: "2026-02-20 10:30:00"
    total_purchases: "47"
```

**Facebook** originally used HBase to power its **Messages** feature, storing billions of messages across its user base. At peak, HBase handled over **20 petabytes** of message data.

### Google BigTable

BigTable is Google's proprietary wide-column store and was described in a landmark 2006 paper by Chang et al. It powers several of Google's core services:

- **Google Analytics** uses BigTable to store website traffic data for billions of websites.
- **Google Earth** stores satellite imagery tiles in BigTable — each tile is a cell value, keyed by geographic coordinates and zoom level.
- **Gmail** stores email data in BigTable.

BigTable's key insight: by using the row key, column family, column qualifier, and timestamp as a multi-dimensional key, it achieves extremely efficient **range scans** — reads of contiguous row key ranges are very fast because data is stored sorted by row key.

### Apache Cassandra

Cassandra is a **distributed**, **leaderless** wide-column store developed by Facebook (2008) and open-sourced through Apache. It is designed for **high write throughput** and **high availability** with no single point of failure.

Key features:
- **Peer-to-peer architecture** — No master node. Every node is equal. Data is replicated across multiple nodes automatically.
- **Tunable Consistency** — You choose consistency level per query: ONE (fastest, least consistent) to ALL (slowest, most consistent). QUORUM is a common middle ground.
- **Ring topology** — Nodes are arranged in a logical ring. Data is distributed using **consistent hashing** on the partition key.
- **CQL (Cassandra Query Language)** — SQL-like syntax but with NoSQL semantics. No JOINs or subqueries.

**Instagram** uses Cassandra to store over **1 billion user photos** and their associated metadata, supporting billions of reads and writes daily.

Cassandra Data Model:
```sql
CREATE TABLE user_activity (
    user_id UUID,
    activity_time TIMESTAMP,
    action TEXT,
    details TEXT,
    PRIMARY KEY (user_id, activity_time)
) WITH CLUSTERING ORDER BY (activity_time DESC);
```

Here, `user_id` is the partition key (determines which node stores the data), and `activity_time` is the clustering key (determines sort order within the partition).


## 6. Graph Databases

Graph databases store data as a network of nodes and edges — finding "friends of friends" in a relational database requires expensive multi-level JOINs; in a graph database, you simply traverse the edges, like following paths on a map instead of doing address lookups in a spreadsheet. Technically, graph databases store **nodes** (entities), **edges** (relationships), and **properties** (attributes on both). They are optimized for **traversal queries** — following relationships across many levels. **Native graph processing** systems like Neo4j store relationships directly on disk adjacent to the nodes they connect, enabling **index-free adjacency**: to find connected nodes, you follow a pointer — no index lookup required.

### Neo4j and Cypher Query Language

**Neo4j** is the world's most popular graph database. It uses **Cypher**, a declarative query language optimized for graph traversal.

```cypher
// Find all friends of Alice who also know Bob
MATCH (alice:Person {name: "Alice"})-[:FRIEND]->(friend)-[:FRIEND]->(bob:Person {name: "Bob"})
RETURN friend.name

// Find the shortest path between Alice and Charlie
MATCH path = shortestPath((alice:Person {name: "Alice"})-[*]-(charlie:Person {name: "Charlie"}))
RETURN path
```

**Panama Papers investigation** — Journalists at ICIJ (International Consortium of Investigative Journalists) used Neo4j to analyze 11.5 million leaked documents about offshore tax havens. The interconnected network of companies, people, and accounts — impossible to analyze with spreadsheets — was mapped as a graph, revealing links between world leaders, corporations, and offshore accounts.

### Use Cases for Graph Databases

**Fraud Detection** — Banks use graph databases to detect fraud rings. A single fraudulent transaction looks innocent in isolation, but a graph reveals that the same phone number, address, or device is connected to dozens of different accounts — a pattern that indicates identity fraud. **PayPal** uses graph-based fraud detection to protect hundreds of millions of transactions.

**Knowledge Graphs** — Google's Knowledge Graph (2012) represents over **500 billion facts** about 5 billion entities as a graph, enabling Google to answer complex natural language queries (e.g., "Who is the wife of the president of France?") by traversing entity relationships.

**Network and IT Operations** — IT infrastructure (servers, switches, routers, virtual machines, services) naturally forms a graph. When a service goes down, graph traversal quickly identifies which upstream dependencies caused the failure.

**Drug Discovery** — Pharmaceutical companies model the interactions between genes, proteins, diseases, and drugs as a graph. Graph traversal reveals indirect relationships — e.g., a drug targeting gene A might affect disease X via a path: Gene A → Protein B → Pathway C → Disease X. **AstraZeneca** uses graph analytics in its drug discovery pipeline.

### Comparison: Neo4j vs Relational DB for Relationship Queries

For a social network with 1 million users, finding 4th-degree connections (friends of friends of friends of friends):

| System | Query Time |
|--------|-----------|
| Relational DB (MySQL) | 4+ hours (multiple JOINs) |
| Neo4j (Graph DB) | **2 seconds** |

Source: Neo4j benchmark study. This illustrates why graph databases are not just a preference but a practical necessity for relationship-heavy workloads.


## Summary Comparison of NoSQL Databases

| Type | Example | Data Model | Best For | Example Use Case |
|------|---------|------------|----------|-----------------|
| Key-Value | Redis, DynamoDB | key → value | Caching, sessions | Twitter timeline cache |
| Document | MongoDB, CouchDB | key → JSON doc | Catalogs, profiles | Uber driver locations |
| Wide-Column | HBase, Cassandra | row → col families | Time-series, analytics | Instagram photos |
| Graph | Neo4j | nodes + edges | Relationships, networks | Panama Papers investigation |



