# Project 4 Pitch

A guide to my fourth project for General Assembly.

**Contents**

1. [Overview](https://github.com/jtreeves/project_4_pitch#overview)
2. [Library](https://github.com/jtreeves/project_4_pitch#library)
3. [API](https://github.com/jtreeves/project_4_pitch#api)
4. [App Backend](https://github.com/jtreeves/project_4_pitch#app-backend)
5. [App Frontend](https://github.com/jtreeves/project_4_pitch#app-frontend)
6. [Plan](https://github.com/jtreeves/project_4_pitch#plan)

## Overview

This project will be distributed over four repositories:
- A library of algorithms, written in Python
- An API that uses the library, written in Python using the Django framework and a SQL database
- A backend for a main app that uses the API, written in JavaScript using the Express framework and a Mongo database
- A frontened for a main app that works with its backend repository, written in JavaScript using the React framework


## Library

This [library](https://github.com/jtreeves/matrix_regression) will be made publically available after it is uploaded to Python's database of libraries. It contains all the code for determining regression equations, as well as the code for evaluating said regressions and presenting their results in a raw format.

### File Structure

```
regressions_library  
|-- matrices  
|   |-- matrix.py  
|   |-- magnitude.py  
|   |-- dot_product.py  
|   |-- column.py  
|   |-- additions.py  
|   |-- scalar.py  
|   |-- multiplication.py  
|   |-- determinant.py  
|   |-- cofactors.py  
|   |-- minors.py  
|   |-- inverse.py  
|   |-- transpose.py  
|-- regressions  
|   |-- run_all.py  
|   |-- best.py  
|   |-- error.py  
|   |-- linear.py  
|   |-- quadratic.py  
|   |-- cubic.py  
|   |-- hyperbolic.py  
|   |-- exponential.py  
|   |-- logarithmic.py  
|   |-- logistic.py  
|   |-- sinusoidal.py  
|-- tests  
|   |-- matrices.py  
|   |-- regressions.py  
|-- READE.md  
|-- .gitignore  
```

### Code Examples

**Linear Regression**
```python
def linear(data):
    independent_matrix = []
    dependent_matrix = []
    for i in range(len(data)):
        independent_matrix.append([data[i][0], 1])
        dependent_matrix.append([data[i][1]])
    transposition = transpose(independent_matrix)
    product = multiplication(transposition, independent_matrix)
    product_matrix = matrix(product, dtype='float')
    inversion = inv(product_matrix)
    inversion_list = matrix.tolist(inversion)
    second_product = multiplication(inversion_list, transposition)
    solution = multiplication(second_product, dependent_matrix)
    equation = lambda x: solution[0][0]*x + solution[1][0]
    inaccuracy = error(data, equation)
    result = {
        'constants': solution,
        'error': inaccuracy
    }
    return result
```

**Error Calculation**
```python
def error(data, equation):
    summation = 0
    for i in range(len(data)):
        summation += (data[i][1] - equation(data[i][0]))**2
    result = summation**(1/4)
    return result
```

## API

This [API](https://github.com/jtreeves/regressions_api) will directly pull information from the library. Anyone can use it after getting an API key. It can provide regression models for various data sets.

### Models

![ERD](/images/erd-r.png)

### Routes

| Method | Model       | Path       | File     | Description                   |
| ------ | ----------- | ---------- | -------- | ----------------------------- |
| POST   | users       | /signup/   | views.py | Sign up a new user            |
| POST   | regressions | /          | views.py | Create a new regression       |
| GET    | regressions | /\<int:pk\>/ | views.py | Get an existing regression    |
| PUT    | regressions | /\<int:pk\>/ | views.py | Update an existing regression |
| DELETE | regressions | /\<int:pk\>/ | views.py | Delete an existing regression |

### File Structure

```
regressions_api
|-- configurations
|   |-- __init__.py
|   |-- asgi.py
|   |-- settings.py
|   |-- urls.py
|   |-- wsgi.py
|-- regressions
|   |-- middleware
|   |-- migrations
|   |-- templates
|   |   |-- regressions
|   |   |-- about.html
|   |   |-- base.html
|   |   |-- index.html
|   |   |-- math.html
|   |   |-- signup.html
|   |   |-- usage.html
|   |-- __init__.py
|   |-- admin.py
|   |-- apps.py
|   |-- models.py
|   |-- tests.py
|   |-- urls.py
|   |-- views.py
```

### User Stories

- As a potential user, I want to know about its appeal, so I have a reason to sign up.
- As a potential user, I want to see specific examples of how it can be used by customers, so I know how I can implement it.
- As a potential user, I want to understand the mathematical logic that it implements and how it differs from any competitors, so I can understand the logic.
- As a potential user, I want to be able to sign up for an API key, so I can use it.
- As a user, I want to be able to upload my data to their database by using my API key, so I can access it.
- As a user, I want to be able to view my data stored in their database by using my API key, so I can access it.
- As a user, I want to know that no one else can access my data, so I know it is secure.
- As a user, I want to get extensive info from the API, so I know that it was worth signing up for.
- As a user, I want to get the data in a raw format, so I can easily customize it to my needs.

### Designs

**Home Page**
![Home Page](/images/wireframe-r1.png)

**Math Explanation**
![Math Explanation](/images/wireframe-r2.png)

**Usage Guide**
![Usage Guide](/images/wireframe-r3.png)

**Sign Up**
![Sign Up](/images/wireframe-r4.png)

## App Backend

This repository will serve as the [backend for the main app](https://github.com/jtreeves/predictions-backend). It will directly pull from the API. However, unlike the API, when the information is displayed on the app's frontend, it will be in a visually appealing way, as opposed to in a raw format.

### Models

![ERD](/images/erd-p.png)

### Routes

| Method | Model       | Path     | File       | Description                        |
| ------ | ----------- | -------- | ---------- | ---------------------------------- |
| POST   | users       | /signup  | users.js   | Sign up a new user                 |
| POST   | users       | /login   | users.js   | Log in an existing user            |
| GET    | users       | /:id     | users.js   | Display a user's data              |
| PUT    | users       | /:id     | users.js   | Update a user's data               |
| DELETE | users       | /:id     | users.js   | Delete a user's account            |
| POST   | predictions | /:id     | budgets.js | Create a new prediction            |
| GET    | predictions | /all/:id | budgets.js | View all of a user's predictions   |
| GET    | predictions | /:id     | budgets.js | View one of a user's predictions   |
| PUT    | predictions | /:id     | budgets.js | Update one of a user's predictions |
| DELETE | predictions | /:id     | budgets.js | Delete one of a user's predictions |

### File Structure

```
predictions-backend
|-- controllers
|   |-- users.js
|   |-- predictions.js
|-- models
|   |-- schemas
|   |   |-- subschemas
|   |   |   |-- Favorite.js
|   |   |   |-- Note.js
|   |   |-- User.js
|   |   |-- Prediction.js
|   |-- index.js
|-- middleware
|   |-- authentication.js
|-- test
|   |-- users.test.js
|   |-- predictions.test.js
|-- server.js
|-- package.json
|-- package-lock.json
|-- README.md
|-- .gitignore
```

## App Frontend

This repository will serve as the [frontend for the main app](https://github.com/jtreeves/predictions-frontend). Unlike the API, when it displays the information it receives from the usser, it will be in a visually appealing way, as opposed to in a raw format.

### File Structure

```
predictions-frontend
|-- public
|   |-- index.html
|   |-- manifest.json
|   |-- robots.txt
|   |-- favicon.ico
|-- src
|   |-- components
|   |   |-- pages
|   |   |   |-- welcome
|   |   |   |   |-- Home.js
|   |   |   |   |-- About.js
|   |   |   |-- profile
|   |   |   |   |-- Home.js
|   |   |   |   |-- Analyze.js
|   |   |-- elements
|   |   |   |-- main
|   |   |   |   |-- Navigation.js
|   |   |   |   |-- Form.js
|   |   |   |   |-- Header.js
|   |   |   |   |-- Footer.js
|   |   |   |-- welcome
|   |   |   |   |-- Introduction.js
|   |   |   |   |-- Signup.js
|   |   |   |   |-- Login.js
|   |   |   |-- profile
|   |   |   |   |-- List.js
|   |   |   |   |-- View.js
|   |   |   |   |-- Add.js
|   |   |   |   |-- Update.js
|   |   |   |   |-- Delete.js
|   |   |-- middleware
|   |   |   |   |-- Authentication.js
|   |   |   |   |-- Private.js
|   |   |   |   |-- Regression.js
|   |   |   |   |-- SpreadsheetInput.js
|   |   |   |   |-- GraphOutput.js
|   |-- App.js
|   |-- App.css
|   |-- App.test.js
|   |-- setupTests.js
|   |-- reportWebVitals.js
|   |-- index.js
|-- package.json
|-- package-lock.json
|-- README.md
|-- .gitignore
```

### User Stories

- As a potential user, I want to know about its appeal, so I have a reason to sign up.
- As a potential user, I want to see specific examples of how it can be used by customers, so I know how I can implement it.
- As a potential user, I want to be able to sign up with an email and password, so I can create an account
- As a user, I want to be able to log in to my account with my email and password, so I can use the site.
- As a user, I want to be able to submit data sets, so I can get them analyzed.
- As a user, I want to be able to submit my data sets in a CSV format, so the process only involves one step and uses a format in which I probably already have the data.
- As a user, I want to be able to see regression models that fit the data I submitted, so I can better understand my original data.
- As a user, I want to get the analysis in an easily digestible format, so I can understand it without needing a background in math.
- As a user, I want to be able to access previously uploaded data sets and their analyses, so I do not need to repeatedly re-upload the same data every time I want to analyze it.
- As a user, I want to be able to favorite specific models of my data, so I do not need to look at unideal formats.
- As a user, I want to be able to add notes to my models and view them at a future date, so I can use the site to keep track of my thoughts on my initial data and the site's analysis.
- As a user, I want to know that no one else can access my data, so I know it is secure.

### Designs

**Home Page**
![Home Page](/images/wireframe-p1.png)

**About**
![About](/images/wireframe-p2.png)

**Sign Up**
![Sign Up](/images/wireframe-p3.png)

**Log In**
![Log In](/images/wireframe-p4.png)

**Blank Profile**
![Blank Profile](/images/wireframe-p5.png)

**Filled Profile**
![Filled Profile](/images/wireframe-p6.png)

**Add New Data Set**
![Add New Data Set](/images/wireframe-p7.png)

**View Data Set**
![View Data Set](/images/wireframe-p8.png)

## Plan

### Sunday

- Create publishable versions of all repos
- Publish three main repos with Heroku
- Publish library with Python
- Connect app with API with library
- Ensure data flow works from frontend to backend to API to library, and back again

### Monday

- Implement modules to import CSV data from the user and provide visually appealing graphs as an end result (using D3)
- Edit the appearance of all repos
- Ensure nothing key is missing from any repo

### Tuesday

- Stretch goals with machine learning for sinusoidal and logistic models
- Finalize styling
- Optimize
- Ensure everything cohesively works together