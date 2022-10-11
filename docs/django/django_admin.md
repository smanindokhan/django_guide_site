# ADMIN

<br>

To create the admin-
```console
python manage.py createsuperuser
```

<br>

To connect models to django admin-
```console
app>admin.py>register model
```

<br>

- To see a model in our admin panel we have to register it first.

<br>

In admins.py-

```py
from django.contrib import admin
from cars.models import Car

# Register your models here.
admin.site.register(Car)
```

