# Домашнее задание 26. Развертывание web-приложения.
Будем разворачивать nginx + php(wordpress) + python (CTFd) + js(nodejs);
## Структура стенда
Все компоненты запускаются на одной vagrant VM в докер-контейнерах с помощью Docker-compose.
- Ansible-роли:
  - common - установка необходимых пакетов на ОС
  - docker-host - установка пакетов Docker и Docker-compose
  - docker-nginx - разворачивание докер-контейнера nginx
  - docker-ctfd - разворачивание web-приложения CTFd докер-контейнерах
  - docker-node - разворачивание web-приложения на nodejs
  - docker-wordpress - разворачивание wordpress
## Запуск и проверка
- Клонируем репозиторий:
```
git clone https://github.com/linuxprolab/hw26.web
cd hw26.web
```
- Поднимаем VM:
```
vagrant up
```
- Запускаем плейбук ansible:
```
ansible-playbook playbooks/main.yml -i inventories/all.yml 
```
- CTFd доступен по локальном хосте по URL `https://localhost:8081/`.
- nodejs доступен по локальном хосте по URL `https://localhost:8081/`.
- Wordpress доступен по локальном хосте по URL `https://localhost:8083/`.