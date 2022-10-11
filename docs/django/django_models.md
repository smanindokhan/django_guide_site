# MODELS

<br>


Creates set of instruction but doesn't apply (1)
```console
python manage.py makemigrations name 
```

Runs the migrations (2)
```console
python manage.py migrate 
```

To see SQL code that's running
```console
python manage.py sqlmigrate appname 0001 
```
<br>

- Any time a model is made or any changes is made repeat (1) & (2)



<br>

## Create

```py
from office.models import Patients
```
<br>

```py
Patients.objects.create(first_name='susan',last_name='smith',age=40)
mylist=[Patients(first_name='midfmi',last_name='smixth',age=50),Patient(first_name='mimxi',last_name='smitah',age=30)]
Patients.objects.bulk_create(mylist)
```

<br>


## Read
```py
Patients.objects.all()
Patients.objects.all()[0]
Patients.objects.get(pk=1) #pk=primary key and SQL index start at 1
Patients.objects.filter(last_name='smith')
Patients.objects.filter(last_name='smith').filter(age=40)
```
<br>

```py
from django.db.models import Q  #for conditional operators
Patients.objects.filter(Q(last_name='smith')&Q(age=40))
```
<br>

- Field lookup

```py
Patients.objects.filter(last_name__startswith='s')
Patients.objects.filter(age__in=[20,30,50])
Patients.objects.filter(age__gte=39) #gte=greater than or equal to
```

<br>

## Update   

```py
carl= Patients.objects.get(pk=1)
carl= Patients.objects.get(pk=1)
carl.save()
```


To validate data in a model-    

```py
from django.core.validators import MaxValueValidator, MinValueValidator  #can be of more types

heart_rate = models.IntegerField(default=60, validators=[MinValueValidator(1), MaxValueValidator(300)])
```

<br>

## Delete   

```py
data= Patients.objects.get(pk=1)
data.delete()
```
