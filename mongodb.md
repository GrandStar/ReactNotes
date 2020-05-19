# MongoDB

MongoDB is a cross-platform, document oriented database that provides, high performance, high availability, and easy scalability. MongoDB works on concept of collection and document.

**Database**

Database is a physical container for collections. Each database gets its own set of files on the file system. A single MongoDB server typically has multiple databases.

**Collection**

Collection is a group of MongoDB documents. It is the equivalent of an RDBMS table. A collection exists within a single database. Collections do not enforce a schema. Documents within a collection can have different fields. Typically, all documents in a collection are of similar or related purpose.

**Document**

A document is a set of key-value pairs. Documents have dynamic schema. Dynamic schema means that documents in the same collection do not need to have the same set of fields or structure, and common fields in a collection's documents may hold different types of data.

#### Why Use Mongodb <a id="why-use-mongodb"></a>

Organizations of all sizes are adopting MongoDB because it enables them to build applications faster, handle highly diverse data types, and manage applications more efficiently at scale.

* Development is simplified as MongoDB documents map naturally to modern, object-oriented programming languages.
* MongoDB can be easily scaled within and across multiple distributed data centers.
* Working with data as flexible JSON documents, rather than as rigid rows and columns, is proven to help developers move faster.

#### Query Language Comparison <a id="query-language-comparison"></a>

MySQL

```text
INSERT INTO users (user_id, age, status)VALUES ('bcd001', 45, 'A')

SELECT * FROM users

UPDATE users SET status = 'C' WHERE age > 25
```

MongoDB

```text
db.users.insert({
  user_id: 'bcd001',
  age: 45,
  status: 'A'
});

db.users.find();

db.users.update(
  { age: { $gt: 25 } },
  { $set: { status: 'C' } },
  { multi: true }
)

```

## Express and Mongodb - Client <a id="express-and-mongodb---client"></a>

The mongo shell is an interactive JavaScript interface to MongoDB. You can use the mongo shell to query and update data as well as perform administrative operations.

#### Start the `mongo` shell <a id="start-the-mongo-shell"></a>

**NOTE: Ensure that MongoDB is running before attempting to start the mongo shell.**

```text
mongo
```

#### Select database <a id="select-database"></a>

* To show the list of databases:

```text
show dbs
```

* To display the database you are using:

```text
db
```

* To switch database:

```text
use <database>
```

#### CURD <a id="curd"></a>

CRUD is an acronym for Create, Read, Update and Delete, which are 4 types of operations in MongoDB.

* Create - add new documents to a collection
* Read - retrieve documents from a collection
* Update - modify existing documents in a collection
* Remove - remove documents from a collection

#### Create Operations <a id="create-operations"></a>

Create or insert operations add new documents to a collection. If the collection does not currently exist, insert operations will create the collection.

MongoDB provides the following methods to insert documents into a collection:

* db.collection.insertOne\(\)
* db.collection.insertMany\(\)

For example:

![Example](http://tutorial.haochuan.io/diagram/dist/crud-annotated-mongodb-insertOne.bakedsvg.svg)

#### Read Operation <a id="read-operation"></a>

Read operations retrieves documents from a collection; i.e. queries a collection for documents. MongoDB provides the following methods to read documents from a collection:

* db.collection.find\(\)

Find all documents...

You can specify query filters or criteria that identify the documents to return. For exmaple,

find\({object}\) ----- object : restriction 

* `db.users.find()` will give you all documents in the `users` collection.
* `db.users.find({status: "pending"})` will only give you the documents with `status="pending"`

![Example](http://tutorial.haochuan.io/diagram/dist/crud-annotated-mongodb-find.bakedsvg.svg)

#### Update Operation <a id="update-operation"></a>

Update operations modify existing documents in a collection. MongoDB provides the following methods to update documents of a collection:

* db.collection.updateOne\(\)
* db.collection.updateMany\(\)
* db.collection.replaceOne\(\)

```text
db.users.updateOne({age: 26}, {$set: {status: 'reject'}});
```

![Example](http://tutorial.haochuan.io/diagram/dist/crud-annotated-mongodb-updateMany.bakedsvg.svg)

#### Delete Operation <a id="delete-operation"></a>

Delete operations remove documents from a collection. MongoDB provides the following methods to delete documents of a collection:

* db.collection.deleteOne\(\)
* db.collection.deleteMany\(\)
* db.collection.remove\(\)  ---- one or multiple. second parameter: true only one.
* remove must has a parameter... or .... delete everything.

```text
db.users.deleteOne({age: 26}});
```

![Example](http://tutorial.haochuan.io/diagram/dist/crud-annotated-mongodb-deleteMany.bakedsvg.svg)

## **mongoose** 

**Schemas**  


**Mongoose defines a schema for your data models so your documents follow a specific structure with pre-defined data types.**

**Validation**

**Mongoose has built in validation for schema definitions. This saves you from writing a bunch of validation code that you have to otherwise write with the MongoDB dirver.**

**Instance Methods**

**Mongoose provides optional pre and post save operations for data models. This makes it easy to define hooks and custom functionality on successful reads / writes.**

**Returning results**

**Mvongoose makes returning updates documents or query results easier**  


