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

## Library

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

## API

### Models

![ERD](/images/erd-r.png)

### Routes

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

### Models

![ERD](/images/erd-p.png)

### Routes

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

### Monday

### Tuesday