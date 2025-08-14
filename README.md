# Django
Create a new environment --
python -m venv myworld

Avtivate the environment --
myworld\Scripts\activate.bat

Install Django
python -m pip install Django

Verify Django Version
django-admin --version
Create a new Project(my_tennis_club) of Django
django-admin startproject my_tennis_club

Note:: To rerun the project , Activate the nevironment using below commnad
C:\Users\abc>myworld\Scripts\activate.bat

Navigate to project Folder
cd C:\Users\abc\my_tennis_club

Run The project 
python manage.py runserver

Copy the URL from CMD Logs and open in browser, This will open default view of Django
http://127.0.0.1:8000/

press [CTRL] [BREAK], or [CTRL] [C] to stop the server and you should be back in the virtual environment

To Create the view app called members- Django creates a folder named members in my project, with this content:
python manage.py startapp members

**Views** 
Django views are Python functions that take http requests and return http response, like HTML documents.
A web page that uses Django is full of views with different tasks and missions.
Views are usually put in a file called views.py located on your app's folde

To create and display view, Need to send a response back to the browser.
To execute the view, we must call the view via the URL of it.

Example -
go to folder C:\Users\abc\my_tennis_club\members and open View.py , change the content of it as below
from django.shortcuts import render
from django.http import HttpResponse

def members(request):
    return HttpResponse("Hello world!")

**URLs**
Create a file named urls.py in the same folder as the views.py file, and type this code in it:
from django.urls import path
from . import views
urlpatterns = [
    path('members/', views.members, name='members'),
]

Now, go to folder C:\Users\abc\my_tennis_club\ and open urls.py , change the content of it as below
from django.contrib import admin
from django.urls import include, path

urlpatterns = [
    path('', include('members.urls')),
    path('admin/', admin.site.urls),
]

Run the server again and In the browser window, type 127.0.0.1:8000/members/ in the address bar.
You will see view displaying Hello world

**Templates**
In the Django Intro page, we learned that the result should be in HTML, and it should be created in a template, so let's do that.
Create a templates folder inside the members folder, and create a HTML file named myfirst.html
Open the HTML file and insert the following to filre- my_tennis_club/members/templates/myfirst.html:
<!DOCTYPE html>
<html>
<body>

<h1>Hello World!</h1>
<p>Welcome to my first Django project!</p>

</body>
</html>

Modify the View -Open the views.py file in the members folder -my_tennis_club/members/views.py, and replace its content with this:

from django.http import HttpResponse
from django.template import loader

def members(request):
  template = loader.get_template('myfirst.html')
  return HttpResponse(template.render())

Change Settings
To be able to work with more complicated stuff than "Hello World!", We have to tell Django that a new app is created.
This is done in the settings.py file in the my_tennis_club folder.
Look up the INSTALLED_APPS[] list and add the members app like this:my_tennis_club/my_tennis_club/settings.py:

INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'members'
]

Then run this command:
python manage.py migrate

Start the server by navigating to the /my_tennis_club folder and execute this command:
python manage.py runserver
In the browser window, type 127.0.0.1:8000/members/ in the address bar.







