# Проект Kittygram
### Через Kittygram возможно создание, редактирование и просмотр котиков!
Использованные технологии:
- Python,
- Django,
- Node.js,
- JavaScript,
- DRF,
- JWT & Djoser,
- PostgreSQL,
- Docker

### Как пользоваться проектом?
Клонируем репозиторий:
```python
git clone git@github.com:Amir800S/kittygram_final.git
```
Переходим в директорию проекта и запускаем его:
```python
cd kittygram_final
```
Запускаем проект в режиме демона:
```python
sudo docker compose -f docker-compose.production.yml up -d
```
Далее нужно собрать статику проекта и выполнить миграции:
```python
sudo docker compose -f docker-compose.production.yml exec backend python manage.py migrate
sudo docker compose -f docker-compose.production.yml exec backend python manage.py collectstatic
sudo docker compose -f docker-compose.production.yml exec backend cp -r /app/collected_static/. /backend_static/static/
```
Проект настроен на работу на 9000 порту поэтому необходимо изменить конфиг Nginx:
```python
nano /etc/nginx/sites-enabled/default
```
```python
location / {
    proxy_pass http://127.0.0.1:9000;
}
```
В файле kittygram_workflow.yml - настройки для GitHub Actions он находится:
```python
kittygram_final/.github/workflows/kittygram_workflow.yml
```

### Проект с котиками готов к работе!

### *Автор: Сабуров Амир* 
