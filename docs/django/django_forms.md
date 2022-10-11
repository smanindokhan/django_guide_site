# FORMS

<br>

This thing is needed in all django forms-
```html
 <form action="" method="post">
      {% csrf_token %}
      {{form}}
      <input type="submit" value="" />
    </form>
```

<br>

Final form example-
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

<br>


Create forms in html like the one `above>create forms.py in the app>create the form classes>import it in views>add it to view classes`

<br>

Example from views.py-
```py
<!-- redirect and reverse needed for redirecting -->
from django.shortcuts import render, redirect
from django.urls import reverse
from .forms import ReviewForm

#a class from view.py for forms
def rentalreview(request):
    if request.method == 'POST':
        form = ReviewForm(request.POST)
        if form.is_valid():
            print(form.cleaned_data)#it gives a python dictonary
            return redirect(reverse('cars:thankyou'))
    else:
        form = ReviewForm()
    return render(request, 'cars/rentalreview.html', context={'form': form})
```

<br>

Example from forms.py-
```py
from django import forms
 
 
class ReviewForm(forms.Form):
    first_name = forms.CharField(label='First Name', max_length=100)
    last_name = forms.CharField(label='Last Name', max_length=100)
    email = forms.EmailField(label='Email')
    review = forms.CharField(
        label='Please write your review!', widget=forms.Textarea(attrs={'class': 'myform'}))#atrs is used to design the widget
``` 

<br>

###In the .html tags-

<br>

Also can use things like as_table,as_ul,etc-
```py
{{form.as_p}} #wraps the form label around a paragraph tag
```

<br>

Just to get first name label and field not entire form-
```py
{{form.first_name.label_tag}} {{form.first_name}}
```
  