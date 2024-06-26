The following code demonstrates how to use Mongoose as a MongoDB ORM in a simple Node project.


View the following Node project, which has Mongoose already installed:

const mongoose = require('mongoose');

main().catch(err => console.log(err));

async function main() {
  await mongoose.connect('mongodb+srv://xyz456.ab123.mongodb.net');
}


Set up application-side validation. Here’s the schema that we’ll use:

const userSchema = new mongoose.Schema({
        name: {
            type: String,
            required: true,
        },
        phone_number: String,
        age: Number,
        addresses: [
            {
                street: String,
                city: String,
                state: String,
            }
        ],
        favorites: Array
    });


Create the User model:

const User = mongoose.model('User', userSchema);


Test it by creating a new user and querying the database. Note that the name field is empty:

await User.create({
        name: "",
        phone: "7650984321",
        age: 88,
        addresses: [
            {street: "123 Main St", city: "New York", state: "NY"},
            {street: "456 Broadway", city: "New York", state: "NY"}
        ],
        favorites: ["Peanut Butter", "Chocolate", "Sherbert"]
      }
      );

    // Find all customers
  const docs = await User.find();
  console.log(docs);


Take note of the result. The result will be an error message because the name field was empty:

Error: User validation failed: name: Path `name` is required.


To fix the problem, give this user the name Mira Chan:

name: "Mira Chan",