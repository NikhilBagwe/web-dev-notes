## Intro :

- MongoDB is an open-source, document-oreinted NoSQL DBMS.
- It stores data in form of JSON documents.
- Designed for flexibility, scalibility and performance in handling unstructured or semi-structured data.
- It was made by company named as "10gen" which is now renamed as "MongoDB".
- First version of MongoDB was released in 2009.

### NOTE : The name "Mongo" was derived from the word "Humongous" by removing some letters from start and end.

---
 
## SQL vs MongoDB :

### SQL :

- SQL DBs are Relational databases. They use Structured tables to store data in rows and columns.
- The data is fixed i.e row and columns are pre-defined.
- Suitable for applications with well-defined Schemas and fixed Data structures.
- Eg: E-commerce platform, HRMS, etc.

### MongoDB :

- NoSQL DBs are non-relational databases.
- Provide flexibility in data storage, allowing varied data types and structures.
- We can add extra fields anytime.
- Suitable for applications with Dynamic or Evolving data models.
- Eg: CMS, Social Media platforms, etc.
- Example of NoSQL DB - MongoDB, cassandra, redis, etc.

### An JSON obj is called a Document and an object present inside it is called Embeded document.

---

## MongoDB Terminologies :

- In MongoDB, we have a DB inside which we can have multiple collections.
- Inside each Collection we can have Documents in JSON format.
- Data in Documents can be structured or unstructured i.e one document can have additional fields than other documents.
- Thus, MongoDB is Schema-less.

![1](https://github.com/NikhilBagwe/web-dev-notes/assets/67143015/e1274222-add5-41c0-bfa9-579740c64df7)

## Key features :

![2](https://github.com/NikhilBagwe/web-dev-notes/assets/67143015/df5a0185-ca21-48b6-bd1e-1ee51e609c4c)

## Internal Working of MongoDB :

- When a user submits a Form from the frontend, it is handled by NodeJS/ExpressJS present in the backend who requests the DB to store the data.
- So first we connect to the MongoDB server from backend.
- Now, the MongoDB server doesn't directly talks with DB.
- Instead it uses Storage engine which is present inside the MongoDB server.
- The job of Storage engine is to Read/Write data to DB. It also converts JSON to BSON.

## JSON vs BSON :

- In MongoDB, we write in JSON format only but BTS data is stored in BSON(Binary JSON) format, a binary representation of JSON.
- By using BSON we can acheive higher read and write speeds, reduced storage requirements and improved data manipulation capabilities while handling large and complex datasets.
- While using mongodb we will only work with JSON which is easy to read/write.






















