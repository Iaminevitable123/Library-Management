# Library-Management
# Library Management System – DBMS Project

## 📘 Overview

This project is a Library Management System designed for the CSL-220: Database Management Systems Lab. It is based on the analysis of KOHA (an open-source library system) and demonstrates core database design and implementation principles, including normalization and CRUD operations.

## 🔍 Features

- Book issuing, returns, renewals, and donations
- User and employee management
- Library card and membership tracking
- Book reservation system
- Fine calculation and history tracking
- Auditing for book and employee data changes

## 🔗 Sample Application Reference

- [KOHA Demo](https://koha-community.org/demo/)

## 📐 Methodology

### Business Rules

- A book can be issued only once at a given time.
- Each book has one physical location but may have multiple authors, publishers, and genres.
- One user can have one library card with a membership type.
- One shelf belongs to a single section but can contain many books.
- Return date must always be after the issue date.

### ERD and Schema

The system is designed following ER modeling and normalized up to 3NF and BCNF where applicable.

## 🧱 Database Schema (Post-Normalization)

### Main Tables

- `Book(ISBN, Title, ReleaseDate, ConditionCode)`
- `Condition(ConditionCode, ConditionDescription)`
- `Authors(AuthorID, AuthorName)`
- `Genre(GenreID, GenreName)`
- `Publishers(PublisherID, PublisherName)`
- `Sections(SectionID, SectionName)`
- `Bookshelf(BookshelfID, SectionID)`
- `Book_Details(ISBN, AuthorID, PublisherID, GenreID, BookshelfID, Row, Column)`
- `Employee(EmpID, Name, DOB, DOJ, Address, Email, Phone, JobCode, Password, ManagerID)`
- `Jobs(JobCode, JobTitle, Salary)`
- `User(UserID, Name, Address, DOB, Email, Phone, LibCard)`
- `Library_Card(LibCard, IssueDate, PendingFines, FinesPaid, MemberCode)`
- `Membership(MemberCode, MembershipTitle, BorrowLimit, TimeLimit)`
- `Borrow_Return(ISBN, UserID, EmpID, IssueDate, ReturnDate, ActualReturnDate, Fines, ConditionCode, Returned)`
- `Book_Reserve(LibCard, ISBN, ReserveDate)`
- `Book_History(UserID, ISBN, IssueDate, ReturnDate)`
- `Book_Donation(ISBN, UserID, ConditionCode, Date)`

### Audit Tables

- Audit logs for insertions and deletions in:
  - `Book`
  - `Employee`

## 🛠️ Technologies Used

- **Database**: Microsoft SQL Server
- **Development**: SQL (DDL/DML), ER Diagrams

## ✅ Key Outcomes

- Efficient and normalized relational database
- Full implementation of CRUD operations
- Enhanced user experience via reservation and search functionalities
- Security and reliability through auditing mechanisms

## 📌 Limitations

- No support for multi-library branches
- No integration for employee payroll or automated notifications
- Sample data and scope scaled down for academic purposes

## 🏁 Conclusion

The project successfully demonstrates key DBMS concepts including normalization, relational schema design, and system auditing. While limited in scope, it effectively models core library operations and user interactions within a single-branch library system.

