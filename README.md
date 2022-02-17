# django-cors-jwt-playground

POC to explain how to configure and use CORS between two Django microservices ([user management](https://github.com/vchrombie/users-groups) and [shopping cart](https://github.com/vchrombie/shopping-cart))

Exchange of resources between two different django projects using [django-cors-headers](https://pypi.org/project/django-cors-headers/) and REST Framework

---

Clone the project
```
$ git clone https://github.com/vchrombie/django-cors-jwt-playground
$ cd django-cors-jwt-playground
```

Launching `shopping-cart` on `localhost:8080`
```
$ cd shopping-cart
$ poetry install
$ poetry shell
(.venv) $ makemigrations
(.venv) $ migrate
(.venv) $ createsuperuser # username=+918186866445 && password=root
(.venv) $ runserver localhost:8080
```
Now, add some data (Category, Products and Cart items) using the admin panel

Launching `users-groups` on `locahost:8000`
```
$ cd users-groups
$ poetry install
$ poetry shell
(.venv) $ makemigrations
(.venv) $ migrate
(.venv) $ createsuperuser # phone_number=+918186866445 && password=root
(.venv) $ runserver localhost:8000
```

The `users-group` project will fetches data from the `shopping-cart` project using the REST API

`login` using Postman
```
POST
http://127.0.0.1:8000/api/login/
{
    "phone_number": "+918186866445",
    "password": "root"
}
```
![Screenshot from 2022-02-17 20-10-57](https://user-images.githubusercontent.com/25265451/154504866-5751c997-f47b-4342-8714-a2089d50bb9d.png)

`cart view` using Postman
```
GET
http://127.0.0.1:8080/cart/view/
Authorization Bearer Token eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpZCI6MSwiZXhwIjoxNjQ1MTEyNDUxLCJpYXQiOjE2NDUxMDg4NTF9.lTqp9_ZQnxhNHtMe38kEqCJzmh5DM7zi9snanX1mfCE
```
![Screenshot from 2022-02-17 20-11-19](https://user-images.githubusercontent.com/25265451/154504875-25ac42f1-6c03-4493-a5df-3fbcb992c856.png)
