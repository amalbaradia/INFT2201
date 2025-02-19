# INFT2201
# Telephone Directory

A simple telephone directory web application that allows users to search for contact information (name, phone number, address, and category). Built with PHP for the backend and HTML for the frontend.

## Features
- Search contacts by name, phone number, or location.
- Display results dynamically on the page without a reload.
- Show contact information including name, phone number, address, and category.

## Requirements
- Apache server
- PHP
- PostgreSQL database

## Installation

1. Clone or download the repository:
   ```bash
   git clone https://github.com/yourusername/telephone-directory.git

2. Set up your environment

Ensure that you have **Apache**, **PHP**, and **PostgreSQL** installed on your system.

### Install Apache

Follow the installation instructions for your operating system:

- [Apache installation for Windows](https://httpd.apache.org/docs/2.4/getting-started.html)
- [Apache installation for Linux](https://httpd.apache.org/docs/2.4/install.html)

### Install PHP

Install PHP by following the instructions here:

- [PHP installation](https://www.php.net/manual/en/install.php)

### Install PostgreSQL

You can install PostgreSQL by visiting:

- [PostgreSQL installation](https://www.postgresql.org/download/)

## Database setup

1. **Create a database in PostgreSQL** and import the provided contacts table schema.

   Open your PostgreSQL console or GUI and run the following SQL commands to create the database and table:

   ```sql
   CREATE DATABASE telephone_directory;
   \c telephone_directory;

   CREATE TABLE contacts (
       id SERIAL PRIMARY KEY,
       name VARCHAR(100) NOT NULL,
       phone_number VARCHAR(20) UNIQUE NOT NULL,
       address TEXT,
       category VARCHAR(50) CHECK (category IN ('business', 'personal', 'emergency'))
   );
   ```
2. Edit the database connection in `dbconnect.php`

    Open `dbconnect.php` and modify the database connection details to match your setup.

    Example database connection in `dbconnect.php`:

    ```php
    $host = 'localhost'; // Change if using a different host
    $port = '5432'; // Default PostgreSQL port
    $dbname = 'telephone_directory'; // Replace with your database name
    $user = 'your_username'; // Replace with your database username
    $password = 'your_password'; // Replace with your database password

    $dbconnect = pg_connect("host=$host port=$port dbname=$dbname user=$user password=$password");
    if (!$dbconnect) {
        die("Connection failed: " . pg_last_error());
    }
    ```
3. Populate the database with sample data

    Add a few sample contacts into the contacts table to ensure testing works. Here's an example SQL insert:

    ```sql
    INSERT INTO contacts (name, phone_number, address, category)
    VALUES
        ('Jane Doe', '123-456-7890', '123 Main St, Springfield', 'personal'),
        ('John Smith', '987-654-3210', '456 Elm St, Springfield', 'business'),
        ('Emergency Service', '911', '123 Emergency Rd, Springfield', 'emergency');
    ```

## Running the application

    - Place the project folder in the root directory of your Apache server. This could be in `htdocs` (for XAMPP or WAMP) or the `www` directory (for Linux).
    
    - Open your browser and go to `http://localhost/telephone-directory/index.html`.

    - You can now search for contacts by name, phone number, or address.

## Usage

    - Enter a query (name, number, or location) in the search bar.
    - Press the "Search" button to see the results.
    - The results will be displayed below, showing the name, phone number, address, and category of the matching contacts.

## Troubleshooting

    - Database connection issues:** Ensure your PostgreSQL database is running, and the connection details in `dbconnect.php` are correct.
    - Data population:** If no results appear, ensure that the contacts table is populated with data using the SQL insert queries above.
    











