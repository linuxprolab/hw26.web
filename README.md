# Домашнее задание 26. Развертывание web-приложения CTFd.
В качестве web-приложения выбрано CTFd https://ctfd.io/.
## Структура web-приложения.
Web-приложение состоит из следующих компонент-ролей:
- nginx
- CTFd
- db
- cache

Все компоненты запускаются на одной vagrant VM в докер-контейнерах.

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

- На локальном хосте добаляем в файл `/etc/hosts` строку:
```
127.0.0.1 webapp
```
- На локальном хосте открываем в браузере URL `https://webapp:8443/`.