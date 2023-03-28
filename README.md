## FLAKE 8
### How to run flake8
```terminal
docker-compoes run --rm app sh -c "flake8"
```

## Create Django project
```terminal
docker compose run --rm app sh -c "django-admin startproject app ."
```

## Run Tests from docker container
```termnal
docker compose run --rm app sh -c "python manage.py test"
```
## Settings off triggers with github actions

