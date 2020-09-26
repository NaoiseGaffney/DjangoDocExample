# Django Documentation Getting Started Tutorial

(Django Documentation Getting Started Tutorial)[https://docs.djangoproject.com/en/3.1/intro/]

## Initial Configuration

### GitHub

1. Create GitHub Repository using the CI Full Template.
2. Create a development branch (master + development).

### Visual Studio Code

#### Configure Visual Studio Code environment

3. New Window.
4. Clone Repository -> GitHub -> (DjangoDocExample)[https://github.com/NaoiseGaffney/DjangoDocExample].
5. Select development branch.
6. Create a virtual Python environment - Terminal: `python3 -m venv .venv`
7. Activate virtual Python environment - Terminal: `source .venv/bin/activate`
8. Install Django 3.1 - Terminal: `pip install Django`
9. Upgrade pip - Terminal: `pip install pip --upgrade`
10. Check Django version - Terminal: `python -m django --version`

#### Create the Initial Django Project

11. Create a Django **Project** called "mysite" - Terminal: `django-admin startproject mysite`
12. Verify that the initial Django project works - Terminal: `cd mysite`, `python manage.py runserver`, `http://127.0.0.1:8000/`

#### Create the Poll's Application

13. Create a Django **Application** called "polls" - Terminal: `python manage.py startapp polls`
14. Add the first **View** in "polls/views.py.
15. Create the first **URL** in "polls/urls.py" (create the file).
16. Point the root URLconf at the "polls/urls.py".
17. Verify that the new URL's work -  Terminal: `python manage.py runserver`, `http://127.0.0.1:8000/polls/`

#### Database Setup

18. Update "mysite/mysite/settings.py" to use the correct database binding, default is "sqlite3".
19. Update `TIME_ZONE = 'GMT'`.
20. Create the **Database** tables for the `INSTALLED_APPS` in "settings.py" - Terminal: `python manage.py migrate`

#### Creating Models

21. Update "polls/models.py" with the models (Question and Choice).

#### Activating Models (Change the Models in "models.py", run `python manage.py makemigrations` to create migrations for those changes, and `python manage.py migrate` to apply those changes to the database.)

22. Add `polls.apps.PollsConfig` to "mysite/mysite/settings.py".
23. Store the Models as migrations - Terminal: `python manage.py makemigrations polls`
24. (Optional) View, to verify, the SQL statements that are used by `migrate` to create the database tables - Terminal: `python manage.py sqlmigrate polls 0001`
25. Create the **Database** tables for the new Models - Terminal: `python manage.py migrate`

#### Playing with the API

26. `python manage.py shell`, shell ensures that manage.py sets the `DJANGO_SETTINGS_MODULE` environment variable.
27. Add...

```

import datetime
from django.utils import timezone
...
    def __str__(self):
        return self.question_text
...
    def __str__(self):
            return self.choice_text
...
    def was_published_recently(self):
            return self.pub_date >= timezone.now() - datetime.timedelta(days=1)

```

#### Django Admin

28. Create an admin user - Terminal: `python manage.py createsuperuser`
29. Verify that the Admin URL works -  Terminal: `python manage.py runserver`, `http://127.0.0.1:8000/admin/`
30. Make the poll application modifiable in Django Admin in "polls/admin.py".

#### Install and Configure Django Debug Toolbar
`pip install django-debug-toolbar`