# Описание

API для Yatube

Функционал:
Авторизация по JWT токену

Сериализация данных для всех моделей проекта (Post, Comment, Group, Follow)

Стек: Python 3.7, Django, Django REST Framework, Simple-JWT, SQLite3.

Обработка GET, POST, PATCH, PUT и DELETE запросов к базе данных проекта Yatube

В проекте можно посмотреть примеры:
* использования Вью Сетов;
* использования сериализаторов;
* использования JWT + Djoser для аутентификации пользователей;
* разграничения прав доступа;


# Установка

## 1)Склонировать репозиторий
## 2)Создать и активировать виртуальное окружение для проекта

python -m venv venv

source venv/scripts/activate

## 3)Установить зависимости
python pip install -r requirements.txt

## 4)Сделать миграции
python manage.py makemigrations
python manage.py migrate

## 5)Запустить сервер
python manage.py runserver

## Выйти из проекта
Ctrl + C.

# Примеры

Для доступа к API необходимо получить токен: 
Нужно выполнить POST-запрос localhost:8000/api/v1/token/ передав поля username и password. API вернет JWT-токеню

## Получение токена
### POST 
URL /api/v1/jwt/create/  
JSON
{
    "username": "user",
    "password": "password"
}
### Response
JSON
{
    "refresh": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoicmVmcmVzaCIsImV4cCI6MTYzNTc5MjU1MCwianRpIjoiNzI0YmY4Nzc3MDNmNDYwOTk1ZTRmMzg4NmQ0MzgyNjkiLCJ1c2VyX2lkIjoyfQ.Ofgo3Bv-t2Fj01HFKia_fP8N01IGnsu6N-858cdKVDg",
    "access": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoiYWNjZXNzIiwiZXhwIjoxNjM1NzkyNTUwLCJqdGkiOiJhNzRiNDA2OWI3OTM0NTkzODAzMjQxMjIxZWI4N2E3MiIsInVzZXJfaWQiOjJ9.7Auocnm8bi8cZ3KT7z5EqoJ7yCOE6J0hn-u-VhIuNwo"
}


Передав токен можно будет обращаться к методам, например: 

/api/v1/posts/ (GET, POST, PUT, PATCH, DELETE)

## Получение списка постов
### GET 
URL /api/v1/posts/
### Response 
JSON [
    {
        "id": 1,
        "author": "Лев Толстой",
        "text": "Текст Поста",
        "pub_date": "2023-02-1T18:12:20.610315Z",
        "image": null,
        "group": null
    },
    {
        "id": 2,
        "author": "deepxshine",
        "text": "Текст",
        "pub_date": 2023-02-1T18:12:20.610315Z",
        "image": null,
        "group": null
    },
    {
        "id": 3,
        "author": "Will",
        "text": "Крутой пост",
        "pub_date": 2023-02-1T18:12:20.610315Z",
        "image": null,
        "group": null
    }
]


При отправке запроса передавайте токен в заголовке Authorization: Token <токен>



### Автор

[Алексей Евдокимов](https://github.com/deepxshine)
