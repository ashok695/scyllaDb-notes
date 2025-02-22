# 📜 ScyllaDB CQL Commands

> **CQL (Cassandra Query Language)** is used to interact with ScyllaDB.

📌 **For a full list of commands, refer to** `commands.md`

## 🚀 Getting Started with a Single Node

### 🏗️ Creating a Database (Keyspace)
```sql
CREATE KEYSPACE FIRST_DB
WITH replication = {'class': 'SimpleStrategy', 'replication_factor': 3};
```
💡 *In ScyllaDB, a database is called a **keyspace**.*

### 📋 Viewing All Keyspaces
```sql
DESCRIBE KEYSPACES;
```

### 🔄 Switching to a Specific Keyspace
```sql
USE FIRST_DB;
```

## 🛠️ Working with Tables

### 📌 Creating a Table
```sql
CREATE TABLE users (
    id uuid PRIMARY KEY,
    name text,
    age int,
    email text,
    ismale boolean
);
```
💡 *The `id` is the **primary key (partition key)** used for sharding.*

### 📜 Listing Tables in a Keyspace
```sql
DESCRIBE TABLES;
```

## 📥 Inserting Data

💡 **Notes:**
- Always use **single quotes (`'`)** for string values.
- Data should be inserted **in the same order as defined in the table.**

```sql
INSERT INTO users (id, age, email, ismale, name)
VALUES (uuid(), 22, 'ashok@gmail.com', true, 'Ashok');
```

## 📤 Retrieving Data

### 🗄️ Get All Rows and Columns from a Table
```sql
SELECT * FROM users;
```

## 🔄 Updating Data
```sql
UPDATE users SET age = 23 WHERE id = <actual-id>;
```

## ❌ Deleting Data
```sql
DELETE FROM users WHERE id = <actual-id>;
```

## 🔥 Next Steps: Optimization & Advanced Queries

