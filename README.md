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

Navigate to project Folder
cd C:\Users\abc\my_tennis_club

Run The project 
python manage.py runserver

Copy the URL from CMD Logs and open in browser, This will open default view of Django
http://127.0.0.1:8000/

press [CTRL] [BREAK], or [CTRL] [C] to stop the server and you should be back in the virtual environment

To Create the view app called members- Django creates a folder named members in my project, with this content:
python manage.py startapp members

Django Views 
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







