# LDAP

## Задание

Задание

1. Установить FreeIPA;
2. Написать Ansible playbook для конфигурации клиента;
3. * Настроить аутентификацию по SSH-ключам;
4. ** Firewall должен быть включен на сервере и на клиенте.


## Выполнение ДЗ

Копируем файлы в каталог и запускаем Vagrantfile:

```shell
vagrant up
```

В результате выполнения ДЗ были написаны две ansible-роли, которые конфигурируют хост ipaserver в качестве FreeIPA сервера и вводят в домен otus.lab хост ipaclient, создают пользователя Ivan, которому разрешено логиниться на хосты в домене с помощью публичного ключа ssh. 

![image 1](https://github.com/IvanPrivalov/HW23/screens/1.png)

![image 2](https://github.com/IvanPrivalov/HW23/screens/2.png)

## Проверка аутентификации по SSH-ключу:

На локальном хосте из рабочего каталога, где лежит файл id_rsa_freeipa:

Логинимся на сервер:

```shell
[vagrant@ipaclient ~]$ ssh -i ./otus_lab_ssh_key ivan@ipaserver.otus.lab
Creating home directory for ivan.
[ivan@ipaserver ~]$ pwd
/home/ivan
[ivan@ipaserver ~]$ whoami
ivan
[ivan@ipaserver ~]$ 
```

## Проверка задания

1. Выполнить vagrant up.
2. Зайти в web-gui по адресу http://192.168.10.10/, логин для входа - admin, пароль - passw0rd!
3. Для проверки аутентификации по ключам выполнить vagrant ssh ipaclient, затем попробовать залогиниться на ipaserver (ключи лежат в домашней директории пользователя vagrant).







