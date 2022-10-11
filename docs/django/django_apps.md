# APPS      

<br>

- To register an app, this is done after adding the ulrs in project level url patterns.
- `Copy the app class name > settings.py > installed app list > appname.apps.classname`

<br>

Example-    

```py
'cars.apps.CarsConfig'
```

<br>

After this-     

```console
python manage.py makemigrations appname
```
