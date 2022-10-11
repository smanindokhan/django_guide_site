# DJANGO URLS

- To start of we make urls.py in the app we created.  
<br>  

Then we import this 2 lines of code-

```python
from django.urls import path
from . import views
```     
<br>

We then give it a name generally same as the app we created-       

```python
app_name = 'appname'
```
<br>


In app level we first do the imports then add the patterns-

```py
from django.urls import path
from . import views

#Here views.list_patients is the class name in Views
urlpatterns = [

    path('', views.list_patients, name='list_patients'),
]
```  
<br>

- 'include' is added to get the urls from app. One 'include' for all the urls.
<br>

- In the project level urls we do the imports then include the urls from the apps.  

<br>

An Example-

```py
from django.contrib import admin
from django.urls import path, include 

urlpatterns = [
    path('admin/', admin.site.urls),
    path('my_app/', include('my_app.urls')),
]

```
