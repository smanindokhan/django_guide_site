# VIEWS     

<br>

There are 2 types of Views-   

-  Function Based
-  Class Based


<br>

### Function Based  

Some Examples-  

<br>

```py
from django.shortcuts import render
from . import models

# Create your views here.

def list_patients(requests):
    all_patients = models.Patients.object.all()
    #all variables we need to show must be in dict
    context_list = {'patients': all_patients} 
    #context passes out the variables to html files
    return render(requests, 'office/list.html', context=context_list)
    


def list(request):
    all_cars = models.Car.objects.all()
    context = {'all_cars': all_cars}
    return render(request, 'cars/list.html', context=context)


def add(request):
    if request.POST:
        brand = request.POST['brand']
        year = int(request.POST['year'])
        models.Car.objects.create(brand=brand, year=year)
        # if user submitted new car go back to list view
        return redirect(reverse('cars:list'))
    return render(request, 'cars/add.html')


def delete(request):
    if request.POST:
        # delete car
        pk = request.POST['pk']
        try:
            models.Car.objects.get(pk=pk).delete()
            return redirect(reverse('cars:list'))
        except:
            print('Car Not Found!')
            return redirect(reverse('cars:list'))

    return render(request, 'cars/delete.html')
```     


<br>

### Class Based