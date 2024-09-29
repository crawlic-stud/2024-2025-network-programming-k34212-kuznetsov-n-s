University: [ITMO University](https://itmo.ru/ru/)  
Faculty: [FICT](https://fict.itmo.ru)  
Course: [Network programming](https://github.com/itmo-ict-faculty/network-programming)  
Year: 2024/2025  
Group: K34212  
Author: Nikita Kuznetsov
Lab: Lab1  
Date of create: 27.09.2024  
Date of finished: 28.09.2024  

## Лабораторная работа №1 "Установка CHR и Ansible, настройка VPN"

## Описание 
Данная работа предусматривает обучение развертыванию виртуальных машин (VM) и системы контроля конфигураций Ansible а также организации собственных VPN серверов.

## Цель работы
Целью данной работы является развертывание виртуальной машины на базе платформы Microsoft Azure с установленной системой контроля конфигураций Ansible и установка CHR в VirtualBox

## Ход работы
По гайду от [Mikrotik](https://wiki.mikrotik.com/wiki/Manual:CHR_VirtualBox_installation) была установлена виртуальная машина на RouterOS в VirtualBox:

![image](https://github.com/user-attachments/assets/56208be9-fad4-4e97-9cee-f113c2fc160c)

Далее, был куплен сервер на хостинге VDSina для выполнения второй части работы:

![image](https://github.com/user-attachments/assets/8d6fc7ff-30be-4063-a7f5-96688cd975db)

На систему сервера был установлен python3 и Ansible:

![image](https://github.com/user-attachments/assets/5ca50693-24a4-421a-af10-8bd82ff6c24d)

Далее, был установлен Wireguard, созданы публичный и приватный ключ, а также файл конфигурации wg0.conf:

![image](https://github.com/user-attachments/assets/8c0ed7f7-a37d-49d3-bcbc-d28961d6430a)


После чего интерфейс был поднят с помощью команды `wg-quick up` и `systemctl start wg-quick@wg0.service`:

![image](https://github.com/user-attachments/assets/8ca248bd-1144-4a65-94db-37309ae64042)

![image](https://github.com/user-attachments/assets/c6e64de3-d0a4-47b0-afdf-57ad094319dc)


Далее, со стороны клиента в WinBox был настроен интерфейс Wireguard, в котором был указан приватный ключ и порт доступа от интерфейса:

![image](https://github.com/user-attachments/assets/c21cd687-b2ba-4e64-9c52-9175f6e80f2f)

![image](https://github.com/user-attachments/assets/0ee0685a-1400-40ef-add2-33cc20a2b0e9)

### Проверка работоспособности

- Пинг с клиента на сервер:

![image](https://github.com/user-attachments/assets/5edb7c9d-547d-4498-8953-058f1f7e0ec9)

- Доступ в интернет на клиенте:

![image](https://github.com/user-attachments/assets/d475919c-1eb4-4d71-bb8b-d291c74a1b22)


- Пинг с сервера на клиент:

![image](https://github.com/user-attachments/assets/fd51671c-8a90-4c7a-8569-fb5a3d014aea)

- Доступ в интернет на сервере:

![image](https://github.com/user-attachments/assets/dc5d453c-4004-46c9-b7ca-a0ef92a4d0dc)


## Вывод

В результате работы была развернута виртуальная машина для роутера Mikrotik, которая соединяется Wireguard VPN туннелем с удаленным сервером в облаке.
