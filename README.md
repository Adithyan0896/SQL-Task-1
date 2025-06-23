                                                     Library Management System 
Overview:
This SQL schema represents a Library Management System, designed to manage books, authors, publishers, members, and book loans.

Database: LibraryManagementSystem

CREATE DATABASE LibraryManagementSystem;
USE LibraryManagementSystem;


Schema Details

Table: Authors
Stores author details.

CREATE TABLE Authors (
    AuthorID INT AUTO_INCREMENT PRIMARY KEY,
    Name VARCHAR(100) NOT NULL,
    Country VARCHAR(50) NOT NULL
);
Table: Publishers
Stores publisher information.

CREATE TABLE Publishers (
    PublisherID INT AUTO_INCREMENT PRIMARY KEY,
    Name VARCHAR(100) NOT NULL,
    Country VARCHAR(50) NOT NULL
);
Table: Books
Links books to both authors and publishers.

CREATE TABLE Books (
    BookID INT AUTO_INCREMENT PRIMARY KEY,
    Title VARCHAR(150) NOT NULL,
    Genre VARCHAR(50) NOT NULL,
    ISBN VARCHAR(20) NOT NULL UNIQUE,
    AuthorID INT NOT NULL,
    PublisherID INT NOT NULL,
    FOREIGN KEY (AuthorID) REFERENCES Authors(AuthorID),
    FOREIGN KEY (PublisherID) REFERENCES Publishers(PublisherID)
);
Table: Members
Tracks library members and their information.

CREATE TABLE Members (
    MemberID INT AUTO_INCREMENT PRIMARY KEY,
    Name VARCHAR(100) NOT NULL,
    JoinDate DATE NOT NULL,
    Email VARCHAR(100) NOT NULL UNIQUE
);
Table: Loans
Stores details of book borrowings by members.

CREATE TABLE Loans (
    LoanID INT AUTO_INCREMENT PRIMARY KEY,
    BookID INT NOT NULL,
    MemberID INT NOT NULL,
    IssueDate DATE NOT NULL,
    ReturnDate DATE,
    FOREIGN KEY (BookID) REFERENCES Books(BookID),
    FOREIGN KEY (MemberID) REFERENCES Members(MemberID)
);
Sample Queries

-- View all authors
SELECT * FROM Authors;

-- View all publishers
SELECT * FROM Publishers;

-- View all books
SELECT * FROM Books;

-- View all members
SELECT * FROM Members;

-- View all loan records
SELECT * FROM Loans;

Notes:
Primary keys are auto-incremented integers.

Foreign key constraints enforce referential integrity.



