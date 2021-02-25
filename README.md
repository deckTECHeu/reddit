# Profiles REST API

docker-compose run --rm app sh -c "django-admin.py startproject app ."
docker-compose run --rm app sh -c "python manage.py startapp posts"
Add to settings.py:
    'rest_framework',
    # 'rest_framework.authtoken',
    'posts',
docker-compose run --rm app sh -c "python manage.py makemigrations"
docker-compose run --rm app sh -c "python manage.py migrate"
docker-compose run --rm app sh -c "python manage.py test && flake8"
docker-compose run --rm app sh -c "python manage.py createsuperuser"

curl -X "POST" "http://localhost:8000/api/posts" \
     -H 'Content-Type: application/json' \
     -u 'andrzej:Scarlett000' \
     -d $'{
         "title": "Cool Stuff",
         "url": "http://decktech.eu"
     }'