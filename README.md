Log in

Sign up
You said:
What type of database is MongoDB?


A.
Relational


B.
NoSQL


C.
Graph-based


D.
Key-Value Store
ChatGPT said:
The correct answer is:

B. NoSQL

MongoDB is a NoSQL database, meaning it doesn't use the traditional relational model with tables and rows. Instead, it stores data in flexible, JSON-like documents.



You said:
Which format does MongoDB use to store data?


A.
JSON


B.
XML


C.
BSON


D.
CSV
ChatGPT said:
The correct answer is:

C. BSON

MongoDB stores data in BSON (Binary JSON) format, which is a binary-encoded version of JSON. BSON allows for efficient storage and retrieval of data, and it can support more data types than JSON, such as binary data.



You said:
Which command is used to insert a document in MongoDB?


A.
db.collection.insertOne({})


B.
db.collection.create({})


C.
db.collection.write({})


D.
db.collection.add({})
ChatGPT said:
The correct answer is:

A. db.collection.insertOne({})

The insertOne() command is used to insert a single document into a collection in MongoDB. You can also use insertMany() if you want to insert multiple documents at once.



You said:
What is the purpose of _id in MongoDB?


A.
Stores metadata


B.
Acts as the primary key


C.
Specifies the index type


D.
Denotes a temporary field
ChatGPT said:
The correct answer is:

B. Acts as the primary key

In MongoDB, the _id field is used to uniquely identify each document in a collection. It serves as the primary key for the document. By default, MongoDB generates a unique _id for each document, but you can also specify your own value for it.



You said:
hich method retrieves all documents from a collection?


A.
db.collection.getAll()


B.
db.collection.find()


C.
db.collection.fetchAll()


D.
db.collection.retrieve()
ChatGPT said:
The correct answer is:

B. db.collection.find()

The find() method is used to retrieve all documents from a collection in MongoDB. If no query is provided, it will return all documents in the collection.



You said:
How can you update an existing document in MongoDB?


A.
db.collection.modify({})


B.
db.collection.updateOne({})


C.
db.collection.edit({})


D.
db.collection.alter({})
ChatGPT said:
The correct answer is:

B. db.collection.updateOne({})

The updateOne() method is used to update a single document that matches a specified filter in MongoDB. You can also use updateMany() to update multiple documents, or replaceOne() to replace an entire document.



You said:
Which command deletes a single document from a collection?


A.
db.collection.removeOne({})


B.
db.collection.deleteOne({})


C.
db.collection.dropOne({})


D.
db.collection.destroyOne({})
ChatGPT said:
The correct answer is:

B. db.collection.deleteOne({})

The deleteOne() command is used to delete a single document that matches the specified filter in MongoDB. If multiple documents match, only the first one will be deleted.



You said:
What is the main advantage of indexing in MongoDB?


A.
Increases query performance


B.
Stores extra copies of data


C.
Creates database backups


D.
Deletes redundant documents
ChatGPT said:
The correct answer is:

A. Increases query performance

Indexing in MongoDB improves the speed of query operations by allowing the database to find documents more efficiently. Without indexes, MongoDB would need to scan every document in a collection, which can be slow for large datasets. Indexes make this process much faster.



You said:
Which operator is used for filtering multiple conditions in MongoDB queries?


A.
$filter


B.
$and


C.
$match


D.
$query
ChatGPT said:
The correct answer is:

B. $and

The $and operator is used in MongoDB queries to filter documents that match multiple conditions. It allows you to combine multiple conditions that must all be true for the document to be included in the result.



You said:
What is a MongoDB replica set used for?


A.
Storing different databases


B.
Creating backups


C.
Ensuring high availability


D.
Managing user authentication
ChatGPT said:
The correct answer is:

C. Ensuring high availability

A MongoDB replica set is a group of MongoDB servers that maintain the same data set, providing redundancy and ensuring high availability. If one server in the replica set fails, another server can take over, minimizing downtime and ensuring continuous availability of data.



You said:
Database and Collection Creation:

Create a new database called library.
Inside library, create a collection named books.
Insert Data:

Insert at least five book records into the books collection.
Each book should contain fields such as title, author, publishedYear, genre, and ISBN.
Retrieve Data:

Retrieve all books from the collection.
Query books based on a specific author.
Find books published after the year 2000.
Update Data:

Update the publishedYear of a specific book.
Add a new field called rating to all books and set a default value.
Delete Data:

Delete a book by its ISBN.
Remove all books of a particular genre.
Data Modeling Exercise:

Create a data model for an e-commerce platform including collections for users, orders, and products.
Decide on appropriate fields and relationships (embedding vs. referencing).
Implement the structure using MongoDB.
Aggregation Pipeline:

Use aggregation to find the total number of books per genre.
Calculate the average published year of all books.
Identify the top-rated book.
Indexing:

Create an index on the author field to optimize query performance.
Explain the benefits of indexing in MongoDB.
Testing:

Use the MongoDB shell or Compass to verify the inserted and updated records.
Ensure all queries return the expected results.
Documentation:
Create a README.md file with step-by-step instructions on setting up and running your database.
 
Evaluation Criteria:

Proper setup and connection of MongoDB.
Accurate implementation of CRUD operations.
Correct data modeling with appropriate relationships.
Use of aggregation for insightful queries.
Clear and concise documentation.
Proper indexing implementation.
ChatGPT said:
This looks like a comprehensive project to work with MongoDB. Below is a detailed guide on how to complete each task step by step.

1. Database and Collection Creation:
Step 1: Create a new database called library.

javascript
Copy
Edit
use library;
Step 2: Create a collection named books within the library database.

javascript
Copy
Edit
db.createCollection("books");
2. Insert Data:
Step 1: Insert at least five book records into the books collection. Each book should have fields like title, author, publishedYear, genre, and ISBN.

javascript
Copy
Edit
db.books.insertMany([
    {
        title: "The Great Gatsby",
        author: "F. Scott Fitzgerald",
        publishedYear: 1925,
        genre: "Fiction",
        ISBN: "9780743273565"
    },
    {
        title: "1984",
        author: "George Orwell",
        publishedYear: 1949,
        genre: "Dystopian",
        ISBN: "9780451524935"
    },
    {
        title: "To Kill a Mockingbird",
        author: "Harper Lee",
        publishedYear: 1960,
        genre: "Fiction",
        ISBN: "9780061120084"
    },
    {
        title: "The Hobbit",
        author: "J.R.R. Tolkien",
        publishedYear: 1937,
        genre: "Fantasy",
        ISBN: "9780618968633"
    },
    {
        title: "The Catcher in the Rye",
        author: "J.D. Salinger",
        publishedYear: 1951,
        genre: "Fiction",
        ISBN: "9780316769488"
    }
]);
3. Retrieve Data:
Step 1: Retrieve all books from the collection.

javascript
Copy
Edit
db.books.find();
Step 2: Query books based on a specific author (e.g., "George Orwell").

javascript
Copy
Edit
db.books.find({ author: "George Orwell" });
Step 3: Find books published after the year 2000.

javascript
Copy
Edit
db.books.find({ publishedYear: { $gt: 2000 } });
4. Update Data:
Step 1: Update the publishedYear of a specific book (e.g., "The Hobbit").

javascript
Copy
Edit
db.books.updateOne(
    { title: "The Hobbit" },
    { $set: { publishedYear: 1938 } }
);
Step 2: Add a new field called rating to all books and set a default value (e.g., rating: 4).

javascript
Copy
Edit
db.books.updateMany(
    {},
    { $set: { rating: 4 } }
);
5. Delete Data:
Step 1: Delete a book by its ISBN (e.g., "9780451524935").

javascript
Copy
Edit
db.books.deleteOne({ ISBN: "9780451524935" });
Step 2: Remove all books of a particular genre (e.g., "Fiction").

javascript
Copy
Edit
db.books.deleteMany({ genre: "Fiction" });
6. Data Modeling Exercise:
Step 1: Create collections for an e-commerce platform: users, orders, and products.

users: Contains information about users.
orders: Stores customer orders.
products: Lists available products.
Example Structure:

javascript
Copy
Edit
// Users collection
db.createCollection("users");
db.users.insertOne({
    _id: 1,
    name: "John Doe",
    email: "john@example.com",
    password: "hashed_password"
});

// Products collection
db.createCollection("products");
db.products.insertOne({
    _id: 101,
    name: "Laptop",
    price: 1200,
    category: "Electronics",
    stock: 50
});

// Orders collection with references to users and products
db.createCollection("orders");
db.orders.insertOne({
    _id: 1001,
    userId: 1, // Reference to users collection
    productId: 101, // Reference to products collection
    orderDate: new Date(),
    quantity: 1,
    totalPrice: 1200
});
Relationships:

Embedding vs Referencing: In this case, we reference users and products within orders to avoid redundancy and keep the structure flexible.
7. Aggregation Pipeline:
Step 1: Find the total number of books per genre.

javascript
Copy
Edit
db.books.aggregate([
    { $group: { _id: "$genre", totalBooks: { $sum: 1 } } }
]);
Step 2: Calculate the average published year of all books.

javascript
Copy
Edit
db.books.aggregate([
    { $group: { _id: null, avgPublishedYear: { $avg: "$publishedYear" } } }
]);
Step 3: Identify the top-rated book.

javascript
Copy
Edit
db.books.aggregate([
    { $sort: { rating: -1 } },
    { $limit: 1 }
]);
8. Indexing:
Step 1: Create an index on the author field to optimize query performance.

javascript
Copy
Edit
db.books.createIndex({ author: 1 });
