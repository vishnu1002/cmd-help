![MongoDB_SpringGreen](https://github.com/vishnu1002/cmd-help/assets/145321614/c2e75190-b879-4f47-8e63-2d26f8315002)

MongoDB is a flexible and scalable NoSQL database system that stores data in JSON-like documents. It's designed for handling large volumes of structured, semi-structured, and unstructured data. MongoDB offers high availability, scalability, and a powerful query language, making it suitable for a wide range of applications.
Learn more [mongodb.com](https://www.mongodb.com/)

- **Collections** are like tables in relational databases, grouping similar documents together.
- **Documents** are individual records within collections, storing data in JSON-like format.
- **Fields** are the data elements within documents, each with a name and value, akin to columns in tables.

## Installation
Follow the link to Install MongoDB for respective OS:
- [Install on windows](https://www.mongodb.com/docs/manual/tutorial/install-mongodb-on-windows/)
- [Install on macOS](https://www.mongodb.com/docs/manual/tutorial/install-mongodb-on-os-x/)
- [Install on Linux](https://www.mongodb.com/docs/manual/administration/install-on-linux/)

Install Mongo Shell (mongosh) for respective OS:
- [Install Mongo Shell (mongosh)](https://www.mongodb.com/docs/mongodb-shell/install/#std-label-mdb-shell-install)

## Jump to
- [Show Databases](#show-databases)
- [Create Database](#create-database)
- [Create Collections](#create-collections)
- [Show Collections](#show-collections)
- [Drop Current DB](#drop-current-db)
- [insertOne()](#insertone)
- [display Documents](#display-documents)
- [insertMany()](#insertmany)
- [MongoDB Datatypes](#mongodb-datatypes)
- [sort()](#sort)
- [limit()](#limit)
- [find()](#find)
- [updateOne()](#updateone)
- [updateMany()](#updatemany)
- [deleteOne()](#deleteone)
- [deleteMany()](#deletemany)
- [Not Equal ($eq)](#not-equal-eq)
- [Less Than ($lt)](#less-than-lt)
- [Less Than Equal ($lte)](#less-than-equal-lte)
- [Greater Than ($gt)](#greater-than-gt)
- [Greate Than Equal ($gte)](#greate-than-equal-gte)
- [Displaying within a range](#displaying-within-a-range)
- [$in](#in)
- [$nin](#nin)
- [$and](#and)
- [$or](#or)
- [$nor](#nor)
- [$not](#not)
- [createIndex()](#createindex)
- [getIndexes()](#getindexes)
- [dropIndex()](#dropindex)
- [createCollection()](#createcollection)

## Mongosh Beginner Commands --list

Run mongosh within terminal

    mongosh

### Show Databases

    show dbs
    
### Create Database

    use college

### Create Collections

    db.createCollection("students")

### Show Collections

    show collections

### Drop Current DB

    db.dropDatabase()

### insertOne()

    db.students.insertOne({name:"apple", age:"10"})

### display Documents

    db.students.find()

### insertMany()

    db.students.insertMany([{}, {}, {}])

### MongoDB Datatypes

    (
      {
    	nama: "someguy",
    	age: "95",
    	gpa: "9.5",
    	fullTime: false,
    	registerDate: new Date(),
    	girlfriends: null,
    	course: ["Boi", "Chem", "Math"]
    	address: {street: "Fake St.",
    		      city: "Battlefield",
    		      zip: 00000}
      }
    )

### sort()
Display in ascending order (1)

    db.students.find().sort(name:1)
Display in decensing order (-1)

    db.students.find().sort(name:-1)

### limit()

    db.students.find().limit(3)

limit the no.of documents to 3 and display in ObjectId order


### find()

    db.students.find({name:"apple"})

    db.students.find({name:"apple", age:10})

Return only the names:

    db.students.find({}, {name:true})

Return names without _id:
> find({query}, {projection})

    db.students.find({}, {_id:false, name:true})
    

### updateOne()

> updateOne({filter}, {set:{new_value}})

Update a field with name = "apple" to "APPLE"

    db.students.updateOne({name:apple}, {$set:{name:"APPLE"}})

Add new field fulltime = false where name = "apple"

    db.students.updateOne({name:apple}, {$set:{fullTime:"false"}})

Remove fulltime where name = "apple"

    db.students.updateOne({name:apple}, {$unset:{fullTime:""}})


### updateMany()

Update fields which has fullTime to false

    db.students.updateMany({}, {$set:{fullTime:false}})

Update fields where fulltime exists as false and set to true:

    db.students.updateMany({fulltime:{$exists:false}}, {$set:{fullTime:true}})


### deleteOne()
Delete a field where name = "apple"

    db.students.deleteOne({name:"apple"})


### deleteMany()
Delete all fields where fulltime = false

    db.students.deleteMany({fullTime:false})

### Not Equal ($eq)

    db.students.find({name:{$ne:"apple"}})


### Less Than ($lt)

    db.students.find({age:{$lt:9}})


### Less Than Equal ($lte)

    db.students.find({age:{$lte:9}})


### Greater Than ($gt)

    db.students.find({age:{$gt:12}})


### Greate Than Equal ($gte)

    db.students.find({age:{$gte:89}})


### Displaying within a range
Display age > 12 to age age < 89

    db.students.find({age:{$gte:12, $lte:89}})

### $in

    db.students.find({name:{$in:["apple", "pple"]}})


### $nin 

    db.students.find({name:{$nin:["apple", "pple"]}})


### $and

Display fulltime=true and age<22

    db.students.find({$and:[{fullTime:true}, {age:{$lte:22}}]})


### $or

Display fulltime=true or age<22

    db.students.find({$or:[{fullTime:true}, {age:{$lte:22}}]})


### $nor

Displays when both conditions are false

    db.students.find({$nor:[{fullTime:true}, {age:{$lte:22}}]})


### $not

    db.students.find({age:{$not:{$gte:12}}})


### createIndex()

    db.students.createIndex({name: 1})

### getIndexes()

    db.students.getIndexes()

### dropIndex()

    db.students.dropIndex("name_1")


### createCollection()

    db.createCollection("teachers", {capped:true, size:10000000, max: 100, autoIndexId:false})

size = file size in bytes
max = max fields in the doc
autoIndexId = auto indexing
