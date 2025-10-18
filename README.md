# Ex.06 Book Front Cover Page Design
## Date:

## AIM:
To design a book front cover page using HTML and CSS.

## DESIGN STEPS:

### Step 1:
Create a Django Admin project.

### Step 2:
Create an app in the Django interface.

### Step 3:
Create a folder named 'static' in the app folder.

### Step 4:
Create a new HTML file in the static folder.

### Step 5:
Write the HTML code with relevant CSS properties.

### Step 6:
Choose the appropriate style and color scheme.

### Step 7:
Insert the images in their appropriate places.

### Step 8:
Publish the website in the LocalHost.

## PROGRAM:
```
bmi.html
--------
<html>
    <head>
        <title>BMI Calculator</title>
        <style>
            form{
                text-align: center;
                margin-top: 13%;
                margin-left: 36%;
                width: 350px;
                border: 5px solid rgb(182, 89, 3);
                padding: 2%;
            }
            label{
                font-size: 18px;
                font-weight: bold;
            }
            div{
                margin: 10px;
            }
        </style>
    </head>
    <body style="background-color: rgb(146, 241, 241);">
        <form method="post">
            <h1 style="color: rgb(57, 2, 160)">BMI Calculator</h1>
          {% csrf_token %}
            <div>
                <label>Height (cm):</label>
                <input type="text" name="height">
            </div>
            
            <div>
                <label>Weight (kg):</label>
                <input type="text" name="weight"><br>
            </div>
            
            <div>
                <button type="submit">Calculate</button>
            </div>
             
            <div>
                {% if BMI %}
                <h3>Your BMI is: {{ BMI }}</h3>
                {% endif %}
            </div>
            
            
        </form>      
    </body>
</html>

views.py
--------
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

    return render(request, "server_side_processing/bmi.html", {"BMI": bmi})

urls.py
-------

from django.contrib import admin
from django.urls import path
from server_side_processing import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', views.calculate_bmi, name='calculate_bmi'),
]


```
## OUTPUT:


## RESULT:
The program for designing book front cover page using HTML and CSS is completed successfully.
