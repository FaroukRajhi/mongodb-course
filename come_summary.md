Code Summary: INSERT in MongoDB
# Insert a Single Record
To insert a single record into a SQL database, you would use the following command:

INSERT INTO users (first_name, last_name, phone, age) 
VALUES ('Nancy', 'Smith', "5234560987", 29);


To insert the same data into a MongoDB database, use the following:

db.users.insertOne(
    {
        first_name: "Nancy",
        last_name: "Smith",
        phone: "523-456-0987",
        age: 25
    }
)


# Insert Multiple Records
To insert four records into a SQL database, you would use the following command:

INSERT INTO users (first_name, last_name, phone, age)
VALUES
  ('Douglas', 'Lowel', "5234768907", 23),
  ('Kai', 'Tran', "9198761234", 43),
  ('Linzey', 'Rivers', "7659023456", 54),
  ('Mira', 'Chan', "7650981234", 88);


# To insert the same four documents into a MongoDB database, use the following:

db.users.insertMany([
    {
        first_name: "Douglas",
        last_name: "Lowel",
        phone: "523-476-8907",
        age: 23
    },
    {
        first_name: "Kai",
        last_name: "Tran",
        phone: "919-876-1234",
        age: 43,
    },
    {
        first_name: "Linzey",
        last_name: "Rivers",
        phone: "765-902-3456",
        age: 54,
    },
    {
        first_name: "Mira",
        last_name: "Chan",
        phone: "765-098-1234",
        age: 88,
    }
])