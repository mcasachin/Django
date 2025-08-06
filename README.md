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

No go to folder C:\Users\abc\my_tennis_club\members and open View.py , change the content of it as below
from django.shortcuts import render
from django.http import HttpResponse

def members(request):
    return HttpResponse("Hello world!")








