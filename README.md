# Mewgram

A Discord clone built with Django.

## Project Setup (Day 1)

- Custom user model (`CustomUser`) with email login and username for display
- Django REST Framework and JWT authentication configured
- PostgreSQL database connection via `.env` and `python-decouple`
- Media and static file settings added
- Admin interface supports custom user model
- `.gitignore` and `.env` set up for security
- Git repository initialized and first commit made

## Directory Structure

```
manage.py
plan.md
requirements.txt
accounts/
    __init__.py
    admin.py
    apps.py
    models.py
    tests.py
    views.py
    migrations/
        __init__.py
Mewgram/
    __init__.py
    asgi.py
    settings.py
    urls.py
    wsgi.py
.env
.gitignore
```

## Environment Variables

Environment variables are stored in `.env` and injected into the terminal using VS Code settings.

## How to Run (Development)

1. Install dependencies:
   ```sh
   pip install -r requirements.txt
   ```
2. Set up PostgreSQL and create a database (see plan.md or project instructions)
3. Configure your `.env` file with database credentials and secret key
4. Run migrations:
   ```sh
   python manage.py makemigrations
   python manage.py migrate
   ```
5. Create a superuser:
   ```sh
   python manage.py createsuperuser
   ```
6. Start the development server:
   ```sh
   python manage.py runserver
   ```
7. Access the admin panel at [http://127.0.0.1:8000/admin](http://127.0.0.1:8000/admin)

---

This README provides an overview of the Mewgram project, including its setup, directory structure, and next steps for development.
