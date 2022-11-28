# Домашнее задание к занятию "8.4 Работа с Roles"
## Подготовка к выполнению
_________________________________________________
1. Создайте два пустых публичных репозитория в любом своём проекте: vector-role и lighthouse-role. <br>
2. Добавьте публичную часть своего ключа к своему профилю в github.<br>
_________________________________________________
## Основная часть
_________________________________________________
Наша основная цель - разбить наш playbook на отдельные roles. Задача: сделать roles для clickhouse, vector и lighthouse и написать playbook для использования этих ролей. Ожидаемый результат: существуют три ваших репозитория: два с roles и один с playbook.<br>

	1. Создать в старой версии playbook файл requirements.yml и заполнить его следующим содержимым:
```
---
  - name: clickhouse 
    src: git@github.com:AlexeySetevoi/ansible-clickhouse.git
    scm: git
    version: "1.11.0"
```

	2. При помощи ansible-galaxy скачать себе эту роль.<br>
	3. Создать новый каталог с ролью при помощи ansible-galaxy role init vector-role.<br>
__________________________________________________
```
➜  roles ansible-galaxy role init vector
- Role vector was created successfully
➜  roles ll
total 12K
drwxrwxr-x 10 pi pi 4,0K ноя 28 09:48 clickhouse
drwxrwxr-x  9 pi pi 4,0K ноя 28 09:48 lighthouse
drwxrwxr-x 10 pi pi 4,0K ноя 28 10:03 vector
```
__________________________________________________
	4. На основе tasks из старого playbook заполните новую role. Разнесите переменные между vars и default.<br>

```
➜  vector git:(master) ✗ cat vars/main.yml 
vector_url: https://packages.timber.io/vector/{{ vector_version }}/vector-{{ vector_version }}-1.x86_64.rpm
vector_version: 0.21.1
```
```
➜  roles git:(master) ✗ cat vector/defaults/main.yml 
---
vector_config:
  sources:
    our_log:
      type: file
      ignore_older_secs: 600
      include:
        - /home/alex/logs/*.log
      read_from: beginning
  sinks:
    to_clickhouse:
      type: clickhouse
      inputs:
        - our_log
      database: custom
      endpoint: http://62.84.121.235
      table: my_table
      compression: gzip
      healthcheck: false
      skip_unknown_fields: true
```
__________________________________________________
