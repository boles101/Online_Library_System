# Online_Library_System
Simple Online Library System with Api.Net 6 


The Online Library System is a web-based application designed to manage the operations of a library, allowing librarians and users to interact with the library resources efficiently.
It supports two types of users: librarians and normal users, with specific roles and permissions for each.

## Features

- **Librarian**
  - Manage books (Create, Read, Update, Delete)
  - Manage user borrow requests
  - Approve or reject user account registrations
  - Generate reports on book availability and borrowings

- **Normal User**
  - Register and manage their own accounts (pending approval)
  - Search for books using Id
  - Request to borrow books
  - View history of borrowed books
  
## Prerequisites

- .NET 6
- Entity Framework Core
- SQL Server 
- ASP.NET Core Runtime

## Usage

After starting the application, navigate to `http://localhost:5000` to access the Online Library System.

  ### For Librarians
  - Login with your librarian credentials. (UserName = "admin" , Password = "123456")
  - Use the management dashboard to add, update, or delete books.
  - Approve or reject user registration requests from the 'User Management' tab.
  
  ### For Normal Users
  - Register for an account and wait for approval. (2 Users Created : "NormalUser" , "NewUser" . Password = "123456")
  - Once approved, log in to search and request books.
  - View your borrow history for the Logged in User.

## Database Schema

The database consists of several key models integral to the functionality of the Online Library System. Each model serves a distinct purpose within the application:

- **User**: Managed by .NET Identity, this model stores user information including login credentials. Users are categorized into roles which dictate their permissions within the system.
  
- **Book**: Represents the books available in the library. Each book record contains:
  - `Id`: The primary key.
  - `Title`: The title of the book.
  - `Author`: The author(s) of the book.
  - `PublishYear`: The year the book was published.
  - `Quantity Available`: Number in stock.
  
- **Borrow**: Tracks the borrowing details of each book by users. It includes:
  - `BorrowId`: A unique identifier for each borrow transaction. (Guid)
  - `BookId`: Linked to the `Book` model, identifying the borrowed book.
  - `UserId`: Linked to the `User` model, identifying the user who borrowed the book.
  - `BorrowDate`: The date when the book was borrowed.
  - `ReturnDate`: The pre-set date when the book is expected to be returned, typically set to 7 days from the borrow date.
  
- **Role**: Utilized by .NET Identity to define roles within the system. There are two predefined roles:
  - `Admin`: Administrators who can manage books, user accounts, and view reports.
  - `NormalUser`: Regular users who can search for books, request borrows, and view their borrowing history.


