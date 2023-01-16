# api_yamdb
API предназначено для добавления и просмотра произведений, их оценок и комментариев
# Технологии
Python 3.7
Django 2.2.16
Gunicorn 20.0.4
# Шаблон наполнения .env-файла
```
DB_ENGINE=django.db.backends.postgresql # указываем, что работаем с postgresql
DB_NAME=postgres # имя базы данных
POSTGRES_USER=postgres # логин для подключения к базе данных
POSTGRES_PASSWORD=password # пароль для подключения к БД (установите свой)
DB_HOST=db # название сервиса (контейнера)
DB_PORT=5432 # порт для подключения к БД
```
# Инструкция по запуску приложения в контейнере
Запускаем сборку контейнера в фоновом режиме(чтобы логи не мешали последующим действиям):

```
docker-compose up -d
```
По очереди выполняем миграции, создание суперюзера и сбор статики
```
docker-compose exec web python manage.py migrate
docker-compose exec web python manage.py createsuperuser
docker-compose exec web python manage.py collectstatic --no-input
```

### Теперь администрирование проекта доступно по адресу http://localhost/admin

# Примеры запросов API

Регистрация и получение токена
```
http://127.0.0.1/api/v1/auth/signup/
http://127.0.0.1/api/v1/auth/token/
```

Получение произведений
```
http://127.0.0.1/api/v1/titles/
```

Оставить отзыв о произведении
```
http://127.0.0.1/api/v1/titles/{title_id}/reviews/
```

Оставить комментарий  к отзыву
```
http://127.0.0.1/api/v1/titles/{title_id}/reviews/{review_id}/comments/
```

Работа с пользователями
```
http://127.0.0.1/api/v1/users/
```

# Документация и перечень всех эндпоинтов
```
http://127.0.0.1/redoc/
```

# Автор проекта:

# Владимир Семочкин