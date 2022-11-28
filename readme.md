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
➜  roles ansible-galaxy role init vector
- Role vector was created successfully
➜  roles ll
total 12K
drwxrwxr-x 10 pi pi 4,0K ноя 28 09:48 clickhouse
drwxrwxr-x  9 pi pi 4,0K ноя 28 09:48 lighthouse
drwxrwxr-x 10 pi pi 4,0K ноя 28 10:03 vector
```
	2. При помощи ansible-galaxy скачать себе эту роль.<br>
	3. Создать новый каталог с ролью при помощи ansible-galaxy role init vector-role.<br>
__________________________________________________
