# Ex.05 Design a Website for Server Side Processing
## Date: 05/12/2024

## AIM:
 To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side. 


## FORMULA:
P = I<sup>2</sup>R
<br> P --> Power (in watts)
<br> I --> Intensity
<br> R --> Resistance

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
<html>
<head>
<meta charset='utf-8'>
<meta http-equiv='X-UA-Compatible' content='IE=edge'>
<title>Power of a Lamp Filament</title>
<meta name='viewport' content='width=device-width, initial-scale=1'>
<style type="text/css">
body 
{
background-color:lightblue;
}
.edge {
width: 1400px;
margin-left: auto;
margin-right: auto;
padding-top: 250px;
padding-left: 300px;
}
.box {
display:block;
border: light dashed black;
width: 600px;
min-height: 400px;
font-size: 30px;
background-color:lightgray;
}
.formelt{
color:black;
text-align: center;
margin-top: 8px;
margin-bottom: 7px;
}
h1
{
color:light blue;
text-align: center;
padding-top: 15px;
}
</style>
</head>
<body>
<div class="edge">
<div class="box">
<h1>Power of a Light Filament</h1>
<form method="POST">
{% csrf_token %}
<div class="formelt">
intensity : <input type="text" name="intensity" value="{{i}}"></input>(in Wm<sup>-2</sup>)<br/>
</div>
<div class="formelt">
resistance : <input type="text" name="resistance" value="{{r}}"></input>(in ohm)<br/>
</div>
<div class="formelt">
<input type="submit" value="Calculate"></input><br/>
</div>
<div class="formelt">
Power : <input type="text" name="power" value="{{power}}"></input>(in W)<br/>
</div>
</form>
</div>
</div>
</body>
</html>


views.py

from django.shortcuts import render 
def rectarea(request): 
    context={} 
    context['area'] = "0" 
    context['l'] = "0" 
    context['b'] = "0" 
    if request.method == 'POST': 
        print("POST method is used")
        l = request.POST.get('length','0')
        b = request.POST.get('breadth','0')
        print('request=',request) 
        print('Length=',l) 
        print('Breadth=',b) 
        area = int(l) * int(b) 
        context['area'] = area 
        context['l'] = l
        context['b'] = b 
        print('Area=',area) 
    return render(request,'mathapp/math.html',context)


urls.py

from django.contrib import admin 
from django.urls import path 
from mathapp import views 
urlpatterns = [ 
    path('admin/', admin.site.urls), 
    path('areaofrectangle/',views.rectarea,name="areaofrectangle"),
    path('',views.rectarea,name="areaofrectangleroot")
]
```

## SERVER SIDE PROCESSING:

![alt text](<Screenshot 2024-12-05 145721.png>)

## HOMEPAGE:

![alt text](<Screenshot 2024-12-05 145622.png>)

## RESULT:
The program for performing server side processing is completed successfully.
