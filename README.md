# LMS — 31 Права доступа в DRF

## Что добавлено
- JWT-авторизация (simplejwt), все эндпоинты закрыты `IsAuthenticated`
- Регистрация `POST /register/`, вход `POST /login/` (access/refresh), обновление токена `POST /token/refresh/` — доступны без авторизации
- CRUD пользователей `/users/`: смотреть можно любой профиль (чужой — без пароля, фамилии и платежей), редактировать/удалять — только свой
- Поле `owner` у курса и урока, заполняется текущим пользователем при создании
- Группа `moderators` (фикстура `users/fixtures/groups.json`): может смотреть и редактировать любые курсы/уроки, но не создавать и не удалять
- Обычный пользователь видит, редактирует и удаляет только свои курсы и уроки

## Запуск
```
pip install -r requirements.txt
python manage.py migrate
python manage.py loaddata groups.json
python manage.py loaddata payments.json
python manage.py createsuperuser
python manage.py runserver
```
Модератора назначают через админку: добавить пользователя в группу `moderators`.

## Эндпоинты уроков
- `GET /lessons/`, `POST /lessons/create/`, `GET /lessons/<id>/`, `PUT|PATCH /lessons/<id>/update/`, `DELETE /lessons/<id>/delete/`
