## FLAKE 8
### How to run flake8
```terminal
docker-compose run --rm app sh -c "flake8"
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
>These actions get triggered on push to the remote repository.
> The actions are defined in the .github/workflows/checks.yml file.
```yaml
---
name: Checks
on: [push]
jobs:
  test-lint:
    name: Test and lint
    runs-on: ubuntu-20.04
    steps:
      - name: Login to Docker Hub
        uses: docker/login-action@v1
        with:
          username: ${{ secrets.DOCKERHUB_USER }}
          password: ${{ secrets.DOCKERHUB_TOKEN }}
      - name: Checkout
        uses: actions/checkout@v2
      - name: Build and test
        run: docker-compose run --rm app sh -c "python manage.py test"
      - name: Lint
        run: docker-compose run --rm app sh -c "flake8"
```

