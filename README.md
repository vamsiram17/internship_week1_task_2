### Internship_week1_task_2

**Name   : Vamsi Ram**

**E-mail : vamsiramg@gmail.com**

# Web Development using Flask

## What is Flask?

Flask is a python web frame work which provides us with tools and libraries to build interactive web applications. It has three main dependencies,
- Routing
- Debugging
- Web Server Gateway Interface (WSGI)

This part includes from Chapter 1 to Chapter 5.

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


