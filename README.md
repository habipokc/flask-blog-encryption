# flask-blog-encryption

This code is a web application for a blog platform. It allows users to register, login, create and edit blog posts, leave comments on posts, and perform administrative actions. The code is built using the Flask web framework in Python.

Let's go through the code to understand its functionality:

  First, the necessary packages are imported, including Flask, render_template, redirect, url_for, flash, abort, and various other packages for specific  functionalities like form handling, database interaction, user authentication, and image handling.

  The Flask application is created and configured with a secret key. CKEditor is initialized for rich text editing support, and Bootstrap is applied for styling the templates. Gravatar is configured to generate profile picture URLs for users.

  The application is connected to a SQLite database file named "blog.db" using SQLAlchemy.

  A User class is defined as a model representing users in the database. It inherits from the UserMixin class provided by Flask-Login, which adds user authentication-related methods. The User class has a one-to-many relationship with BlogPost and Comment classes, representing the authorship of blog posts and comments made by users.

  A BlogPost class is defined as a model representing blog posts in the database. It has a foreign key relationship with the User class, indicating the author of the post. It also has a one-to-many relationship with the Comment class for comments on the post.

  A Comment class is defined as a model representing comments in the database. It has foreign key relationships with both the User and BlogPost classes, indicating the comment author and the parent post.

  The database tables are created using the db.create_all() method.

  A decorator function named admin_only is defined to restrict certain routes to the admin user only. It checks if the current user's ID is not equal to 1 (assuming ID 1 represents the admin user) and aborts the request with a 403 error if the condition is not met.

Several routes are defined:

  The '/' route displays all the blog posts on the index page.
  The '/register' route handles user registration, including form validation and password hashing. If the user already exists, a flash message is displayed.
  The '/login' route handles user login, including form validation and password checking. If the email or password is incorrect, flash messages are displayed.
  The '/logout' route logs out the user.
  The '/post/int:post_id' route displays a specific blog post along with its comments. Users can leave comments on the post if they are logged in.
  The '/about' and '/contact' routes display static pages.
  The '/new-post' route allows the admin user to create a new blog post.
  The '/edit-post/int:post_id' route allows the admin user to edit an existing blog post.
  The '/delete/int:post_id' route allows the admin user to delete a blog post.
  Finally, the application is run in debug mode.

In summary, this code creates a blog platform with user registration, login, blog post creation/editing, comment functionality, and administrative privileges. It utilizes a database to store user information, blog posts, and comments, and provides a user-friendly interface using Flask and various extensions.
