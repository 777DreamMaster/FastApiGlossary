# REST. FastAPI. Swagger

### В проекте представленны файлы 
- /app/db.py - конфигурация подключения к базе данных
- /app/initial_terms.py - начальные термины для заполнения 
- /app/main.py - основной файл приложения с логикой роутов
- /app/models.py - модель таблиц в базе данных
- /app/schemas.py - типы данных для запросов и ответов


Для создания контейнера приложения представлен Dockerfile:

```
FROM python:3.11-slim

WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY ./app /app

CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8000"]
```

Для запуска контейнера docker-compose:

``` 
services:
  app:
    build:
      context: .
      dockerfile: Dockerfile
    ports:
      - "8000:8000"
    volumes:
      - .:/app
    command: uvicorn app.main:app --host 0.0.0.0 --port 8000 --reload
```

## Для запуска проекта необходимо

1. Клонировать проект
```aiignore
git clone https://github.com/777DreamMaster/FastApiGlossary.git
```
2. Собрать и запустить контейнеры:
```bash
docker-compose up --build
```
OpenApi будет доступно по адресу:

```bash
http://localhost:8000/docs
```
![img.png](images/img.png)
![img_1.png](images/img_1.png)
![img_2.png](images/img_2.png)
![img_3.png](images/img_3.png)
![img_4.png](images/img_4.png)
![img_5.png](images/img_5.png)