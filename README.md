# Flask Hello World

## Overview
This is a minimal Flask application that runs on GCP and returns "Hello, World!" when accessed via a web browser.

## Requirements
Ensure you have the following installed:
- Python (>=3.7)
- pip (Python package manager)
  
Run these commands to install Python:
```
sudo apt update
sudo apt install python3 python3-pip python3-venv python3-dev build-essential
```
Confirm you have python installed by running:
```
python3 --version
```
Install flask by running:
```
sudo apt install python3-flask
```
Confirm you have flask installed by running:
```
flask --version
```
Install git by running:
```
sudo apt install git
```
Confirm you have git installed by running:
```
git --version
```
---

## Exercise 1 DUE 03/03
### Setup Instructions

1. **After starting you GCP VM, ssh into it and clone the repository:**
   ```sh
   git clone <repository_url>
   cd flask-hello-world
   ```

2. **Run the application:**
   ```sh
   python app.py
   ```

3. **Access the application:**
   Open a web browser and go to:
   ```
   On your VM you will see: 
   * Running on http://127.0.0.1:5000

   However, this is the home IP and will not work. 127.0.0.1 needs to be updated with the external IP to your VM.
   On the details page of your vm, there will be a public endpoint. Copy and paste that into your browser with port 5000. 
   ```
   You should see "Hello, World!" displayed on the page.

4. To terminate the server upon completion of the assignment, you will need to execute **Ctrl + C**.
   !!IMPORTANT!! ALWAYS STOP YOUR VM WHEN YOU ARE DONE USING IT.

## Understanding the Code

```python
from flask import Flask

app = Flask(__name__)

@app.route('/')
def hello_world():
    return "Hello, World!"

if __name__ == '__main__':
    app.run(debug=True)
```

### Breakdown: 
- `Flask(__name__)` initializes a Flask web application.
- `@app.route('/')` maps the root URL (`/`) to the `hello_world` function.
- `return "Hello, World!"` sends the response when the URL is accessed.
- `app.run(debug=True)` starts the development server with debug mode enabled.

---

## Exercise 2 DUE 03/05
### Assignment Instructions
Modify the page by adding a base.html file to the repository to set the look and feel of your local application.
  
1. Create a directory within the respository at the root level called 'templates'
2. In the templates directory create a file called base.html and copy and paste the below contents to the html file.
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{% block title %}Flask App{% endblock %}</title>
</head>
<body>
    <header>
        <h1>My Flask Application</h1>
    </header>

    <main>
        {% block content %}{% endblock %}
    </main>

    <footer>
        <p>&copy; 2025 Flask App</p>
    </footer>
</body>
</html>
```

  3. In the templates directory create another html file called index.html and copy and paste the below contents to the html file.
```
{% extends 'base.html' %}

{% block title %}Home - Flask App{% endblock %}

{% block content %}
    <h2>Hello, World!</h2>
{% endblock %}
```

  4. Update the app.py file to have this content:
```python
from flask import Flask, render_template

app = Flask(__name__)

@app.route('/')
def home():
    return render_template('index.html')

if __name__ == '__main__':
    app.run(debug=True)
```
5. To terminate the server upon completion of the assignment, you will need to execute **Ctrl + C**.
      !!IMPORTANT!! ALWAYS STOP YOUR VM WHEN YOU ARE DONE USING IT.

## Troubleshooting
- If Flask is not found, ensure dependencies are installed using `pip install -r requirements.txt`.
- If the port is busy, change `app.run(debug=True)` to `app.run(host='0.0.0.0', port=8080)`. Don't forget to update the port in the url.

---
Happy coding! 🚀
