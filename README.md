Library Management System:
Books: BookID, Title, Author, ISBN
Members: MemberID, Name, Address, Phone
Loans: LoanID, BookID, MemberID, LoanDate, ReturnDate
Authors: AuthorID, Name, Nationality  
Relationships:
Books and Loans: One-to-Many
Members and Loans: One-to-Many
Books and Authors: Many-to-Many
SQL Table Creation:
CREATE TABLE Authors (
    AuthorID INT PRIMARY KEY,
    Name VARCHAR(100),
    Nationality VARCHAR(50)
);

CREATE TABLE Books (
    BookID INT PRIMARY KEY,
    Title VARCHAR(200),
    ISBN VARCHAR(13),
    AuthorID INT,
    FOREIGN KEY (AuthorID) REFERENCES Authors(AuthorID)
);

CREATE TABLE Members (
    MemberID INT PRIMARY KEY,
    Name VARCHAR(100),
    Address VARCHAR(255),
    Phone VARCHAR(20)
);

CREATE TABLE Loans (
    LoanID INT PRIMARY KEY,
    BookID INT,
    MemberID INT,
    LoanDate DATE,
    ReturnDate DATE,
    FOREIGN KEY (BookID) REFERENCES Books(BookID),
    FOREIGN KEY (MemberID) REFERENCES Members(MemberID)
);
Data Manipulation Commands:
Insert data into  tables:
INSERT INTO Authors (AuthorID, Name, Nationality) VALUES (1, 'George Orwell', 'British');
INSERT INTO Books (BookID, Title, ISBN, AuthorID) VALUES (1, '1984', '9780451524935', 1);
INSERT INTO Members (MemberID, Name, Address, Phone) VALUES (1, 'John Doe', '123 Main St', '555-1234');
INSERT INTO Loans (LoanID, BookID, MemberID, LoanDate, ReturnDate) VALUES (1, 1, 1, '2023-09-01', '2023-09-15');
Updating and Deleting Data:
Update data:
UPDATE Members SET Address = '456 Elm St' WHERE MemberID = 1;
Delete data:
DELETE FROM Loans WHERE LoanID = 1;
Executing Joins:
Write SQL queries using joins to retrieve related data across tables. Example query to retrieve loan information along with book and member details:
SELECT Loans.LoanID, Books.Title, Members.Name, Loans.LoanDate, Loans.ReturnDate
FROM Loans
JOIN Books ON Loans.BookID = Books.BookID
JOIN Members ON Loans.MemberID = Members.MemberID;
Use DDL, DML, DCL, and TCL Commands:
DDL (Data Definition Language):
ALTER TABLE Books ADD Publisher VARCHAR(100);
DML (Data Manipulation Language):
INSERT INTO Books (BookID, Title, ISBN, AuthorID) VALUES (2, 'Animal Farm', '9780451526342', 1);
DCL (Data Control Language):
GRANT SELECT ON Books TO Public;
TCL (Transaction Control Language):
BEGIN TRANSACTION;

INSERT INTO Loans (LoanID, BookID, MemberID, LoanDate, ReturnDate) VALUES (2, 2, 1, '2023-09-20', '2023-10-05');
COMMIT;
![author,bookTable](https://github.com/user-attachments/assets/ac1bd180-b4e1-4f86-9a08-4b9dab13e124)
![Members,loans](https://github.com/user-attachments/assets/3f8d11c4-f408-49b8-a479-4481ec193b3f)
![DELET ALET](https://github.com/user-attachments/assets/df3dabab-9f0c-4917-ab37-0370f6c7a4c1)
![gant](https://github.com/user-attachments/assets/1cd78839-78e7-4c3b-accd-b231a10beceb)
![DELET ALET](https://github.com/user-attachments/assets/30032dc5-2b23-49af-b41a-9d65b69e891f)
