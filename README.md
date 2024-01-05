# flask-one
Demo flask app for JWT authentication

1. Installation: `pip install flask-jwt-extended`
2. Run the app with: `flask run`
3. We can test this app using HTTPie with in following way:
```
$ http GET :5000/protected

HTTP/1.0 401 UNAUTHORIZED
Content-Length: 39
Content-Type: application/json
Date: Sun, 24 Jan 2021 18:09:17 GMT
Server: Werkzeug/1.0.1 Python/3.8.6

{
    "msg": "Missing Authorization Header"
}


$ http POST :5000/login username=test password=test

HTTP/1.0 200 OK
Content-Length: 288
Content-Type: application/json
Date: Sun, 24 Jan 2021 18:10:39 GMT
Server: Werkzeug/1.0.1 Python/3.8.6

{
    "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJmcmVzaCI6ZmFsc2UsImlhdCI6MTYxMTUxMTgzOSwianRpIjoiMmI0NzliNTQtYTI0OS00ZDNjLWE4NjItZGVkZGIzODljNmVlIiwibmJmIjoxNjExNTExODM5LCJ0eXBlIjoiYWNjZXNzIiwic3ViIjoidGVzdCIsImV4cCI6MTYxNDEwMzgzOX0.UpTueBRwNLK8e-06-oo5Y_9eWbaN5T3IHwKsy6Jauaw"
}


$ export JWT="eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJmcmVzaCI6ZmFsc2UsImlhdCI6MTYxMTUxMTgzOSwianRpIjoiMmI0NzliNTQtYTI0OS00ZDNjLWE4NjItZGVkZGIzODljNmVlIiwibmJmIjoxNjExNTExODM5LCJ0eXBlIjoiYWNjZXNzIiwic3ViIjoidGVzdCIsImV4cCI6MTYxNDEwMzgzOX0.UpTueBRwNLK8e-06-oo5Y_9eWbaN5T3IHwKsy6Jauaw"


$ http GET :5000/protected Authorization:"Bearer $JWT"

HTTP/1.0 200 OK
Content-Length: 24
Content-Type: application/json
Date: Sun, 24 Jan 2021 18:12:02 GMT
Server: Werkzeug/1.0.1 Python/3.8.6

{
    "logged_in_as": "test"
}
```