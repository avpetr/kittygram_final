![example workflow](https://github.com/avpetr/kittygram_final/actions/workflows/kittygram_workflow.yml/badge.svg)
# Проект Kittygram 
Kittygram - соцсеть для любителей котов (не хватает собачек).

## Запуск проекта
1. Для запуска проекта необходимо загрузить файл [_docker-compose.production.yml_](https://github.com/avpetr/kittygram_final/blob/main/docker-compose.production.yml) 
2. Создать файл .env в той же директории и заполнить следующим образом:
```
POSTGRES_USER = имя_пользователя
POSTGRES_PASSWORD = пароль
POSTGRES_DB = имя_БД
DB_HOST = db (имя контейнера хоста БД)
DB_PORT = 5432 (порт БД)
SECRET_KEY = секретный_ключ
DEBUG = True | False
ALLOWED_HOSTS = разрешенные_хосты (например:localhost,127.0.0.1)
```
4. Запустить Docker Compose, далее собрать статику и сделать миграции следующими командами:
```bash
sudo docker compose -f docker-compose.yml pull
sudo docker compose -f docker-compose.yml down
sudo docker compose -f docker-compose.yml up -d
sudo docker compose -f docker-compose.production.yml exec backend python manage.py migrate
sudo docker compose -f docker-compose.production.yml exec backend python manage.py collectstatic
sudo docker compose -f docker-compose.production.yml exec backend cp -r /app/collected_static/. /backend_static/static/
```
## Стек технологий
- Django
- ReactJS
- Ngingx
- Docker


 Автор: avpetr
