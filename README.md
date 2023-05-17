\djangoreactproject>
 - py -m venv env 
 - env\scripts\activate.bat
 - py -m pip freeze > requirements.txt
 - pip install -r requirements.txt

T1> pip install django
T1> django-admin startproject djangoproject

\djangoreactproject\djangoproject>
T2> npx create-react-app reactapp

djangoreactproject
 |-dangoproject
   |-djangoproject
   |-reactapp
   |-manage.py

\djangoreactproject\djangoproject\reactapp>
T2> npm run build

\djangoreactproject\djangoproject\djangoproject>settings.py
::import os
::TEMPLATES[{...,'DIRS':[os.path.join(BASE_DIR, 'reactapp/build')],...}]
::STATICFILES_DIRS = [os.path.join(BASE_DIR, 'reactapp/build/static')]

\djangoreactproject\djangoproject\djangoproject>views.py
::from django.shortcuts import render
::def index(request): return render(request, 'index.html')

\djangoreactproject\djangoproject\djangoproject>urls.py
::from . import views
::urlpatterns = [...,path('', views.index, name='index'),...]

\djangoreactproject>
T1> pip install whitenoise

\djangoreactproject\djangoproject\djangoproject>settings.py
::MIDDLEWARE = [...,'whitenoise.middleware.WhiteNoiseMiddleware',...]
::DEBUG = False
::ALLOWED_HOSTS = ['*']
::STATIC_ROOT = BASE_DIR / 'productionfiles'

\djangoreactproject\djangoproject>
T1> py manage.py collectstatic
T1> py manage.py makemigrations
T1> py manage.py migrate
T1> py manage.py runserver

T1> python manage.py inspectdb
T1> python manage.py inspectdb > models.py