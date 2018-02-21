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
```
docker exec -it $(docker ps | grep web | awk '{print $NF}') /bin/bash

cd /code && python runtests.py
```

### Or if you want to use another Testing API for creating a Todo

 ### I. Create a Todo
 
 #### 1. Get the cookie Token
```
curl -c cookie.txt http://localhost:8000/api-auth/login/

cat cookie.txt | tail -n 1 | awk {'print $NF'} #grab the value xxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```
 #### 2. Create the todo
```
 curl http://localhost:8000/todolist/ \
 -X POST \
 -H "Content-Type: application/json" \
 -H "Accept: text/html,application/json" \
 -H "X-CSRFToken: xxxxxxxxxxxxxxxxxxxxxxxxxxxxx" \
 -H "Cookie: csrftoken=xxxxxxxxxxxxxxxxxxxxxxxxxxxxx" \
 -u amy:amy \
 -d '{"title": "today","text": "review"}'
 ```
 Response: 201 OK
 {"created":"2018-02-21T19:29:04.596022Z","title":"today","text":"review","owner":"amy"}
 
 
 ### II. Update a Todo
 
 #### 1. Get the cookie Token
```
curl -c cookie.txt http://localhost:8000/api-auth/login/

cat cookie.txt | tail -n 1 | awk {'print $NF'} #grab the value xxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```
 #### 2. Update the todo
 ```
  curl http://localhost:8000/todolist/1/ \
 -X PUT \
 -H "Content-Type: application/json" \
 -H "Accept: text/html,application/json" \
 -H "X-CSRFToken: xxxxxxxxxxxxxxxxxxxxxxxxxxxxx" \
 -H "Cookie: csrftoken=xxxxxxxxxxxxxxxxxxxxxxxxxxxxx" \
 -u amy:amy \
 -d '{"title": "today","text": "work", "id": 1}'
 ```
 Reponse: 200 OK
 {"created":"2018-02-21T18:52:18.240258Z","title":"today","text":"work","owner":"amy"}
 
  ### III. Get a Todo
  ```
  curl http://localhost:8000/todolist/1/
  ```
  Reponse: 200 OK
  {"created":"2018-02-21T18:52:18.240258Z","title":"today","text":"work","owner":"amy"}
  
  ### IV. Delete a todo
  
 #### 1. Get the cookie Token
```
curl -c cookie.txt http://localhost:8000/api-auth/login/

cat cookie.txt | tail -n 1 | awk {'print $NF'} #grab the value xxxxxxxxxxxxxxxxxxxxxxxxxxxxx 
```
 #### 2. delete the todo
```
  curl http://localhost:8000/todolist/1/ \
 -X DELETE \
 -H "Content-Type: application/json" \
 -H "Accept: text/html,application/json" \
 -H "X-CSRFToken: xxxxxxxxxxxxxxxxxxxxxxxxxxxxx" \
 -H "Cookie: csrftoken=xxxxxxxxxxxxxxxxxxxxxxxxxxxxx" \
 -u amy:amy
```
 Reponse: 204 OK

## Additional Contribution in:
> django-rest-swagger/myapp
> tests/test_end_to_end_todolist.py
