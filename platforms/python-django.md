# Working with Django

This document provides guidelines and best practices for AI agents working on Django projects. Django is a high-level Python web framework that encourages rapid development and clean, pragmatic design.

## 1. Core Concepts

- **The MVT Architecture**: Django follows the Model-View-Template (MVT) architectural pattern.
  - **Model**: The single, definitive source of your data. It contains the essential fields and behaviors of the data you’re storing. Generally, each model maps to a single database table.
  - **View**: A function that takes a web request and returns a web response. The response is typically the HTML contents of a web page, or a redirect, or a 404 error, etc.
  - **Template**: A text file that defines the structure of a file (such as an HTML page). Django's template language is used to embed dynamic content.
- **"Batteries-Included"**: Django comes with a lot of built-in features, including an Object-Relational Mapper (ORM), an authentication system, and an automatic admin interface.

## 2. Project Structure

- **Project vs. App**:
  - A **Project** is a collection of configurations and apps for a particular website. A project can contain multiple apps.
  - An **App** is a web application that does something – e.g., a weblog system, a database of public records, or a simple poll app. An app is a self-contained module that can be reused across different projects.
- **`manage.py`**: A command-line utility that lets you interact with your Django project.

## 3. Core Components

### Models and the ORM

Models are defined in `models.py`. Each model is a Python class that subclasses `django.db.models.Model`. The attributes of the model represent database fields.

Django's Object-Relational Mapper (ORM) is a powerful way to interact with your database using Python code instead of writing SQL.

- **Defining a Model**:

  ```python
  # myapp/models.py
  from django.db import models

  class Article(models.Model):
      title = models.CharField(max_length=200)
      content = models.TextField()
      pub_date = models.DateTimeField('date published')
  ```

- **Migrations**: The ORM uses a migration system to track changes to your models and propagate them to the database.
  - `python manage.py makemigrations`: Creates new migration files based on the changes you have made to your models.
  - `python manage.py migrate`: Applies the migrations to the database.
- **Querying Data**:
  - `Article.objects.all()`: Get all articles.
  - `Article.objects.filter(title__contains='Django')`: Get articles with "Django" in the title.
  - `Article.objects.get(id=1)`: Get a single article by its primary key.

### Views

Views are defined in `views.py`. They take an `HttpRequest` object and return an `HttpResponse` object.

- **Function-Based Views (FBVs)**: The simplest way to write a view.

  ```python
  # myapp/views.py
  from django.http import HttpResponse
  from .models import Article

  def article_list(request):
      latest_articles = Article.objects.order_by('-pub_date')[:5]
      output = ', '.join([a.title for a in latest_articles])
      return HttpResponse(output)
  ```

- **Class-Based Views (CBVs)**: An alternative way to write views, allowing you to reuse common functionality.

### Templates

Templates are typically stored in a `templates` directory inside an app. Django's template language allows you to embed dynamic data and use template tags for logic.

- **`{{ variable }}`**: Renders the value of a variable.
- **`{% tag %}`**: Executes a template tag (e.g., `{% if ... %}`, `{% for ... %}`).

### URLs

The `urls.py` file maps URL patterns to views.

```python
# myproject/urls.py
from django.urls import path, include

urlpatterns = [
    path('myapp/', include('myapp.urls')),
    # ...
]

# myapp/urls.py
from django.urls import path
from . import views

urlpatterns = [
    path('', views.article_list, name='article_list'),
]
```

## 4. The Admin Interface

Django automatically generates a powerful admin interface from your models. To use it, you need to register your models in `admin.py`.

```python
# myapp/admin.py
from django.contrib import admin
from .models import Article

admin.site.register(Article)
```

## 5. Development Workflow

- **Start a project**: `django-admin startproject myproject`
- **Start an app**: `python manage.py startapp myapp`
- **Run the development server**: `python manage.py runserver`
