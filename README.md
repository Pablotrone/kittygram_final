#  Проект KITTYGRAM - это социальная сеть для любителей котиков.

Kittygram — это социальная сеть для любителей кошек, где пользователи могут делиться фотографиями своих питомцев и находить новых друзей с общими интересами.

## Как развернуть проект:

1. Скачайте файл docker-compose.yml из репозитория по [ссылке](https://github.com/Pablotrone/kittygram_final/blob/main/docker-compose.yml);
2. В корневой директории проекта создайте файл .env (переменные окружения)
   (nano .env или touch.env);
3. В этом файле укажите:
   '''
   POSTGRES_DB=<база данных>
   POSTGRES_USER=<имя пользователя>
   POSTGRES_PASSWORD=<пароль>
   DB_NAME=<имя базы данных>
   DB_HOST=db
   DB_PORT=5432
   SECRET_KEY=<ключ Django>
   DEBUG=<DEBUG True/False>
   ALLOWED_HOSTS=<разрешенные хосты>
   '''
5. Запустите Docker Compose:
   sudo docker compose -f docker-compose.yml pull
   sudo docker compose -f docker-compose.yml down
   sudo docker compose -f docker-compose.yml up -d
6. Сделайте миграции и соберите статику:
   sudo docker compose -f docker-compose.yml exec backend python manage.py migrate
   sudo docker compose -f docker-compose.yml exec backend python manage.py collectstatic
   sudo docker compose -f docker-compose.yml exec backend cp -r /app/collected_static/. /backend_static/static/
   
## Автодеплой на GitHub Action

Добавьте перменные в GitHub Actions/Secrets:

DOCKER_PASSWORD - пароль от Docker Hub
DOCKER_USERNAME - имя пользователя Docker Hub
HOST - ip сервера
SSH_KEY - ключ ssh для доступа к удаленному серверу
SSH_PASSPHRASE - пароль ssh
TELEGRAM_TO - id пользователя TELEGRAM
TELEGRAM_TOKEN - TELEGRAM токен
USER - имя пользователя сервера

## Технологический стек

Python Django Django REST Framework 
PostgreSQL 
Nginx gunicorn Docker Docker-compose Docker Hub GitHub%20Actions

## Автор:
## Paul Tsupko https://github.com/Pablotrone


