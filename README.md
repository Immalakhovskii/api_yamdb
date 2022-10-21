# YaMDb #
*Web API service YaMDb is a team project made with two other junior Python developers. That is why the project forked and has different contributors. If you are going to start YaMDB and using Docker it is more convinient to try out dockerized YaMDB which is available here: https://github.com/Immalakhovskii/yamdb_docker. Here you'll find instructions how to start YaMDb as well*

---
### Description ###
Web API service YaMDb collects scores and reviews on different works of art (titles) in different categories (e.g. films, music, books) and genres (e.g. drama, comedy, ballad). Anonymous can read descriptions of titles, reviews and comments. Authenticated user can publish own reviews to titles, give a score to titles, comment own reviews and other users. Titles, categories and genres can be created and updated by Admin. While the project activated see full detailed API documentation here: http://127.0.0.1:8000/redoc/ 

### Technology Stack ###
Python 3.7 / Django 2.2.16 / Django REST framework 3.12.4

### How to start YaMDb ###
```
# clone repository, create virtual enviroment and install dependencies
git clone https://github.com/Immalakhovskii/api_yamdb.git
cd api_yamdb/
python -m venv venv
python.exe -m pip install --upgrade pip
python -m pip install -r requirements.txt

# activate virtual enviroment 
source venv/Scripts/activate            # (Windows) 
source venv/bin/activate                # (macOS and Linux)

# prepare to start development server 
cd api_yamdb/
cp .env.example .env                    # copy .env.example with valid data as .env
python manage.py migrate
python manage.py loaddata db_dump.json  # load prearrenged dtabase
python manage.py createsuperuser        # or create superuser for clear project
   
# start!
python manage.py runserver
```
Now admin site of the project available at http://127.0.0.1:8000/admin/. API requests can be performed by addresses starting with http://127.0.0.1:8000/api/v1/ (see full list of available requests here: http://127.0.0.1:8000/redoc/). If prearranged database dump was loaded the project has 10 genres, 4 titles, 4 categories and superuser Admin
```
# accesses to admin zone as Admin if db_dump loaded
Username: Admin
Password: youllneverguess
``` 

- Actual enviromental variables for the YaMDb stored at api_yamdb/.env.example. Safety precautions ignored for the public availability of the project

To stop development server press **ctrl (command) + c**

### Get JWT token ###
- To receive **token** make POST request with "email" and "username" to http://127.0.0.1:8000/api/v1/auth/signup/. After receiving confirmation code make POST request with "confirmation_code" and "username" to http://127.0.0.1:8000/api/v1/auth/token/. Token must be passed with **"Bearer"** header
