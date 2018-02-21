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

### Or if you want to use another Testing API for creating a Todo

### I. Go to 
GET http://localhost:8000/api-auth/login/
#### Get the token
csrftoken xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

### II. Login
#### Set Header with the previous csrftoken value
X-CSRFToken xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
POST http://localhost:8000/api-auth/login/?username=amy&password=amy

Response: 200 OK

### III. Create a todo

#### 2. Set Header with the previous csrftoken value & application type
X-CSRFToken xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

Content-Type application/json

Accept application/json
#### 3. Set the json content with 
{
	"title": "hello",
	"text": "world",
	"csrfmiddlewaretoken": "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
}
#### 4. Create a todo
POST http://localhost:8000/todolist/

Response: 200 OK

## Additional Contribution in:
> django-rest-swagger/myapp
> tests/test_end_to_end_todolist.py
