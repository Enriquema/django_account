# Prerequisites
You need to have django 5.1 installed

# Configure the account app into your django app
1. start your account app
django-admin startapp account

2. copy and overwrite all the account content with this module

3. modify your settings.py and add the followin code
"""
LOGIN_REDIRECT_URL = '<your main view>'
LOGIN_URL = 'login'
LOGOUT_REDIRECT_URL = 'login'/'<your main view>'
"""

4. To configure app smtp email you must add the following code to the settings.py (Page 65from book)
"""
EMAIL_HOST = 'smtp.gmail.com'
EMAIL_HOST_USER = 'your_account@gmail.com
EMAIL_HOST_PASSWORD = ''
EMAIL_PORT = 587
EMAIL_USE_TLS = True
"""

5. Install Pillow
"""
pip install Pillow==10.4
"""

6. Edit settings.py and add the following lines
"""
MEDIA_URL = 'media/'
MEDIA_ROOT = BASE_DIR / 'media'
"""

7. To configure the authentication throught username or email you must add the following lines to settings.py
AUTHENTICATION_BACKENDS = [
    'django.contrib.auth.backends.ModelBackend',
    'account.authentication.EmailAuthBackend',
]
