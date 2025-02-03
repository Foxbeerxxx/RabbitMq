# Домашнее задание к занятию "`Очереди RabbitMQ`" - `Татаринцев Алексей`



### Задание 1 Установка RabbitMQ


1. ` Устанавливаю RabbitMQ на ВМ , 192.168.100.1`
```
sudo apt install rabbitmq-server
```
2. `Проверяем статус`
```
sudo systemctl status rabbitmq-server
```
![1](https://github.com/Foxbeerxxx/RabbitMq/blob/main/img/img1.png)`

3. `Включение плагина управления Management Plugin`

![2](https://github.com/Foxbeerxxx/RabbitMq/blob/main/img/img2.png)`

4. `Перезапускаем сервис`
5. `И стучимся на localhost`
```
http://localhost:15672
```

6. `Сервис отвечает пробую логиниться под guest`
![3](https://github.com/Foxbeerxxx/RabbitMq/blob/main/img/img3.png)`

![4](https://github.com/Foxbeerxxx/RabbitMq/blob/main/img/img4.png)`

7. `Чтобы зайти под своим пользователем, добавлю его, добавлю в админы и перезагружу сервис, проверяем`
```
sudo rabbitmqctl add_user alexey Cnews220

sudo rabbitmqctl set_user_tags alexey administrator
sudo rabbitmqctl set_permissions -p / alexey 
```
![5](https://github.com/Foxbeerxxx/RabbitMq/blob/main/img/img5.png)`


### Задание 2  Отправка и получение сообщений

1. `Устанавливаю недостающие компоненты для выполнения скрипта`
2. `Запускаю producer.ру`
![6](https://github.com/Foxbeerxxx/RabbitMq/blob/main/img/img6.png)`

3. `Запускаю скрипт  consumer.py`
![7](https://github.com/Foxbeerxxx/RabbitMq/blob/main/img/img7.png)`




---

### Задание 3 Подготовка HA кластера


1. `Устанавливаю на вторую VM - RabbitMQ - 192.168.100.5`
2. `Запускаю сервис`
![8](https://github.com/Foxbeerxxx/RabbitMq/blob/main/img/img8.png)`

3. `Правлю хост файл на двух ВМ`
![9](https://github.com/Foxbeerxxx/RabbitMq/blob/main/img/img9.png)`

4. `Создание кластера на rmq02`
```
sudo rabbitmqctl stop_app
sudo rabbitmqctl join_cluster rabbit@rmq01
sudo rabbitmqctl start_app

```
5. `Как итог нода создалась`

![10](https://github.com/Foxbeerxxx/RabbitMq/blob/main/img/img10.png)`

`Принцип работы понятен`
`Дайте материал с лекции  хочу для себя ( файлы для Docker Compose) - Владимир обещал оставить ссылку, хочу попробовать все поднять в докере`
`Вот эти`

![11](https://github.com/Foxbeerxxx/RabbitMq/blob/main/img/img11.png)`