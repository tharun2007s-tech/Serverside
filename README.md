# Ex.05 Design a Website for Server Side Processing
## Date:

## AIM:
 To design a website to calculate the body mass index in the server side. 


## FORMULA:
BMI = W/(H*H)
<br> W --> Weight (in kg)
<br> H --> Height (in cm)

## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub.

### Step 2:
Create Django Admin project.

### Step 3:
Create a New App under the Django Admin project.

### Step 4:
Create python programs for views and urls to perform server side processing.

### Step 5:
Create a HTML file to implement form based input and output.

### Step 6:
Publish the website in the given URL.

## PROGRAM :
```
template.html
<!DOCTYPE html>
<html>
<head>
    <title>BMI Calculator</title>
</head>
<body>
    <form method="POST">
  {% csrf_token %}
  <label>Height (cm):</label>
  <input type="text" name="height"><br>
  <label>Weight (kg):</label>

  <input type="text" name="weight"><br>

  <button type="submit">Calculate</button>
</form>

{% if BMI %}
  <h3>Your BMI is: {{ BMI }}</h3>
{% endif %}
</body>
</html>

urls.py
from django.contrib import admin
from django.urls import path
from bmiapp import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', views.calculate_bmi, name='calculate_bmi'),
]

views.py
from django.shortcuts import render

def calculate_bmi(request):
    bmi = None

    if request.method == "POST":
        try:
            height_cm = float(request.POST.get("height"))
            weight_kg = float(request.POST.get("weight"))
            height_m = height_cm / 100  # convert cm to meters
            
            bmi = weight_kg / (height_m * height_m)

            print(f"Calculated BMI: {bmi:.2f}")  # Output to console

        except (TypeError, ValueError, ZeroDivisionError):
            bmi = None

    return render(request, "bmiapp/template.html",{"BMI":bmi})
```



## SERVER SIDE PROCESSING:

![alt text](<Screenshot 2025-09-24 153329.png>)


## HOMEPAGE:

![alt text](<Screenshot (27).png>)


## RESULT:
The program for performing server side processing is completed successfully.
