1. Database and Collection Creation:
Step 1: Create a new database called library.

use library;
Step 2: Create a collection named books within the library database.
db.createCollection("books");
2. Insert Data:
Step 1: Insert at least five book records into the books collection. Each book should have fields like title, author, publishedYear, genre, and ISBN.

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
Step 1: Retrieve all books from the collection;
db.books.find();
Step 2: Query books based on a specific author (e.g., "George Orwell").

db.books.find({ author: "George Orwell" });
Step 3: Find books published after the year 2000.

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

db.books.updateMany(
    {},
    { $set: { rating: 4 } }
);
5. Delete Data:
Step 1: Delete a book by its ISBN (e.g., "9780451524935").

db.books.deleteOne({ ISBN: "9780451524935" });
Step 2: Remove all books of a particular genre (e.g., "Fiction").


db.books.deleteMany({ genre: "Fiction" });
6. Data Modeling Exercise:
Step 1: Create collections for an e-commerce platform: users, orders, and products.

users: Contains information about users.
orders: Stores customer orders.
products: Lists available products.
Example Structure:

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


db.books.aggregate([
    { $group: { _id: "$genre", totalBooks: { $sum: 1 } } }
]);
Step 2: Calculate the average published year of all books.

db.books.aggregate([
    { $group: { _id: null, avgPublishedYear: { $avg: "$publishedYear" } } }
]);
Step 3: Identify the top-rated book.

db.books.aggregate([
    { $sort: { rating: -1 } },
    { $limit: 1 }
]);
8. Indexing:
Step 1: Create an index on the author field to optimize query performance.


Edit
db.books.createIndex({ author: 1 });
Benefits of Indexing:

Improves query performance: Indexes allow for faster lookups, reducing the need to scan all documents in the collection.
Speeds up sorting operations: When sorting by indexed fields, the database can use the index to quickly order the data.
Efficient data retrieval: Especially for large collections, indexes reduce the time needed to retrieve specific documents based on queries.
9. Testing:
Use the MongoDB shell or MongoDB Compass to verify the inserted, updated, and deleted records.
Run queries like find(), aggregate(), and update() to ensure they return the expected results.
10. Documentation:
Create a README.md file that includes:

Project Overview: Explain the purpose of the project.
Setup Instructions: How to set up and run MongoDB locally.
Usage: Step-by-step instructions on performing CRUD operations and running aggregation queries.
Indexing: Explanation of how indexing improves performance.
Testing: Steps to verify the operations using MongoDB tools.
