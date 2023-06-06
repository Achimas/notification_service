# Сервис уведомлений

Сервис разработан на django rest framework с celery и flower


## Установка и запуск

1. Склонировать репозиторий с Github:

````
git clone git@github.com:Achimas/notification_service.git
````
2. Убедиться, что на компьютере установлена последняя версия Redis, затем перейти в директорию проекта

3. Создать виртуальное окружение:

````
python -m venv venv
````

4. Активировать окружение: 

````
venv/scripts/activate
````
5. В файле .evn заполнить необходимые данные: ```TOKEN = '<your token>'```
 
6. Установка зависимостей:

```
pip install -r requirements.txt
```

7. Создать и применить миграции в базу данных:
```
python manage.py makemigrations
python manage.py migrate
```
8. Запустить сервер
```
python manage.py runserver
```
9. Запустить celery
```
celery -A notification_service worker -l info
```
10. Запустить flower

```
celery -A notification_service flower --port=5555
```
***
### Запуск тестов
``` 
python manage.py test
```
***
## Установка проекта с помощью docker-compose


1. Склонировать репозиторий с Github
```
git clone git@github.com:Achimas/notification_service.git
```
2. Перейти в директорию проекта
3. В файле .evn заполнить необходимые данные: ```TOKEN = '<your token>'```
4. Запустить контейнеры 
``` 
docker-compose build -t mailing .
docker run mailing
 ```
5. Остановка работы контейнеров 
```
sudo docker-compose stop
```
***
```http://127.0.0.1:8000/api/``` - api проекта

```http://127.0.0.1:8000/api/clients/``` - клиенты

```http://127.0.0.1:8000/api/mailings/``` - рассылки

```http://127.0.0.1:8000/api/mailings/fullinfo/``` - общая статистика по всем рассылкам

```http://127.0.0.1:8000/api/mailings/<pk>/info/``` - детальная статистика по конкретной рассылке

```http://127.0.0.1:8000/api/messages/``` - сообщения

```http://127.0.0.1:8000/docs/``` - docs проекта

```http://127.0.0.1:5555``` - celery flower

***

**Техзадание:** 
[https://www.craft.do/s/n6OVYFVUpq0o6L](https://www.craft.do/s/n6OVYFVUpq0o6L)

### Выполнены 1,5,6,9,11,12 дополнительные пункты техзадания

