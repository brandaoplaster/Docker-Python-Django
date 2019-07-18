# Table of Contents

* [Requirements](#requirements)
* [Getting Started](#getting-started)
  * [Built with](#built-with)
  * [Follow the step by step](#follow-the-step-by-step)
  * [Create as images](#create-as-images)
  * [Create the django project](#create-the-django-project)
  * [Create django applications](#create-django-applications)
  * [The project settings](#the-project-settings)
* [License](#license)
* [Contact](#contact)

# Requirements

The minimum requirements are the following software.
```
Docker version 18.09.6
```
```
docker-compose version 1.22.0
```

# Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

## Built With

* Docker
* Docker-composer
* Python
* Django
* Mysql

**Note** 
> The version of Django and MySQL can be changed.

## Follow the step by step

1 - Clone Docker-Python-Django inside your Django project:
```
git clone https://github.com/brandaoplaster/Docker-Python-Django.git
```
2 - Enter the Docker-Python-Django folder and rename env-example to .env.
```
cp env-example .env
```
3 - Change PROJECT_NAME in the .env file.
```
PROJECT_NAME=MY_PROJECT
```
4 - Inside the Docker folder create one the following requirements.txt file and include the next commands.

```
Django==2.1.5
mysqlclient==1.3.14
django-mysql==2.2.0
```


## Create as images
To create an image and start the containers, run the command.
```
 docker-compose up -d
```

## Create the django project
Run the command to create a project, in project_name enter the name of your project.

**Note**
>The endpoint of this command is required.
```
docker-compose run django django-admin.py startproject project_name .
```

## Create django applications
To create applications run this command.
```
docker-compose run django python manage.py startapp app_name

```

## The project settings
Include the name of your application from the installed applications.
```
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    
    'app_name',
]
```
By default the DATABASES configuration comes with sqlite3.
```
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': os.path.join(BASE_DIR, 'db.sqlite3'),
    }
}
```
**Optional**

But if you are using another database, just make the necessary change. In this case the configuration is for mysql.

```
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'DB_NAME',
        'USER': 'DB_USER',
        'PASSWORD': 'DB_PASSWORD',
        'HOST': 'mysql',
        'PORT': '3306',
        'TEST': {
            'NAME': 'DB_NAME_TEST',
        },
    }
}
```

## Django Migrations:
 To access the Django container run the command.
```sh
 docker-compose exec django bash
```
**Note**
>After executing the above command it will be inside the Django container and the next command can be executed.

Perform the migrations.
```sh
 python manage.py makemigrations
```
And after that.

```sh
 python manage.py migrate
```


## Author

* **Brandao Plaster**


## Contact

Brandao Plaster - [@BrandaoPlaster](https://twitter.com/BrandaoPlaster) - 

Project: [https://github.com/brandaoplaster/OneExchangeValue](https://github.com/brandaoplaster/OneExchangeValue)


## License

This project is licensed under the [MIT License](https://opensource.org/licenses/MIT).