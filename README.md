# Library-management.sql
-- Database: Library Management System

-- Create Books Table CREATE TABLE Books ( book_id INT PRIMARY KEY AUTO_INCREMENT, title VARCHAR(255), author VARCHAR(100), genre VARCHAR(50), availability BOOLEAN DEFAULT TRUE );

-- Create Members Table CREATE TABLE Members ( member_id INT PRIMARY KEY AUTO_INCREMENT, name VARCHAR(100), contact VARCHAR(15), email VARCHAR(100) UNIQUE );

-- Create BorrowedBooks Table CREATE TABLE BorrowedBooks ( borrow_id INT PRIMARY KEY AUTO_INCREMENT, book_id INT, member_id INT, borrow_date DATE DEFAULT CURRENT_DATE, return_date DATE, FOREIGN KEY (book_id) REFERENCES Books(book_id), FOREIGN KEY (member_id) REFERENCES Members(member_id) );

-- Insert Sample Data INSERT INTO Books (title, author, genre, availability) VALUES ('The Great Gatsby', 'F. Scott Fitzgerald', 'Fiction', TRUE), ('1984', 'George Orwell', 'Dystopian', TRUE), ('To Kill a Mockingbird', 'Harper Lee', 'Classic', TRUE);

INSERT INTO Members (name, contact, email) VALUES ('Alice Johnson', '9876543210', 'alice@example.com'), ('Bob Smith', '9876543211', 'bob@example.com');

INSERT INTO BorrowedBooks (book_id, member_id, borrow_date, return_date) VALUES (1, 1, '2025-03-01', '2025-03-15'), (2, 2, '2025-03-05', NULL);

-- Query to List Borrowed Books with Member Details SELECT m.name, b.title, bb.borrow_date, bb.return_date FROM BorrowedBooks bb JOIN Books b ON bb.book_id = b.book_id JOIN Members m ON bb.member_id = m.member_id;

