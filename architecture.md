# 🚀 ScyllaDB Concepts - A Fun Theory Class!

> **Gonna be a theory class!!!** Don't be bored, or make your face sleepy 😴 -> *joke*

I'm gonna try to make this interesting! 😆

---

## 🛠 General Concepts:

### 🔁 Replication:
Making multiple copies of data spread across nodes to **prevent data loss**.

### 🔀 Sharding:
Dividing data into smaller parts (**shards**) and storing across various nodes.

💡 *These two are database techniques used for improving scalability, availability, and fault tolerance.*

### 📦 Node:
A **database instance** used to store the data.

### 🏢 Cluster:
A **group of nodes** forming a cluster to store and replicate data.

---

## 🏗️ ScyllaDB Architecture:

![Architecture Diagram](/images/architecture.png)

### 1️⃣ Shared Nothing Architecture
ScyllaDB is a **shared nothing architecture**, meaning there is **no single point of failure**.

### 🔥 What Does Shared Nothing Mean?
Users can create either a **single node** or **multiple nodes**.

#### Single Node:
- Entire data is stored **on that node**.
- Using **sharding**, data is spread across the **available CPU cores**.
- Since this is a single node, **no replication happens**.

#### Multiple Nodes (Example: 3 Nodes):
- Data is **partitioned and stored across nodes**.
- Each node **manages its own data**.
- **Sharding still happens within a node.**
- When replication is enabled, copies of data (replicas) are stored across nodes for **higher availability and performance**.
- **No shared memory, CPU, or disk space. Each node is independent.**

---

## 🧩 Sharding:

💡 *We already know that sharding splits data into smaller chunks.*

### How Does Sharding Work?
Imagine we have **10 rows** to store in a **single node**.

❌ Instead of storing all **data in a single CPU core**,
✅ We **split** data into **10 chunks** and store them across **different cores**.

💡 *Why is this helpful?*
If a user asks for **one row**, instead of scanning the entire table, we can just fetch the row **directly from the specific core**. 🔥

### Example:
Imagine we have **10 tasks**. We know we need to **shard** the data. But **how?** 🤔

1️⃣ Identify the **Primary Key** – This is a **unique identifier** for each row. In our case, `_id` is unique.
2️⃣ Convert the **Primary Key** into a **Token** (using hashing techniques).
3️⃣ ScyllaDB decides **which core stores which data** based on **token range** and **available cores**.
4️⃣ **Sharding is fully handled by ScyllaDB!** 🎉

### Visual Representation of sharding:
![Architecture Diagram](/images/sharding.png)

---

## 🔁 Replication:
Replication ensures **higher availability** and **fault tolerance** by storing **multiple copies** of data across nodes.

### Key Components of Replication:

#### 1️⃣ **Replication Factor**
The number of copies stored across different nodes.
If one node **fails**, other nodes serve the data.

#### 2️⃣ **Replication Strategies**
- **Simple Strategy** 🏢
  - Contains **only one data center**.
  - Data is replicated across **all nodes** in that cluster.

- **Network Topology Strategy** 🌍
  - **Multiple data centers**, each with its own cluster.
  - Each cluster contains **multiple nodes**.
  - We can specify **different replication factors** for each data center.

📌 *Example:* Imagine we have a **data center in the USA** and one in **India**.
- **USA DC** → **4 replicas**
- **India DC** → **3 replicas**

Now, data is **replicated separately** in each location based on the required **availability & redundancy**.

---

## 🔄 Consistency Levels:

We have made copies of data and spread them across nodes, right? Now, we tell ScyllaDB how many copies it refers to during **reads/writes**.

### Types of Consistency Levels:

- **ONE** → Fastest, but accuracy is low because it refers to only one copy.
- **QUORUM** → A balance between speed and accuracy.
- **ALL** → Slowest, but ensures data correctness by referring to all copies.

---

 **TOO MUCH THEORY, RIGHT?!**
Let's jump into **practical examples**. 🚀🔥
next -> CQL.md file