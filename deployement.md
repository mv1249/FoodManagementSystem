## Deployment on Heroku Cloud

+ Open then present working folder where all working files are present,then create a virtual environment,this step is optional,one can skip and directly move to the `heroku` commands,if you already have the `requirements.txt` file,so for creating the virtual environment in python use the command
  
```
virtualenv .

.\Scripts\activate
```

+ After this install all the requirements,which ever libraries were used in the project,make sure to install these 2 dependencies for sure 

```
pip install django

pip install django-heroku

pip install gunicorn
```

+ After installing all your requirements,then inorder to safe them into the `requirements.txt` file we need to use the command shown ↓,this command will save all the requirements in the txt file

```
pip freeze > requirements.txt
```

+ After installing all the pacakges,in the `settings.py` file of your `project`,you have to add these following lines to the top of `settings.py`: `import django_heroku`and to the bottom of the file add this : `django_heroku.settings(locals())`,and save the file

+ After making that file,now is the turn to make the `Procfile`,it's a file which has no extensions,so in that procfile you have to add this command `web: gunicorn myproject.wsgi`,here make sure that you cahnge your project name from `myproject` to you respective project name,as in this case my project name was `foodsystem` so i should write : `web: gunicorn foodsystem.wsgi`and save the file

## Heroku commands

+ So once all requirements and the settings are configured,it's time for deploying the application on heroku server,so for that we have to install heroku CLI,so once heroku CLI is installed follow the given commands

```
heroku login
```
+ This command ↑ will login to your heroku account GUI,now inorder to create an app,use the command ↓,where app_name is the name which you want your django app to be for public usecase

```
heroku create app_name
```
+ Then you need to create an empty repository by using the commands below ↓,you have to use this commands step by step,after the `commit` command you will have created your repository on heroku server,now you just need to push your code,so for that you use `git push heroku master` , so this will push your code on heroku server

```
git init

git add .

git commit -m "First commit"

git push heroku master
```
+ Once this is done,type the following commands to activate your database and inorder to run the app,follow this commands step by step,so first you need to create your superuser,so that you can use your database present at the heroku server,so run the following commands step by step,once all the commands are successfully executed run the last command which is `heroku run`
  
```
heroku run python manage.py makemigrations

heroku run python manage.py makemigrate

heroku run python manage.py createsuperuser

heroku run
```


