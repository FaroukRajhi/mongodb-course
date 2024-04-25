Translate a SQL insert statement.
Insert a document into mongoDB.
Identify the _id as the primary key.

INSERT INTO users (first_name, last_name, phone, age) VALUES ('John', Smith', "686542", 29);

db.users.insertOne(

    {
        first_name: 'John',
        last_name: 'Smith',
        phone: '998632',
        age: 29
    }
)

db: To signify action on the currently selected database.
users: To identify the collection.
insertOne: as the command to insert a single document , the field names and the corresponding 

To insert multiple values , in SQL 
INSERT INTO users (first_name, last_name, phone, age) VALUES ('John', Smith', "686542", 29), ('douglas', Smith', "33333", 40); and so on.

in mongoDB

db.users.insertMany(

    {
        first_name: 'John',
        last_name: 'Smith',
        phone: '998632',
        age: 29
    },

    {
        first_name: 'John',
        last_name: 'Smith',
        phone: '998632',
        age: 29
    }
)
and so on.

In mongoDB, each document(row) stored in a collection requires a unique _id field that acts as a primary key.
MongoDB driver automatically generates a unique ObjectID for the _id field of every document(row).
To confirm this, after creating a new document in MongoDB without id_field, you can retrieve the same document:
By using the findOne command.
db.collection.findOne()
example output:
{ _id: ObjectId('662a2ac3f45b48a7022202d8') }




