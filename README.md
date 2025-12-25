# Ex.04 Design a Website for Server Side Processing
## Date:10-12-2025

## AIM:
To create a web page to calculate vehicle mileage and fuel efficiency using server-side scripts.

## FORMULA:
M = D / F
<br> M --> Mileage (in km/l)
<br> D --> Distance Travelled (in km)
<br> F --> Fuel Consumed (in l)

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

## PROGRAM:
```
math.html
<html>
<head>
    <title>Mileage Calculator</title>
    <style>
        body 
        {
            background: grey;
       
        }
        .id1 
        {
            text-align: center;
            color: blue;
        }
        .box 
        {
            text-align: center;
            width: 40%;
            background-color: red;
            border: solid 6px black;
            padding: 25px;
            margin: 60px auto;
            position:fixed;
            top:80px;
            left:350px;
        }
        .result 
        {
            margin-top: 20px;
            font-weight: bold;
        }
    </style>
</head>
<body>
 
    <div class="box">
        <h1 ><u>The Mileage Calculator</u></h1>
        <h3>SIVA R(25007668)</h3>

        <form method="post">
            {% csrf_token %}
            <label>Distance Travelled (km)</label><br>
            <input type="number" name="distance"><br><br>

            <label>Liters Consumed (L)</label><br>
            <input type="number" name="liters"><br><br>

            <button type="submit">Calculate</button>
        </form>

        <div class="result">
            
                Mileage: {{ mileage }} km/L
            
        </div>
    </div>
    
</body>
</html>
```
```
views.py
from django.shortcuts import render


def mileage(request):
    km = int(request.POST.get('distance', 0))
    l = int(request.POST.get('liters', 0))

    mileage = km / l if request.method == 'POST' and l != 0 else 0

    print("kilometer=", km)
    print("liter=", l)
    print("mileage=", mileage)

    return render(request, 'mathapp/math.html', {'km': km, 'l': l, 'mileage': mileage})
    ```
    ```
    ursls.py
    from django.urls import path
from mathapp import views
urlpatterns = [
    path('', views.mileage, name='mileage'),
]
```

## OUTPUT - SERVER SIDE:

<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/3b4a2cbe-aa0b-4815-87a9-ae188784ee98" />


## OUTPUT - WEBPAGE:

![alt text](<Screenshot 2025-12-10 132747.png>)



## RESULT:
The a web page to calculate vehicle mileage and fuel efficiency using server-side scripts is created successfully.
