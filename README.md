# Ansible Nginx

Проект для установки и настройки nginx через Ansible.

Плейбук `playbook-lab02.yml` выполняет на сервере из группы `webservers`:

- устанавливает пакет `nginx`;
- копирует `index.html` в `/var/www/html/index.html`;
- запускает nginx и включает автозапуск сервиса;
- выводит сообщение об успешном деплое.

## Структура плейбука

В начале плейбука указаны основные параметры запуска:

- `hosts: webservers` - группа серверов из `inventory.ini`;
- `remote_user: runner` - пользователь для подключения по SSH;
- `become: yes` - выполнение задач с правами sudo;
- `gather_facts: no` - отключение сбора фактов о сервере.

Далее в блоке `tasks` описаны задачи:

- `Install nginx` - установка пакета через модуль `apt`;
- `Copy index.html` - копирование HTML-файла на сервер;
- `Check if nginx is started and enabled` - запуск и включение сервиса nginx;
- `Print message` - вывод сообщения после выполнения.

Запуск:

```bash
ansible-playbook -i inventory.ini playbook-lab02.yml
```
