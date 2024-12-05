Ponomarev sys-37
Домашнее задание к занятию «Что такое DevOps. СI/СD»
Задание 1
Что нужно сделать:
Установите себе jenkins по инструкции из лекции или любым другим способом из официальной документации. Использовать Docker в этом задании нежелательно.
Установите на машину с jenkins golang.
Используя свой аккаунт на GitHub, сделайте себе форк репозитория. В этом же репозитории находится дополнительный материал для выполнения ДЗ.
Создайте в jenkins Freestyle Project, подключите получившийся репозиторий к нему и произведите запуск тестов и сборку проекта go test . и docker build ..
В качестве ответа пришлите скриншоты с настройками проекта и результатами выполнения сборки.
![image](https://github.com/user-attachments/assets/5227f88b-933f-480e-bf33-22e63d0c1e96)
![image](https://github.com/user-attachments/assets/3918b680-0017-449a-83f5-b360279b4c54)
![image](https://github.com/user-attachments/assets/35ba89b1-fd85-4ce7-92d0-817d73f340c3)


Задание 2
Что нужно сделать:
Создайте новый проект pipeline.
Перепишите сборку из задания 1 на declarative в виде кода.
В качестве ответа пришлите скриншоты с настройками проекта и результатами выполнения сборки.
![image](https://github.com/user-attachments/assets/237d91db-da31-45ef-8a94-847a0069f3f5)
![image](https://github.com/user-attachments/assets/e81b1ca7-5735-4201-8da0-5d893eae3175)
![image](https://github.com/user-attachments/assets/59080b31-1c86-4773-9471-a2a8438884aa)

Задание 3
Что нужно сделать:
Установите на машину Nexus.
Создайте raw-hosted репозиторий.
Измените pipeline так, чтобы вместо Docker-образа собирался бинарный go-файл. Команду можно скопировать из Dockerfile.
Загрузите файл в репозиторий с помощью jenkins.
В качестве ответа пришлите скриншоты с настройками проекта и результатами выполнения сборки.

![image](https://github.com/user-attachments/assets/1cb4694b-f887-4206-88dc-0c51ee4be418)
![image](https://github.com/user-attachments/assets/5256407c-ae9f-4a1c-994f-27f9754aa5d4)
![image](https://github.com/user-attachments/assets/d305e308-1648-4076-9a84-9a670a630354)



