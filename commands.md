
## **1. Keyspace (Database) Management**
### **View Available Keyspaces**
```cql
DESCRIBE KEYSPACES;
```

### **Create a Keyspace**
```cql
CREATE KEYSPACE <KEYSPACE-NAME>
WITH replication = {'class': '<strategy-name>', 'replication_factor': <no.ofreplicas>};
```

### **Use a Specific Keyspace**
```cql
USE <KEYSPACE-NAME>;
```

---

## **2. Table Management**
### **Create a Table**
```cql
CREATE TABLE <table-name> (
    keyname1 datatype PRIMARY KEY,
    keyname2 datatype,
    ...
    keynamen datatype
);
```

---

## **3. Data Operations**

### **Insert Data into a Table**
```cql
INSERT INTO <table-name> (keyname1, keyname2, ..., keynamen)
VALUES (value1, value2, ..., valuen);
```

### **Update Data in the Table**
```cql
UPDATE <table-name> SET <key-name> = <new-value> WHERE PRIMARY_KEY = <primary-key-value>;
```

### **Delete a Record**
```cql
DELETE FROM <table-name> WHERE <primary-key> = <primary-key-value>;
```

---


