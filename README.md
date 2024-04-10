# rust-jwt-auth

Example of JWT authentication and authorization in Rust using Warp

## Getting Started
```bash
cargo run
```

### Login

```bash
curl http://localhost:8000/login -d '{"email": "user@user.com", "pw": "user"}' -H 'Content-Type: application/json'

{"token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzUxMiJ9.eyJzdWIiOiIxIiwicm9sZSI6IlVzZXIiLCJleHAiOjE3MTI3NTU4MzJ9.Ndnz7RS3O3zy5bIOaW64QKmEJh16ksGomi6tgR8M0x21EaSPf7xIVxTHiZstc43c6oh71sNuUjvPNULy22qL_g"}
```


### User Endpoint

```bash
curl http://localhost:8000/user -H 'Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzUxMiJ9.eyJzdWIiOiIxIiwicm9sZSI6IlVzZXIiLCJleHAiOjE3MTI3NTU4MzJ9.Ndnz7RS3O3zy5bIOaW64QKmEJh16ksGomi6tgR8M0x21EaSPf7xIVxTHiZstc43c6oh71sNuUjvPNULy22qL_g' -H 'Content-Type: application/json'

Hello User 1

curl http://localhost:8000/admin -H 'Authorization: Bearer curl http://localhost:8000/user -H 'Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzUxMiJ9.eyJzdWIiOiIxIiwicm9sZSI6IlVzZXIiLCJleHAiOjE3MTI3NTU4MzJ9.Ndnz7RS3O3zy5bIOaW64QKmEJh16ksGomi6tgR8M0x21EaSPf7xIVxTHiZstc43c6oh71sNuUjvPNULy22qL_g' -H 'Content-Type: application/json'' -H 'Content-Type: application/json'

{"message":"no permission","status":"401 Unauthorized"}
```


### Admin Endpoint

```bash
curl http://localhost:8000/login -d '{"email": "admin@admin.com", "pw": "admin"}' -H 'Content-Type: application/json'

{"token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzUxMiJ9.eyJzdWIiOiIyIiwicm9sZSI6IkFkbWluIiwiZXhwIjoxNzEyNzU1OTQ3fQ.6q9FOULjIa0HW0fpkhc2QUxwcQSd10xBgxotgkeJJR5HPLGDWwcq2l3AG8s19kwoCseel4495IbtSRBLYpz7Qw"}

curl http://localhost:8000/admin -H 'Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzUxMiJ9.eyJzdWIiOiIyIiwicm9sZSI6IkFkbWluIiwiZXhwIjoxNzEyNzU1OTQ3fQ.6q9FOULjIa0HW0fpkhc2QUxwcQSd10xBgxotgkeJJR5HPLGDWwcq2l3AG8s19kwoCseel4495IbtSRBLYpz7Qw' -H 'Content-Type: application/json'

Hello Admin 2

curl http://localhost:8000/user -H 'Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzUxMiJ9.eyJzdWIiOiIyIiwicm9sZSI6IkFkbWluIiwiZXhwIjoxNzEyNzU1OTQ3fQ.6q9FOULjIa0HW0fpkhc2QUxwcQSd10xBgxotgkeJJR5HPLGDWwcq2l3AG8s19kwoCseel4495IbtSRBLYpz7Qw' -H 'Content-Type: application/json'

Hello User 2
```
