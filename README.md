# EX01 Developing a Simple Webserver
## Date:
25/09/2024
## AIM:
To develop a simple webserver to serve html pages and display the configuration details of laptop.

## DESIGN STEPS:
### Step 1: 
HTML content creation.

### Step 2:
Design of webserver workflow.

### Step 3:
Implementation using Python code.

### Step 4:
Serving the HTML pages.

### Step 5:
Testing the webserver.

## PROGRAM:
```
from flask import Flask, render_template_string
import platform
import psutil

# Initialize Flask app
app = Flask(__name__)

# Route for the home page
@app.route('/')
def system_info():
    # Fetch system configuration details
    os_info = platform.system() + " " + platform.release()
    processor_info = platform.processor()
    ram_info = round(psutil.virtual_memory().total / (1024 ** 3), 2)  # RAM in GB
    disk_info = round(psutil.disk_usage('/').total / (1024 ** 3), 2)  # Disk space in GB

    # HTML content with placeholders for system info
    html_content = """
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>System Configuration</title>
    </head>
    <body>
        <h1>Laptop Configuration Details</h1>
        <p><strong>Operating System:</strong> {{ os_info }}</p>
        <p><strong>Processor:</strong> {{ processor_info }}</p>
        <p><strong>Total RAM:</strong> {{ ram_info }} GB</p>
        <p><strong>Disk Space:</strong> {{ disk_info }} GB</p>
    </body>
    </html>
    """
    
    # Render the HTML with system info
    return render_template_string(html_content, os_info=os_info, processor_info=processor_info, 
                                  ram_info=ram_info, disk_info=disk_info)

# Run the Flask web server
if __name__ == "__main__":
    app.run(debug=True)
```
## OUTPUT:
![Screenshot (2)](https://github.com/user-attachments/assets/18b48fd4-ca31-4ba3-8760-f934693462d6)


## RESULT:
The program for implementing simple webserver is executed successfully.
