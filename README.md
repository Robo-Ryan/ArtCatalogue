# ArtCatalogue

## Description

An App for Artists to Understand their Work Through Cataloguing their Art

## Table of Contents

- [Prework Study Guide Webpage](#prework-study-guide-webpage)
  - [Description](#description)
  - [Table of Contents](#table-of-contents)
  - [Installation](#installation)
  - [Usage](#usage)
  - [Credits](#credits)
  - [License](#license)
  - [Features](#features)
  - [How to Contribute](#how-to-contribute)
  - [Tests](#tests)

## Installation
<!-- Follow Heroku guide to create a backend app -->

<!-- Link your heroku app to your github repo -->

<!-- Follow Add-on guide to create a Postgresql database in Heroku -->

<!-- Use DBeaver to create SQL tables -->
brew install --cask dbeaver-community

1.	SSL Configuration:
	•	Heroku databases often require SSL for connections. You should check the “SSL” tab
	•	Set the SSL mode to require. This ensures that the connection is encrypted.
In DBeaver:
	•	Go to the SSL tab.
	•	Check the box Use SSL.
	•	Set the SSL mode to require.
 2.	Testing the Connection:
	•	Use the “Test Connection” button to ensure everything is working correctly. If you see any issues, make sure your credentials are correct, and SSL is properly configured.

Useful SQL Queries:
	•	Add a New Tag:
     INSERT INTO tags (name) VALUES ('Technology');
 	•	Associate a Tag with a Post:
      INSERT INTO post_tags (post_id, tag_id) VALUES (1, 2);
  •	Retrieve All Tags for a Post:
      SELECT t.name FROM tags t
      JOIN post_tags pt ON t.id = pt.tag_id
      WHERE pt.post_id = 1;
  •	Insert a New User:
      INSERT INTO users (username, email, password) VALUES ('john_doe', 'john@example.com', 'password123');
  •	Create a New Post:
       INSERT INTO posts (user_id, title, content, published) VALUES (1, 'My First Post', 'This is the content of my first post.', TRUE);
  •	Edit a Post:
       UPDATE posts
       SET content = 'This is the updated content of the post.', 
       updated_at = CURRENT_TIMESTAMP  -- Update the timestamp to reflect the change
       WHERE id = 1;
  •	Delete a Post:
  •	Scheduled Post:


  Step 2: Connect Your Website to the Database
  To interact with the database from your web application, you’ll need to establish a connection using the appropriate database library or ORM (Object-Relational Mapper).
  	1.	Install the pg package:
   npm install pg
   	2.	Use the pg library to connect to your database:
    const { Pool } = require('pg');

const pool = new Pool({
  connectionString: process.env.DATABASE_URL, // This environment variable is automatically set by Heroku
  ssl: {
    rejectUnauthorized: false
  }
});

pool.query('SELECT * FROM users', (err, res) => {
  if (err) {
    console.error(err);
  } else {
    console.log(res.rows);
  }
  pool.end();
});

Step 5: Perform CRUD Operations
You can now use SQL queries to perform CRUD (Create, Read, Update, Delete) operations on your database directly from your web application.

	•	Insert a new user:
pool.query('INSERT INTO users (username, email, password) VALUES ($1, $2, $3)', ['john_doe', 'john@example.com', 'password123'], (err, res) => {
  if (err) {
    console.error(err);
  } else {
    console.log('User added successfully');
  }
});

	•	Retrieve all posts:
 pool.query('SELECT * FROM posts', (err, res) => {
  if (err) {
    console.error(err);
  } else {
    console.log(res.rows);
  }
});
 
## Usage

The landing page includes images 


## Credits

N/A

## License

MIT License

Copyright (c) [2024] [Ryan Merlini]

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

## Features
Create Account
View Catalogue
Modal View Post
Create Post
  Upload Image
  Save as Draft
  Edit Content
  Delete Post
  Add a Tag
List Posts
  Sort by Tag
Schedule A Newsletter Email

## How to Contribute

N/A

## Tests

N/A
