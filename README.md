# EX01 Developing a Simple Webserver

# Date:29-11-2024
# AIM:
To develop a simple webserver to serve html pages and display the configuration details of laptop.

# DESIGN STEPS:
## Step 1:
HTML content creation.

## Step 2:
Design of webserver workflow.

## Step 3:
Implementation using Python code.

## Step 4:
Serving the HTML pages.

## Step 5:
Testing the webserver.

# PROGRAM:
views.py
~~~
from django.shortcuts import render
from http.server import BaseHTTPRequestHandler, HTTPServer

content='''
<html>
<head>
    <style>
/* Reset some default table styles */
table {
  width: 100%;
  border-collapse: collapse; /* Merges the table borders */
  margin: 20px 0; /* Adds space above and below the table */
}

th, td {
  padding: 12px 20px; /* Adds padding inside table cells */
  text-align: left; /* Aligns text to the left */
  border: 1px solid #ddd; /* Light gray border */
}

/* Style for table headers */
th {
  background-color: #4CAF50; /* Green background for header */
  color: white; /* White text color */
}

/* Alternate row colors */
tbody tr:nth-child(odd) {
  background-color: #f9f9f9; /* Light background for odd rows */
}

tbody tr:nth-child(even) {
  background-color: #f1f1f1; /* Slightly darker background for even rows */
}

/* Hover effect */
tbody tr:hover {
  background-color: #ddd; /* Slight gray background on hover */
}


        
    </style>
</head>
<body>

    <table>
        <thead>
            <tr>
                <th colspan="2">Laptop Specification </th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>Device name</td>
                <td>DESKTOP-MOHHBTU</td>
            </tr>
            <tr>
                <td>Processor</td>
                <td>13th Gen Intel(R) Core(TM) i5-1335U   1.30 GHz</td>
            </tr>
            <tr>
                <td>Installed RAM</td>
                <td>16.0 GB (15.7 GB usable)</td>
            </tr>
            <tr>
                <td>System type</td>
                <td>64-bit operating system, x64-based processor</td>
            </tr>
            <tr>
                <td>Pen and touch</td>
                <td>No pen or touch input is available for this display</td>
            </tr>
        </tbody>
    </table>

</body>
</html>
</html>
'''




class myserver(BaseHTTPRequestHandler):
    def do_GET(self):
        print("Get request received....")
        self.send_response(200)
        self.send_header("content-type","text/html")
        self.end_headers()
        self.wfile.write(content.encode()) 
print("This is my webserver!")
server_address = ('',8000)
httpd=HTTPServer(server_address,myserver)
httpd.serve_forever()
~~~
urls.py
~~~
from django.contrib import admin
from django.urls import path
from django.urls import path,include
from myapp import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('myserver', views.myserver),
]
~~~
# OUTPUT:
![Screenshot 2024-11-29 112134](https://github.com/user-attachments/assets/ebf0a7cc-3256-45e5-ba3d-f9c796fb854e)

# RESULT:
The program for implementing simple webserver is executed successfully.
