# Springboot-JWT

# issue a GET request to see the (empty) list of tasks
curl http://localhost:8080/tasks

# issue a POST request to create a new task
curl -H "Content-Type: application/json" -X POST -d '{
    "description": "Buy some milk(shake)"
}'  http://localhost:8080/tasks

# issue a PUT request to update the recently created task
curl -H "Content-Type: application/json" -X PUT -d '{
    "description": "Buy some milk"
}'  http://localhost:8080/tasks/1

# issue a DELETE request to remove the existing task
curl -X DELETE http://localhost:8080/tasks/1


# issues a GET request to retrieve tasks with no JWT
# HTTP 403 Forbidden status is expected
curl http://localhost:8080/tasks

# registers a new user
curl -H "Content-Type: application/json" -X POST -d '{
    "username": "admin",
    "password": "password"
}' http://localhost:8080/users/sign-up

# logs into the application (JWT is generated)
curl -i -H "Content-Type: application/json" -X POST -d '{
    "username": "admin",
    "password": "password"
}' http://localhost:8080/login

# issue a POST request, passing the JWT, to create a task
# remember to replace xxx.yyy.zzz with the JWT retrieved above
curl -H "Content-Type: application/json" \
-H "Authorization: Bearer xxx.yyy.zzz" \
-X POST -d '{
    "description": "Buy watermelon"
}'  http://localhost:8080/tasks

# issue a new GET request, passing the JWT
# remember to replace xxx.yyy.zzz with the JWT retrieved above
curl -H "Authorization: Bearer xxx.yyy.zzz" http://localhost:8080/tasks
