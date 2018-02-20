# TodoList Django REST + Swagger + PostGreSQL

Another DRF Swagger starter kit based on docker and django REST server.

#### An API documentation generator for Swagger UI, Django REST Framework & PostGreSQL

## Requirements
docker-compose installation https://docs.docker.com/compose/install/

## Installation

1. git clone https://github.com/MathieuB1/TodoList-Django_REST_Swagger_PostgreSQL.git

2. docker-compose down && docker-compose build && docker volume prune -f && docker-compose up

3. Open your navigator and go to localhost:8000

## Usage

1. you must login to use POST, PUT and DELETE methods.
Use `amy` as user and password for login


## Testing TodoList API

docker exec -it $(docker ps | grep web | awk '{print $NF}') /bin/bash

cd /code && python runtests.py

### if you want to use another API

### Go to 
GET http://localhost:8000/api-auth/login/
#### Get the token
csrftoken xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

### Login
#### Set Header with the previous csrftoken value
X-CSRFToken xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
POST http://localhost:8000/api-auth/login/?username=amy&password=amy


### Create a todo

#### Generate the CSRF Token (Cookie has to be cleared manually when using POSTMAN)
GET http://localhost:8000/api-auth/login/
#### Set Header with the previous csrftoken value
X-CSRFToken xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
#### Set the Body with 
{title:'hello', test:'world'}
POST http://localhost:8000/todolist/



## Additional Contribution in:
> django-rest-swagger/myapp
> tests/test_end_to_end_todolist.py
