# Django account template

[![Django CI](https://github.com/Enriquema/django_account/actions/workflows/django.yml/badge.svg)](https://github.com/Enriquema/django_account/actions/workflows/django.yml)

This repository is to have a template to easily include the account app/module to your new Django app.

## Prerequisites
You need to have django 5.1 installed.
Check the requirements

## Configure the account app into your django app
1. start your account app
django-admin startapp account

2. copy and overwrite all the account content with this module

3. Remove the account/migrations folder and regenerate the migrations applying the following commands:
```shell
python manage.py makemigrations
python migrate
```

4. modify your settings.py and add the following code
```python
LOGIN_REDIRECT_URL = '<your main view>'
LOGIN_URL = 'login'
LOGOUT_REDIRECT_URL = 'login'/'<your main view>'
```

5. To configure app smtp email you must add the following code to the settings.py (Page 65from book)
```python
EMAIL_HOST = 'smtp.gmail.com'
EMAIL_HOST_USER = 'your_account@gmail.com
EMAIL_HOST_PASSWORD = ''
EMAIL_PORT = 587
EMAIL_USE_TLS = True
```

6. Install Pillow
```shell
pip install Pillow==10.4
```

7. Edit settings.py and add the following lines
```python
MEDIA_URL = 'media/'
MEDIA_ROOT = BASE_DIR / 'media'
```

8. To configure the authentication throught username or email you must add the following lines to settings.py
AUTHENTICATION_BACKENDS = [
    'django.contrib.auth.backends.ModelBackend',
    'account.authentication.EmailAuthBackend',
]

9. You need to include your new account application to your settings INSTALLED_APPS:
```python
# Application definition

INSTALLED_APPS = [
    'account.apps.AccountConfig',
    ...
```

10. And Finally you need to modify your main urls file as follows:
```python
from django.contrib import admin
from django.urls import path, include
from django.conf import settings
from django.conf.urls.static import static

urlpatterns = [
    path('admin/', admin.site.urls),
    path('account/', include('account.urls')),
]

if settings.DEBUG:
    urlpatterns += static(settings.MEDIA_URL,
                          document_root=settings.MEDIA_ROOT)
```
