# YaMDb #
*Web API service YaMDb is a team project made with two other junior Python developers. That is why the project forked and has different contributors. If you are using Docker it is more convinient to try out dockerized YaMDB which is available here: https://github.com/Immalakhovskii/yamdb_docker. Here you'll find instructions how to start YaMDb as well*

---
#### Description ####
Web API service YaMDb collects scores and reviews on different works of art (titles) in different categories (e.g. films, music, books) and genres (e.g. drama, comedy, ballad). Anonymous can read descriptions of titles, reviews and comments. Authenticated user can publish own reviews to titles, give a score to titles, comment own reviews and other users. Titles, categories and genres can be created and updated by Admin. While the project activated see full detailed API documentation here: http://127.0.0.1:8000/redoc/ 

#### Technology Stack ####
Python 3.7 / Django 2.2.16 / Django REST framework 3.12.4

#### How to start YaMDb ####
```
# clone repository
git clone https://github.com/Immalakhovskii/api_yamdb.git 

# create virtual enviroment
python -m venv venv

# activate virtual enviroment 
source venv/Scripts/activate    # (Windows) 
source venv/bin/activate        # (macOS and Linux)

# Install dependencies
python -m pip install -r requirements.txt

# change directory to api_yamdb/ 
cd api_yamdb

# copy .env.example with valid data as .env
cp .env.example .env

# perform migrations
python manage.py migrate

# load dtabase with 10 genres, 4 titles, 4 categories and superuser Admin
python manage.py loaddata db_dump.json

# or create superuser for clear project
python manage.py createsuperuser   

# start development server
python manage.py runserver
```
Now admin site of the project available at http://127.0.0.1:8000/admin/. API requests can be performed by addresses starting with http://127.0.0.1:8000/api/v1/ (see full list of available requests here: http://127.0.0.1:8000/redoc/)
```
# accesses to admin zone as Admin if you loaded db_dump
Username: Admin
Password: youllneverguess
``` 

- Actual enviromental variables for the YaMDb stored at infra/.env.example. Safety precautions ignored for the public availability of the project

To stop development server press ctrl (command) + c

#### Get JWT token ####
- To receive **token** make POST request with "email" and "username" to http://127.0.0.1:8000/api/v1/auth/signup/. After receiving confirmation code make POST request with "confirmation_code" and "username" to http://127.0.0.1:8000/api/v1/auth/token/. Token must be passed with **"Bearer"** header
