## JSON vs BSON
As a developer we will only be dealing with JSON objects to store our data.

BSON data is what MongoDB uses behind the scenes.

The conversion of your JSON to BSON is handled by MongoDBs drivers and translates the data that you insert into BSON.

BSON is binary and is more efficient to save and call, it can also be turned into different types.

## MongoDB data insertion
When inserting a document to a collection within a database we do not need to have strict schemas.

Data can be inserted in a schemaless fashion.

The ObjectId when inserting new data is automatically provided by MongoDB.

You can insert your own ObjectId by adding the key "_id" : ObjectId("afafafafaf").

The only important thing to note here is that the ObjectId has to be unique

## CRUD Operations and MongoDB
You can use MongoDB for a variety of things:
1. Application
2. Analytics/BI Tools
3. Admin

In an application you might have users interact with your app and aggregate data as you go using a MongoDB driver. This app could be in PHP, C++, Python, etc. 

For analytics you can have a BI Connector or shell.

As an administrator you would interact with the database through the shell.

In all cases you are wanting to interact directly with the database through the MongoDB server.

You want to be able to perform CRUD operations as a developer for an app.

Create: insertOne(data, options), insertMany(data, options)
Read: find(filter, options), findOne(filter, options)
Update: updateOne(filter, data, options), updateMany(filter, data, options), replaceOne(filter, data, options)
Delete: deleteOne(filter, options), deleteMany(filter, options)

Example 1: Flight Data
In a flight data collection like in 01-flights.json, we may want to be able to schedule a flight (create), see our flight information (read), update our info if necessary (update), and delete our flight if need be (delete)