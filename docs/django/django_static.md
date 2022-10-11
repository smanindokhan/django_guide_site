# STATIC FILES

<br>

Directory-
```
app/static/appname/files
```

<br>

- After static is set migrate needs to be done


<br>
In html beginning-  

```py
{% load static %}
```

<br>
Then-

```html
<link rel="stylesheet" href="  {% static 'cars/custom.css' %} " />
```
