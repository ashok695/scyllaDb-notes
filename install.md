# 🚀 Installing ScyllaDB Using Docker (Quick & Easy Setup)

---

## 📌 Installation Methods
ScyllaDB can be installed in two ways:
1️⃣ **Using Docker** *(Quick setup - Recommended for learning)*
2️⃣ **Installing Natively** *(For full control over the environment)*

For our learning purposes, we will go through **Docker installation** as it provides an easy and fast setup. ✅

---

## 🔧 Prerequisites
✅ Install **Docker** (if you haven’t already)
🔗 [Download Docker](https://www.docker.com/get-started)

---

## 🚀 Steps to Run ScyllaDB in Docker

### 🔹 Step 1: Create a ScyllaDB Node
> *We will learn about nodes in depth later. For now, think of a node as a database instance.*

Run the following command to create a ScyllaDB container:
```sh
docker run --name scylladb -d scylladb/scylla
```

### 💡 Explanation of Command:
- 🖥️ `docker run` → Command to create a container
- 🏷️ `--name scylladb` → Assigns the container name as **scylladb**
- 🎭 `-d` → Runs the container in **detached mode** (background process)
- 📦 `scylladb/scylla` → Uses the official **ScyllaDB image**

---

### 🔹 Step 2: Check Running Containers
Run the following command to see the list of running containers:
```sh
docker ps
```
🔍 This command will list all running containers in the Docker engine.

### 🔎 What to Look For?
- 🖧 **PORTS Column**: Shows which ports are exposed.
  - 🎯 The most important port for us is **9042** → This is the **CQL (Cassandra Query Language) Port**, which we use to interact with the database.

---

### 🔹 Step 3: Connect to the ScyllaDB Container
Copy the **Container ID** from the output of `docker ps` and run:
```sh
docker exec -it <container-id> cqlsh
```

### 🎯 Explanation of Command:
- 🚀 `docker exec` → Executes a command in a running container
- 🔄 `-it` → Interactive mode (allows user input)
- 📌 `<container-id>` → Replace this with your actual **Container ID**
- 📜 `cqlsh` → Opens the **CQL Shell**, allowing interaction with the database

Once inside the **CQL shell**, you can start querying the database! 🎉

---

## 🎯 Next Steps
🔹 Understanding **ScyllaDB Architecture** *(Shards, Replication, etc.)*

Excitu=? 🚀

