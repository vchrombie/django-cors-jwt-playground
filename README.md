# django-cors-jwt-playground

POC to explain how to configure and use CORS

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
- [`get_cart_items` view](https://github.com/vchrombie/users-groups/blob/e18c8da0624eee0880e3c7416dcc4a296d1b0c07/users/views.py#L45)
- [`cart/` url configuration](https://github.com/vchrombie/users-groups/blob/e18c8da0624eee0880e3c7416dcc4a296d1b0c07/users_groups/urls.py#L33)

![image](https://user-images.githubusercontent.com/25265451/152352965-fe849dcf-cc88-4790-8239-33f1ac3f62a7.png)
