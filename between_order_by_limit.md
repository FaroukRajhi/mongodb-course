SQl statement:

SELECT city, state, pop FROM zips WHERE state = 'NY' AND pop BETWEEN 1000 AND 5000 ORDER BY pop DESC LIMIT 10;

LIMIT 10: limit it to the first 10 results.

**Is equivalent to:**

db.zips.find({state: 'NY', pop: ${gte: 1000, $lte: 5000}}).sort({pop: -1}).limit(10);

or pop: 1 for ascending
db.zips.find({state: 'NY', pop: ${gte: 1000, $lte: 5000}},{_id:0, state: 1, city: 1, pop: 1}).sort({pop: -1}).limit(10);
_id:0 includes city, state and pop fields.

