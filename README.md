## Описание
![Презентация](./media_for_readme/Presentation.gif) <br>

Это API сервиса по сбору средств для финансирования благотворительных проектов. В сервисе реализована возможность регистрации пользователей, добавления благотворительных проектов и пожертвований, которые распределяются по открытым проектам.
Добавлена возможность создания отчета в гугл таблицах, с помощью Google Drive.

## Запуск в Docker

```
docker build -t fastapi .
```
```
docker run -it --rm -p 8000:8000 fastapi
```

Проект будет открыт по адресу <b>127.0.0.1:8000</b>

## Установка
1. Склонируйте репозиторий:
```
git clone git@github.com:PavelHomov/donations-project.git
```
2. Активируйте venv и установите зависимости:
```
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```
3. Создайте в корневой директории файл .env со следующим наполнением:
```
APP_TITLE=Фонд
APP_DESCRIPTION=Сервис
DATABASE_URL=sqlite+aiosqlite:///./<название базы данных>.db
SECRET=<секретное слово>

# Данные с JSON-файла с ключом доступа к сервисному аккаунту
TYPE=
PROJECT_ID=
PRIVATE_KEY_ID=
PRIVATE_KEY=
CLIENT_EMAIL=
CLIENT_ID=
AUTH_URI=
TOKEN_URI=
AUTH_PROVIDER_X509_CERT_URL=
CLIENT_X509_CERT_URL=
EMAIL=
```
4. Примените миграции для создания базы данных SQLite:
```
alembic upgrade head
```
5. Проект готов к запуску.
```
uvicorn app.main:app --reload 
```

Сервис будет запущен и доступен по следующим адресам:
- http://127.0.0.1:8000 - API
- http://127.0.0.1:8000/docs - автоматически сгенерированная документация Swagger
- http://127.0.0.1:8000/redoc - автоматически сгенерированная документация ReDoc

Со схемами запросов и ответов можно ознакомиться в документации или в файле со спецификацией - openapi.json.

### Автор
Павел Хомов
