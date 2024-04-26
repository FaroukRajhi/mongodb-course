Code Summary: DELETE in MongoDB
Delete a Single Record
To delete a record in SQL, we use DELETE. In the following SQL statement, we’re deleting a record from the sales table, where the id is equal to 1234567:

DELETE FROM sales WHERE id = '1234567';
To do the same thing in MongoDB, we use the deleteOne() method:

db.sales.deleteOne({_id: ObjectId("5bd761dcae323e45a93ccff1")})


Delete Multiple Records
To delete multiple records in SQL, we still use a DELETE statement along with a WHERE clause. Here, we’re deleting every store located in Denver or New York:

DELETE FROM sales WHERE storeLocation IN ('Denver', 'New York');
To delete multiple documents in MongoDB, we use the deleteMany() method along with the $in operator:

db.sales.deleteMany({ storeLocation: {$in: [ 'Denver', 'New York' ]} });