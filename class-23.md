# [Django Custom User Model](https://learndjango.com/tutorials/django-custom-user-model)

Django ships with a built-in User model for authentication, however the official Django documentation highly recommends using a custom user model for new projects. The reason is if you want to make any changes to the User model down the road--for example adding a date of birth field--using a custom user model from the beginning makes this quite easy. But if you do not, updating the default User model in an existing Django project is very, very challenging.

## AbstractUser vs AbstractBaseUser

There are two modern ways to create a custom user model in Django: **AbstractUser** and **AbstractBaseUser**. In both cases we can subclass them to extend existing functionality however AbstractBaseUser requires much, much more work. 

**AbstractUser** which actually subclasses AbstractBaseUser but provides more default configuration.

## Custom User Model

Creating our initial custom user model requires four steps:

- update ```settings.py```
- create a new ```CustomUser``` model
- create new ```UserCreation``` and ```UserChangeForm```
- update the admin
