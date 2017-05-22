# We’ll assume you have Django installed already, and then we can check version of Django:
python -m django --version
If not, please install Django:
sudo -E pip install django

# Create a project:
django-admin startproject myproject

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
python manage.py runserver

# Changing the port:
# By default, the runserver command starts the development server on the internal IP at port 8000.
# If you want to change the server’s port, pass it as a command-line argument. For instance, this command starts the server on port 8080:
python manage.py runserver 8080

# If you want to change the server’s IP, pass it along with the port.
# For example, to listen on all available public IPs (which is useful if you are running Vagrant or want to show off your work on other computers on the network), use:
python manage.py runserver 0:8000
# 0 is a shortcut for 0.0.0.0. Full docs for the development server can be found in the runserver reference

# Automatic reloading of runserver
# The development server automatically reloads Python code for each request as needed. You don’t need to restart the server for code changes to take effect.
# However, some actions like adding files don’t trigger a restart, so you’ll have to restart the server in these cases.
