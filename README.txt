# We’ll assume you have Django installed already, and then we can check version of Django:
$ python -m django --version
If not, please install Django:
$ sudo -E pip install django

# Create a project:
$ django-admin startproject myproject

# Let’s look at what startproject created:
myproject/
    manage.py
    myproject/
        __init__.py
        settings.py
        urls.py
        wsgi.py

# The development server
# Let’s verify your Django project works. Change into the outer myproject directory:
$ python manage.py runserver

# Changing the port:
# By default, the runserver command starts the development server on the internal IP at port 8000.
# If you want to change the server’s port, pass it as a command-line argument. For instance, this command starts the server on port 8080:
$ python manage.py runserver 8080

# If you want to change the server’s IP, pass it along with the port.
# For example, to listen on all available public IPs (which is useful if you are running Vagrant or want to show off your work on other computers on the network), use:
$ python manage.py runserver 0:8000
# 0 is a shortcut for 0.0.0.0. Full docs for the development server can be found in the runserver reference

# Automatic reloading of runserver
# The development server automatically reloads Python code for each request as needed. You don’t need to restart the server for code changes to take effect.
# However, some actions like adding files don’t trigger a restart, so you’ll have to restart the server in these cases.

# Creating the Polls app
# Your apps can live anywhere on your Python path. In this tutorial, we’ll create our poll app right next to your manage.py file so that it can be imported as its own top-level module, rather than a submodule of mysite.
# To create your app, make sure you’re in the same directory as manage.py and type this command:
$ python manage.py startapp polls
# That’ll create a directory polls, which is laid out like this:
polls/
    __init__.py
    admin.py
    apps.py
    migrations/
        __init__.py
    models.py
    tests.py
    views.py
# This directory structure will house the poll application.

# Install MySQL:
$ sudo apt-get install libmysqlclient-dev
$ sudo -E pip install mysql-python

# Create a database:
$ CREATE DATABASE django_db CHARACTER SET utf8 COLLATE utf8_general_ci;

# Some of these applications make use of at least one database table, though, so we need to create the tables in the database before we can use them. To do that, run the following command:
$ python manage.py migrate

# Activating models:
$ python manage.py makemigrations polls
$ python manage.py sqlmigrate polls 0001
$ python manage.py migrate

# Playing with the API
$ python manage.py shell

# Install Bootstrap:
$ sudo -E pip install django-bootstrap3
# Install JQuery
$ sudo -E pip install django-jquery
# Install AngularJS
$ sudo -E pip install django-angular

# Creating an admin user:
$ python manage.py createsuperuser

# Removing hardcoded URLs in templates
# Remember, when we wrote the link to a question in the polls/index.html template, the link was partially hardcoded like this:
<li><a href="/polls/{{ question.id }}/">{{ question.question_text }}</a></li>
# The problem with this hardcoded, tightly-coupled approach is that it becomes challenging to change URLs on projects with a lot of templates. However, since you defined the name argument in the url() functions in the polls.urls module, you can remove a reliance on specific URL paths defined in your url configurations by using the {% url %} template tag:
<li><a href="{% url 'detail' question.id %}">{{ question.question_text }}</a></li>

# Running tests
# In the terminal, we can run our test:
$ python manage.py test polls