When querying a SQL database, we use SELECT FROM statements, usually with a WHERE clause.
SELECT * FROM zips LIMIT 1;
Select all from the zipped table and limiting the results to a single record.

In mongoDB:

db.zips.findOne({}) which return one document.
Will return the first document in the collection.
But if we wanted to provide any extra filtering criteria, we do that within those curly brackets.
Let's examine the MongoDB findOne command a bit more.
db.collection.findOne({filter, projection, options})
filter: which consists of field value expressions.
projection: specific field.
options: if we want to add extra option.

Example:

SELECT city FROM zips WHERE state = 'AZ' AND pop < 500;
db.zips.find({state: 'AZ', pop: {$lt: 500}})