# FORMS WITH MODELS

<br>

### ModelClass

Make a model in models.py then register it in admin.py then `make migrations>migrate`


<br>

Example of the model-

```py
from django.db import models
from django.core.validators import MinValueValidator, MaxValueValidator
 
# Create your models here.
class Review(models.Model):
    first_name = models.CharField(max_length=30)
    last_name = models.CharField(max_length=30)
    stars = models.IntegerField(
        validators=[MinValueValidator(1), MaxValueValidator(5)])
```
<br>


Then in forms.py-

```py
from django import forms
from . models import Review
from django.forms import ModelForm
 
class ReviewForm(ModelForm):
    class Meta:
        model = Review
        # we can choose which to keep in fields or we can use '__all__'
 to give everything
        fields = ['first_name', 'last_name', 'stars']
    #if we want to change default labels
        labels = {
            'first_name': 'Your First Name',
            'last_name': 'Your Last Name',
            'stars': 'Rating'
        }
#if we want to change default error message
        error_messages = {
            'stars': {
                'min_value': 'Min Rating is 1!',
                'max_value': 'Max Rating is 5!',
            }
        }
```
<br>


In views.py-
```py
from django.shortcuts import render, redirect
from django.urls import reverse
from .forms import ReviewForm
 
# Create your views here.
def rentalreview(request):
    if request.method == 'POST':
        form = ReviewForm(request.POST)
        if form.is_valid():
            form.save()
```

<br>


Final Form-
```html
<!-- .errors shows the validator errors -->
    <div class="container">
      <form action="" method="post">
        {% csrf_token %}
        {% for field in form %}
        <div class="mb-3">
          {{field.label_tag}}
        </div>
        {{field}}
        {{field.errors}}
        {% endfor %}
        <input type="submit" />
      </form>
    </div>
```


