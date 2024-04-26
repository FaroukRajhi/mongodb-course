I SQL, a JOIN clause is used to combine rows from two or more tables based on a related column between them.
MongoDB joins are performed by using $lookup operator.
This perform a left OUTER JOIN to a collection in the same database to filter in documents.

Let's explore the syntax:

{
    $lookup:
      {
        from: <collection to join>,
        localField: <field from the input document>,
        foreignField: [<pipeline to run on joined collection>],
        as: <output array field>
      }
}

Example:

SELECT t.* a.account_id, a.account_holder FROM transfers t INNER JOIN account_holder a ON t.transfer_id = a.transfers_complete

# Code Summary: SQL JOINs In MongoDB 
In SQL, we use INNER JOIN in our statement to join two tables:

SELECT t.*, a.account_id, a.account_holder
              FROM transfers t
INNER JOIN account_holder a ON t.transfer_id = a.transfers_complete
This SQL JOIN query does the following:

Joins the records of the transfers table with the records of the accounts table.
Uses the transfers_complete field from the accounts table and the transfer_id field from the transfers table.
Projects the account_holder and account_id fields from the accounts table into the transfers table.
To do the same in MongoDB, we use the $lookup operator from the aggregation framework. Inside the $lookup stage, we define the following:

accounts is the collection to join.
transfer_id as localField is the field to use in the equality match from the input documents.
transfers_complete as foreignField is the field to use in the equality match from the transfers collection.
account_id and account_holder are the projected fields in the resulting documents while suppressing the _id field.
account_holder is the name of the new array field to add to the input documents.
Here’s the code:

db.transfers.aggregate( [
    {
      $lookup:
        {
          from: "accounts",
          localField: "transfer_id",
          foreignField: "transfers_complete",
          pipeline: [
 
             { $project: { _id: 0, account_id: 1, account_holder: 1 } }
          ],
          as: "account_holder"
      }
  }] )