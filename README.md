# Library Management System with MySQL Integration

Welcome to the Library Management System with Database Integration! This project integrates a MySQL database to store and retrieve data related to books, users, authors, and genres.

## Features

- **Book Operations**: Add, update, search, and list books.
- **User Operations**: Register users, view user details, and list users.
- **Author Operations**: Add, update, and list authors.
- **Genre Operations**: Add, update, and list genres.
- **Borrow/Return Books**: Mark books as borrowed or returned.
- **User-Friendly CLI**: Command-line interface with clear menu options.
- **Input Validation**: Validate user input using regular expressions.

## Database Design

The database consists of the following tables:

- **Books**: Stores information about books.
- **Users**: Stores information about users.
- **Authors**: Stores information about authors.
- **Genres**: Stores information about genres.

## Setup Instructions

### Prerequisites

- Python 3.x
- MySQL Server
- `mysql-connector-python` library

### Installation

1. **Clone the repository**:
    ```bash
    git clone https://github.com/yourusername/library-management-system.git
    cd library-management-system
    ```

2. **Install the required Python packages**:
    ```bash
    pip install mysql-connector-python
    ```

3. **Set up the MySQL database**:
    - Create a new database:
        ```sql
        CREATE DATABASE library_db;
        ```
    - Use the provided Data Definition Language (DDL) scripts to create the necessary tables:
        ```sql
        USE library_db;

        CREATE TABLE Books (
            book_id INT AUTO_INCREMENT PRIMARY KEY,
            title VARCHAR(255) NOT NULL,
            author_id INT,
            genre_id INT,
            available BOOLEAN DEFAULT TRUE,
            FOREIGN KEY (author_id) REFERENCES Authors(author_id),
            FOREIGN KEY (genre_id) REFERENCES Genres(genre_id)
        );

        CREATE TABLE Users (
            user_id INT AUTO_INCREMENT PRIMARY KEY,
            name VARCHAR(255) NOT NULL,
            email VARCHAR(255) UNIQUE NOT NULL
        );

        CREATE TABLE Authors (
            author_id INT AUTO_INCREMENT PRIMARY KEY,
            name VARCHAR(255) NOT NULL
        );

        CREATE TABLE Genres (
            genre_id INT AUTO_INCREMENT PRIMARY KEY,
            name VARCHAR(255) NOT NULL
        );
        ```

### Configuration

1. **Database Connection**:
    - Establish a connection to the MySQL database using the `mysql-connector-python` library.
    - Create a database cursor to execute SQL queries.

    Example:
    ```python
    import mysql.connector

    def create_connection():
        connection = mysql.connector.connect(
            host='localhost',
            user='yourusername',
            password='yourpassword',
            database='library_db'
        )
        return connection
    ```

### Usage

1. **Run the main program**:
    ```bash
    python main.py
    ```

2. **Main Menu**:
    ```
    1. Book Operations
    2. User Operations
    3. Author Operations
    4. Genre Operations
    5. Quit
    ```

3. **Book Operations**:
    - Add new books
    - Update book availability
    - Search books by book_id, title, author, or genre
    - List all books

4. **User Operations**:
    - Register new users
    - View user details
    - List all users

5. **Author Operations**:
    - Add new authors
    - List all authors

6. **Genre Operations**:
    - Add new genres
    - List all genres

### Error Handling

- Implement error handling to manage database connection issues, invalid inputs, and other potential errors.

## Contributing

Contributions are welcome! Please fork the repository and submit a pull request.

## License

This project is licensed under the MIT License.
