# REST API Game Manager
Django/REST API project to manage Foot ball game



### Funtionality
Management system to monitor games statistics and rankings of a recent tournament.
	- There are three types of users in the system - the league admin, a coach, and a player.
	- All three types of users can login to the site and logout. Upon login they will view the scoreboard, which will display all games and final scores, and will reflect how the competition progressed and who won.
	- A coach may view a list of the players on it, and the average score of the team. When one of the players in the list is selected, his personal details will be presented, including - player’s name, height, average score, and the number of games he participated in.
	- A coach can filter players to see only the ones whose average score is in the 90th percentile across the team.
	- The league admin may view all teams details - their average scores, their list of players, and players details.
	- The admin can also view the statistics of the site’s usage - number of times each user logged into the system, the total amount of time each user spent on the site, and who is currently online. (i.e. logged into the site)

### Concepts

- 'Player', 'Coach', 'Admin' are the three major roles.
- 'Coach' is forming a 'Team' including 'Players' and himself.
- Once the 'Teams' are formed, admin creates a 'Game' by using two teams.
- Once the game is over, admin update the Scoreboards

** All user authentication/Authorisation/Accounting are based on above role based criteria. 

### Data Generator

@ python migrate shell
	>> from create_data import create_data
	>> create_data()

#### url patters are :
## http://127.0.0.1:8000/api/core/player => List
## http://127.0.0.1:8000/api/core/player?q=name => Search view
## http://127.0.0.1:8000/api/core/player?percentile=1 => 90% percentile filter
## http://127.0.0.1:8000/api/core/player/1 => First player RUD operations

Other patterns are same
## http://127.0.0.1:8000/api/core/player
## http://127.0.0.1:8000/api/core/Coach
## http://127.0.0.1:8000/api/core/Team
## http://127.0.0.1:8000/api/core/Game
## http://127.0.0.1:8000/api/core/Scoreboard


### Software

Django==3.1.3
django-rest-auth==0.9.5
djangorestframework==3.12.2
djangorestframework-jwt==1.11.0


### Initial Setup
```

python -m venv <path>

or
virtualenv venv -p python

>> .\Scripts\activate
>> pip install django==2.0.7
>> pip freeze
...

mkdir src
cd src

django-admin startproject game_manager

python .\manage.py runserver
python .\manage.py startapp core


python .\manage.py migrate
python .\manage.py makemigrations

python manage.py flush
python manage.py shell
>>> from create_data import create_data
>>> create_data()
virtualenv -p python3 restapi-basics

# activate it 
# mac: `source bin/activate`
# windows: `.\Scripts\activate`

pip install django==1.11.8 djangorestframework==3.7.3 djangorestframework-jwt==1.11.0

mkdir src && cd src

django-admin startproject game_manager.
django-admin startapp core
```


```
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',

    # rest framework
    'rest_framework',
    'rest_framework.authtoken',
    'rest_auth',
    'core'
]


REST_FRAMEWORK = {
    'DEFAULT_PERMISSION_CLASSES': (
        'rest_framework.permissions.IsAuthenticatedOrReadOnly',
    ),
    'DEFAULT_AUTHENTICATION_CLASSES': (
        'rest_framework_jwt.authentication.JSONWebTokenAuthentication',
        'rest_framework.authentication.SessionAuthentication',
        #'rest_framework.authentication.BasicAuthentication',
    ),
}







