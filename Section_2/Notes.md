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