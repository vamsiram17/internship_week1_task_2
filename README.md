## Internship_week1_task_2
**Name   : Vamsi Ram
E-mail : vamsiramg@gmail.com**

# Web Development using Flask

## What is Flask?

Flask is a python web frame work which provides us with tools and libraries to build interactive web applications. It has three main dependencies,
- Routing
- Debugging
- Web Server Gateway Interface (WSGI)

### Chapter – 1:

Initially we begin by *setting up a virtual environment* in our python compiler.
~~~
**pip install virtualenv**
~~~
Then we need to create a sub folder in our main folder such as
~~~
**python -m venv virtual_environment_name**
~~~ 
Then we need to *install the Flask* by using Python Install Package command,
~~~
**pip install flask**
~~~
We can **check all the packages** that are installed in our virtual environment by using the command, 
~~~
**pip freeze**
~~~
We need to activate the virtual environment in order to build our app using flask.
We can activate the virtual environment by using the command,
~~~
**virtual_environment_name\Scripts\activate**
~~~

### Chapter – 2:

### Basic Application Structure:

Initially we must create an application instance. Then the webserver passes all the requests to this object using WSGI protocol. This application instance can be created as,
~~~
from flask import Flask
app = Flask(__name__)
~~~
The flask application keeps mapping the URL requests to the Python functions. This association between a URL and function is called as route.

A complete application script would look like this.
~~~
*from flask import Flask
app = Flask(__name__)

*@app.route('/')
def index():
    print('The Apex Predator RANDY ORTON')
~~~
### Development Web Server:

The flask application includes a development web server that run with flask run command.
We need to activate the virtual environment created and import the flask package.
Then we need to specify the file containing the python script to the FLASK_APP.

### Chapter – 3:

### Templates:
In Flask templates of the web pages can be written and they can separately be stored in a sub folder inside the root directory.

Now we can import the render_template function from the Flask library which converts a template to a complete HTML page. This process is called rendering.

The render_template() function will invoke the Jinja2 template engine that comes bundled along with the Flask framework. This Jinja2 then substitutes {{ ... }} blocks with the corresponding values, given by the arguments which are provided in the **render_template()** call function.

We can make use of **if, else if and else conditional statements** inside these templates to return the necessary output on the web page.
There is also a feature of **template inheritance** which can be used in order to avoid multiple copies of certain page layouts that are common to all the templates.

This can be achieved by the following command, **{% extends "base.html" %}**
Where extends statement will establish the inheritance link between the templates.
The two contents should have matching block statements so that Jinga2 will then combine these two templates.

### Chapter – 4:

### Web Forms

In order to work with the webforms, we can make use of the **flask-wtf extension**. These are like regular python packages and can be installed using python pip command as
**pip install flask-wtf**.
There are different formats for the application to specify configuration options.The basic method is to define the variables as keys in **app.config**, which uses a dictionary style to work with variables.

After creating a config file,we need to tell Flask to read it and apply it.This can be done right after the Flask application instance is created using the **app.config.from_object()** method.

Also an example of user login form is demonstrated and deployed on the local server which included basic HTML fileds and validators.
Form handling,Redirecting user sessions and Message flashing examples are provided and discussed their applications briefly.

### Chapter – 5:

### Datbases

**SQL:**

- The most commonly used databases for web applications are those based on the relational model are the SQL databases.
- These store data in the form of tables containing rows and columns.
- The columns define the attributes of the data which they store in multiple tables.
- These tables have relational connection between them with the help of primary keys and foreign keys. 

**NoSQL:**

- The database with this structure has the role name explicitly stored with each user.
- If an entry needs to be renamed it can then turn out to be an expensive operation that may require updating a large number of documents.
- With NoSQL databases,having the data duplicated will enable faster querying.

We need to consider different factors when chosing a database, mainly its **Ease of use, Performance, Portability** and **Flask integration**.

In case of Flask, we need to consider **SQLAlchemy**.It is a relational database which supports several database backends.
A database needs to be specified as a URL.

**db = SQLAlchemy(app)**
The db object instantiated from the class SQLAlchemy represents the database and provides access to all the functionality of Flask-SQLAlchemy.
Model definition can be given inside a class and defining functions inside the class with proper return commands.
With the help of db commands,we can **create ,modify,delete and query** different rows among the tables.


### Chapter – 6:

### Email

In order to integrate Email with web application, we can make use of the **flask-mail pckage**.
This extension connects it to a SMTP, Simple Mail Transfer Protocol and passes the email to it for delivery.
~~~
*app.config['MAIL_SERVER']* = 'enter_the_mail_server'

*app.config['MAIL_PORT']* = (enter the port)

*app.config['MAIL_USE_TLS']* = True

*app.config['MAIL_USERNAME']* = os.environ.get('MAIL_USERNAME')

*app.config['MAIL_PASSWORD']* = os.environ.get('MAIL_PASSWORD')
~~~
We can send mails from the python shell by importing the **Message method** from the **flask_mail package**.
Then we can integrate the Emails with the web applicartion using app.config() and defining a function.


### Chapter – 7:

### Large Application Structure

In this book they proposed a structure in order to efficiently handle the development of Web Applications for large scale structures.

This method include four top-level folders:

- The Flask application which is inside a package generically named app.
- The migrations folder that contains the database migration scripts.
- Unit tests which are written in a tests package.
- The venv folder that contains the Python virtual environment.

Also there need to be some files for configuration which are:

- **requirements.txt** which lists the package dependencies so that it is easy to regenerate an identical virtual environment on a different computer.
- **config.py** that stores the configuration settings.
- **flasky.py** that defines the Flask application instance, and also includes a few tasks that help manage the application.

### Chapter – 8:

### User Authentication

This can be done wit the help of Flask extension called **Flask-Login**. 

This extension manages the user logged-in state, so that for example users can log in to the application and then navigate to different pages while the application "remembers" that the user is logged in. It also provides the "remember me" functionality that allows users to remain logged in even after closing the browser window.
~~~
*from flask_login import LoginManager

*app = Flask(__name__)
.....
*login = LoginManager(app)
~~~
The Flask-Login extension works with the application's user model,and certain properties and methods could be implemented in it.

There are four required items which are:

- **is_authenticated**
- **is_active**
- **is_anonymous**
- **get_id()**

Flask-Login keeps track of the logged in user by storing its unique identifier in Flask's user session, a storage space assigned to each user who connects to the application.
There needs to be application's help in loading a user. For that reason, the extension expects that the application will configure a user loader function which looks like,
~~~
*from app import login

*@login.user_loader

*def load_user(id):

    *return User.query.get(int(id))
~~~
An example of login form is explained integrating all the above mentioned methods.

### Chapter – 9:

### User Roles

In case of a **simple application** we may need just **two roles** namely, one for **regular users** and one for **administrators**. In this case, having an is_administrator Boolean field in the User model may be all that is necessary.
Whereas in case of a more complex application may need additional roles with varying levels of power in between regular users and administrators.
Several application permisiion commands can be stated and defined inside a Permisiion class.

There can be four main user roles:
- None
- User
- Moderator
- Administrator

Once these roles are created then they are assigned and verified with the users.

### Chapter – 10:

### User Profiles

- Some additional information of the users can be stored in the database.
- An intreactive **User Profile Page** can be created wherein the user information can be gathered and displayed.
- We can also provide **Profile Edit** option for the users.
- We can add add user images and avatars, but instead of uploading images in the server,we can use the Gravatar service to provide images for all users.
- We can also make use of Jinja2 Sub-Templates to make more interactive user profile pages.

*Chapter 11 to Chapter 13 mainly focussed on developing a blog and discussing ways to improve the appearance and enabling different features such as likes,comments and displaying the previous blogs in the main informtion page.Creating a blog involved incorporating various packages like rendering templates and databases.*

### Chapter – 14:

### Application Program Interfaces

Flask is an ideal framework to build RESTful Application Program Interfaces.The six defining features of this REST architecture are:
- Client Server
- Stateless
- Cache
- Uniform Interface
- Layered System
- Code on demand

There are several Request methods such as **GET**, **POST**, **PUT** and **DELETE**.

We can create an API Blueprint because the routes associated with a RESTful API form a self-contained subset of the application, so putting them in their own blueprint is the best way to keep them well organized.

We can use the Flask HTTPAuth to perform user authentication.There are different ways to authenticate the user,Token Based or Serializing Resoures to and from JSON.


### Chapter – 15:

### Testing

- We can test the developed web application with the help of Unit Tests.
- These are used to confirm whether the code is working in the expected way or not and these unit tests also emsure that there is no regressions.
- We can obtain the **Code Coverage reports** with the help of Python **coverage package**.
- Flask comes equipped with a test client.This test client replicates the environment that exists when an application is running inside a web server, allowing tests to act as clients and send requests.
- End to end testing can be done by using **selenium**.

### Chapter – 16:

### Performance

The **get_debug_queries()** function returns the queries issued during the request as a list.The commands include
- statement  --> The SQL statement
- parameters --> The parameters used in the SQL statement.
- start_time --> time the query was issued.
- end_time   --> time query was returned.
- duration   --> duration of the query in seconds.
- context    --> string that indicates the source code location.

### Chapter – 17:

### Deployment

Several methods to deploy the web application are explained which include 
- Cloud Deployment - through EC2 service by AWS.
- Containers - Platform as a Service using Docker

The entire process to deploy the web application using Heroku Platform is explained clearly which inclues preparing the application to testing.

