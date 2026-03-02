# Mewgram

A Discord clone built with Django.

## Project Setup

- Python and Django project initialized
- Basic Django app structure created
- `.env` file configured for environment variables (secret key, database credentials, etc.)
- `.gitignore` set up to exclude sensitive and unnecessary files
- Git repository initialized

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

## Version Control

Sensitive files like `.env` are excluded from git using `.gitignore`.

## Next Steps

- Implement Django models and views
- Set up database and authentication
- Build chat and messaging features

---
This README provides an overview of the Mewgram project, including its setup, directory structure, and next steps for development.
