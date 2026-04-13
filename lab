CREATE DATABASE library_query_lab;
USE library_query_lab;

-- MEMBER TABLE
CREATE TABLE MEMBER (
    MemberID INT PRIMARY KEY AUTO_INCREMENT,
    FullName VARCHAR(100) NOT NULL,
    Email VARCHAR(100) NOT NULL UNIQUE,
    Age INT CHECK (Age >= 12),
    Phone VARCHAR(15) NOT NULL DEFAULT 'N/A'
);

-- BOOK TABLE
CREATE TABLE BOOK (
    BookID INT PRIMARY KEY AUTO_INCREMENT,
    Title VARCHAR(255) NOT NULL,
    ISBN VARCHAR(50) NOT NULL UNIQUE,
    Price DECIMAL(8,2) CHECK (Price >= 0),
    Availability ENUM('AVAILABLE','BORROWED') DEFAULT 'AVAILABLE'
);

-- BORROW TABLE
CREATE TABLE BORROW (
    BorrowID INT PRIMARY KEY AUTO_INCREMENT,
    MemberID INT,
    BookID INT,
    BorrowDate DATE NOT NULL,
    FOREIGN KEY (MemberID) REFERENCES MEMBER(MemberID),
    FOREIGN KEY (BookID) REFERENCES BOOK(BookID)
);
-- MEMBER
INSERT INTO MEMBER (FullName, Email, Age, Phone) VALUES
('Amin Khan','amin@gmail.com',22,'01711111111'),
('Rahim Uddin','rahim@gmail.com',25,'01811111111'),
('Karim Hasan','karim@gmail.com',17,'01911111111'),
('Anika Rahman','anika@gmail.com',20,'N/A'),
('Sajid Khan','sajid@gmail.com',30,'01611111111'),
('Tanvir Hasan','tanvir@gmail.com',15,'N/A'),
('Arman Hossain','arman@gmail.com',28,'01511111111'),
('Jannat Islam','jannat@gmail.com',19,'01722222222');

-- BOOK
INSERT INTO BOOK (Title, ISBN, Price, Availability) VALUES
('Database Systems','ISBN001',1500,'AVAILABLE'),
('Data Structures','ISBN002',1200,'BORROWED'),
('Operating System','ISBN003',2000,'AVAILABLE'),
('Computer Networks','ISBN004',800,'BORROWED'),
('Machine Learning','ISBN005',2500,'AVAILABLE'),
('Data Science','ISBN006',1800,'AVAILABLE'),
('Artificial Intelligence','ISBN007',3000,'BORROWED'),
('Programming in C','ISBN008',600,'AVAILABLE');

-- BORROW
INSERT INTO BORROW (MemberID, BookID, BorrowDate) VALUES
(1,2,'2024-01-01'),
(2,4,'2024-01-02'),
(3,2,'2024-01-03'),
(4,7,'2024-01-04'),
(5,4,'2024-01-05'),
(6,7,'2024-01-06'),
(7,2,'2024-01-07'),
(8,4,'2024-01-08'),
(1,7,'2024-01-09'),
(2,2,'2024-01-10');
-- show all
SELECT * FROM MEMBER;
SELECT * FROM BOOK;
SELECT * FROM BORROW;

-- distinct availability
SELECT DISTINCT Availability FROM BOOK;

-- Age >= 18
SELECT * FROM MEMBER WHERE Age >= 18;

-- Price between 500 and 2000
SELECT * FROM BOOK WHERE Price BETWEEN 500 AND 2000;

-- Availability filter
SELECT * FROM BOOK WHERE Availability IN ('AVAILABLE','BORROWED');

-- Name starts A or ends n
SELECT * FROM MEMBER 
WHERE FullName LIKE 'A%' OR FullName LIKE '%n';

-- Phone not N/A and Age > 20
SELECT * FROM MEMBER 
WHERE Phone <> 'N/A' AND Age > 20;

-- Age not between 12 and 17
SELECT * FROM MEMBER 
WHERE Age NOT BETWEEN 12 AND 17;

-- Title contains Data
SELECT * FROM BOOK 
WHERE Title LIKE '%Data%' OR Title LIKE '%Database%';

-- top 3 expensive
SELECT * FROM BOOK ORDER BY Price DESC LIMIT 3;

-- cheapest 2
SELECT * FROM BOOK ORDER BY Price ASC LIMIT 2;

-- count
SELECT COUNT(*) FROM MEMBER;
SELECT COUNT(*) FROM BOOK;
SELECT COUNT(*) FROM BORROW;

-- avg min max
SELECT AVG(Price), MIN(Price), MAX(Price) FROM BOOK;

-- group by availability
SELECT Availability, COUNT(*) FROM BOOK GROUP BY Availability;

-- borrow count per member
SELECT MemberID, COUNT(*) 
FROM BORROW 
GROUP BY MemberID;
