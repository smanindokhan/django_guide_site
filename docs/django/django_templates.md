# TEMPLATES     

<br>

-  In app level always make a folder with sub-directories as `templates / appname / .html files`   

<br>

Then we need to import os-

```py
import os
``` 

<br>

For project level templates, in settings for templates add that to `DIR=[]` to find templates-   

```py
DIR = [os.path.join(BASE_DIR, 'templates/')]
```

<br>

In the template html file we index a list by using `.` `so list_name.0`-

```html
<h2>Her first name was {{first_name.1}}</h2>
```
<br>

To write a comment-

```html
<h2>{# this is a comment #}</h2> <!-- better to use html comment -->
```

<br>


To add filter we add  `|`-

```html
<h2>Her first name was {{first_name | upper}} and last name was {{last_name}}</h2>
```

<br>

- To get a URL `app_name = 'my_app'`, register this in urls.py then name your URLs  

<br>

In anchor tags-

```py
{% url 'my_app:variable' %}
```
<br>

### BLOCKS

<br>

- For base.html we generally set blocks anything above block content is header and below is footer (common for all html files, when it's extended to other html templates.).    

```py
{% block content %} 
{% endblock %}
```
<br>

An Example-

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>Document</title>
  </head>
  <body>
    <--Static same content for all pages above block here -->
    {% block content %}
    {% endblock  %}
  </body>
</html>
```

<br>


Extend it to get in other html files-   

```py
{% extends 'base.html' %} 
{% block content %}

'''inside here will be all the actual html contents contents,
but we dont have to add typical html layout as we have already 
done it in base.html'''

{% endblock %}
```











