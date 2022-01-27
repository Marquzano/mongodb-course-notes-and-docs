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

## Finding, Inserting, Deleting, and Updating Elements

To clear a database we have to use a delete command.

All commands are always executed on a collection where you want to add or delete documents

When updating you may do the following:
db.flightData.updateOne({distance: 12000}, {marker: 'delete'})

But this will cause an error because in order to update a document it must contain an atomic operator.

You don't pass in a document describing your change like this because MongoDB does not know how to interpret this.

Instead you pass in a document with a special keyword $set.

db.flightData.updateOne({distance: 12000}, {$set: {marker: 'delete'}})

$ in MongoDB means that the word is a reserved operator/word

$set is identified by MongoDB when used in an updateOne operation to describe the changes you want to make. The value of $set is a document. This tells MongoDB for the document that you are finding, please set the key and its value. If the key already exists then the value will simply be updated. If the key doesn't exist then it will simply be added along with its value.

As a filter you can simply pass in an empty document, this will select ALL documents.

## Diving Deeper into Finding Data
You can filter the data you want to find by providing a key

db.flightData.find({intercontinental: true})

You can also find what you want by providing some logic

db.flightData.find({distance: {$gt: 10000}})

This $gt operator represents greater than, this tells MongoDb that you are looking for data that has a distanc greater than 10000.

We could also use this operator with findOne.

flights> db.flightData.findOne({distance: {$gt: 900}})

In this case both flights are greater than 900 in distance but findOne will return the first that it finds in the array that passes through the filter